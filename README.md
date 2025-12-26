# 📱 BoardBridge

[![Kotlin](https://img.shields.io/badge/Kotlin-1.9.0-blue.svg)](https://kotlinlang.org)
[![Firebase](https://img.shields.io/badge/Firebase-32.7.0-orange.svg)](https://firebase.google.com)
[![Compose](https://img.shields.io/badge/Jetpack%20Compose-1.5.0-green.svg)](https://developer.android.com/jetpack/compose)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **Classroom Without Walls** - Live lesson broadcasting for mobile education

BoardBridge connects teachers and students through real-time whiteboard streaming, enabling remote learning accessible from any smartphone.

---

## 🎯 **Problem Statement**

In regions like Malawi, students face significant barriers to quality education:
- Limited access to physical classrooms
- Shortage of qualified teachers
- Geographic isolation
- High cost of educational materials

**BoardBridge solves this** by enabling teachers to broadcast live lessons directly from their phones, allowing multiple students to join, view, and save snapshots for later review.

---

## ✨ **Features**

### For Teachers 👨‍🏫
- 📹 **Live Broadcasting** - Stream whiteboard lessons in real-time
- 📚 **Class Management** - Organize and manage multiple classes
- 👥 **Student Tracking** - Monitor who's joined each session
- 🎥 **Camera Setup** - Flexible camera positioning and controls
- 📊 **Session History** - View recent broadcasts

### For Students 👨‍🎓
- 🔴 **Join Live Sessions** - View broadcasts in real-time
- 📸 **Snapshot Capture** - Save important moments from lessons
- 📂 **Personal Library** - Access saved snapshots anytime
- 🔔 **Live Notifications** - See when teachers go live
- 📱 **Offline Access** - Review saved content without internet

### Shared Features
- 🔐 **Firebase Authentication** - Secure sign-up/sign-in
- ☁️ **Cloud Sync** - All data synced across devices
- 🎨 **Material Design 3** - Beautiful, intuitive interface
- 🌐 **Google Classroom Integration** - Import existing classes
- ♿ **Accessibility** - Designed for low-bandwidth environments

---

## 🏗️ **Architecture**

BoardBridge follows **Clean Architecture** principles with **MVVM** pattern:

```
app/
├── data/
│   ├── model/           # Data classes (User, ClassRoom, LiveSession)
│   └── repository/      # Firebase operations
├── ui/
│   ├── viewmodel/       # Business logic (Auth, Class, LiveSession)
│   ├── theme/           # UI theming
│   └── screens/         # Composable screens
└── utils/               # Helper functions
```

---

## 🛠️ **Tech Stack**

| Category | Technology |
|----------|-----------|
| **Language** | Kotlin 1.9.0 |
| **UI Framework** | Jetpack Compose |
| **Architecture** | MVVM + Clean Architecture |
| **Backend** | Firebase (Auth, Firestore, Realtime DB, Storage) |
| **Authentication** | Firebase Auth + Google Sign-In |
| **Database** | Cloud Firestore + Realtime Database |
| **Camera** | CameraX / Camera2 API |
| **Async** | Coroutines + Flow |
| **DI** | Manual (easily upgradable to Hilt) |
| **Design** | Material Design 3 |

---

## 🚀 **Getting Started**

### Prerequisites
- Android Studio Hedgehog (2023.1.1) or newer
- JDK 17+
- Android SDK 24+ (Target: 34)
- Firebase account

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/boardbridge.git
cd boardbridge
```

2. **Firebase Setup**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project: "BoardBridge"
   - Add Android app with package: `com.example.myapplication`
   - Download `google-services.json`
   - Place it in `app/` directory

3. **Enable Firebase Services**
   - **Authentication**: Email/Password + Google Sign-In
   - **Firestore Database**: Create in test mode
   - **Realtime Database**: Create in test mode
   - **Storage**: Enable for image uploads

4. **Open in Android Studio**
```bash
# Open the project in Android Studio
# Sync Gradle files
# Wait for dependencies to download
```

5. **Run the app**
   - Connect device or start emulator
   - Click Run ▶️
   - Select target device

---

## 📊 **Database Structure**

### Firestore Collections

```
users/
└── {userId}
    ├── uid: String
    ├── email: String
    ├── name: String
    ├── institution: String
    ├── userType: "teacher" | "student"
    └── createdAt: Timestamp

classes/
└── {classId}
    ├── classId: String
    ├── className: String
    ├── teacherId: String
    ├── teacherName: String
    ├── studentCount: Number
    ├── students: Array<String>
    └── createdAt: Timestamp

snapshots/
└── {snapshotId}
    ├── snapshotId: String
    ├── studentId: String
    ├── classId: String
    ├── className: String
    ├── imageUrl: String
    └── timestamp: Timestamp
```

### Realtime Database

```
live_sessions/
└── {sessionId}
    ├── sessionId: String
    ├── classId: String
    ├── className: String
    ├── teacherId: String
    ├── teacherName: String
    ├── isLive: Boolean
    ├── studentCount: Number
    ├── startTime: Timestamp
    └── boardImageUrl: String
```

---

## 📱 **Screenshots**

| Teacher Dashboard | Student Dashboard | Live Session |
|-------------------|-------------------|--------------|
| ![Teacher](screenshots/teacher-dashboard.png) | ![Student](screenshots/student-dashboard.png) | ![Live](screenshots/live-session.png) |

| Sign Up | Class Selection | Broadcasting |
|---------|-----------------|--------------|
| ![Signup](screenshots/signup.png) | ![Classes](screenshots/classes.png) | ![Broadcast](screenshots/broadcast.png) |

---

## 🧪 **Testing**

### Manual Testing

1. **Teacher Flow**
```
Sign Up → Create/Import Classes → Select Class → Start Broadcast
```

2. **Student Flow**
```
Sign Up → Join Classes → View Live Sessions → Capture Snapshots
```

3. **Test Data**
```kotlin
// Add test class in Firebase Console
{
  "classId": "test123",
  "className": "Mathematics 101",
  "teacherId": "your-teacher-uid",
  "teacherName": "Prof. Banda",
  "studentCount": 0,
  "students": []
}
```

---

## 🎨 **Design System**

### Color Palette

```kotlin
// Teacher Theme (Indigo)
Primary: #4F46E5
Secondary: #6366F1
Accent: #818CF8

// Student Theme (Emerald)
Primary: #059669
Secondary: #10B981
Accent: #34D399

// Shared
Gray Light: #F3F4F6
Gray Medium: #6B7280
Gray Dark: #1F2937
```

### Typography
- **Headings**: SF Pro Display / Roboto Bold
- **Body**: SF Pro Text / Roboto Regular
- **Captions**: SF Pro Text / Roboto Light

---

## 🗺️ **Roadmap**

### Phase 1: Core Features ✅
- [x] User authentication
- [x] Teacher/Student dashboards
- [x] Class management
- [x] Live session framework

### Phase 2: Streaming (In Progress) 🚧
- [ ] Camera integration
- [ ] Real-time video streaming
- [ ] Snapshot capture
- [ ] Image storage

### Phase 3: Enhancement 📋
- [ ] Google Classroom integration
- [ ] Push notifications
- [ ] Offline mode
- [ ] Video recording
- [ ] Chat feature

### Phase 4: Scale 🚀
- [ ] Performance optimization
- [ ] Multi-language support
- [ ] Analytics dashboard
- [ ] Web version
- [ ] iOS version

---

## 🤝 **Contributing**

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch
```bash
git checkout -b feature/AmazingFeature
```
3. Commit your changes
```bash
git commit -m 'Add some AmazingFeature'
```
4. Push to the branch
```bash
git push origin feature/AmazingFeature
```
5. Open a Pull Request

### Code Style
- Follow [Kotlin Coding Conventions](https://kotlinlang.org/docs/coding-conventions.html)
- Use meaningful variable names
- Comment complex logic
- Write clean, readable code

---

## 📄 **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 BoardBridge

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

## 👥 **Team**

- **Lead Developer** - [Your Name](https://github.com/yourusername)
- **UI/UX Design** - [Designer Name]
- **Backend** - [Backend Dev]

---

## 🙏 **Acknowledgments**

- [Firebase](https://firebase.google.com/) - Backend infrastructure
- [Jetpack Compose](https://developer.android.com/jetpack/compose) - Modern UI toolkit
- [Material Design](https://m3.material.io/) - Design system
- University of Malawi - Inspiration and testing ground
- The open-source community

---

## 📞 **Contact**

- **Project Link**: [https://github.com/yourusername/boardbridge](https://github.com/yourusername/boardbridge)
- **Email**: boardbridge@example.com
- **Twitter**: [@boardbridge](https://twitter.com/boardbridge)

---

## 🌍 **Impact**

BoardBridge is designed to address educational challenges in Malawi and similar regions where:
- 60% of students lack consistent access to qualified teachers
- Mobile phones outnumber computers 10:1
- Internet bandwidth is limited but growing
- Educational content in local languages is scarce

By leveraging ubiquitous mobile technology, BoardBridge aims to:
- **Democratize Education** - Make quality teaching accessible to all
- **Bridge Gaps** - Connect urban teachers with rural students
- **Enable Flexibility** - Learn anytime, anywhere
- **Build Community** - Foster collaborative learning

---

<div align="center">

**Made with ❤️ for education**

[⭐ Star this repo](https://github.com/yourusername/boardbridge) • [🐛 Report Bug](https://github.com/yourusername/boardbridge/issues) • [✨ Request Feature](https://github.com/yourusername/boardbridge/issues)

</div>
