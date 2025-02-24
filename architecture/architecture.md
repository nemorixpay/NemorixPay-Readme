# NemorixPay - Official document

<p align="left"></p>

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/Logo%20Nemorix.png" width="400" title="NemorixPay logo">
</p>

## Subsection: System Architecture

NemorixPay implements the Clean Architecture software design pattern and the BLoC state management pattern. Details of these patterns can be found here:

* [NemorixPay: Clean Architecture](https://github.com/nemorixpay/NemorixPay-Readme/blob/main/architecture/cleanarchitecture.md)
* [NemorixPay: BloC](https://github.com/nemorixpay/NemorixPay-Readme/blob/main/architecture/bloc.md)

### High-Level Architecture of NemorixPay (Mobile App)

**1. Presentation Layer** (Flutter UI & State Management)
  * Framework: Flutter
  * State Management: BloC (Business Logic Component)
  * UI Components: Material UI / Cupertino UI
  * Main Screens:
    * Login & Onboarding
    * Dashboard
    * Send & Receive Payments
    * Transaction History
    * Settings
  * Interaction with Domain Layer: The UI triggers events handled by BloC, which updates the state accordingly.

**2. Domain Layer** (Business Logic & Use Cases)
  * Contains the core business rules and logic.
  * Defines use cases like payment processing, account management, and real-time exchange rate updates.
  * Interfaces with repositories, ensuring that the business logic remains independent from the data sources.
  * Integrates with Stellar SDK for blockchain transaction handling.

**3. Data Layer** (Repositories & External APIs)
  * Repositories: Fetch and manage data from different sources.
  * Remote Data Sources:
    * Horizon API (Stellar) for blockchain transactions.
    * REST APIs for fiat conversion and KYC validation.
  * Local Storage:
    * SharedPreferences or Hive for caching user settings and non-sensitive data.


