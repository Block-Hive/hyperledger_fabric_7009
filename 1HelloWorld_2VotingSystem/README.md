# 🚀 Hyperledger Fabric: Hello World & Voting System

## 📌 Introduction

This repository contains two projects built on **Hyperledger Fabric**:

1️⃣ **Hello World** – A simple **"first blockchain application"** to understand Fabric's structure.  
2️⃣ **Voting System** – A decentralized blockchain-based voting application ensuring security and transparency.  

Both projects use **Smart Contracts (Chaincode)** to interact with the Fabric ledger.

---

## 🛠️ Prerequisites

Ensure you have already **installed and set up Hyperledger Fabric** using the test network.  
If not, refer to the **[Hyperledger Fabric Setup Guide](https://github.com/hyperledger/fabric-samples)**.

---

## 🚀 Steps to Initialize & Use **Hello World** and **Voting System**

The following **one shell script** contains **all necessary steps** to execute both projects **separately**:

```sh
#!/bin/bash

# ==========================
# 1️⃣ HELLO WORLD SETUP
# ==========================

echo "🚀 Setting up Hello World Smart Contract..."

# Step 1: Navigate to the Fabric Test Network
cd fabric-samples/test-network || { echo "Test Network Not Found!"; exit 1; }

# Step 2: Start Fabric Network (if not running)
echo "🔄 Starting Fabric Test Network..."
./network.sh up

# Step 3: Deploy Hello World Smart Contract
echo "📜 Deploying Hello World Smart Contract..."
./network.sh deployCC -ccn hello -ccp ../chaincode/hello-world -ccl go

![Network-up = chaincode installed](images/BlockchainHelloW1.png)

# Step 4: Interact with Hello World Smart Contract
echo "📝 Initializing Hello World Ledger..."
peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com \
--tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem" \
-C mychannel -n helloworld -c '{"function":"InitLedger","Args":[]}'

![initialised Hello World](images/BlockchainHelloW2.png)

echo "📢 Querying Hello World Ledger..."
peer chaincode query -C mychannel -n hello -c '{"Args":["HelloWorld"]}'

echo "✅ Hello World Smart Contract Deployed Successfully!"


# ==========================
# 2️⃣ VOTING SYSTEM SETUP
# ==========================

echo "🚀 Setting up Voting System Smart Contract..."

# Step 1: Deploy Voting System Smart Contract
echo "📜 Deploying Voting System Smart Contract..."
./network.sh deployCC -ccn voting -ccp ../voting-system/chaincode -ccl go

# Step 2: Interact with Voting System Smart Contract
echo "🗳️ Initializing Voting System..."
peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com \
--tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem" \
-C mychannel -n voting -c '{"function":"InitVoting","Args":["Candidate1", "Candidate2"]}'

echo "📢 Querying Voting Ledger..."
peer chaincode query -C mychannel -n voting -c '{"function":"GetVotes","Args":[]}'

echo "✅ Voting System Smart Contract Deployed Successfully!"


# ==========================
# SHUTDOWN INSTRUCTIONS
# ==========================
echo "🔴 To stop the network, run:"
echo "cd fabric-samples/test-network && ./network.sh down"
