<img src="assets/logo.png" width="112" height="112" alt="A round brown dipper with a white breast leans towards a ripple.">

# Blyx Dipper

Parse quoted CSV records, preserve embedded line breaks, and validate a row width before consuming a file.

Splitting each line on commas changes both field contents and record counts when a field contains a quoted comma or newline. RFC 4180 describes the quoting and doubled-quote rules that the Dipper parser uses. [RFC 4180, Common Format and MIME Type for CSV Files](https://www.rfc-editor.org/rfc/rfc4180#section-2)

## Editor extension

Install **RahulChaube.blyx-dipper** to run the worked example and use the framework’s function completions in a Blyx file. Open an empty `.blyx` file, enter `blyx-dipper-demo`, then choose **Blyx: Run File**. [Editor downloads](https://www.blyx-lang.space/packages/dipper#editor) · [Download the extension](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-dipper-0.1.0.vsix) · [Starter with framework source](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-dipper-starter-0.1.0.zip)

## Install and run

Install the Blyx 0.2.1 compiler and a Rust toolchain with a host linker. Clone the versioned release, then run its small example and regression suite.

```sh
cargo install --locked --version 0.2.1 blyxc
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-dipper.git
cd blyx-dipper
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

Expected output from the small example

```text
1
2
0
```

## Import a two-column notes file

The importer preserves a literal quote in the first note and an embedded newline in the second. Give it a UTF-8 CSV file to check its width before reading the note column.

```sh
blyxc native-run project.blyx
```

Try an input file with `blyxc native-run project.blyx -- notes.csv`. The first row supplies the header.

Project output

```text
a comma, and a "quote"
two
lines
```

[Run the portable example in the browser](https://www.blyx-lang.space/play?example=package-dipper) · [Follow the handbook exercise](https://doc.blyx-lang.space/guide/dipper) · [Download the release](https://github.com/Rahulchaube1/blyx-dipper/releases/tag/v0.1.0)

## Use the framework in your own project

From the folder containing your entry file, clone the release into `vendor/dipper`.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-dipper.git vendor/dipper
```

```blyx
use vendor::dipper::dipper;

fn main() {
    // Tokens for a quoted field containing a comma followed by a second field.
    let shape = di_shape([2, 0, 1, 0, 2, 1, 0, 3]);
    println!(at(shape, 0));
    println!(at(shape, 1));
    println!(len(di_shape([2, 0])));
}
```

Run `blyxc native-run main.blyx`. For the complete native workflow also import `use vendor::dipper::csv;`.

Parse a UTF-8 string in memory. Delimiters are commas. Records accept CRLF, LF or CR; embedded quoted newlines preserve their original bytes. Spaces are data. A malformed quote discards partial results. Empty input contains zero rows; a blank line holds one empty cell. di_bad_row applies a caller-supplied column count.

| API | Behavior |
| --- | --- |
| `di_parse(input), di_ok(records)` | Import csv. Parse into F-prefixed field events and R end-of-row events. A lone E-prefixed event describes a syntax error. |
| `di_cell(records, row, column)` | Return one string for a present cell, including an empty cell; an absent cell returns an empty list. |
| `di_bad_row(records, width)` | Return the first zero-based row of the wrong width, −1 for success or −2 for a parse or argument error. |
| `di_transition(state, token), di_shape(tokens)` | Walk the portable quote state machine. A valid stream yields [rows, fields]. |

## Contribute

When opening an issue, include the smallest reproducing Blyx input, the compiler version and the output you expected. [Source and issues](https://github.com/Rahulchaube1/blyx-dipper/issues) · [Blyx community](https://www.blyx-lang.space/community)

Dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
