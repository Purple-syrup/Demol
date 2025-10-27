# 🧬 DeMol — Tokenizing Machine-Learned Drug IP as Onchain RWAs

## 🚀 Overview

DeMol is building a radical new infrastructure where **decentralized AI agents, verifiable computation, and on-chain governance** combine to accelerate and democratize drug discovery.

We tokenize real-world drug IP as verifiable on-chain assets, enabling open scientific collaboration, transparent funding, and equitable participation — all while bringing **AI-powered drug design** and **DeFi primitives** into one ecosystem.

> *“The future of pharma is autonomous, intelligent, and open.”*

---

## 🧠 What It Does

DeMol brings together **AI agents, blockchain infrastructure, and DAO governance** to transform how drug research happens openly, collaboratively, and transparently.

### 🔬 Analyze Molecules
Run predictive models to evaluate activity, toxicity, drug-likeness, and synthesizability — all fully verifiable and automated.

### 🧪 Generate Molecules
Use AI agents (via **ELiZA OS**) to create novel drug-like scaffolds and explore chemical space with intelligence and speed.

### 💎 Tokenize Promising Compounds
Molecules meeting eligibility thresholds are automatically minted as **on-chain IP NFTs**, complete with metadata and scientific scoring stored securely on **AWS S3**.

### 🗳️ Propose & Vote
A **DAO** governs the process — members review, vote, and fund the most promising molecules for further real-world R&D.

### 💰 Share the Upside
Researchers and DAO participants earn a stake in the success of funded compounds through transparent royalties and governance rights.

---

## 🏗️ How We Built It

DeMol integrates **Machine Learning**, **Chainlink**, **ELiZA OS**, **AWS**, **Supabase**, and **Avalanche** to deliver a fully decentralized scientific pipeline.

### 🤖 Machine Learning
Implemented specialized ML models using **PyTorch** and **AttentiveFP** to power molecular evaluation and design:
- Toxicity prediction model (multi-endpoint)
- Lipinski + QED scoring for drug-likeness and developability
- Generative scaffold model for new compound creation
- Synthetic Accessibility (SA) scoring (Ertl & Schuffenhauer)

These are orchestrated via **ELiZA OS** and **AWS** for verifiable inference.

### 🔗 Blockchain & Tokenization
- Smart Contracts: ERC-721 for molecules, ERC-20 for governance and funding.
- Networks: **Avalanche C-Chain** (main deployment) and **Ethereum Sepolia** (cross-chain testing).
- **Chainlink Automation** triggers molecule minting and data updates.
- **Chainlink Functions** verify inference results and ensure secure execution.
- **Chainlink CCIP** enables cross-chain interoperability and liquidity movement.

### 🧰 DAO & Governance
- **Supabase** powers off-chain proposal data storage and fast UI queries.
- DAO participants vote on which compounds to fund.
- Royalties and rewards flow transparently through on-chain logic.

### 💻 Frontend
- Built using **Bolt.new**, **Next.js**, **TailwindCSS**, and **Framer Motion**.
- Wallet interactions handled with **wagmi** and **ethers.js**.
- Hosted on **Netlify** for speed and scalability.
- Designed for accessibility, scientific credibility, and real-time blockchain integration.

### ⚙️ AI Agent Orchestration (ELiZA OS)
- ML models run as **modular, verifiable ELiZA agents**.
- ELiZA ensures transparency and cryptographic verifiability of all inference and scoring results.
- Agent outputs directly trigger on-chain minting or proposal logic.

---

---

## 🚀 Problem

Drug discovery is **costly**, **centralized**, and **slow**.  
Promising molecules often die in the lab due to lack of funding or limited accessibility.  
There’s no transparent way for the public or investors to participate early in the process.

---

## 💡 Solution

DeMol creates an **onchain marketplace for drug intellectual property** by:

1. Running molecules through **AI agents (ELiZA OS)** for scoring and validation.
2. Storing inference metadata securely on **AWS S3**.
3. Verifying results and triggering NFT minting through **Chainlink Functions + Automation**.
4. Minting ERC-721 tokens on **Avalanche** representing the drug IP.
5. Enabling funding, governance, and royalty flows through DeFi primitives.

Each tokenized Drug IP becomes a **verifiable, investable digital asset**.

---

## 🧩 Architecture Overview

```
Molecule Submission
      ↓
ELiZA Runtime — ML Inference + Scoring
      ↓
AWS S3 — Metadata Storage
      ↓
Chainlink Functions — Verify Inference Signature
      ↓
DeMol Upkeep (Chainlink Automation) — Auto Mint Trigger
      ↓
DeMolToken (Avalanche ERC-721) — Mint Drug IP NFTs
      ↓
Frontend DApp — View, Fund, Govern IPs
```

