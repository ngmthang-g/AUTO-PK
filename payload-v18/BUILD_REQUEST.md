# v1.8 Windows build request

- Base source: `dist/ThanLongItemConsolidator-v1.7-source.zip`
- Base SHA-256: `6f73fbd081f8cddf833cde0900e5e5a55f7f7b96e70fe1c6b231e634c42d49be`
- Patch: `payload-v18/v1.8-stock-sell-drop.patch`
- Normalized patch SHA-256: `3cbe076618f90198e1300521aaa1e546c9e0bcd7f774ae7c58e66eb3124f209f`
- Required gate: Windows MSVC x64 build, 13 logic tests, v1.8 verifier and mutation self-test.
- Scope: replace only the T1 NPCShop resolver, add one manual Drop T1 button, and preserve every protected production function.
- Publish only new versioned v1.8 files; do not overwrite or delete old release files.
