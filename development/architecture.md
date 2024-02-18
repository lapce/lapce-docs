# Architecture

<img src="../.gitbook/assets/file.drawing.svg" alt="" class="gitbook-drawing">

## Frontend

The frontend uses [Floem](https://github.com/lapce/floem) for the GUI of Lapce.

## Proxy

The `lapce-proxy` sub crate provides the interface between the frontend, and the file system, plugins and [LSP](https://microsoft.github.io/language-server-protocol/) servers, so Lapce talks to files, plugins, LSP servers through the proxy. The reason for that is to provide the ability for remote development. In remote development mode, the `lapce-proxy` binary runs on the remote host, to provide seamless code editing, project management and language interaction .

## File Editing

Here is the flow of a typical file editing process. When you open a file in the GUI, `lapce-app` talks to `lapce-proxy` which reads the file from local disk and responds with the content of the file. `lapce-app` stores the file content locally. `lapce-proxy` receives the change, and applies the change locally which make the file content in sync. When you save the file in the GUI, `lapce-app` sends the file save request to `lapce-proxy`, and `lapce-proxy` saves the file to the local disk.
