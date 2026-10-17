# mac-bin-static
Static command-line binaries for macOS

## rsync for macOS

[![build](https://github.com/gening/mac-bin-static/actions/workflows/build.yml/badge.svg)](https://github.com/gening/mac-bin-static/actions/workflows/build.yml)

Self-contained rsync binaries for macOS, built on GitHub Actions. No Homebrew or MacPorts required.

- Depends only on macOS system libraries under `/usr/lib` (see list below)
- xxHash statically linked (`xxh3` / `xxh128` checksums available)
- Built without OpenSSL, zstd, lz4, IDN
- Intel: macOS 10.13+ · Apple Silicon: macOS 11+

<!-- AUTO-START -->
**Latest build:** rsync 3.5.1 (xxHash 0.8.3), 2026-10-17

| Download | Target | SHA256 |
|---|---|---|
| [rsync-macos-x86_64](https://github.com/gening/mac-bin-static/releases/latest/download/rsync-macos-x86_64) | x86_64 | `1c9c58f525e0db74b33c55f7a6b0a1a90b102a7286d73cf5108971251141023b` |
| [rsync-macos-arm64](https://github.com/gening/mac-bin-static/releases/latest/download/rsync-macos-arm64) | arm64 | `ee0d4b548fa7ef2334f91e9f9520ed41f2747f16b9ea8c62a6e4428a8294bce7` |
| [rsync-macos-universal](https://github.com/gening/mac-bin-static/releases/latest/download/rsync-macos-universal) | universal | `521999102c58c753553562e75954b39a580d5922a396ab79fbba7cc5e2b21bf3` |

Dynamic dependencies:
```
dist/rsync-3.5.1-macos-universal (architecture x86_64):
	/usr/lib/libiconv.2.dylib (compatibility version 7.0.0, current version 7.0.0)
	/usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1351.0.0)
	/usr/lib/libcharset.1.dylib (compatibility version 1.0.0, current version 1.0.0)
dist/rsync-3.5.1-macos-universal (architecture arm64):
	/usr/lib/libiconv.2.dylib (compatibility version 7.0.0, current version 7.0.0)
	/usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1351.0.0)
	/usr/lib/libcharset.1.dylib (compatibility version 1.0.0, current version 1.0.0)
```
<!-- AUTO-END -->

### Install

```bash
curl -LO https://github.com/gening/mac-bin-static/releases/latest/download/rsync-macos-arm64   # or x86_64 / universal
chmod +x rsync-macos-arm64
xattr -d com.apple.quarantine rsync-macos-arm64 2>/dev/null
./rsync-macos-arm64 --version
```

### Verify

```bash
shasum -a 256 rsync-macos-arm64     # compare with the table above
otool -L rsync-macos-arm64          # only /usr/lib/... entries
```

All versions: see [Releases](https://github.com/gening/mac-bin-static/releases).
