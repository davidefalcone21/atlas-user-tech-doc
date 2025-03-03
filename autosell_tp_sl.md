# User Action Requirement: Set Take Profits and Stop Loss

---

## 1. Overview

- **User Action:**  
  `Set Take Profits and Stop Loss`

- **Short Description:**  
  Allows users to create and manage automated selling profiles with multiple take profit targets and stop loss levels that automatically create limit sell orders when the user makes a purchase.

- **Scope:**  
  Multi-chain risk management system that enables users to pre-define exit strategies that will be automatically applied to new purchases, with the ability to create, edit, and activate different profiles for various trading styles.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point:** User navigates to "Settings" from main menu, then selects "Auto Sell"
    - **Additional parameters:**
        - Profile selection or creation
        - Trade types to apply profile to (Swaps, Limits, DCA)
        - Multiple take profit levels (percentage and sell amount for each)
        - Stop loss level (percentage and sell amount)
        - Slippage setting for auto-created orders
        - Expiration time for auto-created orders
        - Profile activation status (On/Off)

- **Expected Outcome / Response:**  
  User is able to create and manage multiple automated selling profiles, each with a customized combination of take profit levels and stop loss parameters. These profiles, when active, will automatically generate limit sell orders whenever the user makes a purchase, ensuring a predefined exit strategy is in place without manual intervention.

- **User Interface Behavior:**  
  **Stage 1: Auto Sell Profile Selection**
  ```
  Auto Sell Profiles
  
  Select an existing profile to edit or create a new one:
  ```

  **Buttons for Stage 1:**
  ```
  Row 1:
  "Profile 1"
  
  Row 2:
  "Profile 2"
  
  Row 3:
  "New Profile"
  
  Row 4:
  "Back"
  ```

  **Stage 2: Profile Configuration Message**
  ```
  AutoSell will automatically set your specified limit sell orders for purchases when enabled.
  
  Select the function(s) and wallets you want to enable the AutoSell Profile for. 
  NOTE: For classic AutoSell leave "Swaps, Limit, DCA" green and select "All Wallets".
  
  Sell Orders:
  Click "Add Order" to add additional orders to your strategy. Reply "none" to either prompt to remove an order.
  - Set a stop-loss by clicking "T/P: -" and replying with a negative percentage (-XX%) and updating the sell amount to 100% or less.
  - Set a take profit strategy by clicking "T/P: -" and replying with a positive percentage (XX%) then update the sell amount for each target. 
  
  Set as many orders as you would like. The Amount column for your take profit strategy should add up to only 100%. Structure accordingly.
  
  Example: -25% SL with 4 TP targets.
  -25%; 100%
  100%; 50% (i.e. takes out your initials)
  250%; 20%
  400%; 20%
  900%; 10%
  
  Finally, set your slippage and expiration for the Auto Sell limit orders.
  You can turn the profile on or off and delete if you no longer want the profile.
  ```

  **Buttons for Stage 2:**
  ```
  Row 1:
  "Swaps ✅" | "Limits ✅" | "DCA ✅" (toggleable activation)
  
  Row 2:
  "T/P: 200%" | "Amount: 50%"
  
  Row 3:
  "T/P: 1000%" | "Amount: 10%"
  
  Row 4:
  "SL: -40%" | "Amount: 100%"
  
  Row 5:
  "+ Add Order"
  
  Row 6:
  "Slippage: 25%"
  
  Row 7:
  "Expires: 30d"
  
  Row 8:
  "OFF" or "ON ✅" | "Delete"
  
  Row 9:
  "Back"
  ```

### 2.2 Process Flow
- **Step 1:** User navigates to "Settings" from the main menu.

- **Step 2:** User selects "Auto Sell" from the settings options.

- **Step 3:** Bot displays a list of existing Auto Sell profiles and an option to create a new one.

- **Step 4:** User either:
    - Selects an existing profile to edit
    - Selects "New Profile" to create a fresh one

- **Step 5:** Bot displays the profile configuration interface with current settings (if editing) or default settings (if new).

- **Step 6:** User configures which trade types the profile should apply to by toggling the "Swaps", "Limits", and "DCA" buttons (green checkmark indicates active).

- **Step 7:** User sets up take profit and stop loss targets:
    - For take profits (positive percentage):
        - Clicks on an existing "T/P: X%" button or adds a new order row
        - When prompted, enters the percentage gain at which to take profit (e.g., 200%)
        - Clicks on the corresponding "Amount: X%" button
        - When prompted, enters the percentage of holdings to sell at this level (e.g., 50%)
        - Repeats for multiple take profit levels if desired

    - For stop loss (negative percentage):
        - Clicks on an existing "SL: X%" button or adds a new order row
        - When prompted, enters the percentage loss at which to stop loss (e.g., -40%)
        - Clicks on the corresponding "Amount: X%" button
        - When prompted, enters the percentage of holdings to sell at this level (typically 100%)

- **Step 8:** User configures additional parameters:
    - Sets slippage for auto-created orders by clicking "Slippage: X%" and entering desired percentage
    - Sets expiration time for auto-created orders by clicking "Expires: Xd" and entering desired duration

- **Step 9:** User activates the profile by toggling the "ON/OFF" button to the ON position (green checkmark).

- **Step 10:** User clicks "Back" to save the profile and return to the Auto Sell profile selection screen.

- **Step 11:** When the user makes a purchase while the Auto Sell profile is active:
    - Bot automatically creates limit sell orders based on the profile's take profit and stop loss settings
    - Orders are created with the specified slippage and expiration time
    - User receives confirmation that Auto Sell orders have been created
    - Orders will execute if/when the price reaches the specified levels

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