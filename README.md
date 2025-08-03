# 🧩 Rubik’s Cube Solver – React-Only Visual Simulator

This project is a fully frontend-based Rubik’s Cube Solver built entirely using **React.js**. It visually simulates a 3D Rubik’s Cube, supports scramble and reset functions, and uses an optimal solving strategy—all within the browser, without any backend.

---

## 🚀 Features

- 🎯 **Optimal Move Solver**  
  Uses a custom implementation of a two-phase solving algorithm to find solutions within **20 moves or fewer**.

- 🧊 **3D Cube Visualizer (CSS + React)**  
  Dynamic cube UI built using HTML structure + CSS 3D transforms (no Three.js or WebGL).

- 🔁 **Interactive Controls**  
  - Scramble the cube  
  - Visualize step-by-step moves  
  - Replay/reset

- 🧠 **Custom Move Engine**  
  A custom logic engine simulates cube rotations and tracks state changes accurately.

- 📈 **Move Tracking & Logging**  
  - Tracks move history  
  - Displays number of moves required  
  - Shows current move message

---

## 📦 Tech Stack

| Technology     | Purpose                            |
|----------------|-------------------------------------|
| React.js       | UI & component logic                |
| HTML/CSS       | Cube structure & 3D animation       |
| useState/useEffect | State handling for cube faces & moves |
| JavaScript     | Move logic engine & state transitions |

---

## 🧠 Problem-Solving Approach

### 1. Cube State Modeling
- Cube represented as 6 face arrays (U, D, L, R, F, B), each with 9 stickers.
- State transitions tracked on every move.

### 2. Move Engine Logic
- Move functions simulate actual cube rotations (`U`, `R`, `F'`, etc.).
- Each move updates relevant facelets and adjacent edge/corner stickers.

### 3. Solving Algorithm
- Implemented a simplified version of **Kociemba’s Two-Phase Algorithm**.
- Phase 1: Brings cube to an intermediate, easier-to-solve state (edges/orientations).
- Phase 2: Solves permutation efficiently in ≤ 20 moves.

---

## 🧰 Data Structures Used

- **2D Arrays** → For representing each face
- **Queue** → For potential Phase-1 BFS (optional)
- **Objects** → Mapping move functions and color states
- **State Hooks** → React `useState` for tracking real-time UI

---

## 🎨 Visual Simulation

- No external 3D libraries used
- Entire 3D cube rendered via **CSS transform** + perspective
- Each cubelet (`piece`) and sticker (`element`) individually styled

---

## ⚡ Performance

- **Time Complexity:** ~O(b^d) where `b` is branching factor (18 moves), `d` is move depth (≤ 20)
- **Space Complexity:** Minimal (stored states only for current, next, and history)
- No memory-heavy pruning tables (since it's React-only)

---

## 📁 Project Structure

```bash
rubiks-cube-solver-react/
├── public/
├── src/
│   ├── components/
│   │   ├── Solver.jsx        # Main cube engine & visualizer
│   │   ├── CubeFace.jsx      # Face rendering
│   │   └── Controls.jsx      # Scramble / Solve / Replay
│   ├── styles/
│   │   └── cube.css          # 3D cube styling
│   ├── utils/
│   │   └── moveEngine.js     # Move logic functions
│   ├── App.jsx
│   └── index.js
├── README.md
└── package.json
