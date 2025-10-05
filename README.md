## **Project Vihaan: A Whitepaper**

**A Living Currency for a Living World**

### **Abstract**

Project Vihaan introduces a cryptocurrency engineered to function as a practical, high-performance medium of exchange. It directly solves the critical issues of transaction fees, speed, scalability, and price volatility that have prevented the widespread adoption of digital currencies.

Vihaan's foundation is a **block-lattice** architecture. This data structure enables asynchronous, near-instantaneous, and completely **feeless** transactions. To prevent spam, the protocol uses a dynamic Proof of Work system as a rate-limiter, which is imperceptible to normal users but makes malicious abuse computationally expensive.

The network is secured by a two-node system: **Guardian Nodes** that validate transactions and **Sovereign Wallets** that grant users exclusive control over their funds. Consensus is achieved through an incentivized **Delegated Proof of Stake (DPoS)** system. Guardians must stake a significant quantity of Vihaan Coin (VHC), which is subject to **slashing** for malicious behavior. In return for securing the network, Guardians are rewarded via a fixed **1% annual inflation**, distributed daily based on their voting weight.

To achieve its primary goal of price stability, Vihaan detaches user-driven currency issuance from network security rewards. New coins can be created on-demand by any user through an open **Calibrated Proof of Work (Cal-PoW)** system. This process anchors the currency's value to the real-world cost of electricity, ensuring the currency remains stable and resistant to speculative volatility.

---

### **1. Introduction**

#### **1.1 The Unfulfilled Promise of Cryptocurrency**

The original vision for cryptocurrency was a peer-to-peer electronic cash system. Today, most digital assets are too slow, expensive, and volatile for practical commerce, functioning instead as speculative vehicles.

#### **1.2 The Vihaan Solution: A Living Currency**

Vihaan (a Sanskrit word for "dawn") is engineered to be **a living currency for a living world**. This philosophy guides its design, which is focused on unwavering principles:

1.  **Instant & Feeless:** Transactions must be fast and free.
2.  **Economically Secure:** The network must be protected by clear and robust economic incentives for honest participation and penalties for malicious acts.
3.  **Inherently Stable:** The currency's value must be anchored to a real-world metric to give users and merchants the confidence to transact.

---

### **2. The Vihaan Architecture: A Foundational Leap**

#### **2.1 The Block-Lattice Ledger**

Vihaan employs a **block-lattice**, a Directed Acyclic Graph (DAG) structure where every user has their own personal blockchain ("account-chain"). A transaction consists of a `send` block on the sender's chain and a `receive` block on the receiver's chain. These are processed asynchronously, enabling near-instantaneous and **feeless** transactions at scale.

#### **2.2 The Two-Node System**

*   **Guardian Nodes (Validators):** The security backbone of the network.
*   **Sovereign Wallets (User Nodes):** Lightweight wallets that give users complete control over their funds.

#### **2.3 Spam & Ledger Bloat Resistance**

To prevent a malicious actor from bloating the ledger with limitless, zero-cost transactions, Vihaan implements two layers of defense:

*   **Dynamic Proof of Work (dPoW):** Every transaction requires a tiny, trivial amount of computational work, calculated locally on the user's device in a fraction of a second. If a user attempts to send transactions at an abnormally high rate, the difficulty of this PoW increases for them automatically. This acts as a powerful rate-limiter, making large-scale spam attacks computationally expensive and impractical, while remaining completely unnoticeable to normal users.
*   **Ledger Pruning (Future Implementation):** To manage long-term ledger size, nodes will eventually have the option to prune old account-chains that have reached a zero balance. This allows the network to maintain a lean and efficient history without sacrificing security.

---

### **3. Consensus & Security: Incentivized DPoS**

Vihaan uses a Delegated Proof of Stake system with direct economic incentives and penalties to ensure robust network integrity.

#### **3.1 The DPoS Mechanism**

Users delegate the voting weight of their VHC to Guardian Nodes. A Guardian's influence in consensus is proportional to the total VHC delegated to it. When a conflicting transaction is detected, a weighted vote among Guardians determines the canonical transaction with near-instant finality.

