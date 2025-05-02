# 🚛 Route and Load Planner

A Python-based logistics optimization tool that combines **load planning** (packing items into vehicles) and **route planning** (solving the vehicle routing problem) to streamline delivery operations.

Built with:
- 🔧 Flask (backend logic)
- 📦 Google OR-Tools (optimization engine)
- 🗺️ OpenRouteService (real-world distances)
- 🧮 OpenCage (geocoding addresses)

---

## 📌 Features

| Feature | Description |
|--------|-------------|
| 📦 **Load Optimization** | Assigns items to vehicles based on weight and volume limits. |
| 🛣️ **Route Optimization** | Solves the routing problem using real-world distance matrices. |
| 📁 **CSV Upload Support** | Upload your own `items.csv` and `vehicles.csv`. |
| 🗺️ **Route Visualization** | Displays delivery routes on an interactive map. |
| 📤 **CSV Output** | Download results as CSV (vehicle assignments and route order). |

---

## 🔧 How It Works

1. **Upload** two CSV files:
   - `items.csv`: List of items with weight, volume, and address
   - `vehicles.csv`: List of vehicles with max weight and volume

2. **System Workflow**:
   - Geocode addresses → assign coordinates
   - Calculate road distances via OpenRouteService
   - Assign items to vehicles (based on constraints)
   - Optimize routes (Vehicle Routing Problem)
   - Display results on map and offer CSV download

---

## 📂 Example Input

### items.csv

| id | weight | volume | address                  |
|----|--------|--------|---------------------------|
| 1  | 10     | 0.3    | MG Road, Bangalore        |
| 2  | 5      | 0.1    | Koramangala, Bangalore    |
| 3  | 7      | 0.2    | Indiranagar, Bangalore    |

### vehicles.csv

| id  | max_weight | max_volume |
|-----|------------|------------|
| V1  | 100        | 10         |
| V2  | 80         | 8          |

---

## 📤 Example Output

### assigned_loads.csv

| vehicle_id | item_id | item_weight | item_volume |
|------------|---------|-------------|-------------|
| V1         | 1       | 10          | 0.3         |
| V1         | 2       | 5           | 0.1         |
| V2         | 3       | 7           | 0.2         |

### optimized_routes.csv

| vehicle_id | stop_order | address                |
|------------|------------|------------------------|
| V1         | 1          | MG Road, Bangalore     |
| V1         | 2          | Koramangala, Bangalore |
| V1         | 3          | (return to depot)      |

---

