## **Project Vihaan: Whitepaper**

### **Abstract**

Project Vihaan introduces a cryptocurrency, Vihaan Coin (VHC), engineered to function as a practical and stable medium of exchange for the global economy. It is built on the high-performance, feeless architecture of the [Nano protocol](https://nano.org), inheriting its block-lattice data structure and Open Representative Voting consensus mechanism. Vihaan introduces two fundamental innovations to this foundation. First, it implements a novel issuance model called **Calibrated Proof of Work (Cal-PoW)**, which anchors the currency's value to the real-world cost of electricity. This is achieved through a memory-hard, ASIC-resistant puzzle that allows any user to mint new coins at a predictable cost, creating a natural price equilibrium. Second, it establishes a sustainable, non-inflationary incentive model for network validators (Representatives) by providing a **dynamic discount** on the minting puzzle difficulty, directly proportional to their delegated voting weight. With an initial supply of zero and a fair launch model, Vihaan is designed to be a decentralized, stable, and truly usable digital currency for everyday transactions.

---

### **1. Introduction**

#### **1.1 The Unfulfilled Promise of Cryptocurrency**

The initial vision for cryptocurrency was a peer-to-peer electronic cash system. However, a decade after its inception, the majority of digital assets have evolved into speculative instruments rather than practical currency. Their adoption for daily commerce is fundamentally hindered by four critical flaws: prohibitive transaction fees, slow confirmation times, limited scalability, and extreme price volatility. A currency that can lose 10% of its value overnight is unsuitable for merchants and savers alike.

#### **1.2 The Vihaan Solution: A Living Currency**

Vihaan is a project designed to solve these issues and deliver on the original promise of cryptocurrency. It is engineered from first principles to be a **living currency for a living world**, prioritizing utility and stability over speculation.

#### **1.3 Core Design Principles**

Vihaan's architecture is guided by three unwavering principles:

1.  **Instantaneous and Feeless:** Transactions must be frictionless to compete with and surpass existing payment systems.
2.  **Inherently Stable:** The currency's value must be anchored to a tangible, real-world metric to provide confidence and predictability for users and merchants.
3.  **Sustainably Secure:** The network must be protected by a robust, decentralized consensus mechanism with clear and permanent economic incentives for honest participants, achieved without protocol-level inflation.

---

### **2. Foundational Architecture**

Vihaan leverages the proven design of the [Nano protocol](https://nano.org) as its architectural base.

#### **2.1 The Block-Lattice Ledger**

Instead of a single, monolithic blockchain, Vihaan employs a **block-lattice**, which is a Directed Acyclic Graph (DAG) where each account has its own individual blockchain (an "account-chain"). A transaction consists of two blocks: a `send` block on the sender's chain and a corresponding `receive` block on the receiver's chain. These are processed asynchronously by the network, enabling near-instantaneous confirmations and immense scalability. This structure eliminates the need for a fee market, making all transactions **feeless**.

#### **2.2 Consensus: Open Representative Voting (ORV)**

Network consensus is achieved through a lightweight and efficient Delegated Proof of Stake (DPoS) variant called Open Representative Voting.
*   **Delegation:** Any user can delegate the voting weight of their VHC balance to a **Representative** node of their choice, at no cost. The user retains full control of their funds.
*   **Voting:** When a conflicting transaction (e.g., a double-spend) is detected, online Representative nodes vote on which transaction is valid. **The vote is weighted logarithmically based on the total amount of VHC delegated to each Representative. This means that while larger representatives have more influence, their power does not grow linearly with their delegated stake, promoting greater network decentralization and mitigating the risk of voting power concentration.** A transaction is confirmed once it has received votes from Representatives holding over 50% of the online voting weight.
*   **Security Model:** This system is secure, decentralized, and energy-efficient. It notably **does not involve staking, fund-locking, or slashing penalties**, removing barriers to participation and risk for users.

#### **2.3 The Integrated Node and Sovereign Wallet**

To maximize decentralization and user sovereignty, the official Vihaan software is a self-contained package that can operate in two modes:
1.  **Sovereign Wallet:** A secure, user-controlled node for sending and receiving VHC. It gives the user exclusive control over their private keys.
2.  **Representative Node:** A 24/7 node that contributes to network consensus by validating transactions.

This integrated design ensures that users are never required to depend on third-party services to access or secure their funds.

#### **2.4 Spam Resistance via Dynamic Proof of Work**

To prevent malicious actors from spamming the feeless network, every transaction requires a trivial amount of computational work, calculated by the user's device. The difficulty of this work is dynamic; it increases for any single account attempting to broadcast transactions at an abnormally high rate. This acts as an effective rate-limiter, making large-scale spam attacks computationally infeasible while remaining imperceptible to normal users.

---

### **3. Economic Model: Calibrated Proof of Work (Cal-PoW)**

The most significant innovation in Vihaan is its economic model, designed to create long-term price stability. This is achieved by separating currency issuance from network security rewards and anchoring the value of VHC to a globally understood metric: the cost of energy.

#### **3.1 Issuance Philosophy and Mechanism**

Anyone, at any time, can mint a fixed amount of **1 VHC** by solving a computational puzzle. This **Calibrated Proof of Work** is not a competitive mining race. It is a standardized process with a predictable cost, open to all participants.

#### **3.2 The Cal-PoW Puzzle: Sequential Memory-Hard Hash Chain (SMHC)**

The puzzle is a practical implementation of a **Verifiable Delay Function (VDF)**, specifically designed to be ASIC-resistant and fair.

*   **Objective:** To calibrate the cost of minting 1 VHC to approximately **₹1.00 INR (Indian Rupee)**, which corresponds to roughly **$0.012 USD** at current exchange rates. This cost is a function of electricity consumption during the computation time.
*   **Technical Specifications:**
    *   **Algorithm:** A sequential chain of **2^28 (268,435,456)** iterations of the **BLAKE3** hashing algorithm.
    *   **Memory Requirement:** The algorithm requires a dedicated memory buffer of **2 GiB (Gibibytes)**. Each iteration involves multiple random-access reads from this buffer, with the input of the next hash being dependent on the output of the previous one.
    *   **ASIC Resistance:** The bottleneck of this process is **memory latency**—the physical time it takes to fetch data from RAM. This is a deliberate design that cannot be easily optimized by parallel-processing hardware like GPUs or ASICs, ensuring that standard consumer hardware remains competitive.

#### **3.3 Rapid Puzzle Verification**

A Proof of Work solution must be quickly verifiable. The SMHC puzzle achieves this via a **checkpointing system**.

*   **Proof Generation:** While solving the puzzle, the minter generates **256** cryptographic checkpoints. Each checkpoint is a hash of the internal state at every **2^20 (1,048,576)** iterations.
*   **Verification:** To validate a submitted solution, a node does not re-run the entire 268 million iterations. It performs a series of spot-checks, for example, by re-computing the work between checkpoint #73 and #74 to confirm the hash matches. This verification process is thousands of times faster than the original computation, making it highly efficient.

#### **3.4 The Price Anchor Effect**

This on-demand issuance mechanism creates a powerful economic equilibrium.
*   **Price Ceiling:** If the market price of 1 VHC rises significantly above the ₹1 energy cost to mint it, rational actors will be incentivized to mint new coins and sell them for a profit. This influx of new supply will exert **downward pressure** on the price, guiding it back toward the anchor.
*   **Price Floor:** If the market price of 1 VHC falls below the ₹1 energy cost, minting becomes unprofitable and ceases. With no new supply being created, organic market demand will exert **upward pressure** on the price, guiding it back toward the anchor.

---

### **4. Network Security & Incentivization**

To ensure the long-term health and decentralization of the network, Vihaan provides a direct, non-inflationary economic incentive for those who run Representative nodes.

#### **4.1 Dynamic Minting Discount for Representatives**

Instead of being rewarded through protocol inflation, registered Representatives receive a **discount on the Cal-PoW puzzle difficulty**. **This economic incentive is kept separate from the consensus mechanism's logarithmic voting weight. The discount is directly proportional to the total linear amount of VHC delegated to the Representative, rewarding them for the trust they have earned from the community.**

*   **Discount Formula:**
    `Discount Percentage = (Representative's Linear Delegated Vote / Total Linear Delegated Vote Online) * 20%`
*   **Maximum Discount:** The formula is capped to provide a maximum possible discount of **20%** to a single entity, even if they were to hypothetically control 100% of the vote.

**This model creates a balanced system. The logarithmic voting weight encourages decentralization at the consensus level by diminishing the power of single large entities. Simultaneously, the linear discount ensures that the economic incentive to run a node remains strong and directly proportional to the amount of stake entrusted to the Representative.** A Representative with a larger delegated stake earns a larger discount, allowing them to mint VHC for a lower electricity cost and creating a profitable incentive to maintain a reliable, high-performance node.

---

### **5. Tokenomics**

#### **5.1 Token Details**

*   **Name:** Vihaan Coin
*   **Ticker:** VHC

#### **5.2 Supply Model**

*   **Initial Supply:** **0 VHC**.
*   **Issuance:** The entire supply is brought into existence exclusively through the public Calibrated Proof of Work mechanism.
*   **Supply Cap:** There is **no hard cap**. The total supply is dynamic, designed to expand and contract to meet the demands of the economy it serves.
*   **Inflation:** There is **zero protocol-level monetary inflation**. New coins are only created by users expending real-world energy, not to pay for security.

#### **5.3 Initial Distribution**

Vihaan is a **fair launch** project.
*   There is **no pre-mine**, **no Initial Coin Offering (ICO)**, and **no allocation** of coins for founders, private investors, or a development team. Every single VHC must be minted through the same public, proof-of-work process available to everyone from day one.

---

### **6. Conclusion**

Project Vihaan presents a comprehensive solution to the critical challenges preventing the mainstream adoption of cryptocurrency. By integrating the high-performance, feeless architecture of Nano with a novel economic model based on Calibrated Proof of Work, Vihaan achieves robust price stability. Its unique, non-inflationary incentive structure ensures the network remains secure and decentralized in perpetuity. By defining clear technical parameters and sound economic principles, Vihaan provides a complete blueprint for a currency built not for speculation, but for lasting, global utility. It is **a living currency for a living world.**
