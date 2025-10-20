## **Project Vihaan: Whitepaper**

### **Abstract**

Project Vihaan introduces a cryptocurrency, Vihaan Coin (VHC), engineered to function as a practical and stable medium of exchange for the global economy. It is built on the high-performance, feeless architecture of the [Nano protocol](https://nano.org), inheriting its block-lattice data structure and Open Representative Voting consensus mechanism. Vihaan introduces two fundamental innovations to this foundation. First, it implements a novel issuance model called **Calibrated Proof of Work (Cal-PoW)**, which **establishes a price anchor by linking the cost of new issuance** to the real-world cost of time and electricity. This is achieved through a **Verifiable Delay Function (VDF)**, a sequential and non-parallelizable puzzle that allows any user to mint new coins at a predictable cost, creating a natural price equilibrium. Second, it establishes a sustainable, non-inflationary incentive model for network validators (Representatives) by providing a **dynamic bonus on the minting reward**, directly proportional to their delegated voting weight. With an initial supply of zero and a fair launch model, Vihaan is designed to be a decentralized, stable, and truly usable digital currency for everyday transactions.

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
*   **Voting:** When a conflicting transaction (e.g., a double-spend) is detected, online Representative nodes vote on which transaction is valid. The vote is weighted logarithmically based on the total amount of VHC delegated to each Representative. This means that while larger representatives have more influence, their power does not grow linearly with their delegated stake, promoting greater network decentralization and mitigating the risk of voting power concentration. A transaction is confirmed once it has received votes from Representatives holding over 50% of the online voting weight.
*   **Security Model:** This system is secure, decentralized, and energy-efficient. It notably **does not involve staking, fund-locking, or slashing penalties**, removing barriers to participation and risk for users.

#### **2.3 The Integrated Node and Sovereign Wallet**

To maximize decentralization and user sovereignty, the official Vihaan software is a self-contained package that can operate in two modes:
1.  **Sovereign Wallet:** A secure, user-controlled node for sending and receiving VHC. It gives the user exclusive control over their private keys.
2.  **Representative Node:** A 24/7 node that contributes to network consensus by validating transactions.

This integrated design ensures that users are never required to depend on third-party services to access or secure their funds.

#### **2.4 Spam Resistance via Dynamic Proof of Work**

To prevent malicious actors from spamming the feeless network, every transaction requires a trivial amount of computational work, calculated by the user's device. The difficulty of this work is dynamic; it increases for any single account attempting to broadcast transactions at an abnormally high rate. This acts as an effective rate-limiter, making large-scale spam attacks computationally infeasible while remaining imperceptible to normal users. **This dynamic, anti-spam PoW is computationally trivial and entirely distinct from the Calibrated Proof of Work (Cal-PoW) mechanism used for minting new currency, which is discussed in Section 3. Furthermore, as the underlying Nano protocol evolves with new spam resistance solutions, Vihaan will integrate these upgrades to ensure long-term network efficiency and security.**

---

### **3. Economic Model: Calibrated Proof of Work (Cal-PoW)**

The most significant innovation in Vihaan is its economic model, designed to create long-term price stability. This is achieved by separating currency issuance from network security rewards and anchoring the **cost of new issuance** to the cost of energy and time. The Cal-PoW mechanism moves away from parallelizable "Proof of Work" (like Bitcoin) to a **"Proof of Sequential Work" (PoSW)** model, formally implemented as a **Verifiable Delay Function (VDF)**.

#### **3.1 Issuance Philosophy and Mechanism**

Anyone, at any time, can mint a fixed amount of **1 VHC** by solving a computational puzzle. This **Calibrated Proof of Work** is not a competitive mining race. It is a standardized process with a predictable time cost, open to all participants.

A VDF has two crucial properties that make this possible:
1.  **Sequentiality:** The puzzle requires a specific number of sequential steps to solve. It cannot be significantly sped up with parallel processors (e.g., GPUs or ASICs). This prevents a hardware arms race and ensures the puzzle takes a similar amount of time for all participants, from a user with a laptop to a dedicated mining farm.
2.  **Efficient Verifiability:** The solution includes a compact proof that can be verified by the network in milliseconds, without re-running the entire computation.

#### **3.2 The Cal-PoW Puzzle: A Verifiable Delay Function (VDF)**

Vihaan implements Wesolowski's VDF, which is based on repeated squaring in an RSA group of unknown order. This anchors Vihaan's value not to a quantity of hashes, but to a fixed unit of **human time**.

*   **Objective:** To establish a stable, real-world cost for minting 1 VHC by targeting a **fixed solve time** (e.g., `T_target = 5 minutes`) on standard consumer hardware. The computational difficulty is dynamic, adjusting weekly to ensure the minting time remains stable.

*   **VDF Setup:** The protocol defines a public RSA modulus `N = p * q`. The large prime factors `p` and `q` are generated via a trusted setup (e.g., a multi-party computation ceremony) and then destroyed, ensuring that no one knows the factorization. This "unknown order" is cryptographically essential to prevent shortcuts in solving the puzzle.

*   **The Puzzle (Evaluation):**
    1.  A minter takes a public **challenge**, `x` (derived from network data like their previous block hash).
    2.  The network provides the current **difficulty**, `T` (a large integer representing the number of required steps).
    3.  The minter must compute the output `y` by performing `T` sequential squarings:
        `y = x^(2^T) mod N`
    This computation is inherently sequential; to find the result of the *k-th* squaring, one must have completed the *(k-1)th* squaring. This is what enforces the time delay.

*   **Proof Generation and Verification:** While computing `y`, the minter also generates a small, cryptographic **proof**, `π`. The `mint` block submitted to the network contains the output `y` and the proof `π`. A validating node does *not* re-run the 5-minute computation. Instead, it uses the proof `π` to verify the correctness of `y` in a single, rapid calculation that takes only milliseconds. This makes the system highly efficient and scalable, avoiding ledger bloat.

#### **3.3 Representative-Anchored Dynamic Difficulty (RADD)**

The "sinking anchor" problem—where hardware improvements (Moore's Law) make a *fixed* puzzle cheaper over time—is the primary failure of static Proof-of-Work anchors. Vihaan solves this using the RADD mechanism. The VDF's difficulty, `T`, is not a hard-coded constant. It is a dynamic network variable set by the Open Representative Voting (ORV) consensus.

1.  **Target Time (T_target):** The protocol contains a hard-coded constant: `T_target = 5 minutes`.
2.  **Continuous Benchmarking:** All Representatives (validators) continuously benchmark the VDF puzzle, measuring how long it takes *their* hardware to solve for 1 VHC with the current difficulty `T`.
3.  **Weekly Vote:** Once per week, every Representative publicly votes on what the new difficulty `T` should be, based on their goal of hitting the 5-minute target. (e.g., "My hardware solved it in 4 minutes, so I vote to increase `T` by 25%").
4.  **Consensus:** The network's official difficulty `T` for the next minting epoch (the next week) is the **delegated-vote-weighted median** of all Representative votes.

This model forces all hardware to compete on the same `TIME` anchor, democratically set by the network, rather than a technological arms race.

#### **3.4 The Price Anchor Effect**

This on-demand issuance mechanism creates a powerful economic equilibrium.
*   **Price Ceiling:** If the market price of 1 VHC rises significantly above the energy and time cost to mint it, rational actors will be incentivized to mint new coins and sell them for a profit. This influx of new supply will exert **downward pressure** on the price, guiding it back toward the cost of production.
*   **The Source of Value (The "Demand" Floor):** The Cal-PoW mechanism does not create a mechanical price floor. If market demand collapses, the price can fall below the minting cost, at which point new issuance will simply cease. Like all currencies, Vihaan's value floor is derived from the collective trust, network effect, and market demand from its users. Vihaan is designed to foster this trust by providing an instant, feeless, and decentralized medium of exchange. Its utility as a practical payment system is the foundation for its demand, and the stability offered by the "ceiling" anchor makes it usable for merchants and savers, creating a strong foundation for social consensus.

**Security of the Monetary Policy:** A concern is that Representatives might collude to vote for a low difficulty `T` to make minting cheaper for themselves. This attack is transparent and economically self-defeating. A Representative's income (their minting bonus) depends on the trust of their delegators. Voting for a low `T` is a public, on-chain act of deliberate inflation. Any user can see this malicious vote and will **immediately re-delegate their vote** away from the "inflationist" rep to an honest one. The short-term profit from cheating is minuscule compared to the permanent loss of their delegated vote and their entire minting-bonus income stream.

---

### **4. Network Security & Incentivization**

To ensure the long-term health and decentralization of the network, Vihaan provides a direct, non-inflationary economic incentive for those who run Representative nodes.

#### **4.1 Dynamic Minting Bonus for Representatives**

Instead of being rewarded through protocol inflation, registered Representatives receive an economic bonus on their minting reward. This incentive is kept separate from the consensus mechanism's logarithmic voting weight.

The puzzle difficulty `T` (the 5-minute solve time) is **universal for all participants**. This ensures Representatives are neutral guardians of the public cost-anchor.

A Representative's incentive comes as a **bonus (or "yield")** on the coins they mint.

*   **Bonus Formula:**
    `Bonus Percentage = (Representative's Linear Delegated Vote / Total Linear Delegated Vote Online) * 80%`

*   **Hard Cap & Anti-Centralization:** The maximum bonus any single representative can receive is hard-capped at **20%**.

This model creates a balanced system. A Representative with a **5% vote share** (a healthy, trusted node) earns a **4% bonus** (`5% * 80% = 4%`). When they solve the standard 5-minute puzzle, their `mint` block is allowed to credit their account with **1.04 VHC** instead of the standard 1.0 VHC.

This 4% "yield" on their minting operation is a highly profitable incentive that easily covers the operational costs of a secure node. It achieves this *without* creating a conflict of interest, as all Representatives are still incentivized to vote for and defend the single, public 5-minute `T_target`.

Crucially, the 20% hard cap is hit if a representative acquires **25% of the total delegated vote**. This creates a powerful economic disincentive against further centralization; a representative who controls 51% of the vote receives *no additional bonus* for their excess (and dangerous) vote share, making centralization unprofitable.

---

### **5. Tokenomics**

#### **5.1 Token Details**

*   **Name:** Vihaan Coin
*   **Ticker:** VHC

#### **5.2 Supply Model**

*   **Initial Supply:** **0 VHC**.
*   **Issuance:** The entire supply is brought into existence exclusively through the public Calibrated Proof of Work (VDF) mechanism.
*   **Supply Cap:** There is **no hard cap**. The total supply is **elastic**, designed to **expand** to meet the demands of the economy it serves.
*   **Inflation:** There is zero protocol-level subsidy inflation. New supply is only created when users expend real-world energy and time, directly linking supply expansion to market demand.

#### **5.3 Initial Distribution**

Vihaan is a **fair launch** project.
*   There is **no pre-mine**, **no Initial Coin Offering (ICO)**, and **no allocation** of coins for founders, private investors, or a development team. Every single VHC must be minted through the same public, proof-of-work process available to everyone from day one.

---

### **6. Conclusion**

Project Vihaan presents a comprehensive solution to the critical challenges preventing the mainstream adoption of cryptocurrency. By integrating the high-performance, feeless architecture of Nano with a novel economic model based on a Verifiable Delay Function, Vihaan achieves robust price stability anchored to time. Its unique, non-inflationary incentive structure ensures the network remains secure and decentralized in perpetuity. By defining clear technical parameters and sound economic principles, Vihaan provides a complete blueprint for a currency built not for speculation, but for lasting, global utility. It is **a living currency for a living world.**
