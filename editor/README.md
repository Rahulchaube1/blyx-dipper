# Blyx Dipper

Parse quoted CSV records, preserve embedded line breaks, and validate a row width before consuming a file.

This extension includes the Blyx Dipper 0.1.0 source, a runnable example and completions for its public functions. It uses the Blyx Language extension for syntax highlighting and execution.

## Run in the editor

1. Open an empty file named `dipper-demo.blyx`.
2. Type `blyx-dipper-demo` and select **Dipper — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
1
2
0
```

## Use Dipper in a project

Extract the starter into a new folder. It contains `main.blyx`, the licensed framework source in `vendor/dipper`, and a VS Code task. With the Blyx 0.2.1 compiler and host toolchain installed, run `blyxc native-run main.blyx` from that folder. Type `blyx-dipper-` in a Blyx file to see the framework completions. [Download the starter ZIP](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-dipper-starter-0.1.0.zip)

[API and input requirements](https://www.blyx-lang.space/packages/dipper) · [Framework source](https://github.com/Rahulchaube1/blyx-dipper/tree/bd945ed8a3151e302073a37ac3b3c64aa1c1b8f5) · [Report an issue](https://github.com/Rahulchaube1/blyx-dipper/issues)

[GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) · [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube)
