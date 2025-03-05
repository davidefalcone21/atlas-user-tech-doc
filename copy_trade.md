# User Action Requirement: Copy Trade

---

## 1. Overview

- **User Action:**  
  `Copy Trade`

- **Short Description:**  
  Allows users to automatically copy the buying and selling activities of specified target wallets, with customizable parameters for trade size, sell behavior, and execution settings.

- **Scope:**  
  Multi-chain wallet tracking and trade mirroring system that enables users to automatically follow the trading strategies of successful traders or specific project wallets across all supported blockchains (SOL, ETH, BNB, BASE, TON).

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point:** User clicks "Copy Trade" button from main menu
    - **Additional parameters for setup:**
        - Target wallet tag (custom identifier)
        - Target wallet address to track
        - Buy size (percentage of target's trade or fixed amount)
        - Copy Sells toggle (Yes/No)
        - Fee settings (priority fee, tip, anti-MEV)
        - Slippage percentage

- **Expected Outcome / Response:**  
  User can create, manage, and monitor multiple copy trade setups, each tracking a different target wallet. When active, the bot will automatically execute similar trades when the target wallet makes buys or sells (if enabled), using the user's predefined parameters.

- **User Interface Behavior:**  
  **Stage 1: Copy Trade Overview Screen**
  ```
  Copy Trade allows you to copy the buys and sells of any target wallet. 
  🟢 Indicates a copy trade setup is active.
  🟠 Indicates a copy trade setup is paused.
  You do not have any copy trades setup yet. Click on the New button to create one!
  ```

  **Buttons for Stage 1:**
  ```
  Row 1:
  "[WALLETTAG1] 🟢" (if any exist)
  
  Row 2:
  "[WALLETTAG2] 🟠" (if any exist)
  
  Row 3:
  "NEW +"
  
  Row 4:
  "Back to Menu"
  ```

  **Stage 2: New Copy Trade Setup Screen**
  ```
  To setup a new Copy Trade:
  - Assign a unique name or "tag" to your target wallet, to make it easier to identify.
  - Enter the target wallet address to copy trade.
  - Enter the percentage of the target's buy amount to copy trade with, or enter a specific [Native Token] amount to always use.
  - Toggle on Copy Sells to copy the sells of the target wallet.
  - Click "Add" to create and activate the Copy Trade.
  
  To manage your Copy Trade:
  - Click the "Active" button to "Pause" the Copy Trade.
  - Delete a Copy Trade by clicking the "Delete" button.
  ```

  **Buttons for Stage 2:**
  ```
  Row 1:
  "Chain: [CHAIN]" (to select which blockchain to track)
  
  Row 2:
  "Tag: --"
  
  Row 3:
  "Wallet Address: --"
  
  Row 3:
  "Buy Size: --" | "Copy Sells: [YES/NO]"
  
  Row 4:
  "Slippage: [Percentage]%"
  
  Row 5:
  "Priority Fee: [Setting]" | "Tip: [Setting]"
  
  Row 6:
  "Anti-MEV: [Setting]"
  
  Row 7:
  "CONFIRM ADD"
  
  Row 8:
  "Back"
  ```

  **Stage 3: Copy Trade Management Screen (after selecting existing setup)**
  ```
  Copy Trade: [WALLETTAG]
  Target Wallet: [Wallet Address]
  Status: Active/Paused
  
  Settings:
  - Buy Size: [Percentage or Fixed Amount]
  - Copy Sells: [Enabled/Disabled]
  - Slippage: [Percentage]%
  - Priority Fee: [Setting]
  - Tip: [Setting]
  - Anti-MEV: [Setting]
  
  Recent Copied Transactions:
  [List of recent transactions copied from this wallet]
  ```

  **Buttons for Stage 3:**
  ```
  Row 1:
  "Active ✅" or "Paused 🟠" (toggleable)
  
  Row 2:
  "Edit Settings"
  
  Row 3:
  "Delete Copy Trade"
  
  Row 4:
  "Back to Copy Trades"
  ```

### 2.2 Process Flow
- **Step 1:** User clicks "Copy Trade" button from the main menu.

- **Step 2:** Bot displays the Copy Trade overview screen showing any existing copy trade setups with their status indicators.

- **Step 3:** User either:
    - Selects an existing copy trade setup to manage it
    - Clicks "NEW +" to create a new copy trade setup

- **Step 4:** If creating a new setup, user configures:
    - Chain: Selects which blockchain to track (SOL, ETH, BNB, BASE, TON)
    - Tag: Clicks "Tag: --" button and enters a memorable name for this target wallet
    - Wallet Address: Clicks "Wallet Address: --" button and enters the address to track
    - Buy Size: Clicks "Buy Size: --" button and enters either:
        - A percentage (e.g., "50%") to use 50% of the relative amount the target uses
        - A fixed amount (e.g., "0.5 SOL") to always use the same amount regardless of target's trade size
    - Copy Sells: Toggles whether to also automatically sell when the target wallet sells
    - Slippage: Sets the slippage percentage for copied trades
    - Fee Settings: Configures priority fee, tip, and anti-MEV settings for copied trades

- **Step 5:** User clicks "CONFIRM ADD" to activate the copy trade setup.

- **Step 6:** Bot begins monitoring the target wallet for transactions.

- **Step 7:** When the target wallet makes a transaction:
    - For buys: If copy trade is active, bot automatically buys the same token using the configured parameters
    - For sells: If copy trade is active AND copy sells is enabled, bot automatically sells the token
    - For each automated transaction, the bot sends a notification message to the user:
        - "Copy Trade Alert: [WALLETTAG] bought [TOKEN] - Your bot has automatically purchased [AMOUNT] [TOKEN] for [COST] [NATIVE TOKEN]. [TRANSACTION LINK]"
        - "Copy Trade Alert: [WALLETTAG] sold [TOKEN] - Your bot has automatically sold [AMOUNT] [TOKEN] for [RECEIVED] [NATIVE TOKEN]. [TRANSACTION LINK]"

- **Step 8:** User can manage existing copy trade setups by:
    - Toggling between Active and Paused states
    - Editing the configuration settings
    - Deleting the copy trade setup entirely
    - Viewing the history of transactions copied from the target wallet

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