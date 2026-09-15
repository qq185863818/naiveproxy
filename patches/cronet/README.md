# Patched Cronet for naiveproxy Chromium 150

This directory contains the Chromium-side Cronet modifications used by the
patched Linux x64 workflow.

The patch targets the Chromium revision recorded in `CHROMIUM_VERSION`:
`150.0.7871.63`. It is independent of the older Chromium 144 patches in the
cyCronet project.

Included functionality:

- custom TLS cipher-suite order, named groups, signature algorithms, ALPS
  codepoint selection, extension permutation, empty `trust_anchors`, and
  randomized GREASE signature algorithms;
- HTTP/HTTPS proxy credentials and SOCKS5 RFC 1929 authentication;
- Cronet certificate-verification bypass through `Cronet_EngineParams`;
- native Cronet WebSocket C API with callbacks, fragmented-message assembly,
  graceful cleanup, custom upgrade headers, and browser-like cache flags;
- duplicate Cookie header preservation and HTTP/2 Cookie/priority handling;
- preservation of a caller-supplied Referer header.

Apply from the naiveproxy repository root:

```bash
git apply patches/cronet/cronet-v150-cycronet-features.patch
```

The patch does not include Python/Rust bindings or existing local naiveproxy
source changes.
