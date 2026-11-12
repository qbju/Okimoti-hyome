# Okimoti-hyome

A client-side XCompact experiment: Japanese phrase-dictionary substitution → Zstandard → Base8192.

## Run

Open `index.html` through a static web server (GitHub Pages works). The first encode/decode loads `@bokuweb/zstd-wasm@0.0.27` from jsDelivr.

## Design notes

- Dictionary substitution is a reversible pre-processing stage with an embedded phrase table. This prototype does **not** use a trained Zstandard dictionary file.
- Zstandard compression is performed in-browser using WebAssembly.
- Base8192 maps 13-bit values to 8,192 Unicode code points selected from Unicode letter/number/punctuation/symbol categories.
- The alphabet is generated from the browser's Unicode property database. Unicode-version differences can change the alphabet; this is a prototype limitation and must be fixed with a checked-in immutable code-point table before relying on cross-device interchange.
- The X-weight counter is approximate. It is not an official X character counter and does not guarantee that a post will be accepted.
- The app does not upload the input text. The Zstd module is fetched from jsDelivr.

## License

The application code in this repository is provided under the MIT License unless otherwise noted. The Zstd WebAssembly dependency retains its own license.
