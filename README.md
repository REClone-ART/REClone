# 🎮 REClone – Reverse-Engineering Capcom's RE Engine

**REClone** is an open-source, metadata-driven reimplementation of Capcom’s proprietary RE Engine (used in Resident Evil, Devil May Cry, Monster Hunter, etc). Our goal is to reverse-engineer the engine’s architecture and rebuild a minimal, working clone using reflection-based serialization (RSZ), ECS, Lua scripting, and asset pipelines.

> 🧠 Powered by reverse-engineered data, modding tools, and REFramework introspection.

---

## 🚧 Project Status

This is an early-stage **research + prototyping** project. Contributions are welcome.

- ✅ RSZ Deserializer prototype (WIP)
- ✅ ECS core structure
- ⬜ RSZ → Prefab instancing
- ⬜ Lua scripting API
- ⬜ Asset (.mesh, .mdf2) loaders
- ⬜ Timeline / animation research
- ⬜ Scene / camera system

---

## 🧱 Architecture Overview

```mermaid
graph TD
    A[RSZ Type System] --> B[ECS Core]
    B --> C[Prefab Loader]
    B --> D[Lua Scripting]
    D --> E[Asset Interface]
