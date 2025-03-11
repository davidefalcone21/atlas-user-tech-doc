# User Action Requirement: Direct Onramp

---

## 1. Overview

- **User Action:**  
  `Direct Onramp`

- **Short Description:**  
  Enables users to purchase crypto directly into their trading wallets using fiat payment methods like Apple Pay and credit cards through integrations with payment processors such as Moonpay.

- **Scope:**  
  Fiat-to-crypto gateway that streamlines the process of funding trading wallets without requiring users to first purchase on exchanges and then transfer to their trading wallets.

---

## 2. Detailed Functionality

### 2.1 Functional Requirements
- **Input / Parameters:**
    - **Entry Point:** User clicks "Direct Onramp" button from main menu
    - **Additional parameters:**
        - Destination chain and wallet
        - Desired crypto asset to purchase
        - Fiat amount to spend
        - Payment method selection
        - User KYC verification (handled by payment processor)

- **Expected Outcome / Response:**  
  User is able to purchase crypto assets directly into their trading wallet using familiar payment methods. The bot facilitates the connection with payment processors while ensuring funds are delivered to the correct wallet address.

- **User Interface Behavior:**  
  **Initial Onramp Screen:**
  ```
  💳 Direct Onramp
  
  Purchase crypto directly into your trading wallet using fiat payment methods.
  Powered by our integration partners (Moonpay, etc.)
  
  Select your destination wallet and the crypto you wish to purchase:
  ```

  **Buttons for Initial Screen:**
  ```
  Row 1:
  "Chain: [CHAIN]" (destination chain selection)
  
  Row 2:
  "⬅️ PREV" | "[WALLET NAME]" | "➡️ NEXT" (destination wallet selection)
  
  Row 3:
  "Asset: [CRYPTO]" (asset selection, defaulting to chain's native token)
  
  Row 4:
  "Continue to Payment"
  
  Row 5:
  "Back to Menu"
  ```

  **Asset and Amount Selection:**
  ```
  Select Asset and Amount
  
  Chain: [Selected Chain]
  Wallet: [Selected Wallet]
  
  Available Assets to Purchase:
  • [Native Token]
  • USDC
  • USDT
  • [Other available tokens...]
  
  Enter fiat amount to spend:
  [Currency Selector] [Input Field]
  
  Estimated [Crypto] to receive: [Amount]
  (Rates provided by [Provider], includes all fees)
  ```

  **Buttons for Asset Selection:**
  ```
  Row 1:
  "[NATIVE TOKEN]" | "USDC" | "USDT" (common options)
  
  Row 2:
  "100" | "250" | "500" | "1000" (quick amount selection in user's local currency)
  
  Row 3:
  "USD" | "EUR" | "GBP" | "[OTHER CURRENCIES]" (currency selection)
  
  Row 4:
  "Back" | "Continue"
  ```

  **Payment Method Selection:**
  ```
  Select Payment Method
  
  Purchase: [Amount] [Fiat Currency] of [Crypto]
  Destination: [Wallet Address] on [Chain]
  
  Available Payment Methods:
  • Credit/Debit Card
  • Apple Pay
  • Google Pay
  • Bank Transfer
  • [Other available methods...]
  
  Note: You will be redirected to our payment partner's secure platform to complete your purchase.
  ```

  **Redirect Notice:**
  ```
  Redirecting to Payment Processor
  
  You will now be redirected to [Payment Processor] to complete your purchase.
  
  Purchase Details:
  • Amount: [Fiat Amount] [Currency]
  • Asset: [Crypto]
  • Destination: [Wallet Address]
  
  ⚠️ Important: Please ensure you complete the process on the payment processor's site. After completion, return to this chat to confirm your transaction.
  
  [Deep Link or QR Code for Web Redirect]
  ```

  **Completion Confirmation:**
  ```
  Purchase Status
  
  Your purchase of [Crypto] using [Payment Method] is:
  [Pending/Complete/Failed]
  
  Transaction ID: [ID]
  
  Once complete, funds will appear in your:
  [Wallet Name] on [Chain]
  
  Estimated delivery time: [Time Estimate]
  ```

### 2.2 Process Flow
- **Step 1:** User clicks the "Direct Onramp" button from the main menu.

- **Step 2:** Bot displays the initial onramp screen where user can configure:
    - Destination chain (which blockchain to receive crypto on)
    - Destination wallet (which of their wallets to fund)
    - Crypto asset to purchase (native token, stablecoin, etc.)

- **Step 3:** User clicks "Continue to Payment" to proceed.

- **Step 4:** Bot displays the asset and amount selection screen where user can:
    - Confirm or change the crypto asset to purchase
    - Select their preferred fiat currency
    - Enter the amount they wish to spend
    - See an estimate of how much crypto they will receive

- **Step 5:** User selects an amount and clicks "Continue".

- **Step 6:** Bot displays the payment method selection screen where user can choose from available payment options.

- **Step 7:** User selects a payment method and proceeds.

- **Step 8:** Bot displays a redirect notice with:
    - Summary of the purchase details
    - Information about the redirection process
    - Either a deep link (for mobile) or a QR code/link (for desktop)
    - Instructions to return to the bot after completion

- **Step 9:** User is redirected to the payment processor's platform (Moonpay, etc.) where they:
    - Complete KYC verification if required (first-time users)
    - Enter payment details
    - Confirm the purchase

- **Step 10:** After completing payment on the processor's platform, user returns to the bot.

- **Step 11:** Bot checks the status of the transaction with the payment processor and displays the status to the user.

- **Step 12:** Once the transaction is complete, bot confirms the delivery of crypto to the user's wallet and updates balances.

### 2.3 External Integration Requirements

- **Payment Processors:**
    - APIs for initiating purchases
    - Webhook notifications for transaction status updates
    - Secure redirect mechanisms (deep links for mobile, web links for desktop)

- **KYC Handling:**
    - All KYC verification is handled by the payment processor
    - Bot does not store or process KYC information

- **Security Considerations:**
    - Wallet addresses must be verified before submission to payment processor
    - Transaction details should be cryptographically signed to prevent tampering
    - Return URL must include verification parameters to prevent spoofing
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