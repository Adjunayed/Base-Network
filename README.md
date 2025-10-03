Base Network:
A Solidity & Hardhat starter project for building, testing, and deploying smart contracts on Base (Coinbase’s Layer 2).

📖 Overview

This project helps developers to:

Write & compile Solidity smart contracts.

Test contracts with Hardhat.

Deploy on Base Sepolia Testnet and Base Mainnet.

Verify contracts on BaseScan / Blockscout.


🛠 Tech Stack

Solidity

Hardhat

OpenZeppelin Contracts

Base Network (L2 by Coinbase)


⚡ Installation

# clone repo
git clone https://github.com/<your-username>/Base-Network.git
cd Base-Network

# install dependencies
npm install

# compile contracts
npx hardhat compile

# run tests
npx hardhat test


---

🔑 Environment Variables

তুমি একটি .env ফাইল তৈরি করবে (উদাহরণ নিচে দেওয়া হলো):

PRIVATE_KEY=0xYOUR_WALLET_PRIVATE_KEY
BASE_MAINNET_RPC=https://mainnet.base.org
BASE_SEPOLIA_RPC=https://sepolia.base.org
BASESCAN_API_KEY=your_basescan_api_key


---

⚙️ Hardhat Configuration (example)

hardhat.config.js

require('dotenv').config();
require("@nomicfoundation/hardhat-toolbox");

const { PRIVATE_KEY, BASE_MAINNET_RPC, BASE_SEPOLIA_RPC, BASESCAN_API_KEY } = process.env;

module.exports = {
  solidity: "0.8.20",
  networks: {
    hardhat: {},
    baseSepolia: {
      url: BASE_SEPOLIA_RPC || "https://sepolia.base.org",
      chainId: 84532,
      accounts: [PRIVATE_KEY]
    },
    baseMainnet: {
      url: BASE_MAINNET_RPC || "https://mainnet.base.org",
      chainId: 8453,
      accounts: [PRIVATE_KEY]
    }
  },
  etherscan: {
    apiKey: {
      baseMainnet: BASESCAN_API_KEY,
      baseSepolia: BASESCAN_API_KEY
    }
  }
};


---

🚀 Deployment

Deploy to Base Sepolia Testnet

npx hardhat run --network baseSepolia scripts/deploy.js

Deploy to Base Mainnet

npx hardhat run --network baseMainnet scripts/deploy.js


---

✅ Verify Contract

npx hardhat verify --network baseMainnet <DEPLOYED_CONTRACT_ADDRESS> "arg1" "arg2"


---

📂 Project Structure

/contracts     -> Solidity contracts  
/scripts       -> Deployment scripts  
/test          -> Unit tests  
.env           -> Environment variables  
hardhat.config.js  
README.md


---

🔐 Security Notes

Never commit .env with private keys.

Use multisig or hardware wallets for production deployment.

Always test on Base Sepolia before mainnet deployment.



---

📚 Resources

Base Official Docs

BaseScan Explorer

Hardhat Docs

