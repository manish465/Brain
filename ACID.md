---
tags:
  - Database
---
ACID (Atomicity, Consistency, Isolation, Durability) ensures reliable database transactions, making them secure and fault-tolerant.

1. **Atomicity** (All or Nothing)
    - A transaction is either **fully completed** or **fully rolled back** if it fails.
    - Example: If money is deducted from one account but not added to another in a transfer, the entire transaction is rolled back.
2. **Consistency** (Valid State)
    - The database moves from **one valid state to another** while enforcing all rules (constraints, triggers, etc.).
    - Example: If a bank transfer violates an account’s minimum balance rule, the transaction is rejected.
3. **Isolation** (Concurrent Transactions)
    - Transactions **execute independently**, preventing dirty reads, lost updates, or inconsistent data.
    - Example: If two people try to book the last seat in a flight, only one succeeds.
4. **Durability** (Permanent Changes)
    - Once a transaction is **committed**, it is permanently saved, even if the system crashes.
    - Example: After confirming a hotel booking, the reservation persists even after a power failure.
### **Why ACID Matters?**
- Ensures **data integrity** and **reliability** in databases.
- Prevents **corruption** due to system crashes or concurrent operations.
- Essential for **banking, e-commerce, and transactional systems**.