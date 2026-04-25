---
layout: post
title: "Getting Started with Raylib in C++"
date: 2026-04-20 10:00:00 +0900
categories: [gamedev, cpp, raylib]
type: Tutorial
thumbnail: "/assets/images/blog/2026-04-20-getting-started-with-raylib/thumbnail.png"
excerpt: "A walkthrough of setting up a Raylib project in C++, from CMake configuration to drawing your very first window."
---

Raylib is a fantastic little library for prototyping 2D and 3D games without the ceremony of a full engine. In this tutorial we'll set up a fresh C++ project, link Raylib, and render our first window.

## Project layout

```
my-game/
├── CMakeLists.txt
└── src/
    └── main.cpp
```

## CMake configuration

```cmake
cmake_minimum_required(VERSION 3.20)
project(my_game CXX)

find_package(raylib CONFIG REQUIRED)
add_executable(my_game src/main.cpp)
target_link_libraries(my_game PRIVATE raylib)
```

## First window

```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 450, "Hello Raylib");
    SetTargetFPS(60);

    while (!WindowShouldClose()) {
        BeginDrawing();
            ClearBackground(RAYWHITE);
            DrawText("Hello, Waffle!", 280, 200, 20, DARKGRAY);
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

That's it — build, run, and you should see a small window with your first message rendered. From here you can iterate quickly into sprites, input handling and physics.
