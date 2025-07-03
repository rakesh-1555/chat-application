# 🚀 Advanced Real-Time Chat Application

A modern, feature-rich real-time chat application built with Next.js 14, Firebase, and Tailwind CSS. This application provides seamless messaging experiences with user authentication, real-time messaging, emoji support, and beautiful UI components.

![Chat App Demo](https://img.shields.io/badge/Next.js-black?style=for-the-badge&logo=next.js)
![Firebase](https://img.shields.io/badge/Firebase-orange?style=for-the-badge&logo=firebase)
![React](https://img.shields.io/badge/React-blue?style=for-the-badge&logo=react)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css)

## ✨ Features

### 🔐 Authentication

- **User Registration** - Create new accounts with email/password
- **User Login** - Secure authentication with Firebase Auth
- **Session Management** - Persistent login sessions
- **Form Validation** - Client-side validation with error handling

### 💬 Real-Time Messaging

- **Instant Messaging** - Real-time message delivery using Firebase Firestore
- **Chat Rooms** - Create and join different chat rooms
- **Message History** - Persistent message storage and retrieval
- **Online Status** - See who's currently online
- **Auto-scroll** - Automatic scrolling to latest messages

### 🎨 User Experience

- **Emoji Support** - Rich emoji picker for expressive messaging
- **Avatar Generation** - Random avatar generation for users
- **Responsive Design** - Works seamlessly on desktop and mobile
- **Beautiful UI** - Modern design with DaisyUI components
- **Toast Notifications** - User-friendly feedback messages
- **Loading States** - Smooth loading indicators

### 🛠️ Technical Features

- **Environment Variables** - Secure configuration management
- **Real-time Updates** - Live message synchronization
- **Error Handling** - Comprehensive error management
- **Code Organization** - Clean, modular component structure

## 🏗️ Project Structure

```
advanced-chat-yt-main/
├── app/
│   ├── components/
│   │   ├── ChatRoom.js         # Main chat interface
│   │   ├── MessageCard.js      # Individual message display
│   │   ├── MessageInput.js     # Message composition
│   │   ├── Users.js            # User list component
│   │   └── UsersCard.js        # User card display
│   ├── login/
│   │   └── page.js            # Login page
│   ├── register/
│   │   └── page.js            # Registration page
│   ├── layout.js              # Root layout
│   ├── page.js                # Home page
│   └── globals.css            # Global styles
├── lib/
│   └── firebase.js            # Firebase configuration
├── public/                    # Static assets
├── .env.local                 # Environment variables (create this)
├── .env.example              # Environment template
├── package.json              # Dependencies
├── tailwind.config.js        # Tailwind configuration
└── README.md                 # This file
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ and npm/yarn
- Firebase project with Firestore and Authentication enabled
- Git (for cloning)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/advanced-chat-yt-main.git
   cd advanced-chat-yt-main
   ```

2. **Install dependencies**

   ```bash
   npm install
   # or
   yarn install
   ```

3. **Set up environment variables**

   Copy the example environment file:

   ```bash
   cp .env.example .env.local
   ```

   Fill in your Firebase configuration in `.env.local`:

   ```env
   NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key_here
   NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_auth_domain_here
   NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id_here
   NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_storage_bucket_here
   NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_messaging_sender_id_here
   NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id_here
   NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID=your_measurement_id_here
   ```

4. **Run the development server**

   ```bash
   npm run dev
   # or
   yarn dev
   ```

5. **Open your browser**

   Navigate to [http://localhost:3000](http://localhost:3000) to see the application.

## ⚙️ Firebase Setup

### 1. Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Create a project"
3. Follow the setup wizard

### 2. Enable Authentication

1. In Firebase Console, go to "Authentication"
2. Click "Get started"
3. Enable "Email/Password" sign-in method

### 3. Setup Firestore Database

1. Go to "Firestore Database"
2. Click "Create database"
3. Start in test mode (configure security rules later)
4. Choose a location

### 4. Get Configuration

1. Go to Project Settings (gear icon)
2. Scroll down to "Your apps"
3. Click "Web" icon to add web app
4. Copy the configuration object
5. Add values to your `.env.local` file

### 5. Firestore Security Rules (Optional)

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Users can read/write their own user document
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }

    // Messages can be read/written by authenticated users
    match /messages/{messageId} {
      allow read, write: if request.auth != null;
    }

    // Chat rooms can be read/written by authenticated users
    match /chatrooms/{chatroomId} {
      allow read, write: if request.auth != null;
    }
  }
}
```

## 📦 Dependencies

### Core Dependencies

- **Next.js 14.0.3** - React framework with App Router
- **React 18** - UI library
- **Firebase 10.7.0** - Backend services (Auth, Firestore)
- **Tailwind CSS 3.3.0** - Utility-first CSS framework
- **DaisyUI 4.4.19** - Tailwind CSS components

### Additional Libraries

- **emoji-picker-react** - Emoji selection component
- **moment** - Date/time manipulation
- **random-avatar-generator** - Avatar generation
- **react-hot-toast** - Toast notifications
- **react-icons** - Icon library

## 🛠️ Available Scripts

```bash
# Development
npm run dev          # Start development server

# Production
npm run build        # Build for production
npm run start        # Start production server

# Code Quality
npm run lint         # Run ESLint
```

## 🎨 Customization

### Tailwind Configuration

The project uses Tailwind CSS with DaisyUI for styling. Customize themes in `tailwind.config.js`:

```javascript
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx,mdx}",
    "./components/**/*.{js,ts,jsx,tsx,mdx}",
    "./app/**/*.{js,ts,jsx,tsx,mdx}",
  ],
  theme: {
    extend: {
      // Your custom theme extensions
    },
  },
  plugins: [require("daisyui")],
  daisyui: {
    themes: ["light", "dark"], // Add your preferred themes
  },
};
```

### Adding New Features

1. **Components** - Add new components to `app/components/`
2. **Pages** - Create new routes in the `app/` directory
3. **Styling** - Use Tailwind classes or extend the theme
4. **Firebase Rules** - Update security rules as needed

## 🚀 Deployment

### Vercel (Recommended)

1. Push your code to GitHub
2. Connect your repository to [Vercel](https://vercel.com)
3. Add environment variables in Vercel dashboard
4. Deploy automatically on push

### Other Platforms

- **Netlify** - Similar to Vercel with environment variable support
- **Railway** - Full-stack deployment platform
- **Heroku** - Traditional platform with Node.js support

## 🔧 Troubleshooting

### Common Issues

1. **Firebase Connection Issues**

   - Verify environment variables are correct
   - Check Firebase project permissions
   - Ensure Firestore is enabled

2. **Authentication Problems**

   - Verify Email/Password is enabled in Firebase Auth
   - Check security rules
   - Clear browser cache/cookies

3. **Real-time Updates Not Working**
   - Check Firestore security rules
   - Verify network connection
   - Check browser console for errors

### Debug Mode

Enable debug logging by adding to your environment:

```env
NEXT_PUBLIC_DEBUG=true
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) for the amazing React framework
- [Firebase](https://firebase.google.com/) for backend services
- [Tailwind CSS](https://tailwindcss.com/) for styling utilities
- [DaisyUI](https://daisyui.com/) for beautiful components
- [React Icons](https://react-icons.github.io/react-icons/) for iconography

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/yourusername/advanced-chat-yt-main/issues) page
2. Create a new issue with detailed information
3. Reach out to the maintainers

---

**Built with ❤️ using Next.js and Firebase**
