# User Action Requirement: Sell Dust for PGN

---

## 1. Overview

- **User Action:**  
  `Sell Dust for PGN`

- **Short Description:**  
  Allows users to automatically convert all small token balances ("dust") below a specified threshold into PGN tokens in a gas-optimized way, while preserving native tokens and stablecoins.

- **Scope:**  
  Multi-chain portfolio cleanup utility that helps users consolidate numerous small token positions into the ecosystem token (PGN), optimizing wallet management and potentially increasing PGN holdings.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point:** User clicks "Sell Dust for PGN" button from main menu
    - **Additional parameters:**
        - Wallet selection
        - Dust threshold value in USD
        - Confirmation of action

- **Expected Outcome / Response:**  
  Bot identifies all token balances below the specified threshold (excluding native tokens and stablecoins), calculates their combined value, and executes optimized transactions to convert them all to PGN tokens. User receives a summary of the conversion process with total value consolidated.

- **User Interface Behavior:**  
  **Initial Information Screen:**
  ```
  📊 Sell Dust for PGN
  
  This feature will automatically swap all your small token balances (dust) below the specified threshold into PGN tokens.
  
  Assets excluded from conversion:
  • Native tokens (SOL, ETH, BNB, etc.)
  • Stablecoins (USDC, USDT, DAI, etc.)
  
  Current Settings:
  - Selected Wallet: [Wallet Name]
  - Dust Threshold: $[Amount] USD
  
  Tokens Identified as Dust:
  [Number] tokens with total value approximately $[Combined Value] USD
  ```

  **Buttons:**
  ```
  Row 1:
  "⬅️ PREV" | "[WALLET NAME]" | "➡️ NEXT" (wallet selection)
  
  Row 2:
  "Dust Threshold: $[Value]" (configurable threshold)
  
  Row 3:
  "View Dust Tokens" (shows detailed list of tokens to be converted)
  
  Row 4:
  "CONVERT TO PGN" (confirmation button)
  
  Row 5:
  "Back to Menu"
  ```

  **Dust Tokens Detail Screen (when "View Dust Tokens" is clicked):**
  ```
  Dust Tokens in [Wallet Name]:
  
  1. [Token Symbol 1]: [Amount] ($[USD Value])
  2. [Token Symbol 2]: [Amount] ($[USD Value])
  3. [Token Symbol 3]: [Amount] ($[USD Value])
  ...
  
  Total Value: $[Combined Value] USD
  Estimated PGN to Receive: ~[PGN Amount] PGN
  ```

  **Confirmation and Processing Screen:**
  ```
  Converting Dust to PGN...
  
  The bot is now executing optimized swaps to convert [Number] dust tokens to PGN.
  This process may require multiple transactions to complete efficiently.
  
  Status: [In Progress/Complete]
  Transactions: [Completed]/[Total]
  
  Please wait while your dust is being converted...
  ```

  **Completion Screen:**
  ```
  Dust Conversion Complete!
  
  Successfully converted [Number] tokens to PGN:
  • Total Value Converted: $[Value] USD
  • PGN Received: [Amount] PGN
  • Gas Spent: [Amount] [Native Token]
  
  Your wallet is now cleaner and your PGN balance has increased!
  ```

### 2.2 Process Flow
- **Step 1:** User clicks the "Sell Dust for PGN" button from the main menu.

- **Step 2:** Bot analyzes the selected wallet and identifies all token balances below the current dust threshold, excluding native tokens and stablecoins.

- **Step 3:** Bot displays the initial information screen with the count and combined value of dust tokens.

- **Step 4:** User can:
    - Change the selected wallet using PREV/NEXT buttons to apply the function to a different wallet
    - Adjust the dust threshold by clicking the "Dust Threshold" button and entering a new value
    - View detailed list of dust tokens by clicking "View Dust Tokens"
    - Proceed with conversion by clicking "CONVERT TO PGN"

- **Step 5:** If user clicks "CONVERT TO PGN", bot displays a confirmation message asking them to confirm the action.

- **Step 6:** Upon confirmation, bot initiates the conversion process:
    - Groups tokens by DEX or conversion route to optimize gas usage
    - Executes batched transactions where possible
    - Shows real-time progress of the conversion

- **Step 7:** Once all conversions are complete, bot displays the completion screen with detailed results:
    - Number of tokens converted
    - Total value converted
    - Amount of PGN received
    - Gas costs for the process

- **Step 8:** User can return to the main menu, with their wallet now containing fewer small token balances and an increased PGN position.

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