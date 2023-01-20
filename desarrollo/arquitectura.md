# Arquitectura

<img src="../.gitbook/assets/file.drawing.svg" alt="" class="gitbook-drawing">

## Frontend

El frontend usa [Druid](https://github.com/linebender/druid) para la GUI de Lapce. Druid es un marco de GUI enfocado en los datos. Y todo el estado y la lógica está en el sub crate `lapce-data`, por ejemplo: búferes de archivos, las pestañas del editor, cursores, etc. El árbol de widgets de la interfaz, el diseño y la lógica de renderizado está en el sub crate `lapce-ui`, incluyendo todo lo relacionado con la interfaz, por ejemplo: eventos del teclado y del mouse, menú contextuales, etc.&#x20;

## Proxy

El sub crate `lapce-proxy` es un intermediario entre el frontend, y el sistema de archivos, plugins y servidores lsp. Entonces Lapce se comunica con los archivos, plugins  y servidores lsp a traves del proxy. La razón de esto es proporcionar la capacidad para el desarrollo remoto. En el modo desarrollo remoto, el binario `lapce-proxy`  se ejecuta en la máquina remota, así que eso permite leer los archivos, ejecutar los plugins y servidores, en la máquina remota.

## Edición de archivos

Este es el flujo de un típico proceso de edición de archivos. Cuando abre un archivo en la GUI, `lapce-data` se comunica con `lapce-proxy` el cual lee el archivo del disco local y responde con el contenido de este. `lapce-data` almacena el contenido del archivo localmente. Cuando `lapce-ui` recibe un evento del teclado, modifica el contenido del archivo en `lapce-data`, y solo envía el cambio de esa edición a `lapce-proxy.` `lapce-proxy` recibe los cambios, y aplica los cambios localmente, lo cual sincroniza el contenido del archivo. Cuando guarda el archivo en la GUI,`lapce-data` envia la solicitud de guardado a `lapce-proxy`, y `lapce-proxy` guarda el archivo en el disco local.&#x20;
