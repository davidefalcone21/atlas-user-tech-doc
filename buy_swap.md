# User Action Requirement: Buy Coin (Swap)

---

## 1. Overview

- **User Action:**  
  `Buy Coin (Swap)`

- **Short Description:**  
  Allows users to instantly swap native chain tokens (SOL, ETH, etc.) for specific tokens by providing a contract address or using the buy interface. The process includes token information display, wallet selection, and transaction configuration.

- **Scope:**  
  Chain-specific trading function that enables direct market orders with customizable parameters for slippage, fees, and order size.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point 1:** User sends contract address directly to the chat
    - **Entry Point 2:** User clicks "Buy" button in the main menu, then provides contract address when prompted
    - **Additional parameters:**
        - Wallet selection
        - Swap/Limit/DCA mode selection
        - Buy/Sell mode selection
        - Slippage setting
        - Anti-MEV mode setting
        - Priority fee/Tip settings
        - Amount of native token to swap

- **Expected Outcome / Response:**  
  The process has three main stages:
    1. Token Information Display: Detailed token metrics, market data, and wallet balances
    2. Trade Configuration: Interactive buttons for configuring all swap parameters
    3. Transaction Execution: Progress updates and confirmation details

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

  **Stage 2: Trade Configuration Buttons**
  ```
  Row 1:
  "🔄 REFRESH"
  
  Row 2:
  "⬅️ PREV" | "[WALLET NAME]" | "➡️ NEXT" (wallet selection)
  
  Row 3:
  "SWAP ✓" | "LIMIT" | "DCA" (mode selection)
  
  Row 4:
  "BUY MODE ✓" | "SELL MODE" (direction selection)
  
  Row 5:
  "SLIPPAGE ([Percentage]%)" | "ANTI MEV MODE ([Current Setting])"
  
  Row 6:
  "PRIORITY FEE ([Current Fee])" | "TIP ([Current Tip])"
  
  Row 7:
  "[Amount 1] [Native Token]" | "[Amount 2] [Native Token]" (preset amounts)
  
  Row 8:
  "[Amount 3] [Native Token]" | "[Amount 4] [Native Token]" (preset amounts)
  
  Row 9:
  "X [Native Token]" (custom amount)
  
  Row 10:
  "CONFIRM"
  ```

  **Stage 3: Transaction Messages**
    - Waiting message: "Transaction initiated: Swapping [Amount] [Native Token] for approximately [Token Amount] [Token Symbol]... Please wait."
    - Confirmation message: "Transaction confirmed! [Transaction Explorer Link]"

### 2.2 Process Flow
- **Step 1:** User initiates the buy process by either:
    - Sending a contract address directly to the chat
    - Clicking "Buy" button and then providing the contract address when prompted

- **Step 2:** Bot automatically identifies the blockchain based on the contract address format and retrieves token information including:
    - Token name, symbol, and contract details
    - Security status (mint/freeze renounced)
    - Market metrics (market cap, liquidity, price)
    - Volume data (5m, 15m, 1h, 24h)
    - User's current balance of both native token and the selected token

- **Step 3:** Bot displays comprehensive token information and the full trade configuration interface.

- **Step 4:** User configures the trade by:
    - Selecting the desired wallet using PREV/NEXT buttons
    - Confirming swap mode (vs. limit or DCA)
    - Confirming buy mode (vs. sell)
    - Setting slippage if desired
    - Setting Anti-MEV protection if desired
    - Setting priority fee/tip if desired
    - Selecting an amount of native token to swap (preset buttons or custom)

- **Step 5:** User clicks "CONFIRM" to execute the transaction.

- **Step 6:** Bot displays waiting message with transaction details and initiates the swap on the selected blockchain.

- **Step 7:** Once transaction is confirmed on-chain, bot updates the message with:
    - Confirmation status
    - Link to transaction on blockchain explorer
    - Final amount of tokens received
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