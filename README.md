# herdr out-of-tree patched builds

Out-of-tree GitHub Actions builds of upstream [herdrdev/herdr](https://github.com/herdrdev/herdr): manually dispatch, pick an upstream tag, publish the patched static-musl binaries to Releases.

`patches/classic-16-color-sgr.patch` (mirroring the local NixOS module's patch) exists because herdr re-encodes every palette color as `38;5;N` (256-color form) when re-emitting SGR to the host terminal, and Windows Terminal's bold-as-bright only brightens classic 16-color SGR (30–37/90–97) — so bold text stayed normal color with bold font weight instead of becoming bright. The patch re-encodes palette indices 0–15 as classic 16-color SGR (foreground and background), letting the host terminal apply its own bold-is-bright policy.
