# 🌍 GoChain

An open-source **Rust-based blockchain prototype** tailored for **West Africa**, integrating:

* ✅ **Delegated Proof of Stake (DPoS) consensus**
* ✅ **Mobile-first access via USSD, SMS, and lightweight apps**
* ✅ **Governance-ready and compliance-friendly architecture**
* ✅ **Modular components for privacy (ZKPs), identity (SSI), and scalability (Layer 2-ready)**

---

## 🎯 Purpose

GoChain is designed to **bridge the blockchain gap in West Africa**, focusing on:

* **Inclusivity:** Reaches unbanked users via USSD, SMS, and low-data apps.
* **Efficiency:** Low energy, low bandwidth, high transaction speed using DPoS.
* **Modularity:** Supports privacy-preserving transactions, decentralized identity, and Layer 2 scalability.
* **Governance & Compliance:** On-chain governance with regional compliance modules for flexible adaptation.

---

## 🛠 Components

### 1. Blockchain Node (Rust/Substrate)

* Substrate-based node template modified for **DPoS (21 elected validators)**.
* Integrated governance (proposals, referenda, treasury).
* Forkless upgrades via Wasm runtime.

### 2. USSD Gateway Backend (Node.js)

* Exposes blockchain functions through USSD/SMS using Africa's Talking or Twilio.
* Features:

  * Check balance.
  * Send tokens.
  * Access governance proposals.

### 3. Infrastructure & Deployment

* Docker Compose setup for quick local development.
* Scripts for cloud or local server deployment.
* Monitoring integration (Prometheus, Grafana).

### 4. (Optional) Light Client App (React Native)

* Minimalist wallet app with offline-first design.
* Fallback to USSD commands inside the app.

---

## 🚀 Quick Start

### Prerequisites

* Rust & Cargo installed.
* Node.js and npm installed.
* Docker (optional for automation).

### Install & Run

```bash
git clone https://github.com/yourorg/gochain
cd gochain

# Build the blockchain node
cd blockchain-node
cargo build --release

# Run the node locally
./target/release/gochain-node --dev

# In a new terminal, start the USSD Gateway backend
cd ../ussd-backend
npm install
node index.js
```

### Test USSD Menu (Simulated Example)

1. Access the USSD backend via Africa's Talking sandbox or curl:

```bash
curl -X POST http://localhost:3000/ussd -d "text=1&phoneNumber=+1234567890"
```

2. Receive response with your blockchain balance.

---

## 💡 Example Use Cases

* Community-driven microfinance with transparent elections.
* Rural merchant payments using only basic phones.
* NGO aid distribution with SSI-based eligibility checks.
* Cross-border trade with Layer 2 sidechains (future phases).

---

## 📜 License

MIT License.
See [LICENSE](LICENSE) for details.

---

## 🤝 Contributing

We welcome contributions from the community.

1. Fork the repository.
2. Create your feature branch.
3. Push to your branch and create a Pull Request.
4. Document your changes.

---

## 📚 Documentation & Roadmap

* [Architecture Overview](docs/architecture.md)
* [USSD API Specification](docs/ussd-api.md)
* [Governance Design](docs/governance.md)
* [Roadmap](docs/roadmap.md)

---
