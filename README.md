# airdrop-smartcontract
A complete Web3 airdrop project with Solidity smart contract, Hardhat deployment scripts, and a simple frontend (HTML/JS) for users to claim rewards
airdrop-project/
 ├── contracts/
 │   └── Airdrop.sol
 ├── frontend/
 │   ├── index.html
 │   ├── app.js
 │   └── style.css
 ├── scripts/
 │   └── deploy.js
 ├── hardhat.config.js
 ├── package.json
 ├── README.md
 └── .gitignore
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Airdrop {
    address public owner;
    mapping(address => uint256) public rewards;
    mapping(address => bool) public claimed;

    constructor() {
        owner = msg.sender;
    }

    function setReward(address user, uint256 amount) external {
        require(msg.sender == owner, "Only owner");
        rewards[user] = amount;
    }

    function claim() external {
        require(!claimed[msg.sender], "Already claimed");
        uint256 amount = rewards[msg.sender];
        require(amount > 0, "No reward set");
        claimed[msg.sender] = true;
        payable(msg.sender).transfer(amount);
    }

    receive() external payable {}
}
const hre = require("hardhat");

async function main() {
  const Airdrop = await hre.ethers.getContractFactory("Airdrop");
  const airdrop = await Airdrop.deploy();
  await airdrop.waitForDeployment();
  console.log("Airdrop deployed at:", await airdrop.getAddress());
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
let provider, signer, contract;
const contractAddress = "YOUR_DEPLOYED_CONTRACT_ADDRESS";
const abi = [
  "function claim() external",
  "function rewards(address) view returns(uint256)",
  "function claimed(address) view returns(bool)"
];

document.getElementById("connect").onclick = async () => {
  provider = new ethers.BrowserProvider(window.ethereum);
  signer = await provider.getSigner();
  contract = new ethers.Contract(contractAddress, abi, signer);
  alert("Wallet connected!");
};

document.getElementById("claim").onclick = async () => {
  const tx = await contract.claim();
  await tx.wait();
  alert("Airdrop claimed!");
};

body {
  font-family: Arial, sans-serif;
  background: #101820;
  color: #f2f2f2;
  text-align: center;
  padding: 50px;
}
button {
  margin: 10px;
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  background: #00c4ff;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
}
button:hover {
  background: #009dcf;
}
# 🚀 Airdrop Project

This project is a simple Ethereum airdrop contract with a frontend interface.

## Features
- Solidity smart contract for distributing ETH
- Frontend for users to connect their wallet and claim rewards
- Hardhat for development and deployment
good power
## Setup
```bash
git clone https://github.com/YOUR_USERNAME/airdrop-project.git
cd airdrop-project
npm install
npx hardhat compile
npx hardhat run scripts/deploy.js --network sepolia
M251167m@
---s ready to upload**, so you don’t need to copy each manually? https://cloud.google.com/application/web3/faucet/ethereum/sepolia
good power
Proof of AI refers to Proof of Artificial Intelligence (PoAI), a consensus mechanism specifically designed for the AI economy. It ensures fair attribution and rewards across contributions like data, models, and agents, promoting transparency and collaboration within a decentralized AI ecosystem.⠀⠀
LUMIDA3586
Have you tried Qwen3 235B for deeper reasoning?
Did you find any model that feels consistently reliable?
Hey, are you trying to build a community online?
https://testnet.bitverse.zone/app/?token=BTC-USD
Are you looking for something more organized?
Are you thinking about launching an online product?
Just arrived at Camp Haven 🫎🔥 First night by the campfire, roasting marshmallows and sharing stories under the stars ✨ Loving every moment here! @DataHaven_xyz