#### **3.2 Becoming a Guardian: Staking & Slashing**

To be eligible to participate in consensus, a user must register their node and lock up a significant quantity of VHC as a security deposit.

*   **Minimum Stake Requirement:** The minimum stake required to register a Guardian node is fixed at **1,000,000 VHC**.
*   **Stake Lock-up Period:** Once staked, these funds are locked for a minimum of **30 days** after a Guardian voluntarily unregisters, preventing short-term attacks.
*   **Slashing Conditions:**
    *   **Major Offense (Malicious Vote):** **100%** of the stake is slashed for definitively malicious acts like voting for conflicting transactions (double-spending).
    *   **Minor Offense (Excessive Downtime):** **5%** of the stake is slashed if a Guardian node's uptime falls below **95%** over a rolling **30-day** period.

#### **3.3 Guardian Incentives: Protocol Inflation**

In return for securing the network, Guardians are rewarded via a predictable, fixed **1% annual protocol inflation**. The new coins from this inflation are created by the protocol and distributed daily to all active and honest Guardian nodes.

*   **Reward Distribution Mechanics:** The daily reward pool (approximately **0.002721%** of the total supply) is distributed to Guardians proportional to their total delegated voting weight.

---

### **4. Currency Issuance & Price Stability: The Economic Core**

Separate from the protocol inflation used for security, Vihaan's value is stabilized by an open issuance mechanism available to all users.

#### **4.1 On-Demand Issuance: Calibrated Proof of Work (Cal-PoW)**

Any user can mint a fixed amount of **1 VHC** by solving a Calibrated Proof of Work puzzle. This is not a competitive race but a standardized process with a predictable cost.

#### **4.2 The Puzzle: The Memory-Hard Latency Loop**

The puzzle is **memory-hard**, designed to be bottlenecked by the speed of commodity RAM to ensure fair access and prevent ASIC-driven centralization.

*   **Technical Specifications:** The puzzle requires a fixed RAM allocation of **2 GB** and involves a sequential chain of **2^28** (approx. 268 million) random-access memory reads. The goal is to anchor the minting cost to approximately **₹1 (approx. $0.012 USD)** worth of electricity.

#### **4.3 The Price Anchor Effect**

This on-demand issuance creates a powerful economic equilibrium.

*   **Price Ceiling:** If VHC's market price rises above the energy cost to mint it, users will mint new coins, increasing supply and putting **downward pressure** on the price.
*   **Price Floor:** If VHC's market price falls below the cost to mint it, minting halts. Market demand then puts **upward pressure** on the price.

---

### **5. Tokenomics & Initial Distribution**

#### **5.1 Token Details**

*   **Name:** Vihaan Coin
*   **Ticker:** VHC

#### **5.2 Supply Model**

Vihaan has a dynamic supply with a dual-issuance model and no hard cap:

1.  **Primary Issuance (Cal-PoW):** The majority of the supply is created on-demand by users, anchoring the currency's value.
2.  **Security Issuance (Inflation):** A fixed 1% annual inflation on the total supply is created by the protocol to reward Guardian nodes.

#### **5.3 Initial Supply & Distribution**

Vihaan is designed as a "fair launch" project to ensure maximum decentralization and equal opportunity.

*   **Initial Supply:** **0 VHC**. There is no pre-mine, no initial coin offering (ICO), and no allocation for founders, private investors, or insiders. The entire supply must be brought into existence through the publicly accessible Calibrated Proof of Work mechanism.

---

### **6. Conclusion**

Project Vihaan is a comprehensive system designed to deliver on the original promise of cryptocurrency. It combines a feeless, instantaneous transaction layer with a robustly secure, incentivized consensus model and a revolutionary price-stabilizing issuance mechanism. By defining clear economic rules and technical parameters, Vihaan provides a complete blueprint for a currency built not for speculation, but for lasting utility.

It is **a living currency for a living world.**
