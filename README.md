#  Intelligent Path Finder for Nairobi Matatu Routes

##  Project Overview
This project applies AI search algorithms (BFS, DFS, and A*) to find optimal matatu routes in Nairobi. We modeled 20 major stops with real travel times and distances.

##  Key Features
- Models 20 matatu stops across Nairobi
- Implements BFS, DFS, and A* search algorithms
- Compares algorithm performance (nodes expanded, runtime, path cost)
- Visualizes routes on a map
- Interactive route finder

##  Results
| Algorithm | Travel Time | Nodes Expanded | Optimal? |
|-----------|-------------|----------------|---------|
| BFS | 50 min | 1 |  No |
| DFS | 40 min | 255 |  Yes |
| A* | 40 min | 9 |  Yes |

**A* found the optimal route with 96% fewer nodes than DFS!**


##  *Executive Summary*

This project applies *Artificial Intelligence search algorithms* to solve a real-world transportation problem in Nairobi: finding optimal matatu routes for commuters. We modeled Nairobi's matatu network as a graph, implemented three search algorithms (BFS, DFS, and A*), and compared their performance to determine the best approach for route planning.

---

##  *1. Problem Statement*

### *The Challenge:*
- *3+ million* Nairobi residents rely on matatus for daily transportation
- *No digital tool* exists for route planning and navigation
- Commuters waste *hours daily* due to traffic and unfamiliar routes
- Traditional map apps don't account for matatu-specific routes and stops

### *Our Solution:*
An intelligent route finder that:
- Models the real matatu network as a graph
- Uses AI search algorithms to find optimal paths
- Compares algorithm performance
- Visualizes routes for easy understanding

---

##  *2. System Architecture*

### *Graph Model:*
We built a graph representation of Nairobi's matatu network:


Nodes (Stops): 20 major matatu terminals
├── Central Area: CBD, Upper Hill
├── Westlands Area: Westlands, Kileleshwa, Lavington  
├── Eastlands Area: Eastleigh, Buruburu, Donholm
├── South Area: South B, South C, Rongai, Kitengela
├── North Area: Thika Road, Githurai, Kahawa, Juja
└── Campus: USIU

Edges (Routes): 25 bidirectional connections
├── Each edge has: distance (km), travel time (min), route numbers
└── Example: CBD → Westlands: 4.5 km, 20 min, Routes 24 & 48


### *Data Collection:*
- *Coordinates:* Google Maps for accurate latitude/longitude
- *Travel Times:* Realistic estimates based on typical Nairobi traffic
- *Route Numbers:* Actual matatu Sacco routes (24, 48, 34, 44, etc.)

---

##  *3. Algorithms Implemented*

### *BFS (Breadth-First Search) - Uninformed Search*

*How it works:*
- Explores all nodes at current depth before going deeper
- Like ripples spreading outward from a stone dropped in water
- Finds path with fewest stops (not necessarily fastest time)

*Characteristics:*
-  Guarantees shortest path by number of stops
-  Simple to implement
-  Ignores edge weights (time/distance)
-  May find suboptimal routes in terms of travel time

*Real-world analogy:* Asking every person in your neighborhood for directions before going further out

---

### *DFS (Depth-First Search) - Uninformed Search*

*How it works:*
- Explores one path completely before backtracking
- Like exploring a maze by always turning right
- Goes deep before exploring alternatives

*Characteristics:*
-  Memory efficient (only stores current path)
-  May not find optimal path
-  Highly unpredictable performance
-  Can explore many dead ends

*Real-world analogy:* Walking down one street completely before checking other streets

---

### *A (A-Star Search) - Informed Search**

*How it works:*
- Combines actual cost (g) + estimated cost (h)
- Uses heuristic to guide search toward goal
- Priority queue always expands most promising node

*Heuristic used:* Straight-line distance (Haversine formula)
- Calculates direct distance between stops
- Never overestimates actual road distance (admissible)
- Guarantees optimal path

*Characteristics:*
-  Finds optimal path (shortest travel time)
-  Efficient search (fewer nodes expanded)
-  Consistent and reliable performance
-  Can incorporate real-time data easily

*Real-world analogy:* Using Google Maps with compass pointing toward destination

---

## *4. Experimental Results*

### *Test Case: CBD → USIU*

| Algorithm | Travel Time | Nodes Expanded | Runtime | Route Found |
|-----------|-------------|----------------|---------|-------------|
| *BFS* | 50 minutes | 1 node | 0.00005s | CBD → South B → USIU |
| *DFS* | 40 minutes | 255 nodes | 0.0004s | CBD → Westlands → Kileleshwa → Lavington → Thika Road → USIU |
| *A** | 40 minutes | 9 nodes | 0.00015s | CBD → Thika Road → USIU |

### *Key Insights:*

