# User Action Requirement: Show Positions

---

## 1. Overview

- **User Action:**  
  `Show Positions` (Triggered via "Positions" button or `/positions` command)

- **Short Description:**  
  Displays a comprehensive overview of all token holdings in the selected wallet, including portfolio summary, detailed token positions, and quick sell options.

- **Scope:**  
  Chain and wallet-specific portfolio view that allows users to monitor their holdings and take immediate selling actions.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Trigger:** "Positions" button from main menu or `/positions` command
    - **Additional parameters:** Chain and wallet selection via UI buttons

- **Expected Outcome / Response:**  
  User receives a detailed breakdown of their portfolio for the selected wallet, including:
    1. Wallet address
    2. Portfolio summary (total tokens, total value, native token balance, positions value)
    3. Detailed list of individual token positions with performance metrics
    4. Interactive buttons to select chains/wallets, sell specific tokens, navigate between pages, and refresh data

- **User Interface Behavior:**  
  The bot responds with a structured message displaying portfolio information followed by multiple rows of interactive inline keyboard buttons:

  **Message structure:**
  ```
  📍 Wallet Address:
  [Wallet Address]
  
  📊 Portfolio Summary
  Tokens: [Number of tokens]
  Total Balance: $[Total USD Value]
  ├ [Chain]: $[Native Token USD Value] - ([Native Token Amount]) [Chain Symbol]
  └ Positions: $[Non-native Tokens USD Value]
  
  🪙 Token Positions
  [Token 1 Name] - 📈 (chart link) - $[USD Value] - ([Native Token Value]) [Chain Symbol]
  [Token 1 Contract Address]
  Balance: [Token 1 Amount] [Token 1 Symbol]
  PNL: [Color indicator] [Percentage]% ($[USD Value])
  MCap & Liquidity
  
  [Additional token entries follow the same format]
  ```

  **Button Layout:**
  Row 1: "<-" | "[CHAIN]" | "->" (Chain navigation)
  Row 2: "W1 ✓" | "W2" | "W3" (Wallet selection with current wallet marked)
  Row 3+: "Sell [Token 1]" | "Sell [Token 2]" | "Sell [Token 3]" (Multiple rows as needed)
  Row N-1: "◀️" | "Page 1/X" | "▶️" (Pagination controls)
  Row N: "🔄 Refresh" (Refresh button)

### 2.2 Process Flow
- **Step 1:** User activates the "Show Positions" function via the "Positions" button or `/positions` command.
- **Step 2:** Bot retrieves current wallet information for the default chain and wallet.
- **Step 3:** Bot queries blockchain APIs to gather token balances, prices, and performance metrics.
- **Step 4:** Bot compiles all portfolio data into a structured display.
- **Step 5:** Bot displays the complete portfolio message with chain/wallet selection, token sell options, pagination, and refresh buttons.
- **Step 6:** User can:
    - Navigate between chains using "<-" and "->" buttons
    - Select different wallets using wallet buttons
    - Directly initiate a sell action for any displayed token
    - Navigate between pages if there are many tokens
    - Refresh the data to get the latest portfolio information
- **Step 7:** When a user changes chain or wallet, the bot updates the portfolio display with data from the newly selected wallet.
- **Step 8:** If a user clicks a "Sell [Token]" button, the bot initiates the sell process for that specific token.

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