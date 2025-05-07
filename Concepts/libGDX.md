---
tags:
  - Java
  - LibGDX
---
libGDX is a **cross-platform game development framework** written in Java. It allows developers to write a game once and deploy it on multiple platforms, including **Windows, macOS, Linux, Android, iOS, and HTML5 (via WebGL).**

### **Key Features of libGDX**

1. **Cross-Platform** – Write your game once, run it on multiple platforms.
2. **Open-Source** – Free to use under the Apache 2.0 license.
3. **Lightweight** – Does not require a game engine; it's a framework providing tools to build games from scratch.
4. **Performance-Oriented** – Uses **LWJGL** (for desktop), **OpenGL ES** (for mobile), and **WebGL** (for HTML5).
5. **Modular Architecture** – Provides various modules for:
    - Graphics (2D & 3D)
    - Audio (Sound & Music)
    - Input Handling (Keyboard, Mouse, Touch)
    - Physics (Box2D integration)
    - Asset Management
    - Scene2D UI Toolkit
### **Key Features of libGDX**

1. **Cross-Platform** – Write your game once, run it on multiple platforms.
2. **Open-Source** – Free to use under the Apache 2.0 license.
3. **Lightweight** – Does not require a game engine; it's a framework providing tools to build games from scratch.
4. **Performance-Oriented** – Uses **LWJGL** (for desktop), **OpenGL ES** (for mobile), and **WebGL** (for HTML5).
5. **Modular Architecture** – Provides various modules for:
    - Graphics (2D & 3D)
    - Audio (Sound & Music)
    - Input Handling (Keyboard, Mouse, Touch)
    - Physics (Box2D integration)
    - Asset Management
    - Scene2D UI Toolkit
### **Why Use libGDX?**

- **Java-Based** – Ideal if you are comfortable with Java.
- **High Performance** – Close to native performance using OpenGL.
- **Great for 2D Games** – Provides a scene graph API (**Scene2D**).
- **Large Community & Documentation** – Strong support from developers.

### **How libGDX Works?**

libGDX uses a **shared codebase** approach:
1. Core logic is written in a shared `core` module.
2. Platform-specific backends (Desktop, Android, iOS, HTML5) handle platform-dependent tasks.
### **Typical libGDX Project Structure**

```
MyGame/
├── android/      (Android-specific code)
├── core/         (Main game logic)
├── desktop/      (Desktop launcher)
├── ios/          (iOS-specific code)
├── html/         (HTML5 launcher)
└── assets/       (Game assets: images, sounds, etc.)
```
### **Alternatives**

- Unity (C#)
- Godot (GDScript, C#)
- Unreal Engine (C++, Blueprints)
- Phaser.js (JavaScript for web games)