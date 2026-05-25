# R4X Robot - Interactive Profile Page

An immersive, highly interactive 3D portfolio and profile experience featuring a custom-rendered procedural robot, fluid dynamics simulation, and dynamic layout transitions.

**[✨ Live Demo Link](https://blitz-003.github.io/portfolio/)**

---

## 🚀 Overview

This project pushes the boundaries of creative front-end engineering by blending real-time 3D web graphics with fluid dynamics. It replaces static profile layouts with an active canvas where a procedurally modeled 3D robot reacts to user interactions and seamless interface transitions.

### Key Features

- **Procedural 3D Modeling:** Fully built using primitive geometries and hierarchical structures in Three.js—no heavy external 3D models required.
- **Real-Time Fluid Simulation:** An interactive Navier-Stokes grid-based fluid simulation overlaid onto the canvas, responding to mouse movements with colorful dye propagation.
- **Dynamic Layout Mechanics:** A multi-stage responsive transition sequence that expands content banners dynamically based on the 3D robot’s viewport screen coordinates.
- **Interactive UI/UX:** Modern, glassmorphic UI overlay with functional tabs, skill bars, and navigation links.

---

## 🛠️ Tech Stack & Concepts

The project is built entirely on core web web standards and high-performance graphics frameworks:

- **HTML5 & CSS3:** Structural layout and responsive interface featuring modern styling, glassmorphism (`backdrop-filter`), and customized interactive UI controls.
- **JavaScript (ES6+):** Application logic, layout stage state machine, and interaction handling.
- **Three.js:** Handles the 3D scene creation, camera configurations, lighting setups, and real-time mesh rendering loop.
- **Fluid Dynamics Shaders & Math:** Implements grid-based velocity and density steps (`vel_step`, `den_step`) mapping mathematical physical properties straight onto a 2D interactive canvas overlay.
- **FontAwesome:** Lightweight vector iconography for social, profile, and navigation elements.

---

## 🧠 Technical Highlights

### 1. Hierarchical 3D Animation

The R4X Robot is engineered programmatically via mathematical structures in Three.js. It features hierarchical node structures where components like arms, legs, and antennas are children of a core root mesh. This allows localized math calculations for movements, such as a smooth sinus-wave floating animation.

### 2. Viewport-Bounded Dynamic Scaling

To prevent UI overlap, the interface utilizes a real-time boundary calculation sequence:

```javascript
// Vector anchor placed precisely at the right boundary edge of the robot mesh
const meshRightEdgeVector = new THREE.Vector3(BODY_R * 1.05, BODY_HALF_H, 0);
robotRoot.localToWorld(meshRightEdgeVector);
meshRightEdgeVector.project(camera);

// Convert device coordinates to viewport width percent values
const screenRightEdgePercent = (meshRightEdgeVector.x * 0.5 + 0.5) * 100;
const dynamicCalculatedWidth = 100 - screenRightEdgePercent;
```
