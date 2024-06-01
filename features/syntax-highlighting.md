# Syntax highlighting

Language support such as tokenizing and highlighting is provided by [Tree Sitter][tree-sitter-website]. Each language requires a Tree Sitter grammar to have tokenization and queries to provide additional features such as syntax highlighting.

## Grammars

To learn more about queries, see [Creating Parsers][tree-sitter-parsers].

Lapce has select few (Rust, JSON, TOML) grammars built-in for convenience. All other languages need to provide an externally loadable grammar in a form of shared library. Lapce will update all supported grammars by default on start-up.

Grammars are stored in `$LOCAL_DATA_DIR/grammars` directory. Each grammar should be named `${DLL_PREFIX}tree-sitter-${NAME}.${DLL_SUFFIX}` where `${NAME}` refers to language name and `${DLL_PREFIX}`/`${DLL_SUFFIX}` refer to OS defined constants for shared libraries (see [`DLL_PREFIX`][rust-dll-prefix] and [`DLL_EXTENSION`][rust-dll-extension]).

Grammars are loaded in order:

  1. User provided grammar
  2. System provider grammar
  3. Built-in grammar

## Queries

To learn more about queries, see [Syntax Highlighting#Queries][tree-sitter-queries].

Queries are stored in `$SETTINGS_DIR/queries/$LANGUAGE`. Currently only `highlights.scm` are supported.

## Language

For Lapce to know how to deal with files, it's required to include a language definition which contains which filenames or extensions to match to language, what indent or comment type it uses and additional configuration (that depends on tree-sitter) such as code lens (unrelated to LSP code lens) or sticky headers tokens.

Languages are defined in [`lapce-core/src/language.rs`][lapce-core-language].

## Language Server Protocol

LSPs should define `DocumentSelector` via the extension API and/or through `volt.toml` extension manifest.
It can be otherwise defined through `language_id_from_path` in [`lapce-proxy/src/buffer.rs`][lapce-proxy-buffer].

[lapce-core-language]: https://github.com/lapce/lapce/blob/master/lapce-core/src/language.rs
[lapce-proxy-buffer]: https://github.com/lapce/lapce/blob/master/lapce-proxy/src/buffer.rs
[rust-dll-prefix]: https://doc.rust-lang.org/std/env/consts/constant.DLL_PREFIX.html
[rust-dll-extension]: https://doc.rust-lang.org/std/env/consts/constant.DLL_EXTENSION.html
[tree-sitter-website]: https://tree-sitter.github.io
[tree-sitter-parsers]: https://tree-sitter.github.io/tree-sitter/creating-parsers
[tree-sitter-queries]: https://tree-sitter.github.io/tree-sitter/syntax-highlighting#queries
