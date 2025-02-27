# User Action Requirement: Buy Coin (DCA)

---

## 1. Overview

- **User Action:**  
  `Buy Coin (DCA)`

- **Short Description:**  
  Allows users to create dollar-cost averaging (DCA) orders that automatically spread purchases of a token over time within specified price ranges and intervals to reduce the impact of volatility.

- **Scope:**  
  Chain-specific advanced trading function that enables users to implement automated investment strategies with customizable parameters for timing, price ranges, and duration.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point 1:** User sends contract address directly to the chat, then switches to DCA mode
    - **Entry Point 2:** User clicks "Buy" button, provides contract address when prompted, then switches to DCA mode
    - **Additional parameters:**
        - Wallet selection
        - Swap/Limit/DCA mode selection (DCA selected)
        - Buy/Sell mode selection
        - Slippage setting
        - Anti-MEV mode setting
        - Priority fee/Tip settings
        - Total amount of native token for the DCA strategy
        - Minimum price boundary (in USD or market cap)
        - Maximum price boundary (in USD or market cap)
        - Time interval between purchases (e.g., 30m)
        - Total duration of the DCA strategy (e.g., 12h)

- **Expected Outcome / Response:**  
  The process has three main stages:
    1. Token Information Display: Detailed token metrics, market data, and wallet balances (same as Swap/Limit)
    2. DCA Strategy Configuration: Interactive buttons for setting all parameters including price boundaries, intervals, and duration
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

  **Stage 2: DCA Configuration Buttons**
  ```
  Row 1:
  "🔄 REFRESH"
  
  Row 2:
  "⬅️ PREV" | "[WALLET NAME]" | "➡️ NEXT" (wallet selection)
  
  Row 3:
  "SWAP" | "LIMIT" | "DCA ✓" (mode selection)
  
  Row 4:
  "BUY MODE ✓" | "SELL MODE" (direction selection)
  
  Row 5:
  "SLIPPAGE" | "ANTI MEV MODE ([Current Setting])"
  
  Row 6:
  "PRIORITY FEE" | "TIP"
  
  Row 7:
  "[Amount 1] [Native Token]" | "[Amount 2] [Native Token]"
  
  Row 8:
  "[Amount 3] [Native Token]" | "[Amount 4] [Native Token]"
  
  Row 9:
  "X [Native Token]" (custom amount)
  
  Row 10:
  "MIN PRICE $[Value]" (minimum price boundary)
  
  Row 11:
  "MAX PRICE $[Value]" (maximum price boundary)
  
  Row 12:
  "INTERVAL 30M" | "DURATION 12H"
  
  Row 13:
  "CREATE ORDER"
  ```

  **Stage 3: DCA Creation Messages**
    - Confirmation message: "DCA strategy created: Total investment of [Amount] [Native Token] into [Token Symbol] spread over [Duration] with purchases every [Interval]. Price range: $[Min Price] to $[Max Price]. The first purchase will execute shortly. You will be notified after each execution."

### 2.2 Process Flow
- **Step 1:** User initiates the process by either:
    - Sending a contract address directly to the chat
    - Clicking "Buy" button and then providing the contract address when prompted

- **Step 2:** Bot automatically identifies the blockchain and retrieves token information (same as Swap/Limit functions).

- **Step 3:** Bot displays comprehensive token information and the DCA configuration interface.

- **Step 4:** User selects "DCA" mode from the trade type options.

- **Step 5:** User configures the DCA strategy by:
    - Selecting the desired wallet using PREV/NEXT buttons
    - Confirming buy mode (vs. sell)
    - Setting slippage if desired
    - Setting Anti-MEV protection if desired
    - Setting priority fee/tip if desired
    - Selecting the total amount of native token for the entire DCA strategy
    - Setting the minimum price boundary (can be USD price or market cap value)
    - Setting the maximum price boundary (can be USD price or market cap value)
    - Confirming or adjusting the time interval between purchases (default 30m)
    - Confirming or adjusting the total duration of the DCA strategy (default 12h)

- **Step 6:** User clicks "CREATE ORDER" to finalize the DCA strategy.

- **Step 7:** Bot confirms the strategy creation with details and begins the automated DCA process.
- Call back button to return to see list of open orders

- **Step 8:** For each interval during the specified duration:
    - Bot checks if the current price is within the specified range (min to max price)
    - If in range, executes a proportional buy order based on the interval and total amount
    - User receives notification with transaction details after each execution
    - Bot updates the strategy status with progress and remaining budget

- **Step 9:** When the strategy completes (duration reached or total amount used):
    - Bot sends a final summary of all executions
    - User receives total tokens acquired, average purchase price, and other statistics
    - Call back button to return to positions of the wallet

---

## 3. Affected Systems and Dependencies

- **Chain Specific Requirements:**  
  `[Indicate if this action is chain-specific. For example, “This action applies only to the Binance Smart Chain and Ethereum networks” or “This action displays portfolio data across all chains, with sorting options by chain.”]`

- **Integration Points:**
    - **Telegram API:** `[Details regarding message formatting, command parsing, etc.]`
    - **External Trading APIs / Exchanges:** `[Details on order submission, tracking, and status updates.]`
    - **Blockchain Network APIs:** `[Details on blockchain-specific requirements such as fee calculations, chain validations, etc.]`
    - **Signal Providers (if applicable):** `[Describe how signals affect this action.]`

- **Portfolio / Order Management:**  
  `[Specify how this action interacts with the portfolio system (e.g., updating portfolio balances, order histories, etc.).]`

- **Other Systems:**  
  `[List any other affected or integrated systems.]`

---

## 4. Error Handling and Edge Cases

- **Common Error Scenarios:**
    - `[Describe a scenario, e.g., “Invalid order parameters” and how the bot should respond.]`
    - `[Example: “User tries to cancel an order that does not exist.”]`

- **Validation & Fallback Mechanisms:**  
  `[Detail any input validations, fallback procedures, or safety checks that should be in place.]`

---

## 5. Non-Functional Requirements

- **Performance:**  
  `[Specify performance metrics such as maximum response time or acceptable latency.]`

- **Security:**  
  `[Outline security measures including data encryption, authentication, and secure session management.]`

- **Scalability:**  
  `[Discuss how the system should handle growth in user base and transaction volume.]`

- **Usability:**  
  `[Provide guidelines on the user experience, including clarity of commands and response messages.]`

---

## 6. Future Enhancements

- `[List any potential improvements or additional features that could be implemented in future releases.]`

---

**Notes:**
- Replace all placeholders (e.g., `[Action Name]`) with the specific details for the user action.
- Use this template to create individual requirement specification pages for each user action (e.g., `/start`, `/place_limit_order`, `/cancel_order`, `/order_status`, etc.).
- Ensure that each requirement clearly defines how the action functions and its impact on related systems.