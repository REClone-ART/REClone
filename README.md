# 🧬 REClone: Reverse-Engineering the RE Engine

> A community-driven effort to analyze, document, and replicate the core systems of Capcom’s RE Engine — from RSZ serialization to ECS, Lua scripting, and scene composition.

---

## 📌 What is REClone?

**REClone** is a reverse-engineering initiative and prototype framework inspired by the architecture of Capcom's RE Engine. Our goal is to build a modular, open-source clone of the RE Engine's runtime systems for education, tooling, and experimentation.

---

## 🧠 Core Concept: RSZ Reflection is the Heart

RE Engine is a **metadata-driven architecture** built on RSZ (Reflection Serialization). Every object, component, and asset is defined and processed via RSZ metadata types. Understanding and replicating RSZ is the cornerstone of this project.

---

## 🧱 Architecture Overview

```mermaid
graph TD
    A[RSZ Type System]
    B[ECS Core]
    C[Prefab Loader]
    D[Lua Scripting]
    E[Asset Interface]

    A --> B
    B --> C
    B --> D
    D --> E
````

---

## 🔬 Reverse Engineering Plan

### Phase 1: Foundational Research

#### ✅ RSZ Serialization

* Dump all RSZ types via REFramework:

  ```lua
  for name, type in pairs(re.manager:get_types()) do
      log.info(string.format("%s (Size: 0x%X)", name, type:get_size()))
  end
  ```
* Use `RszTool`, `.natives` dumps, and 010 Editor templates to analyze `.scn`, `.pfb`, `.mesh`, `.mdf2` formats.

#### ✅ Subsystem Mapping

| Subsystem   | Hook Target          | Tools                     |
| ----------- | -------------------- | ------------------------- |
| Entity Init | `Entity.create()`    | REFramework, Cheat Engine |
| File Access | `FileSystem.open()`  | RETool, ProcMon           |
| Lua         | `LuaState.execute()` | REFramework Lua Hooks     |

---

### Phase 2: RECloneCore Prototype

#### ✳️ Type System Kernel

```cpp
class RSZType {
public:
    std::string name;
    uint32_t size;
    std::map<std::string, uint16_t> fields;
};
std::vector<RSZType> g_typeDB;
```

#### ✳️ Entity-Component System (ECS)

```cpp
class Entity {
    std::vector<std::shared_ptr<Component>> components;
    void add_component(uint32_t type_id);
};
```

#### ✳️ Asset Loading

* Parse `.mesh`, `.mdf2`, `.tex` using custom tools or convert via Noesis plugins.

#### ✳️ Lua Scripting

```lua
function Entity:update()
    if self:get("Transform").position.y < 0 then
        self:destroy()
    end
end
```

---

### Phase 3: Tool-Driven Validation

| Goal               | Tool                      | Validation         |
| ------------------ | ------------------------- | ------------------ |
| RSZ Field Accuracy | RszTool, REFramework      | > 95% field match  |
| Scene Load         | `.pfb` preview in REClone | Correct transforms |
| Lua Behavior       | Script tests              | Pathfinding & AI   |

---

## 🚀 Getting Started

### Prerequisites

* C++17 compiler
* LuaJIT or Sol2
* Python 3.10+ (for tooling)
* Noesis (for asset inspection)
* REFramework installed on RE Engine game

### Build Instructions (Coming Soon)

---

## 🛠️ Tools We Use

| Tool                                                                   | Purpose                                  |
| ---------------------------------------------------------------------- | ---------------------------------------- |
| [REFramework](https://github.com/praydog/REFramework)                  | Live RE Engine type dump + Lua injection |
| [RszTool](https://github.com/some-reverse-rsz-tool)                    | Static RSZ and `.natives` analysis       |
| [010 Editor + Templates](https://github.com/Wunkolo/RE-010-Templates)  | Reverse file formats                     |
| [Fluffy Manager 5000](https://github.com/fluffyquack/FluffyModManager) | Mod deployment and asset packing         |
| [RE-BHVT-Editor](https://github.com/AlphaZDev/RE-BHVT-Editor)          | Behavior tree visualization              |

---

## 🧩 Contribution Roadmap

### ✅ Milestone 1: Bootstrapped RSZ Loader

* [ ] Parse RSZ header and type IDs
* [ ] Match types to `.natives` info
* [ ] Load single `.pfb` prefab

### 🚧 Milestone 2: Minimal Scene

* [ ] Import `.mesh`
* [ ] Load one material (`.mdf2`)
* [ ] Display via any 3D API (OpenGL/Vulkan)

### 🧪 Milestone 3: Lua Live Scripting

* [ ] Update loop
* [ ] Basic physics triggers
* [ ] AI behavior trees

---

## 💬 Community & Collaboration

We’re actively looking for:

* Reverse engineers
* C++/Lua developers
* Technical artists (shader/material knowledge)
* File format researchers

### 📣 Join us on Discord (Coming Soon)

* Share findings
* Test patches
* Collaborate on scene ports

---

## 💡 Insight to Remember

> "**RSZ is the Rosetta Stone of RE Engine.** Crack the metadata, and the entire runtime unfolds."

---

## 📝 License

This is a reverse-engineering educational research project and is not affiliated with or endorsed by Capcom. All assets and code shared are intended for research purposes only.

```

---
