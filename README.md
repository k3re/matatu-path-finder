# 🚌 Intelligent Path Finder for Nairobi Matatu Routes

## 📌 Project Overview
This project applies AI search algorithms (BFS, DFS, and A*) to find optimal matatu routes in Nairobi. We modeled 20 major stops with real travel times and distances.

## 🎯 Key Features
- Models 20 matatu stops across Nairobi
- Implements BFS, DFS, and A* search algorithms
- Compares algorithm performance (nodes expanded, runtime, path cost)
- Visualizes routes on a map
- Interactive route finder

## 📊 Results
| Algorithm | Travel Time | Nodes Expanded | Optimal? |
|-----------|-------------|----------------|---------|
| BFS | 50 min | 1 | ❌ No |
| DFS | 40 min | 255 | ✅ Yes |
| A* | 40 min | 9 | ✅ Yes |

**A* found the optimal route with 96% fewer nodes than DFS!**


### Run in Google Colab:
[![Open In Colab](https://colab.research.google.com/github/k3re/matatu-path-finder/blob/main/notebooks/matatu_pathfinder.ipynb)
### Run Locally:
```bash
git clone https://github.com/YOUR_USERNAME/matatu-path-finder.git
cd matatu-path-finder
pip install -r requirements.txt
python src/main.py
