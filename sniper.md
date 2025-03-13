# User Action Requirement: Sniper Extension

---

## 1. Overview

- **User Action:**  
  `Sniper Extension`

- **Short Description:**  
  Allows users to automatically snipe new token launches based on customizable parameters, with the ability to target specific contract addresses or token names, and deploy multiple wallets simultaneously with the same settings.

- **Scope:**  
  Multi-chain and multi-wallet sniping system that enables users to participate in new token launches with optimal timing based on liquidity conditions and custom safety parameters.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point:** User clicks "Sniper" button from main menu
    - **Additional parameters:**
        - Specific contract address (optional)
        - Token name or symbol to target (optional)
        - Snipe amount per wallet
        - Slippage percentage
        - Tip amount for transaction priority
        - Liquidity thresholds (min/max)
        - Market cap thresholds (min/max)
        - Safety parameters (dev holdings, mint/freeze authority)
        - Wallet selection for sniping

- **Expected Outcome / Response:**  
  User can create and manage multiple sniping configurations with different parameters. When active, the bot automatically monitors the blockchain for new token launches or liquidity additions that match the criteria, then executes high-speed purchases across selected wallets simultaneously.

- **User Interface Behavior:**  
  **Sniper Dashboard Screen:**
  ```
  🚀 Auto Sniper
  
  Auto Sniper allows you to automatically snipe any new launch on solana based on your custom parameters. 
  🟢 Indicates an auto snipe setup is active.
  🟠 Indicates an auto snipe setup is paused.
  ```

  **Buttons for Sniper Dashboard:**
  ```
  Row 1:
  "SNIPER 1 🟢" (active sniper config)
  
  Row 2:
  "SNIPER 2 🟠" (paused sniper config)
  
  Row 3:
  "+ SNIPER" (create new sniper config)
  
  Row 4:
  "Back to Menu"
  ```

  **New Sniper Configuration Screen:**
  ```
  Configure Sniper
  
  Create a new auto sniper configuration with your desired parameters.
  
  You can target a specific contract address, token name, or set criteria for any new launch.
  Safety parameters help you avoid scams and high-risk launches.
  
  This sniper will be active across all selected wallets simultaneously.
  ```

  **Buttons for New Sniper Configuration:**
  ```
  Row 1:
  "CA: --" (specific contract address, optional)
  
  Row 2:
  "NAME: --" (token name/symbol to target, optional)
  
  Row 3:
  "SNIPE AMOUNT: 0.001 SOL" | "SNIPE SLIPPAGE: 30%"
  
  Row 4:
  "SNIPE TIP AMOUNT: --" (transaction priority fee)
  
  Row 5:
  "Min Liquidity: 1000$" | "Max Liquidity: 3000$"
  
  Row 6:
  "Min Mcap: 1000$" | "Max Mcap: 30000$"
  
  Row 7:
  "Dev Holding < 10%" (toggleable)
  
  Row 8:
  "Mint Auth Revoked" | "Freeze Auth Revoked" (toggleable)
  
  Row 9:
  "Select Wallets" (opens wallet selection)
  
  Row 10:
  "CONFIRM CREATION"
  
  Row 11:
  "Back"
  ```

  **Wallet Selection Screen:**
  ```
  Select Wallets for Sniping
  
  Choose which wallets to use for this sniper configuration.
  All selected wallets will attempt to snipe simultaneously when conditions are met.
  
  Each wallet will use the amount specified in the sniper configuration.
  ```

  **Buttons for Wallet Selection:**
  ```
  Row 1:
  "W1 ☐" | "W2 ☐" | "W3 ☐" (toggle checkboxes)
  
  Row 2:
  "W4 ☐" | "W5 ☐" | "W6 ☐" (if available)
  
  Row 3:
  "Select All" | "Deselect All"
  
  Row 4:
  "Confirm"
  ```

  **Sniper Management Screen (after selecting existing config):**
  ```
  Sniper Configuration: [NAME]
  
  Status: Active/Paused
  
  Target:
  - Contract: [CA or "Any"]
  - Name Filter: [Name or "Any"]
  
  Parameters:
  - Amount: [Amount] SOL per wallet
  - Slippage: [Percentage]%
  - Tip: [Amount]
  - Liquidity Range: $[Min] - $[Max]
  - Mcap Range: $[Min] - $[Max]
  - Dev Holding Check: [On/Off]
  - Authority Checks: [On/Off]
  
  Active Wallets: [Number]
  Successful Snipes: [Number]
  ```

  **Buttons for Sniper Management:**
  ```
  Row 1:
  "Active ✅" or "Paused 🟠" (toggleable)
  
  Row 2:
  "Edit Settings"
  
  Row 3:
  "View Snipe History"
  
  Row 4:
  "Delete Sniper"
  
  Row 5:
  "Back to Snipers"
  ```

### 2.2 Process Flow
- **Step 1:** User clicks the "Sniper" button from the main menu.

- **Step 2:** Bot displays the Sniper Dashboard showing existing sniper configurations with their status.

- **Step 3:** User either:
    - Selects an existing sniper configuration to manage it
    - Clicks "+ SNIPER" to create a new configuration

- **Step 4:** If creating a new configuration, user configures:
    - CA (Contract Address): Specific token to target, or leave empty for any token
    - NAME: Filter by token name/symbol, or leave empty for any name
    - SNIPE AMOUNT: Amount of native token to use per wallet for sniping
    - SNIPE SLIPPAGE: Higher percentage to ensure execution on volatile launches
    - SNIPE TIP AMOUNT: Additional fee to prioritize transactions
    - Liquidity thresholds: Minimum and maximum liquidity to target
    - Market cap thresholds: Minimum and maximum market cap to target
    - Dev Holding: Toggle to only snipe tokens where developer holds less than specified percentage
    - Authority checks: Toggle to only snipe tokens with revoked mint/freeze authorities

- **Step 5:** User clicks "Select Wallets" to choose which wallets to use for sniping.
    - Multiple wallets can be selected to snipe simultaneously
    - Each selected wallet will use the same amount and parameters

- **Step 6:** User clicks "CONFIRM CREATION" to activate the sniper.

- **Step 7:** Bot begins monitoring the blockchain for tokens matching the specified criteria:
    - For specific CA: Monitors for liquidity addition to that token
    - For name filter: Monitors new tokens with matching name/symbol
    - For general criteria: Monitors all new launches meeting parameters

- **Step 8:** When matching conditions are detected:
    - Bot simultaneously executes purchase transactions from all selected wallets
    - Each wallet purchases the specified amount with the configured parameters
    - User receives notifications of successful snipes

- **Step 9:** User can manage existing snipers by:
    - Toggling between Active and Paused states
    - Editing parameters
    - Viewing history of successful snipes
    - Deleting configurations that are no longer needed
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