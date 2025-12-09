# 🚀 RunAnywhere Expo Template

On-device AI demo with RunAnywhere SDK for React Native + Expo.

[![npm](https://img.shields.io/npm/v/runanywhere-react-native)](https://www.npmjs.com/package/runanywhere-react-native)
[![Run on Replit](https://replit.com/badge/github/RunanywhereAI/runanywhere-expo-demo)](https://replit.com/new/github/RunanywhereAI/runanywhere-expo-demo)

## ✨ Features

- 🧠 **100% On-Device AI** - No cloud required, complete privacy
- ⚡ **Fast Inference** - Optimized for mobile with llama.cpp & ONNX Runtime
- 🎤 **Voice AI** - Speech-to-text and text-to-speech
- 📱 **Expo + React Native** - Easy development workflow

## 🔧 Development Mode vs Production

| Feature | Development Mode | Production Mode |
|---------|------------------|-----------------|
| API Key | ❌ Not required | ✅ Required |
| Inference | 100% on-device | Hybrid on-device + cloud |
| Observability | ❌ None | ✅ Dashboard & analytics |
| Policy Engine | ❌ None | ✅ Cost/latency/privacy routing |
| Billing | ❌ Free | ✅ Usage tracking |

This template runs in **Development Mode** - perfect for prototyping!

## 🚀 Quick Start

### Option 1: Fork on Replit

1. Click the "Run on Replit" badge above
2. Install the dev client on your phone (see below)
3. Scan the QR code
4. Start coding!

### Option 2: Local Development

```bash
# Clone the template
git clone https://github.com/RunanywhereAI/runanywhere-expo-demo
cd runanywhere-expo-demo

# Install dependencies
npm install

# Start Expo dev server
npx expo start
```

## 📱 Important: Development Build Required

This SDK uses native modules, so **Expo Go won't work**. You need a development build:

### Build with EAS (Recommended)

```bash
# Install EAS CLI
npm install -g eas-cli

# Login to Expo
eas login

# Configure EAS
eas build:configure

# Build for Android (creates downloadable APK)
eas build --platform android --profile development

# Build for iOS (requires Apple Developer account)
eas build --platform ios --profile development
```

### Pre-built Dev Client

Download our pre-built development client:
- 📥 **Android APK**: [Download](https://expo.dev/artifacts/eas/gHZ2ANknUSsCZfEsYxPcFB.apk) - Anyone can install!
- 📥 **iOS TestFlight**: Coming soon

> **Note on iOS Distribution**: Apple requires either device registration (limited to 100 devices) 
> or TestFlight for public distribution. To enable iOS "vibe coding" for everyone, you'll need to 
> set up TestFlight distribution. Add `"distribution": "store"` to your eas.json build profile 
> and submit via `eas submit --platform ios`. See [Expo iOS Submit docs](https://docs.expo.dev/submit/ios/).

## 📦 SDK Usage

```typescript
import { RunAnywhere } from 'runanywhere-react-native';

// Initialize (Development Mode - no API key needed)
await RunAnywhere.initialize({});

// Load a model
await RunAnywhere.loadModel('lfm2-350m-q4-k-m');

// Generate text
const result = await RunAnywhere.generate('Hello, tell me a joke!', {
  maxTokens: 100,
  temperature: 0.7,
});

console.log(result.text);
```

### Production Mode (Coming Soon)

```typescript
// With API key for cloud features
await RunAnywhere.initialize({
  apiKey: process.env.EXPO_PUBLIC_RUNANYWHERE_API_KEY,
  environment: 'production',
});

// Enables:
// - Cloud observability dashboard
// - Policy engine for routing decisions
// - Hybrid on-device + cloud inference
// - Usage tracking and billing
```

## 🗂️ Project Structure

```
├── app/
│   ├── (tabs)/
│   │   └── index.tsx      # Main demo screen
│   └── _layout.tsx        # Navigation layout
├── app.json               # Expo config
├── package.json           # Dependencies
└── .replit                # Replit configuration
```

## 📚 Resources

- [RunAnywhere Documentation](https://docs.runanywhere.ai)
- [SDK npm Package](https://www.npmjs.com/package/runanywhere-react-native)
- [GitHub Repository](https://github.com/RunanywhereAI/sdks)

## 📄 License

MIT © [RunAnywhere AI](https://runanywhere.ai)
