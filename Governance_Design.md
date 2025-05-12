# 🗳 GoChain – Governance Design

## 🎯 Principles

* **Inclusive:** Every GOX token holder can propose, vote, and participate.
* **Decentralized:** Governance powers spread between token holders, elected council, and validators.
* **Flexible:** Supports proposals for upgrades, treasury funding, compliance changes.
* **Adaptive:** Regional councils or country-based tracks possible for local governance.

---

## 🔧 Governance Layers

| Layer               | Role                                      | Mechanics                                          |
| ------------------- | ----------------------------------------- | -------------------------------------------------- |
| **Token Holders**   | Propose, vote on referenda, elect council | 1 GOX = 1 vote (lock-based or delegation optional) |
| **Council Members** | Fast-track proposals, oversee treasury    | Elected by token holders                           |
| **Validators**      | Ensure proposal execution integrity       | Can veto in emergencies (with slashing risk)       |

---

## 🔄 Governance Process Lifecycle

1. **Proposal Submission**

   * Anyone with a minimum bonded deposit can submit a proposal.
   * Example proposals:

     * Protocol upgrade.
     * Allocate treasury to a local project.
     * Adjust staking parameters.
     * Add new compliance modules (KYC, sanctions lists).

2. **Proposal Queuing**

   * Proposals enter a public queue.
   * Council can prioritize or fast-track.

3. **Referendum Voting**

   * All token holders vote `YES` or `NO`.
   * Quadratic voting or linear voting (configurable).
   * Voting period: e.g., 7 days.
   * Early voting bonus (optional to encourage early decisions).

4. **Enactment**

   * If approved:

     * Protocol automatically enacts changes via forkless upgrade.
     * Treasury funds disbursed via on-chain multi-sig.
   * If rejected:

     * Deposit slashed partially.

---

## 💡 Governance Modules (Substrate Pallets)

* `pallet-democracy`: Handles proposals, referenda.
* `pallet-collective`: Manages council election and voting.
* `pallet-treasury`: Community-managed fund disbursement.
* `pallet-elections-phragmen`: Stake-weighted council elections.
* `pallet-sudo` (Dev only): Initial bootstrapping (must be removed at mainnet).

---

## 🏛 Example Use Cases

| Proposal                             | Triggered By      | Enacted Via                    |
| ------------------------------------ | ----------------- | ------------------------------ |
| Increase validators from 21 to 30    | Token Holder      | Forkless runtime upgrade       |
| Allocate funds to farmer cooperative | NGO + Community   | Treasury payout proposal       |
| Adjust staking reward ratio          | Council or Public | Democracy referendum           |
| Activate optional KYC for a region   | Regional Council  | Configurable compliance module |

---

## 🌍 Regional Governance Tracks (Future Phase)

* Support **per-country or per-region referenda tracks**.
* Example: ECOWAS Governance Track, Nigeria Fast Track.
* Use **Substrate OpenGov pallet** (advanced governance modes).

---

## ⚙ Governance Parameters (Prototype Defaults)

| Parameter             | Value             |
| --------------------- | ----------------- |
| Minimum Proposal Bond | 50 GOX            |
| Voting Period         | 7 days            |
| Enactment Delay       | 2 days            |
| Council Size          | 7 Members         |
| Quorum                | 20% participation |

---

## 🔐 Safeguards

* Validator emergency veto (slashing risk if misused).
* Time-locked treasury disbursements.
* Community audits (on-chain proposal discussions).

---

![image](https://github.com/user-attachments/assets/f1ddd0b9-afad-4b16-ab90-0b0d4ab7177a)
