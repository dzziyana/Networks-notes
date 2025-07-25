#AI-generated
### 📡 What Is a Hidden Terminal?

A **hidden terminal** is a device in a wireless network that:
- **Cannot "hear" another transmitting device** because it’s out of range (i.e. it's “hidden” from it).
- But **can interfere at a common receiver**, causing a **collision**.
---
### 🧠 Think of it Like This:

Imagine three wireless devices: **A**, **B**, and **C**.

- **A** can talk to **B**.
    
- **C** can also talk to **B**.
    
- But **A and C cannot hear each other**.
    

#### Example Scenario:

1. **A** wants to send to **B**, so it checks if the channel is free.
    
2. Since **A can't hear C**, it thinks the channel is free and sends data.
    
3. At the same time, **C** might also send data to **B**, thinking the channel is free too.
    
4. **B receives both transmissions at once → collision**.
    

This is the **hidden terminal problem**.

---

### 🎯 How [[Multiple Access Protocols#MACA (Mult. Access with collision avoidance)|MACA]] Helps

MACA solves this problem using **RTS/CTS (Request to Send / Clear to Send)** handshakes:

1. **A** sends an **RTS** to **B**.
    
2. **B** replies with a **CTS**.
    
3. Nearby nodes that **hear the CTS** (including C) know **not to send** during that time — even if they didn’t hear A’s RTS.
    
4. This helps **prevent C from transmitting**, avoiding a collision at B.
    

✅ **Benefit**: Even if **A and C** can’t hear each other, **C hears B’s CTS**, which warns it to stay silent.