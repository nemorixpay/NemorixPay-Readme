# NemorixPay - Official document

<p align="left"></p>

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/Logo%20Nemorix.png" width="400" title="NemorixPay logo">
</p>
<p align="left"> NemorixPay will be a mobile-first payment solution designed to bring seamless, stable, and efficient transactions to underserved communities in Venezuela and Mexico. Leveraging Stellar’s blockchain, NemorixPay will enable freelancers, small businesses, and content creators to receive payments in USDC, XLM, and other stable assets, bridging the gap between traditional and digital economies.</p>

## :star:Overview of NemorixPay Phase 1

<p align="left">NemorixPay is a mobile-first payment platform designed to facilitate cross-border transactions between the U.S. and Latin America, starting with Mexico and Venezuela. The Phase 1 development focuses on delivering a seamless, secure, and low-cost solution for crypto-based remittances, leveraging blockchain technology to enable instant transactions with minimal fees. The mobile application will support stablecoins like USDC and XLM, providing users with a reliable alternative to traditional remittance services.</p>

### Goals and Scope of the Mobile Application

<p align="left">The primary goal of NemorixPay Phase 1 is to build a functional and user-friendly mobile application that enables:</p>

* **Crypto-to-crypto transactions**: Sending and receiving payments in USDC, XLM, and potentially other stablecoins.
* **Instant and low-cost transfers**: Leveraging the Stellar blockchain networks for fast and inexpensive transactions.
* **Non-custodial wallet support**: Users maintain full control of their funds without reliance on third-party intermediaries.
* **Basic user authentication and security measures**: Ensuring transactions are secure through encryption and authentication protocols.
* **Intuitive UI/UX design**: A mobile-first experience that is simple and accessible for both crypto-savvy users and newcomers.

<p align="left">The scope of Phase 1 is limited to:</p>

* Development of the mobile application for iOS and Android using Flutter.
* Integration with Stellar SDKs for blockchain transactions.
* Secure local storage of transaction history and wallet keys (without storing private keys on servers).
* Basic KYC requirements for initial regulatory compliance is a plus.

<p align="left">Future phases will expand on this foundation by introducing fiat conversion, bank integrations, and additional compliance features.</p>

## :star:Initial Technology Stack

<p align="left">NemorixPay’s mobile application will be built with a modern technology stack optimized for security, scalability, and seamless integration with the Stellar blockchain. The selection of technologies ensures high performance, maintainability, and cross-platform support.</p>

### Core Technologies

* **Programming Language**: Dart
* **Framework**: Flutter (for cross-platform mobile development, Android & iOS)
* **State Management**: BLoC (Business Logic Component)
* **Initial Backend Infrastructure**: Firebase (authentication, database, and cloud functions)
* **Storage**: Secure Storage for sensitive data (e.g., user keys and credentials)
* **Networking**: HTTP & WebSocket for real-time data fetching and transaction updates
* **Cryptography**: Stellar SDK built-in cryptographic tools for signing transactions

### Stellar Blockchain Integration

The mobile app will interact with the Stellar blockchain using the [Stellar Flutter SDK](https://github.com/Soneso/stellar_flutter_sdk), which provides essential tools for:

* **Account Management** – Creating and managing Stellar accounts.
* **Transaction Handling** – Constructing, signing, and submitting transactions to the Stellar network.
* **Balance & Payment Operations** – Querying balances, sending and receiving payments.
* **Soroban Smart Contracts** – (*Future scope*) Exploring contract deployment on Stellar’s Soroban.

📌 *Additional Notes*: The SDK documentation details [transaction signing and submission](https://github.com/Soneso/stellar_flutter_sdk/blob/master/soroban.md), ensuring compliance with Stellar's best practices.

## ⭐System Architecture

The application follows the principles of **Clean Architecture**, promoting a clear separation between the *presentation*, *domain*, and *data layers*. This approach enhances maintainability and scalability.

* **Presentation Layer**: Manages the UI components and user interactions. Utilizes the BLoC pattern to handle state management, ensuring a reactive and streamlined user experience.
* **Domain Layer**: Contains the core business logic and entities. Defines use cases that encapsulate application-specific business rules.
* **Data Layer**: Responsible for data retrieval from external sources, such as the Stellar network, and local storage. Implements repositories that abstract the data sources, providing a clean API to the domain layer.

### **BloC Pattern for State Management in Flutter**

The BloC (_Business Logic Component_) pattern is a powerful state management approach in Flutter that promotes separation of concerns by managing business logic and UI separately. It utilizes **Streams** and **Sinks** to handle state changes reactively, making applications more scalable and testable.

**How it Works**

* **Events**: The UI triggers events when a user interacts with the app.
* **Bloc**: The event is processed within the Bloc, where business logic executes and determines the new state.
* **States**: The UI listens to state changes and updates accordingly.

**Key Benefits**
* Clear separation of UI and logic, enhancing maintainability.
* Reactive programming, improving performance and responsiveness.
* Scalability, making it suitable for complex applications.

Flutter provides the [flutter_bloc](https://pub.dev/packages/flutter_bloc) package, which simplifies the implementation of the BloC pattern and integrates seamlessly with widgets.

### **Security Considerations**

Security is paramount in the design of NemorixPay. Key measures include:

* **Data Encryption**: Sensitive data is encrypted both in transit and at rest.
* **Authentication**: Implementation of robust authentication mechanisms to ensure authorized access.
* **Error Handling**: Comprehensive error handling to manage exceptions and maintain application stability.

By adhering to these initial architectural principles and leveraging the capabilities of the Stellar network, NemorixPay aims to deliver a robust and user-centric platform for cross-border cryptocurrency transactions.
