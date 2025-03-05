# User Action Requirement: Atlas Pro - Prometheus Trading

---

## 1. Overview

- **User Action:**  
  `Atlas Pro - Prometheus Trading`

- **Short Description:**  
  Allows Gold-tier users (holding 1,000,000+ PGN tokens) to configure automated trading based on signals received from the Prometheus signal bot, with separate controls for buy and sell signals.

- **Scope:**  
  Premium feature that enables automated response to external trading signals, creating a fully automated trading system that executes trades based on professional market intelligence.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point:** User navigates to "Atlas Pro Settings" from main menu (only visible to Gold users)
    - **Eligibility Requirement:** User must hold at least 1,000,000 PGN tokens
    - **Additional parameters:**
        - Auto Buy activation status (On/Off)
        - Auto Sell activation status (On/Off)
        - Buy size in native token
        - Slippage percentage
        - Fee settings (priority fee, tip, anti-MEV settings)

- **Expected Outcome / Response:**  
  Gold-tier users can enable automatic trading responses to Prometheus signals, configuring how the bot should react to incoming buy and sell signals, including trade size, execution parameters, and fee settings.

- **User Interface Behavior:**  
  **Information Message:**
  ```
  🔮 Prometheus Integration Settings
  
  Configure how Atlas responds to signals from Prometheus.
  
  Prometheus signals are sent directly to Atlas and will automatically execute based on your settings below.
  
  ⚠️ This feature requires Gold tier status (1,000,000+ PGN tokens).
  
  Current Settings:
  Buy Size: [Amount] [Native Token]
  Slippage: [Percentage]%
  Priority Fee: [Setting]
  Tip: [Setting]
  Anti-MEV: [Setting]
  ```

  **Buttons:**
  ```
  Row 1:
  "Auto Buy 🔴" or "Auto Buy ✅" (toggleable activation)
  
  Row 2:
  "Auto Sell 🔴" or "Auto Sell ✅" (toggleable activation)
  
  Row 3:
  "Buy Size: [Amount] [Native Token]"
  
  Row 4:
  "Slippage: [Percentage]%"
  
  Row 5:
  "Priority Fee: [Setting]" | "Tip: [Setting]"
  
  Row 6:
  "Anti-MEV: [Setting]"
  
  Row 7:
  "Back to Menu"
  ```

### 2.2 Process Flow
- **Step 1:** User navigates to "Atlas Pro Settings" from the main menu.
    - If user does not have 1,000,000+ PGN tokens, they receive a message indicating this is a Gold tier feature and are returned to the main menu.
    - If user has Gold tier status, they proceed to the Prometheus Integration settings.

- **Step 2:** Bot displays the current Prometheus Integration settings with activation status and configuration parameters.

- **Step 3:** User configures the automated response to Prometheus signals:
    - Auto Buy: User toggles whether to automatically buy tokens when Prometheus sends buy signals
    - Auto Sell: User toggles whether to automatically sell initial investment when Prometheus sends sell signals
    - Buy Size: User clicks "Buy Size" button and enters the amount of native token to use for each automated buy
    - Slippage: User clicks "Slippage" button and enters the percentage to allow for automated trades
    - Fee Settings: User configures priority fee, tip, and anti-MEV settings for automated trades

- **Step 4:** User clicks "Back to Menu" to save settings and return to the main menu.

- **Step 5:** When Prometheus sends signals to Atlas (via API endpoint):
    - For Buy Signals:
        - If Auto Buy is enabled, bot automatically purchases the token using the configured buy size and parameters
        - User receives notification of the automated purchase with transaction details
        - If Auto Sell profiles are configured, they are automatically applied to this purchase

    - For Sell Signals:
        - If Auto Sell is enabled, bot automatically sells the initial investment amount of the specified token
        - User receives notification of the automated sell with transaction details
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