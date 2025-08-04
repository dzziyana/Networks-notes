The **Count to Infinity** problem is a well-known issue in **distance vector routing protocols**, such as **[[RIP]] (Routing Information Protocol)**. It occurs due to the way these protocols handle network topology changes, specifically link failures.

### **Problem Explanation**

**In [[Routing algorithms#Distance-vector|distance vector routing]] , each router periodically shares its routing table with its neighbors.** When a link fails, routers must update their routes. However, due to the way updates propagate, routers can end up with incorrect, inflated hop counts, leading to **slow convergence**.

### **Example Scenario**

1. Suppose we have three routers: **A**, **B**, and **C** in a line:
    - A ↔ B ↔ C
    - A can reach C via B with a cost of **2** (A → B → C).
        
2. If the **link between B and C fails**, B should ideally update its route to C as **unreachable**.
    
3. However, A still believes B has a route to C (from previous updates) and advertises that it can reach C with a cost of **2**.
    
4. B, upon receiving this advertisement from A, mistakenly thinks **A has a valid route to C** and updates its route with a cost of **3** (B → A → C).
    
5. In the next update cycle, A now learns about B’s new higher-cost route and increases its cost to **4**, and the process repeats.
    
6. This cycle continues, incrementing the hop count toward infinity (**hence "Count to Infinity"**) until the routers eventually recognize that C is truly unreachable.

# Solutions to the Problem

Several techniques are used to mitigate the Count to Infinity problem:

## Split Horizon
A router ==does not advertise== a route back to the neighbor from which it learned the route.
## Poison Reverse
A router ==explicitly advertises== a route back to the sender with an ==infinite metric== to prevent loops.
## Triggered Updates
Instead of waiting for periodic updates, a router immediately informs neighbors about a failure.
## Hold-Down Timers 
When a route becomes unreachable, the router waits for some time before accepting alternative routes.
## Setting a Maximum Hop Count
[[RIP]], for example, sets the maximum hop count to 16 to prevent indefinite looping.