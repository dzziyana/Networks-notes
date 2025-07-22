#AI-generated *(mostly)*
# Distance-vector
**Each router shares its routing table** (i.e., the "vector" of distances to all known destinations) with its **directly connected neighbors** at regular intervals.
## 🔧 **How it Works:**

- Each router maintains a table:  
    **Destination → Distance (cost) + Next Hop**
    
- Routers periodically send their **entire routing table** to neighbors.
    
- Upon receiving a neighbor's table, a router:
    - Adds 1 (or link cost) to each entry.
    - Updates its table if it finds a shorter path via that neighbor (Bellman-Ford algorithm).
    
- Routes **converge gradually** through repeated updates.
---
### 📉 **Key Features:**

| Feature           | Description                           |
| ----------------- | ------------------------------------- |
| Algorithm         | Bellman-Ford                          |
| Update Type       | Periodic & triggered                  |
| Convergence Speed | Slower, especially in large networks  |
| Loop Prevention   | Basic (split horizon, poison reverse) |
| Complexity        | Simple and lightweight                |

---
### 🔁 **Problems with Distance Vector:**

- **Slow convergence**
    
- **Count-to-infinity** problem
    
- **Routing loops** possible without mitigation techniques
    
---
## Alternatives to Distance Vector Routing

#### 1. **Link-State Routing**
- **Example**: OSPF, IS-IS
- Each router:
    - Discovers its neighbors and link costs.
        
    - Floods **link-state advertisements (LSAs)** to all other routers.
        
    - Uses **Dijkstra's algorithm** to compute shortest paths.
        
- 🧠 **Global view of network**, faster convergence, more scalable.
- ❗ Requires more memory and CPU.
#### 2. **Path Vector Routing**
- **Example**: BGP 
    
- Like Distance Vector, but **includes entire path** (AS path) in advertisements.
    
- Prevents loops by **detecting path repetition**.
    
- Designed for **inter-domain routing** (between ISPs).
---
# Comparison

| Routing Type    | Example Protocol | Key Characteristic                        |
| --------------- | ---------------- | ----------------------------------------- |
| Distance Vector | RIP              | Periodic neighbor updates, simple         |
| Link-State      | OSPF             | Full network map, fast convergence        |
| Path Vector     | BGP              | Advertises paths, loop prevention for ASs |
| Hybrid          | EIGRP            | Combines DV simplicity with LS efficiency |
