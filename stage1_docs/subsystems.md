# Subsystems Map

## Core
- Main Mod Entrypoint (`ic2.core.IC2`)
- Configuration (`ic2.core.utils.config.ic2.IC2Config`)
- Registries (`ic2.api.blocks.BlockRegistries`, `ic2.core.init.*`)

## Energy System (Detailed in energy_system.md)
- Interfaces: `IEnergyTile`, `IEnergySink`, `IEnergySource`, `IEnergyConductor`
- Core implementation: `ic2.core.energy.*`
- Storage: `IEnergyStorage`

## Blocks & Items
- Machines
- Generators
- Upgrades
- Tools
- Armor
- Cables

## Mod Compatibility & Integrations
- JEI
- The One Probe
- Curios API
- Cloth Config API

## Network
- Packets
- Data synchronization

## Rendering
- Client rendering
- GUI/Screens
