# DeFi Script: Uniswap Swap & Aave Supply

![DeFi Ecosystem](https://i.ibb.co/5GqBsDK/30-Jul-Navigating-the-De-Fi-Ecosystem.png)

## Overview of Script

This script demonstrates the integration of two powerful DeFi protocols—Uniswap and Aave—within a single workflow. It begins by swapping USDC for LINK on Uniswap and then automatically supplies the acquired LINK tokens to Aave, where they start earning interest.


## Key Features:

- **Token Swap on Uniswap:** The script initiates a token swap using Uniswap's V3 protocol, converting USDC into LINK.

- **Supply to Aave:** The script then supplies the LINK tokens to Aave's lending pool, enabling interest generation.

- **Ethereum Sepolia Testnet:** The entire workflow is designed to be executed on the Sepolia testnet, making it easy to test without risking real assets.


## Workflow Summary:

1. **Approval:** The script approves the Uniswap Swap Router contract to spend USDC tokens on the user’s behalf.

2. **Swap:** USDC is swapped for LINK using Uniswap.

3. **Supply to Aave:** The LINK tokens are supplied to Aave's lending pool, enabling the user to earn interest on their LINK holdings.


### Diagram Illustration

Below is a diagram that visually represents the workflow of the script:

![Diagram](https://i.ibb.co/qF6N1YL/Fire-Shot-Capture-436-Chat-GPT-chatgpt-com.png)


## Code Explanation:

### Part A - Input Token Configuration

```javascript
const USDC = { ... };
const LINK = { ... };
```

These objects define the properties of the tokens involved in the swap: USDC and LINK. This includes their addresses on the Sepolia network, number of decimals, and other relevant metadata.

### Part B - Approve Token Function

```javascript
async function approveToken(tokenAddress, tokenABI, amount, wallet) { ... }
```

This function handles the approval process, allowing the Uniswap Swap Router to spend the specified amount of USDC on behalf of the user. Approval is a crucial step before any token transfer or swap.

### Part C - Get Pool Info Function

```javascript
async function getPoolInfo(factoryContract, tokenIn, tokenOut) { ... }
```

This function retrieves information about the liquidity pool used for the swap, including the pool’s address, the tokens involved, and the fee structure. It ensures that the swap happens in the correct pool.

### Part D - Prepare Swap Params Function

```javascript
async function prepareSwapParams(poolContract, signer, amountIn) { ... }
```

This function prepares the parameters required for the Uniswap swap transaction. It includes the token addresses, the amount to swap, the recipient, and other essential details.

### Part E - Execute Swap Function

```javascript
async function executeSwap(swapRouter, params, signer) { ... }
```

This function executes the token swap on Uniswap using the parameters prepared earlier. It sends the transaction to the Ethereum network and waits for confirmation.

### Part F - Main Function

```javascript
async function main(swapAmount) { ... }
```

The main function orchestrates the entire workflow. It approves the Uniswap router to spend USDC, swaps USDC for LINK, and then supplies the LINK to Aave. Error handling ensures that each step is executed correctly.

### Part G - Supply to Aave Function

```javascript
async function supplyToAave(lendingPoolAddress, tokenAddress, amount, wallet) { ... }
```

This function handles the supply of LINK tokens to Aave's lending pool. It approves Aave to spend the LINK tokens and then deposits them into Aave, allowing the user to start earning interest.


## How to Run the Script:

1. **Clone the Repository:** 

```bash
git clone https://github.com/AgosVenezia/DeFi-Script.git
```

2. **Install Dependencies:** 

```bash
npm install
```

3. **Configure Environment Variables:** 

Update the `.env` file with your Sepolia RPC URL and private key.

1. **Run the Script:** 

```bash
node index.js
```


## Conclusion:

This project highlights the composability of DeFi protocols, showing how they can be integrated to create more complex financial strategies. By combining Uniswap and Aave, the script not only demonstrates a basic swap but also adds value by automatically earning interest on the swapped tokens. Feel free to experiment with other DeFi protocols and extend this script further!


#### [A project by Agostina Venezia for StackUp](https://earn.stackup.dev/)