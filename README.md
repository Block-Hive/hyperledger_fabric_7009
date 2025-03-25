# 🏗️ Hyperledger Fabric: Private Blockchain & Projects

## 📌 Introduction to Hyperledger Fabric

Hyperledger Fabric is a **permissioned, private blockchain** framework designed for enterprise-grade applications. Unlike public blockchains like Ethereum or Bitcoin, **Fabric operates in a closed environment where only authorized participants can join the network**. It provides:

✅ **Privacy & Confidentiality** – Transactions are visible only to authorized participants.  
✅ **Scalability** – Supports modular architecture for high performance.  
✅ **Smart Contracts (Chaincode)** – Business logic is executed securely on the blockchain.  
✅ **Pluggable Consensus Mechanisms** – Allows flexibility in transaction validation.  
✅ **Identity Management** – Uses certificates and MSPs for user authentication.

Hyperledger Fabric is widely used in **finance, supply chains, healthcare, and government systems** to ensure secure, verifiable, and tamper-proof transactions.

---

## 🚀 Hyperledger Fabric Projects

### 1️⃣ Hello World: Getting Started with Hyperledger Fabric

The **Hello World** project is a simple introduction to **Hyperledger Fabric Smart Contracts**. It helps developers understand:

- Setting up a Fabric network  
- Writing and deploying a basic **Chaincode (Smart Contract)**  
- Interacting with the blockchain using CLI or APIs  
- Querying and updating ledger data  

This project is the foundation for building more complex blockchain applications.

---

### 2️⃣ Voting System: Secure Blockchain-Based Elections

A **decentralized voting system** built on Hyperledger Fabric ensures **fairness, transparency, and security** in elections. Key features:

🔹 **Voter Registration** – Users are authenticated before casting votes.  
🔹 **Immutable Ledger** – Votes are recorded permanently and cannot be altered.  
🔹 **Transparent & Secure** – Results can be verified by all stakeholders.  
🔹 **Smart Contracts for Vote Counting** – Automates tallying without manual intervention.  

This system eliminates traditional voting fraud and enhances trust in elections.

---

### 3️⃣ Food Token System: Digital Token Management on Hyperledger Fabric

The **Food Token System** leverages **Hyperledger Fabric** to manage and redeem **food tokens** securely. It consists of:

🍽️ **Customer Registration** – Users register and receive an initial balance of tokens.  
📲 **QR Code Generation** – Each customer gets a unique QR code linked to their token balance.  
📷 **Vendor Token Redemption** – Vendors scan QR codes to deduct tokens from customer accounts.  
🔐 **Blockchain Security** – Transactions are tamper-proof and verifiable.  

This project demonstrates how **blockchain can enhance digital transactions**, reducing fraud and ensuring seamless token management.

---

## 🛠️ Minimal Steps to Start with Hyperledger Fabric Using Docker

### 🔹 Install Prerequisites

Ensure you have the following installed:
- **Docker** ([Install Guide](https://docs.docker.com/get-docker/))
- **Docker Compose** ([Install Guide](https://docs.docker.com/compose/install/))
- **cURL** ([Install Guide](https://curl.se/))
- **Git** ([Install Guide](https://git-scm.com/downloads))

---

## 📌 One-Command Setup Script for Hyperledger Fabric

To **download, set up, and run Hyperledger Fabric**, execute the following **shell script**:

```sh
#!/bin/bash

# Step 1: Download Hyperledger Fabric Binaries & Samples
echo "Downloading Hyperledger Fabric..."
curl -sSL https://bit.ly/2ysbOFE | bash -s

# Step 2: Navigate to the Fabric Samples Directory
cd fabric-samples/test-network || { echo "Directory not found!"; exit 1; }

# Step 3: Start the Test Network
echo "Starting the Fabric Test Network..."
./network.sh up

# Step 4: Deploy the Sample Smart Contract
echo "Deploying the Sample Smart Contract..."
./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go -ccl go

# Step 5: Interact with the Blockchain
echo "Initializing Ledger..."
peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com \
--tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem" \
-C mychannel -n basic -c '{"function":"InitLedger","Args":[]}'

echo "Querying Ledger..."
peer chaincode query -C mychannel -n basic -c '{"function":"GetAllAssets","Args":[]}'

echo "✅ Hyperledger Fabric is up and running!"
