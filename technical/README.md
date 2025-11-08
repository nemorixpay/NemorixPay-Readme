
# NemorixPay - Official document

<p align="left"></p>

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/Logo%20Nemorix.png" width="400" title="NemorixPay logo">
</p>

# 🧠 Technical Overview

This document provides a summary of the ongoing technical work, performance, partner integration status, and testing environments for the **NemorixPay** project.

## ⚙️ Technical Work

| Area | Description | Status |
|------|--------------|--------|
| **Blockchain Integration** | Early technical work completed using the **Stellar Testnet** for account creation, transaction handling, and QR-based payments. | ✅ Completed |
| **Wallet Basic Operations** | Wallet creation, import, and transaction flows validated in the testnet environment. | ✅ Completed |
| **QR Payments** | QR code generation and scanning tested for P2P and merchant transactions. | ✅ Completed |
| **Initial Backend Sync** | Firebase API integration for user registration, login, and password reset. | ✅ Completed |
| **Prevent Spam Registration** | The system is required to confirm the user’s email address before allowing access. | ✅ Completed |
| **Localization** | Full English and Spanish language support. | ✅ Completed |
| **Local Security Layer** | Encrypted local private key management with test-side access control. | ✅ Completed |
| **Account Access Methods** | Users can currently sign in using email and password credentials. | ✅ Completed |
| **Remote Security Layer** | Encrypted remote private key management with user-side access control. | 🔄 In Progress |
| **Wallet Dashboard** | Simple and intuitive interface for managing balances, transaction history, etc. | 🔄 In Progress |
| **KYC Foundation** | Integrated KYC/AML services via Didit. | 🛠️ Under Review (Testing & Refinement) |
| **Accessibility** | Deployment on both Android and iOS platforms. | 🔄 In Progress |
| **Anchor Integration** | Technical integration with Bitso’s sandbox environment. | ⏳ Pending |
| **MSB Registration** | Money Services Business (MSB) registration in FinCEN. | ✅ Completed |
| **Extended Localization** | Additional Portuguese language support. | ⏳ Pending |
| **Extended Localization** | Additional French language support. | ⏳ Pending |
| **Wallet Advanced Operations** | Expanding wallet support to full SEP-005/BIP-44 derivation standards. | ⏳ Pending |
| **New Account Access Methods** | Users will be able to sign in using Google and Apple ID authentication options. | ⏳ Pending |

## 📊 Analytics Dashboard

Track and analyze NemorixPay’s growth and system performance using visual metrics and analytical dashboards. (*Under Construction*)

[Analytics Dashboard](https://nemorixpay.com/analytics)

<p align = "center">
<a href="https://nemorixpay.com/analytics"><img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/website/analytics.png" alt="Analytics Dashboard" height="400"></a>
</p>

## 🔗 Example Stellar Testnet Accounts

These test accounts and transactions need to be updated monthly, as the Stellar Testnet resets approximately once a month, clearing all previously created accounts and transactions.
As part of our ongoing development process, we regularly create new test accounts and execute transactions to validate NemorixPay’s core features.

**Status**: Active as of **November 7, 2025** (*Under Review*)

- [Account 01 – GBAXMWXKTFLCWUEILWR2LNQLIVC6FNMY7VSLX5B3NAZIDWYUIAVL6Y7N](https://stellar.expert/explorer/testnet/account/GBAXMWXKTFLCWUEILWR2LNQLIVC6FNMY7VSLX5B3NAZIDWYUIAVL6Y7N)

- [Account 02 – GDWJBSBKYNWWAFTX6BVPVGANRZLVH3FHYGJW2XVUK6KHNVEXEYBYNEVJ](https://stellar.expert/explorer/testnet/account/GDWJBSBKYNWWAFTX6BVPVGANRZLVH3FHYGJW2XVUK6KHNVEXEYBYNEVJ)

- [Account 03 – GD5HWKVGKHDQYBUN4RSDHBP7Z3MA7PNYBZIM5ZQXCD3ARIIGGBGLHX43](https://stellar.expert/explorer/testnet/account/GD5HWKVGKHDQYBUN4RSDHBP7Z3MA7PNYBZIM5ZQXCD3ARIIGGBGLHX43)

- [Transaction 01 – 1b4a5dc0a2925a279105271a7afb251d9a7d2639e0e18ae8f0027630ecd7d5c0](https://stellar.expert/explorer/testnet/tx/3807441263271936)


## 🤝 Partners / Integration Status

| Partner / Integration | Role | Status | Notes |
|------------------------|------|--------|-------|
| **Bitso** | Stellar Anchor (MXN ↔ XLM/USDC) | ⏳ Pending |  **MSB approved** - Anchor account activation in progress. |
| **Didit** | KYC Provider | 🛠️ Under Review (Testing) |Phase 1 implemented. Testing and refinement are currently in progress. |
| **Firebase** | Authentication | ✅ Completed | Used for user login, password reset, and data synchronization. |
| **Firebase** | Realtime Database | 🔄 In Progress | Used for secure user data storage and synchronization. |
| **Firebase** | Cloud Firestore | ⏳ Pending | Used for secure remote storage and synchronization of user and account data. |
| **Stellar SDK for Flutter** | Blockchain Layer | ✅ Completed | Provides core account management and payment functionality. |

## 🧪 Open Testing Environment

### **Android**

| Detail | Information |
|---------|--------------|
| **Testing Program** | [Google Play Internal Test](https://play.google.com/apps/internaltest/4701062879481429776) |
| **Test Account** | `tester@nemorixpay.com` |
| **Password** | `tester20!25!` |
| **Status** | ✅ Active |

**Install Directions/Important note:**

When accessing the internal testing program, it must be opened from an Android device while logged in with the provided test account credentials. However, due to an occasional issue with Google Play, the install option may not appear on the device. To work around this, the team logs into the same account on a desktop browser and accesses the link there. Google Play detects the same user (`tester@nemorixpay.com`) on the Android device and allows remote installation using the "**Install on more devices**" option. After a few seconds, the app is successfully installed and ready for testing on the device.

**Creating an account in the app:**

After installation, you will have two options:

1) Create a new account using your personal email:

If you want to use your own email address, it must be valid and accessible.  
After registration, the system will send a verification link to confirm that the email exists.  
You must complete this verification to log in successfully.  
If you don’t have access to this email, you won’t be able to proceed past the sign-in page.  
This serves as our **first security layer** to **prevent spam registrations** and the use of non-existent email accounts.  

2) Use our tester account:

You can use our tester account (email: `tester@nemorixpay.com`, password: `tester20!25!`) to log in successfully, as it is already registered in our system as an active user.  
After logging in, you can create a new account, which will be stored locally on your device.  
Remote storage is still under development and not yet active, if you open the app on another device, you’ll need to create a new local account for that device.  

#

### **iOS**

| Detail | Information |
|---------|--------------|
| **Testing Program** | [TestFlight Internal Test](https://www.apple.com/) |
| **Test Account** | `tester@nemorixpay.com` |
| **Password** | `tester20!25!` |
| **Status** | 🔄 Under Review |

---

## 🧭 Next Steps

- Finalize **Bitso** integration (MSB approved).  
- Complete **KYC Phase 2** implementation with Didit (In progress).  
- Deploy NemorixPay **V1** to Google Play and App Store for open beta testing (In progress).

---

📄 *Last updated: November 2025*
