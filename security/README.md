# NemorixPay - Official document

<p align="left"></p>

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/Logo%20Nemorix.png" width="400" title="NemorixPay logo">
</p>

## Subsection: Security

### 🎯 Overview

Security is a critical aspect of NemorixPay, ensuring that users can safely authenticate and transact on the platform. The authentication system follows best practices by integrating multi-layered security measures, including password-based login, biometric authentication, and Two-Factor Authentication (2FA).

### Authentication Methods

**Basic Authentication (Email & Password)**

*	Users register and log in using email and password.
*	Passwords are hashed and securely stored.

**Biometric Authentication**

*	Supports fingerprint and face recognition.
*	Works as a secondary authentication layer after the initial login.
*	Credentials are stored in Secure Storage, ensuring protection even if the device is compromised.

**Two-Factor Authentication (2FA)**

Users can enable 2FA for additional security via:  
*	SMS-based OTP (One-Time Password).
*	Google Authenticator / Authy via TOTP (Time-Based One-Time Password).
*	OTPs are time-sensitive and expire after a short period.

### Security Best Practices

**Data Encryption**

*	AES-256 encryption for locally stored sensitive data.
*	End-to-End Encryption (E2EE) for authentication-related communications.
*	Secure sensitive data using Secure Storage with OS-level encryption.

**Session Management**

*	User sessions are short-lived to prevent session hijacking.
*	Automatic logout after inactivity timeout.

**Secure API Communication**

*	OAuth 2.0 and JWT-based authentication for API calls.
*	HTTPS/TLS 1.3 enforced for all network communications.
*	Protection against MITM (Man-in-the-Middle) attacks using SSL Pinning.

### Stellar Blockchain Security Considerations

Since NemorixPay interacts with Stellar’s blockchain, additional security layers ensure the safety of user transactions:

*	**Transaction Signing**: All transactions are signed locally before being sent to the Stellar network.
*	**Multi-Signature Wallets**: (Future scope) To enhance fund security, NemorixPay may implement multisig wallets.

📌 **Important**:

*	Stellar SDK supports secure key management and transaction signing [GitHub - Soneso](https://github.com/Soneso/stellar_flutter_sdk/blob/master/soroban.md).
*	Stellar enforces strong cryptographic protections against unauthorized transactions.

This authentication system ensures maximum security while maintaining a smooth user experience. Moreover, **additional security protocols are in place but are not documented here for confidentiality reasons**.
