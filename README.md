# Foundry DeFi Stablecoin Collection

This is a smart contract project for creating a decentralized stablecoin system using Foundry. Based on the Cyfrin Solidity Course, this project implements a USD-pegged stablecoin where users can deposit WETH and WBTC as collateral to mint DSC (Decentralized Stablecoin) tokens.

## 📌 Features

- **Decentralized Stablecoin (DSC)** pegged to USD with overcollateralization
- **Multi-collateral support** for WETH and WBTC deposits
- **Chainlink price feeds** integration for accurate collateral valuation
- **Liquidation mechanism** to maintain system stability
- **Comprehensive testing suite** across multiple environments
- **Gas-optimized** contract deployment and verification
- **Built with Foundry** for robust Ethereum development

## 🚀 Getting Started

### 1. Install Requirements

Make sure you have installed:

- [Git](https://git-scm.com/)
- [Foundry](https://getfoundry.sh/)
- **Optional**: [Gitpod](https://gitpod.io/) for cloud development

### 2. Clone the Repository

```bash
git clone https://github.com/mvirgiawancr/foundry-defi-stablecoin.git
cd foundry-defi-stablecoin
forge build
```

### 3. Configure Environment Variables

Create a `.env` file based on `.env.example`, then add:

```env
SEPOLIA_RPC_URL=<your_rpc_url>
PRIVATE_KEY=<your_private_key>
ETHERSCAN_API_KEY=<your_etherscan_api_key>
```

## 🔧 Usage

### 1. Start a Local Node

```bash
make anvil
```

### 2. Connect MetaMask to Anvil Local Network

To view your stablecoin system in MetaMask while using Anvil:

**Open MetaMask and add a new network with these settings:**

- Network Name: `Anvil Local`
- RPC URL: `http://127.0.0.1:8545`
- Chain ID: `31337`
- Currency Symbol: `ETH`

**Import an Anvil test account to MetaMask:**

- Click on "Import Account" in MetaMask
- Enter one of the private keys provided by Anvil when it starts (e.g., the default key: `0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d`)
- This account should have 10,000 test ETH

After deploying contracts on your local network, you can add the DSC token to MetaMask to view your balance.

### 3. Deploy Smart Contracts

**For local deployment:**

```bash
# Deploy DSC Engine and Stablecoin contracts
make deploy
```

**For testnet deployment:**

```bash
make deploy ARGS="--network sepolia"
```

### 4. Testing

Run various test suites:

```bash
# Local unit tests
forge test

# Forked network tests
forge test --fork-url $SEPOLIA_RPC_URL

# Test coverage
forge coverage

# Coverage with detailed report
forge coverage --report debug
```

## 📊 Scripts and Utilities

### Gas Estimation

```bash
forge snapshot
```

### Code Formatting

```bash
forge fmt
```

### Static Analysis with Slither

```bash
slither . --config-file slither.config.json
```

### 5. Adding DSC Token to MetaMask

To view your DSC tokens in MetaMask:

1. Go to the "Tokens" tab in MetaMask
2. Click "Import Token"
3. Enter the following details:
   - **Token Address**: The deployed DSC contract address
   - **Token Symbol**: `DSC`
   - **Token Decimals**: `18`

For the stablecoin system, after contracts are deployed:

- The DSC token will be available for viewing in MetaMask
- You can monitor your collateral and DSC token balances
- If using Anvil, your tokens will persist only as long as your local node is running

**Note**: When using Anvil, your contract state will persist only as long as your local node is running. Restarting Anvil will reset the blockchain state unless you've configured it to persist data.

## 🧩 Contract Architecture

### DSCEngine

The core engine that handles:

- **Collateral Management**: Deposit and withdrawal of WETH/WBTC
- **DSC Minting/Burning**: Create and destroy stablecoin tokens
- **Liquidation Logic**: Maintain system health through liquidations
- **Price Feed Integration**: Real-time asset pricing via Chainlink oracles

### DecentralizedStablecoin (DSC)

- **ERC-20 compliant** stablecoin token
- **Mintable/Burnable** only by the DSC Engine
- **USD-pegged** value maintained through overcollateralization

**Key features:**

- Overcollateralization requirement (200% minimum collateral ratio)
- Chainlink price feeds for accurate asset valuation
- Liquidation incentives to maintain system stability
- Health factor monitoring for user positions

## 🔗 Dependencies

This project uses the following libraries:

```bash
forge install openzeppelin/openzeppelin-contracts@v4.8.3 --no-commit
forge install smartcontractkit/chainlink-brownie-contracts --no-commit
```

## 🌐 Example Deployed Contracts

### Sepolia Testnet:

- **DSC Engine**: [0x091ea0838ebd5b7dda2f2a641b068d6d59639b98](https://sepolia.etherscan.io/address/0x091ea0838ebd5b7dda2f2a641b068d6d59639b98#code)
- **DSC Token**: [0xf30021646269007b0bdc0763fd736c6380602f2f](https://sepolia.etherscan.io/address/0xf30021646269007b0bdc0763fd736c6380602f2f#code)

## 🛡️ Security Notes

- **Use test funds only** on testnets - never real funds for development
- **Always verify contract addresses** before any interactions
- **Monitor gas costs** when deploying and testing
- **Test thoroughly** before considering mainnet deployment

## 📚 Learning Objectives

This project demonstrates:

- **DeFi Protocol Architecture**: Understanding stablecoin mechanisms
- **Smart Contract Interactions**: Multiple contract system design
- **Oracle Integration**: Chainlink price feed implementation
- **Testing Strategies**: Comprehensive test suite development
- **Deployment Patterns**: Multi-network deployment strategies

## 📜 License

This project is created for educational purposes and is free to use for further development.

## 💙 Thank You!

If you find this project helpful, don't forget to ⭐ the repository on GitHub!

Made with 💖 by Virgi

---

_Note: This is an educational project based on the Cyfrin Foundry Solidity Course. Focus on learning the core concepts of DeFi and stablecoin mechanisms._
