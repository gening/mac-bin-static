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
_(filled in automatically by the workflow)_
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
