# Scaffold-Stacks

**Scaffold-Stacks** is a developer-friendly toolkit for building decentralized applications (dApps) on the [Stacks blockchain](https://www.stacks.co/), inspired by [Scaffold-ETH](https://github.com/scaffold-eth/scaffold-eth). It provides a pre-configured stack to accelerate Stacks dApp development, featuring a React frontend, Clarity smart contracts, Stacks.js for blockchain interactions, and Clarinet for local testing and deployment. Build Bitcoin-secured dApps—like DeFi, NFTs, or decentralized identity—with ease, leveraging Stacks’ unique connection to Bitcoin’s security and finality.

## Why Scaffold-Stacks?

- **Rapid Prototyping**: Jumpstart your Stacks dApp with a ready-to-use template, similar to Scaffold-ETH but tailored for Stacks’ Bitcoin layer.
- **Clarity Smart Contracts**: Write secure, predictable smart contracts in Clarity, with examples for common use cases (e.g., Bitcoin-backed NFTs, BNS domains).
- **Bitcoin Integration**: Build dApps that settle on Bitcoin, using Stacks’ Proof-of-Transfer (PoX) and upcoming sBTC for trustless Bitcoin interactions.
- **Developer-Friendly**: Includes a React frontend with Stacks.js, local testing with Clarinet, and clear documentation for beginners and pros alike.
- **Community-Driven**: Inspired by Scaffold-ETH’s ethos, Scaffold-Stacks encourages contributions to grow the Stacks developer ecosystem.

## Features

- **Frontend**: React app with Stacks.js for wallet connections (Hiro Wallet) and contract interactions.
- **Smart Contracts**: Example Clarity contracts for minting NFTs, managing BNS domains, and basic DeFi (e.g., lending with BTC collateral).
- **Testing**: Clarinet for local contract testing and deployment to Stacks’ testnet.
- **Wallet Integration**: Connects to Hiro Wallet for STX transactions and Bitcoin-anchored operations.
- **Bitcoin Awareness**: Contracts can read Bitcoin’s state (e.g., verify BTC transactions) using Clarity’s native functions.

## Prerequisites

Before you start, ensure you have the following installed:

- [Node.js](https://nodejs.org/) (v16 or later)
- [Yarn](https://yarnpkg.com/) (or npm)
- [Clarinet](https://docs.hiro.so/clarinet) (Stacks’ smart contract development tool)
- [Hiro Wallet](https://wallet.hiro.so/) (browser extension for Stacks)
- [Rust](https://www.rust-lang.org/) (required for Clarity development)
- [Docker](https://www.docker.com/) (optional, for running a local Stacks node)
- A code editor like [VSCode](https://code.visualstudio.com/) with the [Clarity extension](https://marketplace.visualstudio.com/items?itemName=HiroSystems.clarity)

## Getting Started

Follow these steps to set up and run Scaffold-Stacks locally.

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/scaffold-stacks.git
cd scaffold-stacks
```

*Note*: Replace `your-username` with the actual repository owner if forked.

### 2. Install Dependencies

Install frontend and Clarinet dependencies:

```bash
# Install React app dependencies
cd packages/frontend
yarn install

# Install Clarinet (if not globally installed)
cd ../contracts
clarinet check
```

### 3. Run a Local Stacks Node

Start a local Stacks blockchain for development using Clarinet or Docker:

```bash
# Using Clarinet
cd packages/contracts
clarinet integrate

# OR using Docker (alternative)
docker-compose up -d
```

This spins up a local Stacks node, Bitcoin node, and API at `http://localhost:20443`.

### 4. Deploy Clarity Contracts

Deploy the example Clarity contracts to the local network:

```bash
cd packages/contracts
clarinet deploy --network devnet
```

This deploys contracts like `nft-mint.clar` and `simple-defi.clar` to your local Stacks node.

### 5. Start the Frontend

Launch the React frontend to interact with your dApp:

```bash
cd packages/frontend
yarn start
```

Open `http://localhost:3000` in your browser. Connect your Hiro Wallet to interact with the deployed contracts.

### 6. Test Contracts

Run unit tests for Clarity contracts:

```bash
cd packages/contracts
clarinet test
```

This executes tests in the `tests/` directory, ensuring your contracts behave as expected.

## Project Structure

```
scaffold-stacks/
├── packages/
│   ├── contracts/              # Clarity smart contracts and tests
│   │   ├── contracts/          # Clarity contract files (e.g., nft-mint.clar)
│   │   ├── tests/              # Clarinet test files
│   │   ├── Clarinet.toml       # Clarinet configuration
│   │   └── settings/           # Deployment settings
│   ├── frontend/               # React frontend
│   │   ├── src/                # React components, hooks, and Stacks.js integration
│   │   ├── public/             # Static assets
│   │   └── package.json        # Frontend dependencies
├── docker-compose.yml          # Docker setup for local Stacks node
└── README.md                   # This file
```

## Example Use Cases

Scaffold-Stacks includes example contracts to kickstart your project:

1. **Bitcoin-Backed NFT**: Mint NFTs on Stacks that require a Bitcoin transaction as payment, verified via Clarity’s Bitcoin state-reading capabilities.
2. **Simple DeFi**: A lending protocol where users deposit STX as collateral and borrow against BTC, with transactions settled on Bitcoin.
3. **BNS Domain Manager**: Register and manage .btc domains using Stacks’ Blockchain Naming System.

To explore these, check the contracts in `packages/contracts/contracts/` and their frontend interfaces in `packages/frontend/src/components/`.

## Configuration

Customize your setup by editing these files:

- `packages/contracts/Clarinet.toml`: Configure network settings (devnet, testnet, mainnet).
- `packages/frontend/src/config.js`: Update contract addresses and API endpoints.
- `docker-compose.yml`: Adjust ports or node settings for the local Stacks environment.

## Testing on Stacks Testnet

To deploy to Stacks’ testnet:

1. Update `Clarinet.toml` to use the testnet network.
2. Fund your Hiro Wallet with testnet STX via the [Stacks faucet](https://explorer.stacks.co/faucet).
3. Deploy contracts:

```bash
cd packages/contracts
clarinet deploy --network testnet
```

4. Update `packages/frontend/src/config.js` with the testnet contract addresses and API (`https://api.testnet.hiro.so`).

## Contributing

We welcome contributions to make Scaffold-Stacks better! To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit (`git commit -m "Add your feature"`).
4. Push to your fork (`git push origin feature/your-feature`).
5. Open a pull request with a clear description of your changes.

Please follow the [code of conduct](CODE_OF_CONDUCT.md) and check the [contributing guidelines](CONTRIBUTING.md).

## Resources

- [Stacks Documentation](https://docs.stacks.co/) – Official Stacks developer guides.
- [Clarity Documentation](https://docs.hiro.so/clarinet) – Learn Clarity and Clarinet.
- [Stacks.js](https://github.com/hirosystems/stacks.js) – Library for frontend integration.
- [Hiro Wallet](https://wallet.hiro.so/) – Wallet for STX and Bitcoin transactions.
- [Stacks Community](https://community.stacks.org/) – Join the Stacks Discord or X (@Stacks).
- [Scaffold-ETH](https://github.com/scaffold-eth/scaffold-eth) – Inspiration for this project.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

- Built with ❤️ by the Stacks developer community.
- Thanks to [Hiro Systems](https://www.hiro.so/) for Clarinet, Stacks.js, and developer tools.

---

Happy building on Stacks! 🚀 For issues or questions, open a GitHub issue or reach out on the [Stacks Discord](https://community.stacks.org/).
