Export policies define **which routes** an AS advertises to its BGP neighbors. These are largely based on the business relationship:

#### 1. **To Customers**

- Export **everything** (own routes, peers’ routes, providers’ routes).
	 Because the customer pays for transit.

#### 2. **To Peers**

- Export **only own routes** and **customer routes**.
- **Do NOT** export routes from other peers or providers.
- Goal: maintain fairness and avoid becoming a free transit provider.

#### 3. **To Providers**

- Export **only own routes** and **customer routes**.
- Do **not** export peer or other provider routes.
- You're usually paying for this transit, so no reason to offer it to others for free.