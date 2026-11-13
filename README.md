<!-- SPDX-License-Identifier: AGPL-3.0-only -->
# RelaxTax

RelaxTax prepares a US federal income tax return on your own computer. It is written from the IRS forms and instructions themselves, and every number it uses traces back to a pinned IRS file and page.

It is not ready to file with. No return it has made has been filed, and it covers one narrow case so far.

## What it does today

- Form 1040 for tax year 2025, for a single filer whose income is W-2 wages.
- An interview built from the form's own calculation, so it asks only what the return needs and refuses a situation it does not handle rather than guessing.
- W-2s can be typed in or added as a PDF, a scan or a photo. Photos and scans are read on your machine. Every value read from a document waits for you to confirm it.
- It fills the official blank Form 1040 PDF, which it downloads from irs.gov only when you ask it to.

Oregon's Form OR-40 is planned after the federal forms.

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
