# AUTO PK v0.6.2.0

Windows x64 build of ThanLongItemConsolidator with the new Auto PK tab.

## Build integrity

The repository stores the buildable source archive as ordered Base64 chunks under `payload/`. GitHub Actions reconstructs the archive and requires this exact SHA-256 before compiling:

`010794ffb509b50453878b13de3412376f305bfcfcf8a3414d1c1ea9f8edef18`

The Windows workflow then builds the EXE + bridge DLL, runs all logic tests including `auto_pk_logic_tests.exe`, and only after success publishes:

- `dist/ThanLongItemConsolidator-v0.6.2.0-win-x64.zip`
- `dist/ThanLongItemConsolidator-AutoPK-v0.6.2.0-source.zip`
- `dist/SHA256_v0.6.2.0.txt`

The runtime ZIP contains `ThanLongItemConsolidator_v0.6.2.0.exe` and `ThanLongCleanRouteBridge.dll`.
