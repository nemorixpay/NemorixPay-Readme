
# NemorixPay - Official document

<p align="left"></p>

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/Logo%20Nemorix.png" width="400" title="NemorixPay logo">
</p>

# 🧠 Technical Overview

This document provides a summary of the ongoing technical work, partner integration status, and testing environments for the **NemorixPay** project.

---

## ⚙️ Technical Work

| Area | Description | Status |
|------|--------------|--------|
| **Blockchain Integration** | Early technical work completed using the **Stellar Testnet** for account creation, transaction handling, and QR-based payments. | ✅ Completed |
| **Wallet Basic Operations** | Wallet creation, import, and transaction flows validated in the testnet environment. | ✅ Completed |
| **QR Payments** | QR code generation and scanning tested for P2P and merchant transactions. | ✅ Completed |
| **Initial Backend Sync** | Firebase API integration for user registration, login, and password reset. | ✅ Completed |
| **Localization** | Full English and Spanish language support. | ✅ Completed |
| **Local Security Layer** | Encrypted local private key management with test-side access control. | ✅ Completed |
| **Account Access Methods** | Users can currently sign in using email and password credentials. | ✅ Completed |
| **Remote Security Layer** | Encrypted remote private key management with user-side access control. | 🔄 In Progress |
| **Wallet Dashboard** | Simple and intuitive interface for managing balances, transaction history, etc. | 🔄 In Progress |
| **KYC Foundation** | Integrated KYC/AML services via Didit. | 🛠️ Under Review (Testing) |
| **Accessibility** | Deployment on both Android and iOS platforms. | 🔄 In Progress |
| **Anchor Integration** | Technical integration with Bitso’s sandbox environment. | ⏳ Pending (Awaiting MSB license approval) |
| **MSB Registration** | Money Services Business (MSB) registration process. | ⏳ Pending (Awaiting final decision) |
| **Extended Localization** | Additional Portuguese language support. | ⏳ Pending |
| **Wallet Advanced Operations** | Expanding wallet support to full SEP-005/BIP-44 derivation standards. | ⏳ Pending |
| **New Account Access Methods** | Users will be able to sign in using Google and Apple ID authentication options. | ⏳ Pending |

---

### 🔗 Example Stellar Testnet Accounts

- [Account 1 – Test Wallet](https://stellar.expert/explorer/testnet/account/GAN5GYOQHVYDBIH4VDOWCCC3DYIWP3CZQTBLTQSAA75O7UB7H2LJCXC4)
- [Account 2 – Test Wallet](https://stellar.expert/explorer/testnet/account/GAN5GYOQHVYDBIH4VDOWCCC3DYIWP3CZQTBLTQSAA75O7UB7H2LJCXC4)
- [Account 3 – Test Wallet](https://stellar.expert/explorer/testnet/account/GAN5GYOQHVYDBIH4VDOWCCC3DYIWP3CZQTBLTQSAA75O7UB7H2LJCXC4)

---

## 🤝 Partners / Integration Status

| Partner / Integration | Role | Status | Notes |
|------------------------|------|--------|-------|
| **Bitso** | Stellar Anchor (MXN ↔ XLM/USDC) | ⏳ Pending | Awaiting **MSB approval** before activation. |
| **Didit** | KYC Provider | 🛠️ Under Review (Testing) |Phase 1 implemented. Testing and refinement are currently in progress. |
| **Firebase** | Authentication | ✅ Completed | Used for user login, password reset, and data synchronization. |
| **Firebase** | Realtime Database | 🔄 In Progress | Used for secure user data storage and synchronization. |
| **Stellar SDK for Flutter** | Blockchain Layer | ✅ Completed | Provides core account management and payment functionality. |

---

## 🧪 Open Testing Environment (Under Review)

### **Android**

| Detail | Information |
|---------|--------------|
| **Testing Program** | [Google Play Internal Test](https://play.google.com/apps/internaltest/4700964082050049995) |
| **Test Account** | `tester@nemorixpay.com` |
| **Password** | `jhd8fhod8fh8fh` |
| **Status** | ✅ Active |

#

### **iOS**

| Detail | Information |
|---------|--------------|
| **Testing Program** | [TestFlight Internal Test](https://play.google.com/apps/internaltest/4700964082050049995) |
| **Test Account** | `tester@nemorixpay.com` |
| **Password** | `jhd8fhod8fh8fh` |
| **Status** | 🔄 Under Review |

---

## 🧭 Next Steps

- Finalize **Bitso** integration post–MSB approval.  
- Complete **KYC Phase 2** implementation with Didit.  
- Deploy NemorixPay **V1** to Google Play and App Store for open beta testing.

---

📄 *Last updated: October 2025*
