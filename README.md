# InfluencerMarketplaceAndroid

📱 **Complete Android App for Influencer Marketing Marketplace**

Ready-to-use Android application built with Kotlin for the Influencer Marketing Marketplace platform. Connect brands with influencers directly without middlemen.

## 🎯 Features

✅ **Influencer Profiles**
- Connect Instagram/YouTube/TikTok accounts
- Set pricing for Reels, Stories, Posts
- Display engagement rates
- Automatic fake follower detection

✅ **Brand Search & Filters**
- Filter by category, location, followers, budget
- Smart ranking algorithm (engagement + relevance)
- India-focused marketplace

✅ **Booking System**
- Book influencers for campaigns
- Escrow payment system
- Task dashboard & tracking
- Content approval workflow

✅ **Payment Integration**
- Stripe/Razorpay payment gateway
- Secure escrow transactions
- Real-time payment tracking

✅ **User Authentication**
- Firebase Authentication
- Role-based access (Brand/Influencer)
- Secure token management

---

## 📋 Project Structure

```
InfluencerMarketplaceAndroid/
├── app/
│   ├── src/main/
│   │   ├── java/com/influencermarketplace/
│   │   │   ├── ui/
│   │   │   │   ├── activities/
│   │   │   │   │   ├── LoginActivity
│   │   │   │   │   ├── DashboardActivity
│   │   │   │   │   ├── SearchInfluencersActivity
│   │   │   │   │   ├── InfluencerProfileActivity
│   │   │   │   │   ├── BookingActivity
│   │   │   │   │   └── PaymentActivity
│   │   │   │   └── fragments/
│   │   │   │       ├── HomeFragment
│   │   │   │       ├── SearchFragment
│   │   │   │       ├── BookingsFragment
│   │   │   │       └── ProfileFragment
│   │   │   ├── models/
│   │   │   │   ├── User.kt
│   │   │   │   ├── Influencer.kt
│   │   │   │   ├── Brand.kt
│   │   │   │   ├── Booking.kt
│   │   │   │   └── Payment.kt
│   │   │   ├── network/
│   │   │   │   ├── ApiService.kt
│   │   │   │   ├── ApiClient.kt
│   │   │   │   └── AuthInterceptor.kt
│   │   │   ├── database/
│   │   │   │   ├── UserDatabase.kt
│   │   │   │   └── SharedPref.kt
│   │   │   ├── adapters/
│   │   │   │   ├── InfluencerAdapter.kt
│   │   │   │   └── BookingAdapter.kt
│   │   │   ├── viewmodels/
│   │   │   │   ├── LoginViewModel.kt
│   │   │   │   ├── SearchViewModel.kt
│   │   │   │   └── BookingViewModel.kt
│   │   │   └── utils/
│   │   │       ├── Constants.kt
│   │   │       └── Helper.kt
│   │   └── res/
│   │       ├── layout/
│   │       ├── values/
│   │       └── drawable/
│   └── build.gradle
└── README.md
```

---

## 🚀 Quick Start Guide

### Prerequisites
- Android Studio (Latest)
- JDK 11+
- Min SDK: 24 (Android 7.0)
- Target SDK: 34 (Android 14)

### Step 1: Clone the Repository
```bash
git clone https://github.com/HIMANSHU895060/InfluencerMarketplaceAndroid.git
cd InfluencerMarketplaceAndroid
```

### Step 2: Open in Android Studio
1. Open Android Studio
2. Click **File → Open**
3. Navigate to the project folder
4. Click **OK**

### Step 3: Sync Gradle
1. Click **File → Sync Now**
2. Wait for dependencies to download
3. All green ✅ = Ready to go!

### Step 4: Configure Backend URL
Open `app/java/com/influencermarketplace/utils/Constants.kt`:
```kotlin
object Constants {
    const val BASE_URL = "https://your-backend-api.com/api/"
    const val STRIPE_KEY = "your_stripe_public_key"
    const val RAZORPAY_KEY = "your_razorpay_key"
}
```

### Step 5: Setup Firebase (Optional)
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create new project
3. Download `google-services.json`
4. Place in `app/` folder
5. Uncomment Firebase imports in code

### Step 6: Run the App
1. Connect Android device or start emulator
2. Click **Run → Run 'app'**
3. Select device
4. App launches! 🎉

---

## 📱 Key Activities & Fragments

### LoginActivity
- Email/Password authentication
- Role selection (Brand/Influencer)
- Firebase auth integration

### DashboardActivity
- Home feed with tabs
- Navigation between fragments
- Bottom navigation bar

### SearchInfluencersActivity
- Advanced search filters
- Engagement ranking
- Quick booking option

