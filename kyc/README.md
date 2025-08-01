# NemorixPay - Official document

<p align="left"></p>

<p align="left">
  <img src="https://github.com/nemorixpay/NemorixPay-Readme/blob/main/img/Logo%20Nemorix.png" width="400" title="NemorixPay logo">
</p>

## Subsection: KYC Feature

## Overview

The **KYC (Know Your Customer)** feature of NemorixPay implements a comprehensive identity verification system using modern technologies and robust architecture. This feature is essential for compliance with financial regulations and ensuring platform security.

## 🏗️ Architecture

### Clean Architecture Implementation

The feature follows **Clean Architecture** principles with clear separation of responsibilities:

```
lib/features/kyc/
├── data/           # Data Layer
│   ├── datasources/
│   ├── repositories/
│   └── models/
├── domain/         # Domain Layer
│   ├── entities/
│   ├── repositories/
│   └── usecases/
└── presentation/   # Presentation Layer
    ├── bloc/
    ├── pages/
    └── widgets/
```

### State Management

We use **BLoC (Business Logic Component)** for state management:

- **Events**: Actions that trigger state changes
- **States**: Immutable states that represent the UI
- **BLoC**: Business logic that processes events and emits states

## 🛠️ Technologies Used

### Core Dependencies
- **Flutter**: Main framework
- **flutter_bloc**: State management
- **webview_flutter**: External service integration
- **flutter_secure_storage**: Secure data storage
- **equatable**: State comparison
- **dartz**: Functional error handling

### Backend Integration
- **Firebase Functions**: Serverless backend for secure operations
- **HTTPS**: Encrypted communication
- **API Gateway**: Secure authentication handling

## 🔐 Security

### Implemented Security Principles

1. **API Keys Protection**
   - API keys are never exposed in the client
   - All sensitive operations are performed in the backend
   - Authentication through Firebase Functions

2. **Data Protection**
   - Secure storage with `flutter_secure_storage`
   - Sensitive data is not persisted locally
   - HTTPS communication mandatory

3. **Session Management**
   - Sessions with automatic expiration (24h)
   - User permission validation
   - Secure token handling

## 🎯 Main Components

### KYCWebViewWidget
Reusable WebView widget with robust state handling:

```dart
class KYCWebViewWidget extends StatefulWidget {
  final String url;
  final VoidCallback? onPageFinished;
  final VoidCallback? onError;
  final VoidCallback? onNavigationRequest;
}
```

**Features:**
- Loading and error state handling
- Automatic retry button
- Navigation event callbacks
- Integrated help interface

### KYCStatusBanner
Persistent banner to display verification status:

```dart
class KYCStatusBanner extends StatelessWidget {
  final KYCStatus status;
  final VoidCallback? onStartVerification;
  final VoidCallback? onRetry;
}
```

### KYCSession Entity
Main entity representing a verification session:

```dart
class KYCSession extends Equatable {
  final String sessionId;
  final String sessionToken;
  final String url;
  final DateTime createdAt;
  final KYCStatus status;
  
  // Helper methods
  bool get isExpired => DateTime.now().difference(createdAt).inHours >= 24;
  bool get isActive => !isExpired && status != KYCStatus.completed;
}
```

## 📊 System States

### KYCStatus Enum
```dart
enum KYCStatus {
  notStarted,    // User has never started KYC
  inProgress,    // Session created, user in process
  completed,     // KYC completed successfully
  failed,        // KYC failed
  underReview,   // Under manual review
  expired        // Session expired (24h)
}
```

### BLoC States
- `KYCInitial`: Initial state
- `KYCLoading`: Loading data
- `KYCLoaded`: Data loaded
- `KYCSessionCreated`: Session created
- `KYCVerificationStarted`: Verification started
- `KYCStatusUpdated`: Status updated
- `KYCSessionCleared`: Session cleared
- `KYCError`: Operation error

## 🧪 Testing Strategy

### Testing Coverage
- **Unit Tests**: All individual components
- **Widget Tests**: UI components
- **BLoC Tests**: Business logic
- **Integration Tests**: Complete flows
- **Security Tests**: Security validation

### Testing Tools
- `flutter_test`: Testing framework
- `mockito`: Dependency mocking
- `bloc_test`: BLoC testing
- `integration_test`: Integration testing

## 🎨 User Experience

### Verification Flow
1. **Persistent Banner**: Shows current status until verification is complete
2. **Session Start**: Automatic secure session creation
3. **Verification Process**: External interface integrated via WebView
4. **Real-time States**: Automatic state updates
5. **Unlimited Retries**: No artificial restrictions

### UX Features
- **Clear States**: Specific messages for each state
- **Integrated Help**: Instructions dialog
- **Transparent Loading**: Progress indicators
- **Error Handling**: Informative messages and retry options

## 📱 Navigation

### Navigation Flow
```
Home Page (Banner) → KYC Verification Page (WebView)
    ↓
Settings Page → KYC Verification Page (WebView)
```

### Integration
- Persistent banner on Home Page
- Access from Settings for updates
- Smooth navigation between screens

## 🚀 Scalability

### Scalability Features
- **Reusable WebView**: For future integrations
- **Granular States**: For specific handling
- **Modular Architecture**: Easy extension
- **Serverless Backend**: Auto-scalable
- **Complete Testing**: For maintenance

### Future Extensions
- Integration with multiple KYC providers
- Additional biometric verification
- Compliance reports
- Verification analytics

## 🔧 Configuration and Deployment

### Requirements
- Flutter SDK 3.2.3+
- Firebase project configured
- Internet permissions
- WebView configuration

### Dependencies
```yaml
dependencies:
  webview_flutter: ^4.7.0
  flutter_secure_storage: ^9.0.0
  flutter_bloc: ^8.1.3
  equatable: ^2.0.5
  dartz: ^0.10.1
```

## 📈 Metrics and Monitoring

### Implemented Metrics
- WebView loading time
- Verification success rate
- Average completion time
- Errors and retries

### Monitoring
- Structured logs
- Performance metrics
- Error alerts
- Usage analytics

## 🤝 Contribution

### Development Guidelines
1. **New Features**: Follow existing architecture pattern
2. **Testing**: Maintain minimum 80% coverage
3. **Security**: Never expose sensitive data
4. **Documentation**: Update technical documentation

### Code Review Checklist
- [ ] Unit tests included
- [ ] Security validated
- [ ] Performance optimized
- [ ] Documentation updated
- [ ] UX/UI consistent

## 📚 Additional Resources

### Internal Documentation
- Detailed technical documentation (private)
- Troubleshooting guides
- API specifications
- Security configurations

### Community
- Contributions welcome
- Issues and feature requests
- Pull requests with testing
- Change documentation

---

**Last updated**: July 31, 2025  
**Version**: 1.0  
**Author**: Miguel Fagundez  
**License**: Apache 2.0
