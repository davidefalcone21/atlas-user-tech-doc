# User Action Requirement: Social Sniping

---

## 1. Overview

- **User Action:**  
  `Social Sniping`

- **Short Description:**  
  Allows users to automatically execute token purchases based on social media signals and mentions, providing quick entry into tokens that are gaining social traction or being promoted by influential accounts.

- **Scope:**  
  Premium feature that integrates external social media monitoring with automated trading, enabling users to capitalize on early social signals before significant price movements occur.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point:** User navigates to "Social Sniping" from main menu (visible to eligible users)
    - **Eligibility Requirement:** Similar to Atlas Pro (may require specific token holdings)
    - **Additional parameters:**
        - Social Snipe activation status (On/Off)
        - Buy amount in native token
        - Slippage percentage
        - Fee settings (priority fee, tip, anti-MEV settings)
        - Safety parameters (liquidity, market cap thresholds)

- **Expected Outcome / Response:**  
  Eligible users can enable automatic trading responses to social media activity, configuring how the bot should react to mentions of tokens or projects across platforms like Twitter, Telegram, and Discord, with customizable filters and safety parameters.

- **User Interface Behavior:**  
  **Information Message:**
  ```
  🔍 Social Sniping
  
  Automatically detect and snipe tokens mentioned on social media platforms.
  
  Social sniping monitors influential accounts across multiple platforms and executes purchases when tokens are mentioned or promoted, giving you first-mover advantage.
  
  ⚠️ This feature requires premium status (similar to Atlas Pro).
  
  Current Settings:
  Buy Amount: [Amount] [Native Token]
  Slippage: [Percentage]%
  Priority Fee: [Setting]
  Min Liquidity: $[Amount]
  Max Market Cap: $[Amount]
  ```

  **Buttons:**
  ```
  Row 1:
  "Social Snipe 🔴" or "Social Snipe ✅" (toggleable activation)
  
  Row 2:
  "Buy Amount: [Amount] [Native Token]"
  
  Row 3:
  "Slippage: [Percentage]%" | "Priority Fee: [Setting]"
  
  Row 4:
  "Min Liquidity: $[Amount]" | "Max Market Cap: $[Amount]"

  Row 8:
  "Select Wallets" (for multi-wallet execution)
  
  Row 9:
  "Back to Menu"
  ```

  **Social Sources Selection Screen:**
  ```
  Select Social Sources to Monitor
  
  Choose which platforms the bot should monitor for token mentions.
  ```

  **Buttons for Social Sources:**
  ```
  Row 1:
  "Twitter ✅" | "Telegram ✅" | "Discord ✅" (toggleable)
  
  Row 2:
  "Reddit ☐" | "Medium ☐" | "Other ☐" (toggleable)
  
  Row 3:
  "Confirm Selection"
  ```

  **Influencer Selection Screen:**
  ```
  Influencer Tracking
  
  Select which influencer categories or specific accounts to monitor.
  The bot will prioritize mentions from accounts with higher influence scores.
  ```


### 2.2 Process Flow
- **Step 1:** User navigates to "Social Sniping" from the main menu.
    - If user does not have premium status, they receive a message indicating this is a premium feature and are returned to the main menu.
    - If user has premium status, they proceed to the Social Sniping settings.

- **Step 2:** Bot displays the current Social Sniping settings with activation status and configuration parameters.

- **Step 3:** User configures the automated response to social signals:
    - Social Snipe: User toggles whether to automatically buy tokens based on social signals
    - Buy Amount: User sets the amount of native token to use for each automated buy
    - Slippage: User sets the percentage to allow for automated trades
    - Fee Settings: User configures priority fee and other transaction parameters
    - Safety Parameters: User sets minimum liquidity and maximum market cap thresholds

- **Step 4:** User selects which wallets to use for social sniping (similar to Sniper Extension).

- **Step 5:** User activates Social Sniping by toggling the button to "on" status.

- **Step 6:** The external social monitoring system continuously tracks the selected platforms and accounts:
    - When relevant token mentions are detected that meet the criteria
    - The system sends signals to the bot via exposed endpoints

- **Step 7:** When social signals are received:
    - Bot validates the token against safety parameters
    - If validation passes, bot automatically purchases the token using the configured amount and parameters
    - Purchase can be executed across multiple wallets if configured
    - User receives notification of the automated purchase with transaction details and the social source that triggered it