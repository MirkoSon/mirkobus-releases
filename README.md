# MirkoBus releases

This repository is the **distribution channel** for MirkoBus release artifacts. It holds no source code.

Every release contains exactly:

| Asset | Purpose |
|---|---|
| `mirkobus-control-room_<version>_x64-setup.exe` | Per-user Windows installer |
| `mirkobus-control-room_<version>_x64-setup.exe.sig` | minisign signature of the installer |
| `latest.json` | Update manifest read by the MirkoBus updater, including the build identity |
| `mirkobus-v<version>-release-manifest.json` | Build identity and per-file hashes of the installed payload |
| `checksums.txt` | SHA-256 of every asset |

## Trust

This repository is transport only:
- **The installer** is authenticated by its minisign signature. The MirkoBus updater checks it against the public
  key compiled into MirkoBus, and rejects an installer that does not verify.
- **After an update**, MirkoBus verifies that the installed release is exactly the build announced in `latest.json`
  and that every running component runs it.
- **No GitHub artifact attestation exists** for these artifacts.

Releases here are never edited or replaced.
