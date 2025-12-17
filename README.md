# 🚐 Food Van - Mobile Food Ordering App

A comprehensive Android application connecting customers with food vendors, built with **Java** and **Firebase**.

![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)

## 📱 Overview

Food Van is a dual-interface mobile application that serves both **customers** and **vendors**. Customers can browse menus, place orders, and track deliveries, while vendors can manage their food trucks, menus, and orders efficiently.

## ✨ Features

### Customer Features
- 🔐 **Authentication** - Email/Password, Google Sign-In, Phone OTP Verification
- 👤 **Profile Management** - Personal info, profile picture, gender, pronouns
- 📍 **Saved Addresses** - Multiple delivery addresses with Google Maps integration
- 💳 **Payment Methods** - Save and manage payment options
- 📋 **Order History** - View past orders with details
- ⭐ **Favorites** - Save favorite orders for quick reordering
- 🔔 **Notifications** - Real-time order updates and promotions
- 🗺️ **Map Integration** - Find nearby food vans with Google Maps
- 📞 **Phone Verification** - Firebase Phone Auth with OTP

### Vendor Features
- 📊 **Dashboard** - Analytics and order overview
- 🍔 **Menu Management** - Add, edit, delete menu items with images
- 📦 **Order Management** - Accept, prepare, and complete orders
- 💬 **Customer Chat** - In-app messaging with customers
- 📈 **Analytics** - Sales reports and insights
- 🔔 **Push Notifications** - New order alerts

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| **Java** | Primary programming language |
| **Android SDK** | Native Android development |
| **Firebase Auth** | User authentication |
| **Firebase Realtime Database** | Data storage |
| **Firebase Storage** | Image storage |
| **Firebase Cloud Messaging** | Push notifications |
| **Google Maps API** | Location services |
| **Material Design 3** | UI components |
| **WorkManager** | Background tasks & offline sync |

## 📁 Project Structure

```
app/src/main/java/com/example/foodvan/
├── activities/
│   ├── customer/          # Customer-facing activities
│   │   ├── CustomerProfileActivity.java
│   │   ├── EditPersonalInfoActivity.java
│   │   ├── PhoneVerificationActivity.java
│   │   ├── SavedAddressesActivity.java
│   │   ├── PaymentMethodsActivity.java
│   │   ├── OrderHistoryActivity.java
│   │   └── FavoriteOrdersActivity.java
│   └── vendor/            # Vendor-facing activities
│       ├── VendorDashboardActivity.java
│       ├── ManageMenuActivity.java
│       ├── OrderDetailActivity.java
│       └── CustomerChatActivity.java
├── adapters/              # RecyclerView adapters
├── fragments/             # UI fragments
├── models/                # Data models
├── utils/                 # Utility classes
│   ├── SessionManager.java
│   └── PrivacyPolicyManager.java
└── workers/               # WorkManager workers
    └── PhoneVerificationSyncWorker.java
```

## 🚀 Getting Started

### Prerequisites

- Android Studio Hedgehog (2023.1.1) or later
- JDK 11 or higher
- Android SDK 26+ (minimum) / 36 (target)
- Google account for Firebase

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/shivamatram/MIS_APP.git
   cd MIS_APP
   ```

2. **Open in Android Studio**
   - Open Android Studio
   - Select "Open an existing project"
   - Navigate to the cloned directory

3. **Configure Firebase**
   - Create a project in [Firebase Console](https://console.firebase.google.com/)
   - Download `google-services.json` and place it in `app/` directory
   - Enable Authentication (Email, Google, Phone)
   - Enable Realtime Database
   - Enable Storage

4. **Configure Google Maps** (Optional)
   - Get an API key from [Google Cloud Console](https://console.cloud.google.com/)
   - Add to `local.properties`:
     ```properties
     MAPS_API_KEY=your_api_key_here
     ```

5. **Build and Run**
   ```bash
   ./gradlew assembleDebug
   ```

## ⚙️ Configuration

### Firebase Setup

1. **Authentication**
   - Enable Email/Password sign-in
   - Enable Google sign-in
   - Enable Phone authentication
   - Add SHA-1/SHA-256 fingerprints for Phone Auth

2. **Database Rules** (`database.rules.json`)
   ```json
   {
     "rules": {
       "users": {
         "$uid": {
           ".read": "$uid === auth.uid",
           ".write": "$uid === auth.uid"
         }
       },
       "customers": {
         "$uid": {
           ".read": "$uid === auth.uid",
           ".write": "$uid === auth.uid"
         }
       }
     }
   }
   ```

3. **Storage Rules** (`storage.rules`)
   ```
   rules_version = '2';
   service firebase.storage {
     match /b/{bucket}/o {
       match /profile_images/{userId}/{allPaths=**} {
         allow read, write: if request.auth != null && request.auth.uid == userId;
       }
     }
   }
   ```

## 📸 Screenshots

| Customer Home | Profile | Phone Verification |
|---------------|---------|-------------------|
| ![Home](screenshots/home.png) | ![Profile](screenshots/profile.png) | ![Phone](screenshots/phone.png) |

## 🎨 Theme

The app uses a custom **orange theme** aligned with the Food Van brand:

| Color | Hex | Usage |
|-------|-----|-------|
| Primary | `#FF6B35` | Main brand color |
| Primary Dark | `#E55A2B` | Status bar, dark elements |
| Background | `#FAFAFA` | Screen backgrounds |
| Success | `#4CAF50` | Success states |
| Error | `#F44336` | Error states |

## 🧪 Testing

### Test Phone Verification
For development, the app includes a test mode:
- Test Phone: Any 10-digit number starting with 6-9
- Test OTP: `123456`

To disable test mode for production, set `TEST_MODE = false` in `PhoneVerificationActivity.java`.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Shiva Matram**
- GitHub: [@shivamatram](https://github.com/shivamatram)

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

For support, email support@foodvan.app or open an issue in this repository.

---

<p align="center">Made with ❤️ for food lovers everywhere</p>