### InfluencerProfileActivity
- Complete influencer details
- Social media links
- Pricing display
- Booking button

### BookingActivity
- Campaign creation
- Influencer selection
- Task description
- Booking confirmation

### PaymentActivity
- Stripe/Razorpay integration
- Secure payment processing
- Transaction confirmation

---

## 🔌 API Endpoints Required

Your backend should provide these endpoints:

```
AUTHENTICATION:
- POST /auth/login
- POST /auth/signup
- POST /auth/logout

INFLUENCERS:
- GET /influencers
- GET /influencers/{id}
- POST /influencers/profile
- GET /influencers/search (with filters)

BOOKINGS:
- POST /bookings/create
- GET /bookings/{id}
- PUT /bookings/{id}/approve
- GET /bookings/my-bookings

PAYMENTS:
- POST /payments/create
- GET /payments/{id}
- PUT /payments/{id}/confirm
```

---

## 🛠️ Core Dependencies

- **Kotlin**: Modern Android development
- **Retrofit + OkHttp**: API networking
- **Room Database**: Local storage
- **Firebase**: Authentication & real-time database
- **Stripe/Razorpay**: Payment processing
- **Glide**: Image loading
- **Material Design**: Modern UI components
- **Coroutines**: Async operations
- **LiveData + ViewModel**: MVVM architecture

---

## 📝 Sample Data Models

### User
```kotlin
data class User(
    val id: String,
    val email: String,
    val name: String,
    val role: String, // "brand" or "influencer"
    val profilePhoto: String,
    val phone: String
)
```

### Influencer
```kotlin
data class Influencer(
    val id: String,
    val userId: String,
    val instagramHandle: String,
    val youtubeChannel: String,
    val followers: Int,
    val engagementRate: Float,
    val category: String,
    val location: String,
    val reelPrice: Int,
    val storyPrice: Int,
    val postPrice: Int,
    val isFake: Boolean
)
```

### Booking
```kotlin
data class Booking(
    val id: String,
    val brandId: String,
    val influencerId: String,
    val campaignName: String,
    val budget: Int,
    val description: String,
    val status: String, // "pending", "approved", "completed"
    val createdAt: Long,
    val paymentId: String
)
```

---

## 🎨 UI/UX Highlights

✨ Material Design 3
✨ Dark mode support
✨ Smooth animations
✨ Bottom navigation
✨ Responsive layouts
✨ RecyclerView lists
✨ Custom layouts

---

## 🔐 Security Features

✅ JWT token authentication
✅ Encrypted storage (SharedPreferences)
✅ SSL/TLS encryption
✅ Input validation
✅ No hardcoded credentials
✅ Secure payment gateway integration

---

## 📊 Testing

```bash
# Run unit tests
./gradlew test

# Run instrumented tests
./gradlew connectedAndroidTest
```

---

## 🚢 Build & Deploy

### Debug APK
```bash
./gradlew assembleDebug
# APK location: app/build/outputs/apk/debug/app-debug.apk
```

### Release APK
```bash
./gradlew assembleRelease
# APK location: app/build/outputs/apk/release/app-release.apk
```

### Play Store Bundle
```bash
./gradlew bundleRelease
# Bundle location: app/build/outputs/bundle/release/app-release.aab
```

---

## 🐛 Troubleshooting

**Issue**: Gradle sync fails
**Solution**: 
1. Go to File → Settings → Appearance & Behavior → System Settings → Android SDK
2. Update SDK to latest version
3. Sync again

**Issue**: App crashes on launch
**Solution**:
1. Check logcat for errors
2. Ensure backend URL is correct in Constants.kt
3. Check internet permissions in AndroidManifest.xml

**Issue**: Payment not processing
**Solution**:
1. Verify Stripe/Razorpay keys
2. Check network connectivity
3. Review payment logs in logcat

---

## 📱 Screenshots

*(Add your app screenshots here)*

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature/YourFeature`
3. Commit changes: `git commit -m 'Add YourFeature'`
4. Push to branch: `git push origin feature/YourFeature`
5. Open Pull Request

---

## 📄 License

MIT License - See LICENSE file for details

---

## 👨‍💻 Developer

**Your Name**
- GitHub: [@HIMANSHU895060](https://github.com/HIMANSHU895060)
- LinkedIn: [Your Profile]
- Email: your.email@example.com

---

## 🌟 Support

If you found this helpful, please star ⭐ the repository!

---

## 📞 Contact

For issues, questions, or suggestions:
- Open an Issue
- Create a Discussion
- Email the developer

---

**Happy Coding! 🚀**

*Last Updated: January 2026*
