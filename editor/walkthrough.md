## Trace the CSV parser through quoted fields

Parse a UTF-8 string in memory. Delimiters are commas. Records accept CRLF, LF or CR; embedded quoted newlines preserve their original bytes. Spaces are data. A malformed quote discards partial results. Empty input contains zero rows; a blank line holds one empty cell. di_bad_row applies a caller-supplied column count.

1. Open an empty file named `dipper-demo.blyx`.
2. Type `blyx-dipper-demo` and select **Dipper — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
1
2
0
```

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-dipper)
