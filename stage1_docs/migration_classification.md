# Migration Classification

## 1. Transfer almost without changes
- Basic item and block properties
- Internal math logic (e.g. Energy calculation rules, packet stats)
- Most utilities and helper methods

## 2. Partial adaptation of imports, signatures or lifecycle
- Most Block and Item subclasses (Mojang mappings updates)
- Container / Menu Types
- Recipe serializers
- Capabilities logic

## 3. Significant overhaul for Forge 1.20.1
- DeferredRegister and Registry event handling
- Block Entities and NBT serialization methods
- GUI, Screen and Rendering hooks
- Network channels and packet structure

## 4. Almost complete reimplementation keeping external behavior
- Mixins that are sensitive to Minecraft internals
- Access Transformers might need rewriting depending on mapping changes
