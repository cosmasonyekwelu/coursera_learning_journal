# Chapter: Digital Assets (Tokens)

## Key Concepts & Definitions

- **Token / Digital asset**: a representation of value or rights recorded on a blockchain.
- **Native tokens**: tokens intrinsic to a blockchain protocol (e.g. Ether).
- **Utility tokens**: provide access or functionality within a protocol/application.
- **Governance tokens**: grant voting and decision-making rights in decentralized systems.
- **Asset-backed / Security tokens**: tied to real-world assets or financial instruments.
- **Non-Fungible Tokens (NFTs)**: unique tokens representing unique assets (e.g. digital art).

## Role & Importance in Web3

- Enables **ownership** and **value transfer** natively on-chain.
- Aligns **incentives** among users & participants.
- Makes **rules programmable** (minting, burning, transfers) via smart contracts.

## Challenges & Considerations

- Regulatory scrutiny (some tokens may be securities)
- Governance design and power concentration
- Transaction costs & scalability
- Security issues (smart contract vulnerabilities, exploits)
- Interoperability across chains

## The Pre-Blockchain Problem

- Digital files are infinitely reproducible (copy-paste)
- No native concept of digital ownership or scarcity
- Required trusted intermediaries for digital assets

## Blockchain Solution

- **Immutable ledger** prevents double-spending
- **Cryptographic proof** of ownership
- **Decentralized consensus** on asset state

## Major Realizations

1. **Tokens are the building blocks** of Web3 economies
2. **Digital scarcity is now possible** without central authorities
3. **Programmable money** enables entirely new applications

## Important Distinctions

- **Cryptocurrencies vs Tokens:** Native vs built-on-top assets
- **Fungible vs Non-Fungible:** Interchangeable vs unique assets
- **Utility vs Security Tokens:** Usage vs investment characteristics

## Why This Matters

- **Users:** True digital property rights for the first time
- **Developers:** New economic models and incentive structures
- **Businesses:** Token-based customer engagement and loyalty

## ERC-20 Token Example

```solidity
// Simplified ERC-20 interface
contract ERC20 {
    function transfer(address to, uint256 value) public returns (bool);
    function balanceOf(address owner) public view returns (uint256);
    function totalSupply() public view returns (uint256);
}

```

## Reflection / Questions

- Which token type do I think will see more mass adoption (utility, governance, asset-backed, NFTs)?
- How should token governance be designed to avoid centralization?
- What are trade-offs between programmability and security?
- How would you design a token for a use-case (e.g. decentralized marketplace, identity) — what rights, constraints, rules would you include?

## Important Quotes / Lines

> “Tokens allow ownership and value transfer to be native to the digital world.”
>
> “Tokens make rules and scarcity programmable via smart contracts.”

# 🪙 Token Types Cheat sheet

## By Fungibility

| Type                   | Characteristics              | Examples            | Standards |
| ---------------------- | ---------------------------- | ------------------- | --------- |
| **Fungible**           | Interchangeable, identical   | BTC, ETH, USDC      | ERC-20    |
| **Non-Fungible (NFT)** | Unique, verifiable           | CryptoPunks, BAYC   | ERC-721   |
| **Semi-Fungible**      | Both fungible & non-fungible | Game items, tickets | ERC-1155  |

## By Function

| Type            | Purpose              | Examples              |
| --------------- | -------------------- | --------------------- |
| **Payment**     | Medium of exchange   | BTC, ETH, stablecoins |
| **Utility**     | Access to services   | UNI, AAVE             |
| **Governance**  | Voting rights        | COMP, MKR             |
| **Security**    | Investment contracts | Tokenized stocks      |
| **Collectible** | Digital art/items    | NFTs                  |
