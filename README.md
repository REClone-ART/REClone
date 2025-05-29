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

    RSZ Types define all entity/component structure

    ECS stores and executes game logic

    LuaJIT drives gameplay

    .pfb/.scn files are RSZ-serialized scene graphs

🛠 Tooling

We integrate with the RE modding ecosystem:
Tool	Purpose
REFramework	Live game type metadata introspection
RszTool	.natives & .msb parser
010 Editor	Binary format reverse-engineering
Fluffy Mod Manager	Asset pack management (for testing)
📁 Directory Structure

src/
├── core/        → ECS & type system
├── rsz/         → RSZ loader & serializer
├── scripting/   → Lua integration
├── assets/      → Mesh, textures, materials

🚀 Getting Started
Prerequisites

    C++17 or higher

    CMake 3.20+

    LuaJIT (or sol2)

    SDL2 / ImGui (for UI testing)

Build (Linux / Windows)

git clone https://github.com/YourUser/REClone.git
cd REClone
cmake -B build -DCMAKE_BUILD_TYPE=Debug
cmake --build build

👥 Contributing

We are actively looking for:

    Reverse engineers

    C++ developers

    Lua scripters

    3D asset engineers (Blender, Noesis)

    Technical documentation writers

Open a PR or issue to start collaborating. Join our Discord (coming soon!).
📄 License

MIT – Open to use, share, and improve. Attribution welcome.
🙏 Acknowledgments

    REFramework

    RszTool

    REEngine-Modding-Documentation

    Capcom for pushing technical boundaries in game engine design
