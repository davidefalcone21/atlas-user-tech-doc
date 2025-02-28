# User Action Requirement: Sell Coin (Limit Order)

---

## 1. Overview

- **User Action:**  
  `Sell Coin (Limit Order)`

- **Short Description:**  
  Allows users to create conditional sell orders that execute only when a token reaches a specific price or market cap target, enabling automated profit-taking or loss mitigation with options to sell specific amounts, percentages, or entire holdings.

- **Scope:**  
  Chain-specific advanced trading function that enables users to set up automated sells at their desired exit points without constantly monitoring the market.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point 1:** User sends contract address directly to the chat, switches to SELL mode, then LIMIT mode
    - **Entry Point 2:** User clicks "Sell" button, provides contract address when prompted, then switches to LIMIT mode
    - **Entry Point 3:** User clicks "Sell [Token]" from positions screen, then switches to LIMIT mode
    - **Additional parameters:**
        - Wallet selection
        - Swap/Limit/DCA mode selection (LIMIT selected)
        - Buy/Sell mode selection (SELL selected)
        - Slippage setting
        - Anti-MEV mode setting
        - Priority fee/Tip settings
        - Amount/percentage of token to sell
        - Trigger price (in USD or market cap target)
        - Order expiration time
        - Special sell options (INITIALS, 100%, 100% TO PGN)

- **Expected Outcome / Response:**  
  The process has three main stages:
    1. Token Information Display: Detailed token metrics, market data, and wallet balances
    2. Limit Sell Configuration: Interactive buttons for setting all parameters including trigger price and expiry
    3. Order Creation Confirmation: Details of the created sell order and monitoring status

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

  **Stage 2: Limit Sell Configuration Buttons**
  ```
  Row 1:
  "🔄 REFRESH"
  
  Row 2:
  "⬅️ PREV" | "[WALLET NAME]" | "➡️ NEXT" (wallet selection)
  
  Row 3:
  "SWAP" | "LIMIT ✓" | "DCA" (mode selection)
  
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
  "TRIGGER PRICE" (set price or mcap target)
  
  Row 14:
  "EXPIRY 4H" (order duration)
  
  Row 15:
  "CREATE ORDER"
  ```

  **Stage 3: Order Creation Messages**
    - Confirmation message: "Limit sell order created: Sell [Amount/Percentage] of [Token Symbol] when price reaches [Trigger Price] or market cap reaches [Market Cap Target]. Order expires in [Expiry Time]. You will be notified when the order executes."

### 2.2 Process Flow
- **Step 1:** User initiates the process by either:
    - Sending a contract address directly to the chat and switching to SELL mode, then LIMIT mode
    - Clicking "Sell" button, providing the contract address when prompted, then switching to LIMIT mode
    - Clicking "Sell [Token]" from positions screen, then switching to LIMIT mode

- **Step 2:** Bot automatically identifies the blockchain and retrieves token information.

- **Step 3:** Bot displays comprehensive token information and the limit sell configuration interface.

- **Step 4:** User configures the limit sell order by:
    - Selecting the desired wallet using PREV/NEXT buttons
    - Confirming LIMIT mode and SELL mode
    - Setting slippage if desired
    - Setting Anti-MEV protection if desired
    - Setting priority fee/tip if desired
    - Selecting an amount or percentage to sell:
        - Using preset native token value buttons
        - Using preset percentage buttons (25%, 50%)
        - Entering a custom amount in native token value
        - Entering a custom percentage
        - Selecting special options (INITIALS, 100%, 100% TO PGN)
    - Setting the trigger price (can be USD price or market cap value)
    - Setting the order expiration time (default 4H)

- **Step 5:** User clicks "CREATE ORDER" to finalize the limit sell order.

- **Step 6:** Bot confirms the order creation with details and begins monitoring the market for the trigger condition.

- **Step 7:** If the trigger condition is met before expiration:
    - Bot executes the sell order with the specified parameters
    - User receives notification with transaction details and confirmation
    - Bot updates the message with the successful execution and final details

- **Step 8:** If the order expires without the trigger condition being met:
    - Bot cancels the order
    - User receives notification that the order has expired
    - No transaction is executed

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