<!-- SPDX-License-Identifier: AGPL-3.0-only -->
# RelaxTax

RelaxTax prepares a US federal income tax return on your own computer. It is written from the IRS forms and instructions themselves, and every number it uses traces back to a pinned IRS file and page.

The aim is to cover every IRS form an individual return can need, and to be ready for tax year 2027 returns, filed in 2028. It is not ready to file with yet.

## How it is built

RelaxTax downloads the official IRS forms and instructions and pins each file by its hash. Each line's calculation is written into a logic file that quotes the instruction text it comes from, page by page, and a check fails if a quote is not on its page. A second, independent transcription and three independent tax engines are compared against it. From that calculation RelaxTax works out the interview itself, so it asks only the questions the return needs and refuses a situation it does not handle rather than guessing. At the end it fills the official blank PDF.

W-2s can be typed in or added as a PDF, a scan or a photo. Photos and scans are read on your machine, and every value read from a document waits for you to confirm it.

## How it keeps your return private

RelaxTax is one program that serves its pages to your browser on 127.0.0.1 and nowhere else. Your answers are stored in one sealed file that only your SSH key opens. They are never written to a log or sent anywhere. The program reaches the network only when you press a button that downloads forms.

## Platforms

Linux is tested. Windows is tested under wine only. macOS builds, but nobody has run it yet.

## Building

It needs Go and, to fill PDFs, [nib](https://github.com/daniel-alexander4/nib) 2.25.1 or later.

    go build ./...
    go test ./...

`make test` runs the same tests offline. `docs/laws.md` lists every command and the few developer actions that use the network.

## License

AGPL-3.0-only. See `LICENSE`, and `THIRD-PARTY-NOTICES.md` for the parts that keep their own licences.
