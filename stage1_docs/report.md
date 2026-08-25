# Phase 1: Inventory and Decompilation
## Tools Used
- Vineflower 1.10.1
## Artifacts
- Original JAR: Original-Mod-IC2Classic-1.19.2-2.1.3.4.jar
- Original API ZIP: Original-Github-IC2Classic-1.19.x.zip
- Decompiled sources: `decompiled_jar/`

## General Mod Info
- **Mod ID**: ic2
- **Version**: 1.19.2-2.1.3.4 (from JAR)
- **Target MC**: 1.19.2
- **Forge Version**: [41,) (from mods.toml)

## Class and Resource Count
- Original JAR Classes: 2485
- Decompiled Java Files: 2016
- Resources are kept in `decompiled_jar/assets` and `decompiled_jar/data`

## Divergences Between API and JAR
- The JAR contains 2485 classes, whereas the API ZIP only contains 215 Java files.
- The JAR is the complete implementation of the mod and should be the primary reference source for behavior, while the API zip can be used to recover documentation and names for the API package (`ic2.api`).

## Critical Ambiguities and Risks
- Network Packets: Might have changed structure. Need to manually verify payload reading/writing.
- Rendering: Custom item/block renderers usually require complete rewrite in newer Forge versions.
- Client/Server Classloading: Needs to verify `@OnlyIn(Dist.CLIENT)` usage or split classes properly for the Forge 1.20.1 environment.

## Next Steps
1. Setup proper Forge 1.20.1 environment.
2. Adapt Core Mod files (`IC2`, registries).
3. Port Energy System.
4. Port Block & Items implementations.
