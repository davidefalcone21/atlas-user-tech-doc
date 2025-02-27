# User Action Requirement: Buy Coin (Limit Order)

---

## 1. Overview

- **User Action:**  
  `Buy Coin (Limit Order)`

- **Short Description:**  
  Allows users to create conditional buy orders that execute only when a token reaches a specific price or market cap target. The order includes parameters for amount, trigger conditions, and expiration time.

- **Scope:**  
  Chain-specific advanced trading function that enables users to set up automated buys at their desired entry points without constantly monitoring the market.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point 1:** User sends contract address directly to the chat, then switches to LIMIT mode
    - **Entry Point 2:** User clicks "Buy" button, provides contract address when prompted, then switches to LIMIT mode
    - **Additional parameters:**
        - Wallet selection
        - Swap/Limit/DCA mode selection (LIMIT selected)
        - Buy/Sell mode selection
        - Slippage setting
        - Anti-MEV mode setting
        - Priority fee/Tip settings
        - Amount of native token for the order
        - Trigger price (in USD or market cap target)
        - Order expiration time

- **Expected Outcome / Response:**  
  The process has three main stages:
    1. Token Information Display: Detailed token metrics, market data, and wallet balances (same as Swap)
    2. Limit Order Configuration: Interactive buttons for setting all order parameters including trigger price and expiry
    3. Order Creation Confirmation: Details of the created order and monitoring status

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

  **Stage 2: Limit Order Configuration Buttons**
  ```
  Row 1:
  "🔄 REFRESH"
  
  Row 2:
  "⬅️ PREV" | "[WALLET NAME]" | "➡️ NEXT" (wallet selection)
  
  Row 3:
  "SWAP" | "LIMIT ✓" | "DCA" (mode selection)
  
  Row 4:
  "BUY MODE ✓" | "SELL MODE" (direction selection)
  
  Row 5:
  "SLIPPAGE" | "ANTI MEV MODE ([Current Setting])"
  
  Row 6:
  "PRIORITY FEE" | "TIP"
  
  Row 7:
  "[Amount 1] [Native Token]" | "[Amount 2] [Native Token]" | "[Amount 3] [Native Token]" | "[Amount 4] [Native Token]" (preset amounts)
  
  Row 8:
  "X [Native Token]" (custom amount)
  
  Row 9:
  "TRIGGER PRICE" (set price or mcap target)
  
  Row 10:
  "EXPIRY 4H" (order duration)
  
  Row 11:
  "CREATE ORDER"
  ```

  **Stage 3: Order Creation Messages**
    - Confirmation message: "Limit order created: Buy [Amount] [Native Token] worth of [Token Symbol] when price reaches [Trigger Price] or market cap reaches [Market Cap Target]. Order expires in [Expiry Time]. You will be notified when the order executes."

### 2.2 Process Flow
- **Step 1:** User initiates the process by either:
    - Sending a contract address directly to the chat
    - Clicking "Buy" button and then providing the contract address when prompted

- **Step 2:** Bot automatically identifies the blockchain and retrieves token information (same as Swap function).

- **Step 3:** Bot displays comprehensive token information and the full order configuration interface.

- **Step 4:** User selects "LIMIT" mode from the trade type options.

- **Step 5:** User configures the limit order by:
    - Selecting the desired wallet using PREV/NEXT buttons
    - Confirming buy mode (vs. sell)
    - Setting slippage if desired
    - Setting Anti-MEV protection if desired
    - Setting priority fee/tip if desired
    - Selecting an amount of native token for the order (preset buttons or custom)
    - Setting the trigger price (can be USD price or market cap value)
    - Setting the order expiration time (default 4H)

- **Step 6:** User clicks "CREATE ORDER" to finalize the limit order.

- **Step 7:** Bot confirms the order creation with details and begins monitoring the market for the trigger condition.

- **Step 8:** If the trigger condition is met before expiration:
    - Bot executes the buy order with the specified parameters
    - User receives notification with transaction details and confirmation
    - Bot updates the message with the successful execution and final details

- **Step 9:** If the order expires without the trigger condition being met:
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