---

## 🛠️ Components

### 1. **Smart Contracts (Solidity, Avalanche)**
- `DeMolToken.sol` — ERC-721 NFT for tokenized drug IP.
- `DeMolUpkeep.sol` — Chainlink Automation-compatible contract that queues and mints new IPs automatically.

### 2. **ELiZA Agent (Node.js)**
- Runs molecule inference via ELiZA OS Runtime.
- Uploads inference results to AWS S3.
- Queues molecule for Chainlink Automation to mint NFT on Avalanche.

### 3. **Chainlink Integrations**
- **Chainlink Functions:** verifies ELiZA inference signatures or hashes before minting.
- **Chainlink Automation:** monitors for new candidates and automatically calls `mintDrugIP`.

### 4. **AWS Integration**
- **S3** stores model inference metadata and result proofs.
- **SageMaker (optional)** can host your custom ML model for inference.

### 5. **Avalanche Blockchain**
- Provides the onchain infrastructure for minting and managing NFTs.
- Enables DeFi and governance extensions.

---

## ⚙️ Setup Instructions

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/demol.git
cd demol
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Environment Variables
Create a `.env` file in the root directory:
```bash
PRIVATE_KEY=your_private_key
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret
AWS_BUCKET_NAME=your_bucket_name
AVALANCHE_RPC_URL=https://api.avax.network/ext/bc/C/rpc
ELIZA_API_URL=https://api.elizaos.ai/run
```

### 4. Deploy Contracts
Use Hardhat or Foundry to deploy:
```bash
npx hardhat run scripts/deploy.js --network avalanche
```

### 5. Run the ELiZA Agent
```bash
node eliza-agent.js
```

This will:
- Run ML inference on the molecule.
- Upload metadata to S3.
- Queue the molecule to the upkeep contract.

### 6. Register Chainlink Automation
Go to [Chainlink Automation UI](https://automation.chain.link/) and:
- Select **Avalanche C-Chain**
- Add the `DeMolUpkeep` contract
- Fund with LINK tokens

---

## 🌉 Example Flow

1. Researcher submits a molecule `CC(=O)OC1=CC=CC=C1C(=O)O`
2. ELiZA agent runs inference → score: 0.92
3. Metadata uploaded to AWS S3 → hash stored
4. Chainlink verifies and triggers mint
5. Avalanche mints NFT `#23` representing the drug IP
6. DAO can fund further synthesis or licensing using DeFi

---

## 🧠 Technologies

| Technology | Usage |
|----------|--------|
| **ELiZA OS** | AI runtime inference & verifiable ML scoring |
| **AWS** | Metadata & model hosting (S3, SageMaker) |
| **Chainlink** | Onchain automation and offchain data verification |
| **Avalanche** | Onchain NFT minting, governance, and finance layer |

---

## 💎 Why It’s Novel

- First integration of **ELiZA runtime inference** with **tokenized biotech IPs**
- Brings **DeFi liquidity** into **drug discovery**
- **Verifiable, cross-system AI → Blockchain trust layer**
- A new real-world asset (RWA): **Drug IP NFTs**

---

## ✨ Frontend Highlights

> “Welcome to the Future of Drug Discovery & DeFi”  
> “DeMol — Autonomous, Intelligent, and Open Pharma”  
> “Tokenizes real-world drug IP for on-chain ownership.”  

### Features
- Connect Wallet and explore the DAO.
- Submit molecules and view live inference results.
- Participate in governance and funding rounds.
- Built using **Supabase**, **Netlify**, and **React** frontend stack.

---

## 🤝 Team & Future Work

- Expand multi-model AI scoring with toxicity prediction.
- Launch DeMol DAO for governance and funding proposals.
- Enable fractionalized ownership of drug NFTs.
- Integrate decentralized data marketplaces for biopharma datasets.

---

## 📄 License

MIT License © 2025 DeMol Team

---

## 🔗 Links

- **Live App:** [Coming soon]
- **Demo Video:** [YouTube link once ready]
- **Smart Contracts:** `/contracts`
- **Agent Script:** `/agent/eliza-agent.js`
- **Documentation:** `/docs`
- **Twitter:** [https://twitter.com/demolproject](https://twitter.com/demolproject)
- **GitHub:** [https://github.com/yourusername/demol](https://github.com/yourusername/demol)

---

**Built at the edge of science and decentralization.**  
*Welcome to the future of autonomous drug discovery.*
