# Stage 2: Forge 1.20.1 Platform Foundation Migration

## Build System & Toolchain
- **Minecraft**: 1.20.1
- **Forge**: 47.4.10 (verified from official Forge maven)
- **ForgeGradle**: 6.0.+ (updated from 5.1.+ due to Gradle 8 compatibility)
- **Gradle Wrapper**: 8.1.1
- **Java Toolchain**: 17

## Dependencies (Updated to 1.20.1)
- **Curios**: `top.theillusivec4.curios:curios-forge:5.9.1+1.20.1` (verified from maven.theillusivec4.top)
- **Cloth Config**: `me.shedaniel.cloth:cloth-config-forge:11.1.118` (verified from maven.architectury.dev)
- **The One Probe**: Currently disabled in build (`compileOnly fg.deobf(...)` commented out) due to 404 in theillusivec4 maven. A proper Maven coordinate must be found or integrated locally later if necessary.

## Modifications Made
- `build.gradle`, `settings.gradle`, and `gradle-wrapper.properties` updated.
- Copied `mods.toml` to resources and adjusted dependency boundaries.
- Copied all extracted assets and data to `src/main/resources`.
- Copied public `ic2.api` and `ic2.core` directly to `src/main/java`.
- Iteratively fixed compilation errors in `ic2.api` reflecting Mojang and Forge API changes from 1.19.2 to 1.20.1:
  - Adjusted matrix mathematics for `ItemDisplayInfo` and `ProgressDisplayInfo` to use JOML instead of `com.mojang.math.Matrix4f`.
  - Adapted `Font` parameters for rendering (e.g. `DisplayMode.NORMAL`).
  - Adapted block registries logic for `RetextureEvent`.
  - Addressed `DamageSource` differences in `ICustomArmor` and `IC2DamageSource`.
  - Fixed Creative Tabs inputs in `SubItemInput`.
  - Fixed sign text color getter/setter in `PainterHelper`.
  - Adjusted Level accessor in `SimpleCanEffect`.
  - Fixed `IInput` ItemStack comparison for 1.20 (use `is` instead of `sameItem`).
  - Addressed `TeleporterTarget` registry reference changes (using `Registries.DIMENSION`).

## Status & Blockers
- **Build Status**: `ic2.api` compiles successfully. `ic2.core` is also imported, and while the API compiles, the heavy implementation files from `ic2.core` (machines, energy net) are currently in the source tree but may have hidden errors or unlinked implementations until `compileJava` starts compiling them properly.
- **Client/Server separation**: Still needs manual verification per-class during implementation rewrite (Stage 3).
- **Blockers for Stage 3**:
  1. The One Probe repository and dependency coordinate for 1.20.1 needs resolution.
  2. Implementations inside `ic2.core` (blocks, items, energy) will need a massive pass of remapping and signature changes to fully link to Forge 1.20.1 lifecycle and registries.
