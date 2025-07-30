# OSPF-Failover-with-Dual-Path-Redundancy

## 🚀 Purpose
This lab simulates OSPF failover using redundant links between three routers. It demonstrates dynamic path recalculation, route convergence, and protocol resilience during interface failures. It's built for network engineers and learners practicing fault tolerance and Layer 3 dynamic routing.

## 🖼️ Topology / Diagram
See `/assets/ospf-triangle-topology.png`.

- 3 Routers (2911): R1, R2, R3
- Dual links between each router:
  - **Gigabit links** (primary)
  - **Serial links** (backup)
- OSPF enabled on all interfaces

## ⚙️ How It Works
- **Input:** 3 routers with IP addressing, OSPF (area 0) enabled on all links.
- **Process:** OSPF forms adjacencies, calculates best paths (Gig links preferred). When a primary link fails, routing reconverges using the backup serial path.
- **Output:** Stable packet delivery continues via alternate paths after link failure.

## 🧪 Example Run
# Step-by-step in Packet Tracer:
1. Configure IPs and OSPF on R1, R2, R3
2. Verify reachability from R1 to R3
3. Shut down R1’s Gig0/2
```
```
Expected output:
- R1 reroutes traffic to R3 via Serial0/0/1
- OSPF updates routes dynamically
- No end-to-end traffic loss after convergence
```

## 🛠️ Setup Instructions
1. Launch Cisco Packet Tracer.
2. Build topology matching `/assets/ospf-triangle-topology.png`.
3. Assign IPs and enable OSPF on all interfaces.
4. Use `show ip route`, `show ip ospf neighbor` to verify.
5. Test failover by shutting down primary links.

## ⚠️ Error Handling / Edge Cases
- If routes don’t reconverge:
  - Check that OSPF is enabled on both interfaces.
  - Ensure matching Hello/Dead timers.
  - Validate no passive interfaces are blocking adjacencies.
- If serial backup is unused:
  - Manually adjust OSPF cost using `ip ospf cost`.

## 🔁 How to Extend
- Add PCs and ping across routers.
- Inject loopbacks and redistribute static routes.
- Simulate dual failures and measure downtime.
- Export routing table snapshots before/after failover.

## 🧾 Version History
- v1.0: Base triangle topology with OSPF failover
- v1.1: Enhanced with serial backup simulation and cost tuning

## 🧠 Author
John Felix  
GitHub: [https://github.com/Johnfednyfelix]  
LinkedIn: [https://www.linkedin.com/in/johnfelix/]
