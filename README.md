# Silver: Simple Voting DApp

A minimal decentralized voting app built on Ethereum. Users can create polls with multiple options, and votes are recorded on-chain via MetaMask.

## Features
- Smart contract written in Solidity
- Frontend built with React + shadcn/ui
- Connects directly to Ethereum via MetaMask
- No backend or database — pure Web3

## Get Started
1. Deploy the contract from `smart_contracts/VotingContract.sol`
2. Copy the contract address and ABI into `VotingApp.jsx`
3. Run the frontend:
   ```bash
   npm install
   npm run dev
