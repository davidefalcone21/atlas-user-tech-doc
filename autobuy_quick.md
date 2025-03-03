# User Action Requirement: Auto Buy

---

## 1. Overview

- **User Action:**  
  `Auto Buy Settings`

- **Short Description:**  
  Allows users to configure and activate an automated buying system that instantly purchases tokens when contract addresses are sent to the bot, using predefined parameters for amount, slippage, liquidity, and market cap thresholds.

- **Scope:**  
  Chain-specific automated trading functionality that enables users to quickly enter positions without manually configuring each trade, with safety parameters to limit risk.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point:** User navigates to "Settings" from main menu, then selects "Auto Buy"
    - **Additional parameters:**
        - Activation status (On/Off)
        - Wallet selection for each chain
        - Buy amount in native token
        - Slippage percentage
        - Minimum liquidity threshold
        - Minimum market cap threshold
        - Maximum market cap threshold

- **Expected Outcome / Response:**  
  User can configure and activate the Auto Buy feature, which will automatically purchase tokens whenever a contract address is sent to the bot, using predefined parameters to control purchase size and safety checks. This enables rapid entry into opportunities without the need to manually configure each trade.

- **User Interface Behavior:**  
  **Information Message:**
  ```
  Autobuy will immediately buy any token or token address sent to the bot when turned on. Defined parameters are designed to help you move quickly into these trades. Leverage our autosell function, in settings, to enable your sell strategy. 
            
  Set your pre-set buy amount that will be attempted each time you leverage autobuy.
  Set your slippage, likely higher than normal for these fast styled trades. 
  Set your Min Liquidity parameters to limit transactions with low liquidity.
  Set your Max Mcap parameters to limit transactions with Mcaps exceeding your strategy.
            
  To reset any parameter simply reply "none" to the respective prompt.
  ```

  **Buttons:**
  ```
  Row 1:
  "ON/OFF" (toggleable activation)
  
  Row 2:
  "⬅️ PREV" | "W1 - [CHAIN]" | "➡️ NEXT" (wallet and chain selection)
  
  Row 3:
  "Buy amount: 0.02 [Native Token]" | "Slippage: 45%"
  
  Row 4:
  "Min Liquidity: 10k" | "Min Mcap: 1m" | "Max Mcap: 5m"
  
  Row 5:
  "Back"
  ```

### 2.2 Process Flow
- **Step 1:** User navigates to "Settings" from the main menu.

- **Step 2:** User selects "Auto Buy" from the settings options.

- **Step 3:** Bot displays the Auto Buy configuration interface with current settings or default settings.

- **Step 4:** User can navigate between different wallets and chains using the "PREV" and "NEXT" buttons to configure Auto Buy settings for each chain separately.

- **Step 5:** User configures the Auto Buy parameters by clicking on the respective buttons:
    - Buy amount: User clicks "Buy amount: X [Native Token]" and enters the desired amount of native token to use for each auto buy
    - Slippage: User clicks "Slippage: X%" and enters the desired slippage percentage (typically higher for auto buys to ensure execution)
    - Min Liquidity: User clicks "Min Liquidity: X" and enters the minimum liquidity threshold in USD that a token must have to be eligible for auto buy
    - Min Mcap: User clicks "Min Mcap: X" and enters the minimum market cap threshold that a token must have to be eligible for auto buy
    - Max Mcap: User clicks "Max Mcap: X" and enters the maximum market cap threshold that a token must not exceed to be eligible for auto buy

- **Step 6:** User activates the Auto Buy feature by toggling the "ON/OFF" button to the ON position.

- **Step 7:** User clicks "Back" to save the settings and return to the main settings menu.

- **Step 8:** When Auto Buy is active and the user (or someone else) sends a contract address to the bot:
    - Bot automatically retrieves token information
    - Bot checks if the token meets the configured thresholds (min/max market cap, min liquidity)
    - If checks pass, bot immediately executes a buy transaction using the configured amount and slippage
    - User receives confirmation of the transaction with details
    - If Auto Sell is also configured, bot automatically sets up the predefined take profit and stop loss orders for this purchase

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