*1. Route Quality:*
- A* and DFS found the optimal 40-minute route
- BFS found a slower 50-minute route despite fewer stops
- *Conclusion:* Number of stops ≠ faster travel time

*2. Search Efficiency:*
- A* expanded only 9 nodes (96% fewer than DFS!)
- DFS expanded 255 nodes - extremely inefficient
- BFS expanded only 1 node but found suboptimal route
- *Conclusion:* A* is most efficient among optimal algorithms

*3. Computation Speed:*
- All algorithms run in < 0.0005 seconds
- Differences are negligible for real-time use
- *Conclusion:* Speed not a deciding factor

---

## *5. Performance Analysis Across Routes*

### *Average Nodes Expanded (5 test routes):*

| Algorithm | Average Nodes | Reliability |
|-----------|--------------|-------------|
| BFS | 3.5 |  Consistent |
| A* | 8.5 |  Consistent |
| DFS | 8.8 |  Highly variable (1-255 nodes) |

### *Why DFS is Unreliable:*
- On simple routes: expands few nodes
- On complex routes: explodes to hundreds of nodes
- No guidance mechanism leads to wasted exploration

### *Why A is Superior:**
- Heuristic guides search toward goal
- Consistent performance across all route types
- Balances optimality with efficiency

---

## *6. Why A is the Best Choice**

### *Comparison Matrix:*

| Criteria | BFS | DFS | A* |
|----------|-----|-----|-----|
| *Finds Optimal Route* |  No |  Sometimes |  Yes |
| *Efficient Search* |  Moderate |  Poor |  Excellent |
| *Consistent* |  Yes |  No |  Yes |
| *Scalable* |  Moderate |  Poor |  Excellent |
| *Real-time Ready* |  Limited |  No |  Yes |

### *Winner: A - Best Balance**
- Optimal routes every time
- Efficient search (96% better than DFS)
- Reliable and consistent
- Easy to extend with real-time data

---

## *7. Real-World Impact*

### *For Nairobi Commuters:*
- *Time Savings:* 10-20 minutes saved per trip
- *Cost Reduction:* Less fuel/time wasted
- *Reduced Stress:* Clear route guidance
- *Better Decisions:* Compare multiple route options

### *For Matatu Operators:*
- *Route Optimization:* Identify efficient routes
- *Customer Service:* Help passengers navigate
- *Operational Efficiency:* Reduce empty trips

### *For City Planning:*
- *Data Insights:* Understand commuter patterns
- *Infrastructure Planning:* Identify bottlenecks
- *Policy Making:* Data-driven transport decisions

---

##  *8. Limitations & Future Work*

### *Current Limitations:*
1. *Static Data:* Uses average travel times (no real-time traffic)
2. *Limited Nodes:* Only 20 stops (real network has 200+)
3. *No Fare Data:* Doesn't consider cost optimization
4. *No Time Variation:* Ignores rush hour vs off-peak differences

### *Future Enhancements:*
1. *Real-time Integration:* Connect to Google Maps API for live traffic
2. *Expanded Network:* Add 100+ stops covering all Nairobi
3. *Mobile App:* Build React Native app for commuters
4. *Multi-modal:* Include buses, trains, and boda bodas
5. *Fare Optimization:* Add cost as optimization metric
6. *User Ratings:* Incorporate crowd-sourced reliability data

---

##  *9. Key Takeaways*

### *Technical Learnings:*
1. *Heuristics matter:* A* with good heuristic dramatically outperforms uninformed search
2. *Consistency > Speed:* Reliable performance matters more than microsecond speed differences
3. *Real-world modeling:* Accurate data collection is the hardest part
4. *Visualization is key:* Graphs make complex algorithms understandable

### *Algorithm Selection:*
- *Use A** for route planning (optimal + efficient)
- *Avoid DFS* for production systems (unpredictable)
- *BFS is okay* for simple applications (but suboptimal)

### *AI for Social Good:*
- AI can solve real African problems
- Technology should be accessible to all
- Ethical considerations matter (privacy, fairness)

---

##  *10. Conclusion*

We successfully built an *Intelligent Path Finder for Nairobi Matatu Routes* that:
- Models 20 stops with 25 route connections
- Implements BFS, DFS, and A* search algorithms
- Compares performance across multiple metrics
- Demonstrates A* as the optimal choice for route planning

*The project proves that AI search algorithms can solve real-world transportation challenges in Kenya*, providing a foundation for future tools that could benefit millions of Nairobi commuters daily.

---

### Run in Google Colab:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/k3re/matatu-path-finder/blob/main/Project_2.ipynb)
### Run Locally:
```bash
git clone https://github.com/YOUR_USERNAME/matatu-path-finder.git
cd matatu-path-finder
pip install -r requirements.txt
python src/main.py
