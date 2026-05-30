# 🚦 AI-Based Traffic Signal Optimization System

## 1. Project Overview

| Aspect | Description |
|--------|-------------|
| **Problem** | Fixed traffic lights cause congestion and long waiting times |
| **Solution** | AI system dynamically adjusts green light durations based on real-time vehicle counts |
| **Intersection** | 4-way (SC1-North, SC2-South, SC3-East, SC4-West) |
| **Cycle Time** | 120 seconds (total of all 4 signals) |

---

## 2. AI Techniques Used

| # | Technique | Application |
|---|-----------|-------------|
| 1 | State Space Representation | Modeling traffic as (vehicle_count, waiting_time, emergency) |
| 2 | Constraint Satisfaction Problem (CSP) | Enforcing traffic rules (min/max green, cycle sum) |
| 3 | Backtracking Search | Exploring timing combinations systematically |
| 4 | MRV Heuristic | Selecting road with highest urgency first |
| 5 | Forward Checking | Pruning invalid solutions early |
| 6 | Bayesian Inference | Predicting congestion and accident risks |
| 7 | Utility Function | Scoring and selecting optimal schedule |

---

## 3. Input Parameters

| Parameter | Type | Range | Description |
|-----------|------|-------|-------------|
| sc1 | int | 0-200 | Vehicles on North Road |
| sc2 | int | 0-200 | Vehicles on South Road |
| sc3 | int | 0-200 | Vehicles on East Road |
| sc4 | int | 0-200 | Vehicles on West Road |
| emergency_sc1 | bool | True/False | Emergency vehicle on North Road |
| emergency_sc2 | bool | True/False | Emergency vehicle on South Road |
| emergency_sc3 | bool | True/False | Emergency vehicle on East Road |
| emergency_sc4 | bool | True/False | Emergency vehicle on West Road |

---

## 4. Constraints Enforced (CSP)

| # | Constraint | Value | Purpose |
|---|------------|-------|---------|
| 1 | Minimum green time | ≥ 10 seconds | Allow minimum traffic flow |
| 2 | Maximum green time | ≤ 60 seconds | Prevent starvation of other roads |
| 3 | Total cycle time | = 120 seconds | Fixed cycle duration |
| 4 | Opposite roads balance | Difference ≤ 40 seconds | Fairness between opposite directions |
| 5 | Emergency priority | ≥ 30 seconds | Emergency vehicle gets extended green |

---

## 5. Output Format

| Road | Code | Output | Unit |
|------|------|--------|------|
| North Road | SC1 | 35 | seconds |
| South Road | SC2 | 25 | seconds |
| East Road | SC3 | 45 | seconds |
| West Road | SC4 | 15 | seconds |
| **Total** | - | **120** | seconds |

---

## 6. Code Structure

| # | Class/Module | Responsibility |
|---|--------------|----------------|
| 1 | `RoadData` | Stores individual road status (vehicles, emergency, wait time) |
| 2 | `TrafficIntersection` | Manages 4-way intersection and cycle parameters |
| 3 | `TrafficConstraints` | Defines and validates all CSP rules |
| 4 | `TrafficHeuristics` | Calculates priority scores and initial guesses |
| 5 | `BacktrackingSearch` | Performs search with MRV and forward checking |
| 6 | `BayesianPredictor` | Predicts congestion/accident probabilities |
| 7 | `TrafficOptimizer` | Main orchestrator combining all modules |

---

## 7. Performance Metrics

| Metric | Value | Description |
|--------|-------|-------------|
| Cycle Duration | 120 seconds | Time for all 4 signals to complete |
| Min Green Time | 10 seconds | Lowest any road can receive |
| Max Green Time | 60 seconds | Highest any road can receive |
| Search Depth Limit | 20 levels | Maximum recursion depth |
| Emergency Multiplier | 3× | Emergency vehicles get triple urgency score |
| Solution Attempts | Variable | Number of combinations tried (print during run) |

---

## 8. Usage Modes

| # | Mode | Description |
|---|------|-------------|
| 1 | Demo Scenario 1 | Normal traffic (35, 28, 42, 15 vehicles) |
| 2 | Demo Scenario 2 | Emergency vehicle on East Road (40, 25, 55, 10) |
| 3 | Demo Scenario 3 | Rush hour with emergency (75, 68, 82, 55) |
| 4 | Interactive Mode | User enters custom vehicle counts |
| 5 | Exit | Terminates program |

---

## 9. Quick Start

| Step | Command/Action |
|------|----------------|
| 1 | `git clone https://github.com/yourusername/traffic-signal-optimization.git` |
| 2 | `cd traffic-signal-optimization` |
| 3 | `python traffic_optimizer.py` |
| 4 | Select mode (1/2/3) |
| 5 | Input vehicle counts when prompted |

### Python Code Example

| # | Code |
|---|------|
| 1 | `from traffic_optimizer import TrafficOptimizer` |
| 2 | `optimizer = TrafficOptimizer()` |
| 3 | `result = optimizer.process_traffic_data(sc1=45, sc2=30, sc3=60, sc4=20, emergency_sc3=True)` |
| 4 | `print(result)` |

---

## 10. Sample Output

| Component | Output |
|-----------|--------|
| North Road | 35 seconds (████████████████░░░░░░░░░░░░░░) |
| South Road | 25 seconds (████████████░░░░░░░░░░░░░░░░░░) |
| East Road | 45 seconds (██████████████████████░░░░░░░░) 🚨 |
| West Road | 15 seconds (███████░░░░░░░░░░░░░░░░░░░░░░░) |
| Total | 120 seconds ✅ |
| Status | All constraints satisfied |
| Reasoning | East Road: Emergency - extended to 45s; North Road: Heavy traffic - 35s |

---

## 11. Future Enhancements

| # | Enhancement | Description |
|---|-------------|-------------|
| 1 | IoT Integration | Connect to physical vehicle sensors |
| 2 | Reinforcement Learning | Adaptive learning from historical patterns |
| 3 | Computer Vision | Camera-based vehicle counting |
| 4 | Multi-intersection | Coordinate multiple junctions (green wave) |
| 5 | Mobile App | Push notifications to drivers |
| 6 | REST API | External system integration |

---

## 12. Course Outcomes Mapping

| CO | Topic | Implementation |
|----|-------|----------------|
| CO1 | State Space Representation | `RoadData`, `TrafficIntersection` classes |
| CO2 | Search Algorithms | `BacktrackingSearch` with DFS |
| CO3 | CSP & Constraints | `TrafficConstraints` with min/max/cycle rules |
| CO4 | Utility Functions | `_evaluate_solution()` scoring method |
| CO5 | Bayesian Inference | `BayesianPredictor` with Bayes' theorem |
| CO6 | Decision Making | `TrafficOptimizer` orchestrating all modules |

---

## 13. License & Contact

| Item | Information |
|------|-------------|
| License | MIT License |
| Course | Computational Foundations for AI (CFAI) |
| Repository | `https://github.com/yourusername/traffic-signal-optimization` |

---

⭐ Star this repository if you find it useful!
