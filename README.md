# Question-Driven Design (QDD): A Development Methodology

## Overview

**Question-Driven Design (QDD)** is a pragmatic software design and development methodology centered on structured inquiry. It emphasizes building software by continuously asking meaningful "how" questions, attaching measurable goals (typically in the form of tests or observable behaviors), and implementing only the code necessary to satisfy those goals.

---

## QDD Manifesto (Inspired by the Agile Manifesto)

We are uncovering better ways to design and build software by asking questions and delivering answers. Through this work we have come to value:

- **Questions with clear intent** over abstract requirements  
- **Concrete goals and measurable outcomes** over broad specifications  
- **Working answers (via tests or visual output)** over architectural speculation  
- **Incremental clarity through inquiry** over full plans upfront

> That is, while there is value in planning, specification, and abstraction, we value purposeful questioning and actionable answers more.

---

## Core Principles

1. **Start with a concrete question**  
2. _Example:_ _"How do we open a game window?"_
3. **Define the desired outcome**  
4. Often expressed as a test or verification condition.  
5. _Example:_ _"The window should be 800x600 pixels with a title 'Snake Game'."_
6. **Implement the minimum code to fulfill the outcome**  
7. Code must satisfy the previously stated condition only — no more, no less.  
8. **Repeat for the next smallest unit of behavior**  
9. _Example:_ _"How do we draw the snake head?"_, _"How do we handle arrow key input?"_
10. **Document each step with question → goal → solution**  
11. This creates an auditable trail of reasoning behind each implementation decision.

---

## Comparison with Other Methodologies

| Aspect              | QDD                          | TDD             | BDD                               |
|---------------------|------------------------------|------------------|------------------------------------|
| **Primary Driver**  | Meaningful engineering question | Failing test     | Natural-language behavior spec     |
| **Code follows**    | Question + Goal              | Test             | Behavior scenario                 |
| **Suitable for**    | Architecture & feature design | Low-level unit logic | Customer-facing requirements  |
| **Outcome clarity** | High (focused on purpose)    | High             | High                              |
| **Documentation**   | Q&A chains                   | Test suites      | Gherkin / stories                 |

---

## Example: Snake Game (Step-by-Step in QDD)

1. **Question:** How do we open a game window?  
2. **Goal:** Window opens with 800x600 resolution titled "Snake Game".  
3. **Test:** Window appears and remains open.  
4. **Code:** Use `SDL_CreateWindow(...)`

---

1. **Question:** How do we display the snake's head?  
2. **Goal:** Draw a green square at (x, y).  
3. **Test:** Green block appears on screen.  
4. **Code:** Use SDL drawing commands.

---

1. **Question:** How do we move the snake with arrow keys?  
2. **Goal:** Arrow keys change direction.  
3. **Test:** Head changes direction on input.  
4. **Code:** Capture keyboard input and update direction vector.

... and so on.

---

## Using QDD to Design a 3D Game Engine

### Step-by-Step QDD Process:

1. **Question:** How do we create a window that supports 3D rendering?  
2. **Goal:** A visible window with OpenGL or DirectX/Vulkan context.  
3. **Test:** Window appears and `glClear()` or equivalent clears the color buffer.  
4. **Code:** Platform abstraction + context initialization.

---

1. **Question:** How do we define a 3D object in memory?  
2. **Goal:** Create a data structure that holds mesh data.  
3. **Test:** Can upload vertices to GPU and draw a triangle.  
4. **Code:** Implement `Mesh`, `VertexBuffer`, and `ShaderProgram` classes.

---

1. **Question:** How do we apply transformations (position, rotation, scale)?  
2. **Goal:** Draw a mesh at different positions.  
3. **Test:** Object appears in a different location when transform is changed.  
4. **Code:** Add `Transform` component with matrix math.

---

1. **Question:** How do we move the camera?  
2. **Goal:** Camera can pan and orbit using mouse input.  
3. **Test:** Scene view changes with input.  
4. **Code:** Implement `Camera` class and `InputHandler`.

---

1. **Question:** How do we manage a scene with many objects?  
2. **Goal:** Create a structure to manage multiple entities.  
3. **Test:** Can render and update dozens of objects.  
4. **Code:** Implement `SceneGraph` or ECS (Entity-Component-System).

---

1. **Question:** How do we load assets from files?  
2. **Goal:** Import models, textures, shaders (e.g., `.obj`).  
3. **Test:** External model appears in scene.  
4. **Code:** Add file I/O and resource manager.

---

1. **Question:** How do we render with lighting and materials?  
2. **Goal:** Scene has basic shading.  
3. **Test:** Object is lit based on position and material.  
4. **Code:** Add lighting calculations in shaders and material data structures.

... and so on, until the engine reaches desired capabilities.

---

## Benefits

- Forces clarity of intent at every step  
- Naturally modular and testable design  
- Scalable from low-level logic to high-level architecture  
- Builds a well-documented reasoning chain for decisions  

---

## When to Use

- Solo or small team development  
- Projects with exploratory or incremental goals  
- Game development, experimental systems, or UI-first applications  

---

## Relevance and Justification

QDD is not a competitor to other practices like TDD or BDD, but rather a layer above.  
It focuses on _why_ and _how_ we design features before diving into tests or stories. It is:

- Simple, but powerful — especially for individual developers or small teams where overengineering is a risk.  
- Lightweight — minimal overhead compared to heavyweight architectures.  
- Highly relevant for game development, UI tools, 3D engines, R&D, and AI projects.  
- Ideal for uncertainty — where the architecture emerges through experimentation.  
- Complementary to other methods — integrates well with TDD (once you define the question, write the test), BDD (can translate questions to behaviors), and DDD (can inform strategic domain choices).

> In contexts where formal architecture is too heavy, QDD offers just enough structure to maintain momentum, documentation, and design integrity.

---

## Summary

**Question-Driven Design (QDD)** emphasizes progress through inquiry.  
Each code addition must:

- Answer a specific question  
- Fulfill a defined goal  
- Prove itself via a test or visible result  

This method supports both **disciplined engineering** and **creative exploration**, making it particularly effective for iterative, modular projects, including complex systems like 3D engines.

It is **lightweight**, **scalable**, and deeply aligned with the mindset of builders who **learn by doing — one question at a time**.

---