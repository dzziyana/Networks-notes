#AI-generated 
A DNS record that provides the IP of a domain’s name server to avoid circular lookups.

| **Why needed** | When the NS is part of the same domain it serves. |
| -------------- | ------------------------------------------------- |
### Glue Records in Action

1. **Delegation from `ch` to `ethz.ch` DNS Servers**:
    - The `ch` TLD server has an **NS record** for `ethz.ch`, stating that `ns1.ethz.ch` is responsible for it.
    - Example NS record:
        
        `ethz.ch   NS   ns1.ethz.ch`
        
2. **Potential Problem Without Glue Records**:
    
    - If `ns1.ethz.ch` is responsible for resolving `ethz.ch`, but its own IP isn’t known, there’s a circular dependency:
        - To resolve `ns1.ethz.ch`, you’d first need to resolve `ethz.ch`...
        - But `ethz.ch` is only resolvable through `ns1.ethz.ch`! 😵
3. **Solution: Glue Records**:
    
    - The `ch` TLD **also provides an A record** for `ns1.ethz.ch`, which directly includes its IP address.
    - Example **glue record**:
        
        `ns1.ethz.ch   A   212.212.212.1`
        
    - This is **attached to the response from the TLD server**, allowing resolvers to immediately contact `ns1.ethz.ch` without needing to first resolve `ethz.ch`.

---

### **Why This Matters?**

- Glue records **break circular dependencies** by ensuring that DNS resolvers can immediately find the authoritative name server’s IP.
- Without glue records, DNS resolution could enter an infinite loop where a domain’s resolution depends on itself.