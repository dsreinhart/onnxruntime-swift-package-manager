# Why this repository exists

This is a mirror of [`microsoft/onnxruntime-swift-package-manager`][upstream],
which **returned 404 on 25 November 2026** along with `microsoft/onnxruntime`
and `microsoft/onnxruntime-genai`. GitHub redirects renamed repositories and
these do not redirect, so they were deleted or made private rather than moved.

The binaries broke separately. The manifest fetched them from
`https://download.onnxruntime.ai/`, which is a CNAME to
`onnxruntimepackages.azureedge.net` — a certificate covering only
`*.azureedge.net`, so TLS fails for the custom name, and ignoring TLS the files
are 404 anyway. `azureedge.net` is the retired Azure CDN.

ONNX Runtime is MIT licensed (see `LICENSE`), which permits redistribution.
Nothing here is my work and no credit for it is claimed.

## What is in it

`main` and every upstream tag are pushed **exactly as fetched**, so this is a
faithful archive. Tag `1.24.2` is upstream commit
`b7fb7f7dea8a2469e6335d95a61b8f36d0dc83b2`.

Branch `aloudly-mirror` and tag `1.24.2-aloudly.1` add **one commit**, which
changes **only the two `binaryTarget` URLs** in `Package.swift` to point at a
release here.

## The archives are the originals

The two pod archives attached to the `1.24.2-aloudly.1` release were recovered
from a SwiftPM artifact cache, and their SHA256 digests match the checksums
Microsoft had already written into `Package.swift`:

| archive | SHA256 |
|---|---|
| `pod-archive-onnxruntime-c-1.24.2.zip` | `f7100a992d2a8135168c8afd831e6a58b465349101982aa58b3e11d36e600b54` |
| `pod-archive-onnxruntime-extensions-c-0.13.0.zip` | `346522d1171d4c99cb0908fa8e4e9330a4a6aad39cd83ce36eb654437b33e6b5` |

Because they match, the `checksum:` lines in `Package.swift` are untouched —
SwiftPM verifies these downloads against Microsoft's own published digests, not
against anything asserted here. Verify for yourself with `shasum -a 256`.

[upstream]: https://github.com/microsoft/onnxruntime-swift-package-manager
