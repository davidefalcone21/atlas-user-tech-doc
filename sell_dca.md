# User Action Requirement: Sell Coin (DCA)

---

## 1. Overview

- **User Action:**  
  `Sell Coin (DCA)`

- **Short Description:**  
  Allows users to create dollar-cost averaging (DCA) sell orders that automatically distribute the selling of a token over time within specified price ranges and intervals to optimize exit prices and reduce impact on market liquidity.

- **Scope:**  
  Chain-specific advanced trading function that enables users to implement automated exit strategies with customizable parameters for timing, price ranges, and duration.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point 1:** User sends contract address directly to the chat, switches to SELL mode, then DCA mode
    - **Entry Point 2:** User clicks "Sell" button, provides contract address when prompted, then switches to DCA mode
    - **Entry Point 3:** User clicks "Sell [Token]" from positions screen, then switches to DCA mode
    - **Additional parameters:**
        - Wallet selection
        - Swap/Limit/DCA mode selection (DCA selected)
        - Buy/Sell mode selection (SELL selected)
        - Slippage setting
        - Anti-MEV mode setting
        - Priority fee/Tip settings
        - Amount/percentage of token to sell over the DCA period
        - Minimum price boundary (in USD or market cap)
        - Maximum price boundary (in USD or market cap)
        - Time interval between sales (e.g., 30m)
        - Total duration of the DCA strategy (e.g., 12h)
        - Special sell options (INITIALS, 100%, 100% TO PGN)

- **Expected Outcome / Response:**  
  The process has three main stages:
    1. Token Information Display: Detailed token metrics, market data, and wallet balances
    2. DCA Sell Strategy Configuration: Interactive buttons for setting all parameters including price boundaries, intervals, and duration
    3. Strategy Creation Confirmation: Details of the created DCA strategy and monitoring status

- **User Interface Behavior:**  
  **Stage 1: Token Information Display**
  ```
  🪙 [Token Name] ([Token Symbol]) 🔗 (blockchain explorer link)
  [Contract Address]
  🟢 Mint Renounced
  🟢 Freeze Renounced
  🧢 MC: $[Market Cap]
  💧 LIQ: $[Liquidity USD] ([Liquidity Native])
  💰 Price: $[Token Price]
  🚀 DEX: [DEX Name]
  👥 Team Bundle: [Yes/No]
  🎯 Bundled Percent: [Percentage]%
  Top 10 holders %
  Snipers
  🔈 Volume:
  5m: $[5min Vol] | 15m: $[15min Vol]
  1h: $[1h Vol] | 24h: $[24h Vol]
  💳 [Wallet Name] Balance: [Native Token Balance]
  🪙 Token Holdings: [Token Amount] (+ PNL)
  📊 [Chart Link 1] | [Chart Link 2]
  ```

  **Stage 2: DCA Sell Configuration Buttons**
  ```
  Row 1:
  "🔄 REFRESH"
  
  Row 2:
  "⬅️ PREV" | "[WALLET NAME]" | "➡️ NEXT" (wallet selection)
  
  Row 3:
  "SWAP" | "LIMIT" | "DCA ✓" (mode selection)
  
  Row 4:
  "BUY MODE" | "SELL MODE ✓" (direction selection)
  
  Row 5:
  "SLIPPAGE" | "ANTI MEV MODE ([Current Setting])"
  
  Row 6:
  "PRIORITY FEE" | "TIP"
  
  Row 7:
  "Sell [Amount 1] [Native Token]" | "Sell [Amount 2] [Native Token]" (preset amounts)
  
  Row 8:
  "Sell 25%" | "Sell 50%" (preset percentages)
  
  Row 9:
  "X [Native Token]" (custom amount)
  
  Row 10:
  "% [Native Token]" (custom percentage)
  
  Row 11:
  "SELL INITIALS" | "SELL 100%"
  
  Row 12:
  "SELL 100% TO PGN" (SOL chain only)
  
  Row 13:
  "MIN PRICE $[Value]" (minimum price boundary)
  
  Row 14:
  "MAX PRICE $[Value]" (maximum price boundary)
  
  Row 15:
  "INTERVAL 30M" | "DURATION 12H"
  
  Row 16:
  "CREATE ORDER"
  ```

  **Stage 3: DCA Creation Messages**
    - Confirmation message: "DCA sell strategy created: Total sale of [Amount/Percentage] of [Token Symbol] spread over [Duration] with sales every [Interval]. Price range: $[Min Price] to $[Max Price]. The first sale will execute shortly. You will be notified after each execution."

### 2.2 Process Flow
- **Step 1:** User initiates the process by one of the entry points and switches to DCA mode in SELL direction.

- **Step 2:** Bot automatically identifies the blockchain and retrieves token information.

- **Step 3:** Bot displays comprehensive token information and the DCA sell configuration interface.

- **Step 4:** User configures the DCA sell strategy by:
    - Selecting the desired wallet using PREV/NEXT buttons
    - Confirming DCA mode and SELL mode
    - Setting slippage if desired
    - Setting Anti-MEV protection if desired
    - Setting priority fee/tip if desired
    - Selecting an amount or percentage to sell over the DCA period:
        - Using preset native token value buttons
        - Using preset percentage buttons (25%, 50%)
        - Entering a custom amount in native token value
        - Entering a custom percentage
        - Selecting special options (INITIALS, 100%, 100% TO PGN)
    - Setting the minimum price boundary (can be USD price or market cap value)
    - Setting the maximum price boundary (can be USD price or market cap value)
    - Confirming or adjusting the time interval between sales (default 30m)
    - Confirming or adjusting the total duration of the DCA strategy (default 12h)

- **Step 5:** User clicks "CREATE ORDER" to finalize the DCA sell strategy.

- **Step 6:** Bot confirms the strategy creation with details and begins the automated DCA process.

- **Step 7:** For each interval during the specified duration:
    - Bot checks if the current price is within the specified range (min to max price)
    - If in range, executes a proportional sell order based on the interval and total amount/percentage
    - User receives notification with transaction details after each execution
    - Bot updates the strategy status with progress and remaining tokens to sell

- **Step 8:** When the strategy completes (duration reached or total amount/percentage sold):
    - Bot sends a final summary of all executions
    - User receives total native tokens acquired, average sale price, and other statistics