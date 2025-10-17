# Blockchain Core Concepts

**Interactive Demos:** [Anders Brownworth Blockchain Demo](https://andersbrownworth.com/blockchain/)  
**Supplemental Reading:** [Blockchain Demo (Optional)](https://www.coursera.org/learn/web3-blockchain-fundamentals/supplement/z1peo/blockchain-demo-optional)  
**Date Studied:** $(date +%Y-%m-%d)  
**Status:** ✅ Completed  
**Prerequisites:** Chapters 1-3 - Web3, Digital Assets, Bitcoin Transactions

## 🎯 Chapter Overview

This chapter explores the fundamental building blocks of blockchain technology through interactive demonstrations, covering hashing, blocks, blockchain structure, distributed networks, and token mechanics.

## 📝 Core Concepts Explained

### 1. Cryptographic Hashing

**Demo:** [Hash Demonstration](https://andersbrownworth.com/blockchain/hash)

#### What is a Hash?

A cryptographic hash function that takes input data of any size and produces a fixed-size string of characters.

**Key Properties:**

- **Deterministic:** Same input always produces same output
- **Fast to compute:** Easy to calculate hash from input
- **One-way function:** Impossible to reverse engineer input from hash
- **Avalanche effect:** Small input change completely changes hash
- **Collision resistant:** Extremely unlikely two inputs produce same hash

#### Common Hash Algorithms

- **SHA-256:** Used in Bitcoin (256-bit output)
- **Keccak-256:** Used in Ethereum (SHA-3 variant)
- **MD5:** Older algorithm (now considered insecure)

#### Practical Examples from Demo

```
Input: "Hello World"
SHA-256 Hash: a591a6d40bf420404a011733cfb7b190d62c65bf0bcda32b57b277d9ad9f146e

Input: "Hello World!" (added exclamation)
SHA-256 Hash: 7f83b1657ff1fc53b92dc18148a1d65dfc2d4b1fa3d677284addd200126d9069
```

**Notice:** Tiny change → Completely different hash!

### 2. Blocks

**Demo:** [Block Demonstration](https://andersbrownworth.com/blockchain/block)

#### Block Structure

A container that holds multiple transactions with metadata.

**Key Components:**

- **Block Number:** Sequential identifier
- **Nonce:** "Number used once" for mining
- **Data:** Transactions or other information
- **Previous Hash:** Reference to previous block
- **Hash:** This block's cryptographic fingerprint

#### Mining Process

**Goal:** Find a hash that meets difficulty criteria (starts with certain number of zeros)

**How it Works:**

1. Combine: Block Number + Nonce + Data + Previous Hash
2. Calculate hash of this combination
3. Check if hash meets difficulty target
4. If not, change nonce and repeat

**Example from Demo:**

- Difficulty: Hash must start with "0000"
- Miner tries nonces: 0, 1, 2, 3... until finding valid hash
- Valid nonce proves computational work was done

### 3. Blockchain

**Demo:** [Blockchain Demonstration](https://andersbrownworth.com/blockchain/blockchain)

#### Chain Structure

Blocks linked together through cryptographic hashes.

**How Linking Works:**

- Each block contains hash of previous block
- Changing any block would change all subsequent hashes
- Creates immutable, tamper-evident chain

#### Immutability in Action

**Scenario:** Change data in Block 2

1. Block 2's hash changes (because data changed)
2. Block 3's "Previous Hash" no longer matches Block 2's new hash
3. Block 3 becomes invalid
4. All subsequent blocks become invalid

**To "fix" the chain:**

- Re-mine Block 2 with new data
- Re-mine Block 3 with new previous hash
- Re-mine ALL subsequent blocks
- This requires enormous computational power

### 4. Distributed Blockchain

**Demo:** [Distributed Blockchain](https://andersbrownworth.com/blockchain/distributed)

#### Network Consensus

Multiple nodes maintain copies of the blockchain and agree on valid state.

**Key Concepts:**

- **Decentralization:** No single authority controls the network
- **Consensus Mechanism:** Rules for agreeing on valid transactions
- **Longest Chain Rule:** Network accepts the longest valid chain

#### How Nodes Stay Synchronized

1. **New Block Discovery:** Miner finds valid block
2. **Broadcast:** Miner shares block with network
3. **Validation:** Nodes verify block meets all rules
4. **Adoption:** Nodes add valid block to their chain
5. **Mining Continues:** All miners now work on next block

#### Fork Scenarios

**Temporary Fork:** Two miners find blocks simultaneously

- Network temporarily has competing chains
- Next block will determine which chain "wins"
- Orphaned blocks become "stale blocks"

**Malicious Fork:** Attacker tries to rewrite history

- Requires >51% of network computational power
- Economically infeasible for major blockchains

### 5. Tokens

**Demo:** [Tokens Demonstration](https://andersbrownworth.com/blockchain/tokens)

#### Token Transactions

How digital assets are transferred on a blockchain.

**Key Components:**

- **From:** Sender's address/public key
- **To:** Recipient's address
- **Amount:** Quantity being transferred
- **Signature:** Cryptographic proof of authorization

#### Transaction Validation

**Steps for Valid Transaction:**

1. **Signature Verification:** Proof sender authorized transaction
2. **Balance Check:** Sender has sufficient funds
3. **Double-spend Check:** Funds haven't been already spent
4. **Format Check:** Transaction follows protocol rules

#### Blockchain State

- **Not just transactions** - maintains current state
- **UTXO Model (Bitcoin):** Tracks unspent transaction outputs
- **Account Model (Ethereum):** Tracks account balances

## 💡 Key Insights from Interactive Demos

### Major Realizations

1. **Hashing creates digital fingerprints** that make tampering evident
2. **Mining is a probabilistic search** for a rare hash value
3. **Immutability comes from cryptographic linking** between blocks
4. **Distribution provides security** through decentralized consensus

## Security Properties Demonstrated

- **Integrity:** Hash changes detect any modification
- **Immutable History:** Changing past requires redoing all work
- **Decentralized Trust:** No single point of control or failure

> “A blockchain is secure not because it’s unhackable, but because altering it requires redoing massive amounts of verified computational work.”
