# BitVault Protocol: STX Staking & Governance System

## Overview

**BitVault Protocol** is a comprehensive and secure smart contract system for the [Stacks blockchain](https://www.stacks.co/), designed to facilitate **tiered STX staking**, **rewards optimization**, and **decentralized governance**. This protocol introduces a layered reward system based on stake size and lock duration, empowering users with voting rights for protocol upgrades while reinforcing STX-Bitcoin alignment.

## Key Features

### **Staking Mechanism**

- **Flexible Lock Periods**: Choose between 0, 1 month, or 2 months (`0`, `4320`, or `8640` blocks).
- **Tiered Rewards**: Incentives grow with staking amount and lock duration.
- **Cooldown Period**: Unstaking initiates a 24-hour (1440 blocks) waiting period to enhance liquidity security.

### **Governance System**

- **Proposal Lifecycle**: Users with sufficient voting power can submit proposals.
- **On-Chain Voting**: All voting activity is publicly recorded and weighted by user influence.
- **Security Thresholds**: Each proposal must meet minimum participation levels to pass.

### **Tier System**

- Tier 1: ≥ 1,000,000 STX – Basic features
- Tier 2: ≥ 5,000,000 STX – Enhanced governance & rewards
- Tier 3: ≥ 10,000,000 STX – Full access to premium features

### **Data Tracking**

- Individual staking positions
- User reward multipliers
- Governance activity
- Contract STX pool metrics

## Contract Components

### Token

- `BITVAULT-TOKEN`: A placeholder fungible token definition for future extensions (e.g., reward distributions, analytics tracking).

### Public Functions

| Function | Description |
|---------|-------------|
| `initialize-contract` | Sets up initial tier configurations (admin only). |
| `stake-stx` | Lock STX into the protocol with optional duration. |
| `initiate-unstake` | Begin unstaking; triggers cooldown. |
| `complete-unstake` | Finalize STX withdrawal after cooldown period. |
| `create-proposal` | Submit a new governance proposal. |
| `vote-on-proposal` | Cast a vote for/against an active proposal. |
| `pause-contract` / `resume-contract` | Emergency controls by contract owner. |

### Read-Only Utilities

| Function | Description |
|----------|-------------|
| `get-stx-pool` | Total STX in staking pool. |
| `get-contract-owner` | Contract deployer identity. |
| `get-proposal-count` | Total proposals created. |

## Core Logic & Formulas

- **Rewards Calculation**:
  \[
  \text{Rewards} = \frac{{\text{Stake} \times \text{Base Rate} \times \text{Multiplier} \times \text{Blocks}}}{{14400000}}
  \]
  - Base rate: 5%
  - Tier multipliers: 1x, 1.5x, 2x
  - Lock multipliers: 1x (0 months), 1.25x (1 month), 1.5x (2 months)

- **Voting Threshold**: Users must have ≥ 1,000,000 `voting-power` to create proposals. Proposals must achieve ≥ 1,000,000 votes to be valid.

## Security & Controls

- **Admin Access**: All admin functions restricted to `CONTRACT-OWNER`.
- **Emergency Mode**: Global `pause` mechanism prevents staking/un-staking during critical events.
- **Error Handling**: Explicit error codes with strong pattern matching and validation guards (e.g., lock periods, voting periods, stake thresholds).

## Deployment Details

- **Stacks Compatibility**: Built on Clarity for use with the Stacks 2.1+ blockchain.
- **Bitcoin Awareness**: Designed to ensure STX staking aligns with the broader Bitcoin economic layer.

## Future Extensions

- Integration with BTC-pegged rewards via Bitcoin PoX
- NFT-based governance badges
- Delegated voting power model
- Staking analytics and visual dashboards
