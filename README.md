# 🚑 Rural Healthcare: Routing & Dispatch Engine

## 📌 Project Overview
A high-fidelity, real-time routing and allocation engine designed to solve the Rural Healthcare Doctor, Ambulance & Medicine Routing Problem. Built for the CodeRush sprint, this Single Page Application (SPA) simulates concurrent emergency requests, optimal hospital selection, and dynamic fleet dispatching without the need for a heavy backend server.

## 🚀 Live Simulation
**Live Web Demo:** [https://preeminent-valkyrie-4faf08.netlify.app](https://preeminent-valkyrie-4faf08.netlify.app)

## 🧠 Algorithmic Architecture (60% Weight: Correctness + Efficiency)
The core engine is implemented entirely in raw JavaScript for maximum performance natively in the browser.

*   **Custom MinPriorityQueue:** Built from scratch using an array-backed binary min-heap to guarantee $O(\log n)$ insertion and extraction. *Strictly avoids lazy sorting loops.*
*   **Routing Core (Dijkstra's Algorithm):** Achieves $O((V + E) \log V)$ time complexity for finding the shortest path across the generated 500-node graph.
*   **Composite Cost Function:** Routing isn't just about physical distance. It evaluates feasibility via: `Total Cost = Travel Time + Wait Time Penalty`. *(Penalties are mathematically applied when hospital beds drop below the critical threshold).*

## 🛡️ Edge Cases & Resilience (10% Weight)
The simulation strictly manages resource exhaustion and failure states:
*   **Specialist Fallback:** Automatically skips the nearest hospital if the required specialist (e.g., Cardiology) is absent, routing to the next feasible center.
*   **Zero-Resource Handling:** If a hospital's beds or medicine hit 0, it is strictly marked as unfeasible. The request dynamically reroutes.
*   **Fleet Exhaustion:** If all 10 ambulances are currently dispatched, the system traps the request and throws a `QUEUED_NO_AMBULANCE` status to the decision log.

## 💻 UI & Functional Implementation (25% Weight)
*   **Interactive Telemetry:** Integrated with Leaflet.js to render nodes, hospitals, and ambulances on a dark-theme CartoDB map.
*   **Live Path Generation:** Animated glowing cyan polylines track the exact Dijkstra-calculated route dynamically.
*   **Resource Dashboard:** Real-time GSAP-animated progress bars bound to the hospital's mutable bed and medicine states.
*   **Decision Log:** A transparent algorithmic terminal that prints the exact rationale behind why a route was chosen or rejected step-by-step.

## ⚙️ Tech Stack
*   **Core Logic:** Vanilla JavaScript (ES6)
*   **UI/UX:** HTML5, Tailwind CSS (via CDN)
*   **Animations & Maps:** GSAP, Leaflet.js

---
### 👨‍💻 Author
**Raj Dutta**
B.Tech CSE (IoT) | Thakur College of Engineering and Technology, Mumbai
