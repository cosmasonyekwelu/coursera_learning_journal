# Smart Contracts

**Lecture:** [Smart Contracts](https://www.coursera.org/learn/web3-blockchain-fundamentals/lecture/HK9LK/smart-contracts)

## 🎯 Chapter Overview

This chapter introduces smart contracts - self-executing contracts with terms directly written into code that automatically execute when predetermined conditions are met, revolutionizing how we think about agreements and automation.

## 📝 Lecture Notes

### What Are Smart Contracts?

#### Basic Definition

**Smart Contract:** Code that runs exactly as programmed without possibility of downtime, censorship, fraud, or third-party interference.

**Key Characteristics:**

- **Self-executing:** Automatically executes when conditions met
- **Tamper-proof:** Cannot be altered once deployed
- **Transparent:** Code is visible and verifiable by all
- **Deterministic:** Same inputs always produce same outputs

#### Historical Context

**Nick Szabo (1994):** First coined term "smart contracts"

- Originally conceptualized for vending machines
- "A set of promises, specified in digital form, including protocols within which the parties perform on these promises"

### How Smart Contracts Work

#### Basic Execution Flow

```
1. Contract Deployment → Code stored on blockchain
2. Condition Monitoring → Waiting for trigger events
3. Automatic Execution → Code runs when conditions met
4. State Update → Blockchain state changes
5. Transaction Record → Execution recorded permanently
```

#### Key Components

- **Contract Code:** The programmed logic and rules
- **State Variables:** Data stored by the contract
- **Functions:** Executable code that modifies state
- **Events:** Logs that external apps can listen to

### Smart Contract Platforms

#### Ethereum: The Pioneer

- First blockchain with full smart contract capability
- **Solidity:** Primary programming language
- **EVM:** Ethereum Virtual Machine - runtime environment
- **Gas:** Payment for computation and storage

#### Other Smart Contract Platforms

- **Cardano:** Research-driven, formal verification
- **Solana:** High throughput, low fees
- **Polkadot:** Interoperability between chains
- **Avalanche:** Subnets for custom blockchains

### Real-World Smart Contract Examples

#### 1. Simple Escrow Service

```solidity
// Simplified escrow contract
contract Escrow {
    address public buyer;
    address public seller;
    address public arbiter;
    uint public amount;
    bool public released;

    function release() public {
        require(msg.sender == arbiter);
        payable(seller).transfer(amount);
        released = true;
    }
}
```

#### 2. Decentralized Lending

```solidity
// Simplified lending contract
contract Lending {
    mapping(address => uint) public collateral;
    mapping(address => uint) public loans;

    function borrow(uint amount) public {
        require(collateral[msg.sender] >= amount * 2);
        loans[msg.sender] += amount;
        payable(msg.sender).transfer(amount);
    }
}
```

### Smart Contract Benefits

#### 1. Trust Minimization

- No need to trust counterparties
- Code execution is guaranteed
- Eliminates intermediary risks

#### 2. Automation & Efficiency

- Reduces manual processes
- 24/7 operation without human intervention
- Lower operational costs

#### 3. Transparency & Auditability

- All terms visible on blockchain
- Execution history permanently recorded
- Verifiable by all participants

#### 4. Security

- Cryptographic protection
- Immutable once deployed
- Resistance to censorship

### Smart Contract Limitations & Challenges

#### 1. Immutability Challenges

- **Bug Fixes:** Cannot easily patch deployed contracts
- **Upgrades:** Require complex proxy patterns
- **Irreversible:** Mistakes are permanent

#### 2. Oracle Problem

- **Data Inputs:** Need reliable external data sources
- **Centralization Risk:** Oracles become trusted parties
- **Manipulation:** Potential for corrupted data feeds

#### 3. Legal & Regulatory Uncertainty

- **Enforceability:** Legal status varies by jurisdiction
- **Compliance:** KYC/AML requirements
- **Liability:** Who is responsible for bugs?

#### 4. Technical Complexity

- **Gas Costs:** Computation and storage are expensive
- **Scalability:** Limited transactions per second
- **Development:** Steep learning curve

### Smart Contract Use Cases

#### Financial Applications (DeFi)

- **Decentralized Exchanges:** Uniswap, SushiSwap
- **Lending Protocols:** Aave, Compound
- **Stablecoins:** DAI, USDC
- **Yield Farming:** Automated liquidity provision

#### Gaming & NFTs

- **In-game economies:** True digital asset ownership
- **NFT marketplaces:** OpenSea, LooksRare
- **Play-to-earn:** Axie Infinity, STEPN

#### Supply Chain

- **Product tracking:** From manufacturer to consumer
- **Provenance verification:** Authenticity guarantees
- **Automated payments:** Upon delivery confirmation

#### Governance & DAOs

- **Voting systems:** Transparent, tamper-proof voting
- **Treasury management:** Multi-signature requirements
- **Proposal systems:** Community-driven development

### Smart Contract Development Lifecycle

#### 1. Development

- Write code in Solidity or other languages
- Follow security best practices
- Use development frameworks (Hardhat, Truffle)

#### 2. Testing

- Unit tests for all functions
- Integration tests for complex interactions
- Security audits by third parties

#### 3. Deployment

- Deploy to testnet first
- Verify contract code on block explorer
- Initialize with starting parameters

#### 4. Monitoring & Maintenance

- Monitor for unusual activity
- Prepare upgrade mechanisms if needed
- Community governance for changes

### Security Considerations

#### Common Vulnerabilities

- **Reentrancy attacks:** Functions called recursively
- **Integer overflow/underflow:** Math operations exceeding limits
- **Access control:** Unauthorized function execution
- **Front-running:** Transaction ordering manipulation

#### Security Best Practices

- **Use audited libraries:** OpenZeppelin contracts
- **Comprehensive testing:** Multiple test scenarios
- **Formal verification:** Mathematical proof of correctness
- **Bug bounties:** Incentivize security researchers

## 💡 Key Insights from This Chapter

### Major Realizations

1. **Smart contracts are not necessarily legal contracts** - they're automated enforcement mechanisms
2. **Code is law** in smart contract ecosystems - the rules are exactly what's programmed
3. **Immutability is both a feature and a constraint** - careful planning required

### Paradigm Shifts

- **From trust in people** → **trust in code**
- **From manual enforcement** → **automatic execution**
- **From private agreements** → **transparent protocols**

### Why This Matters

- **Developers:** New programming paradigm with real-world consequences
- **Businesses:** Automated, trustless business logic
- **Users:** Transparent, predictable system behavior

## ❓ Questions After This Chapter

- [ ] How do smart contracts interact with the legal system?
- [ ] What happens when a smart contract has a critical bug?
- [ ] How do oracles provide reliable real-world data?
- [ ] What's the difference between EVM and other virtual machines?

## 🛠️ Practical Example: Simple Voting Contract

```solidity
// Simple voting contract
contract SimpleVoting {
    mapping(address => bool) public hasVoted;
    mapping(string => uint) public votesReceived;
    string[] public candidateList;

    constructor(string[] memory candidateNames) {
        candidateList = candidateNames;
    }

    function voteForCandidate(string memory candidate) public {
        require(!hasVoted[msg.sender]);
        require(validCandidate(candidate));

        votesReceived[candidate] += 1;
        hasVoted[msg.sender] = true;
    }

    function validCandidate(string memory candidate) private view returns (bool) {
        for(uint i = 0; i < candidateList.length; i++) {
            if(keccak256(abi.encodePacked(candidateList[i])) ==
               keccak256(abi.encodePacked(candidate))) {
                return true;
            }
        }
        return false;

```

> “Smart contracts let us embed rules and logic into the digital infrastructure itself, so trust is enforced by code rather than institutions.”
