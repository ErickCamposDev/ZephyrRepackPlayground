
# ZephyrRepackPlayground

A React Native playground demonstrating Module Federation with Zephyr Repack Plugin, featuring a Host App that dynamically loads components from a MiniApp.

## Overview

This repository showcases Module Federation in React Native using:

- **Zephyr Repack Plugin** for enhanced module federation
- **Re.Pack** for Rspack bundling
- **HostApp** - consumes remote components
- **MiniApp** - exposes components via Module Federation

## Prerequisites

- Node.js >= 22
- npm >= 10
- pnpm (package manager)
- Ruby >= 3.3.2
- React Native development environment
- [Zephyr Cloud account](https://app.zephyr-cloud.io/)

## Installation

```bash
# Install dependencies for both apps
cd HostApp && pnpm install
cd ../MiniApp && pnpm install

# iOS setup
cd HostApp && pnpm run pods
cd ../MiniApp && pnpm run pods:update
```

## Running the Application

### iOS

1. **Start MiniApp bundler first:**

   ```bash
   pnpm --filter MiniApp start --platform ios
   ```

2. **Run HostApp:**
   ```bash
   pnpm --filter HostApp run ios
   ```

### Android

1. **Set up ADB reverse:**

   ```bash
   cd MiniApp && pnpm run adbreverse
   ```

2. **Start MiniApp bundler:**

   ```bash
   pnpm --filter MiniApp start --platform android
   ```

3. **Run HostApp:**
   ```bash
   pnpm --filter HostApp run android
   ```

### Standalone MiniApp

Run MiniApp independently:

```bash
pnpm --filter MiniApp start:standalone --platform ios
```

## Key Scripts

**HostApp:**

- `pnpm start` - Start bundler (port 8081)
- `pnpm run ios/android` - Run app with `--no-packager` flag

**MiniApp:**

- `pnpm start` - Start bundler (port 9001)
- `pnpm start:standalone` - Run in standalone mode
- `pnpm run adbreverse` - Set up Android port forwarding

## Resources

- [Zephyr Documentation](https://docs.zephyr-cloud.io/recipes/repack-mf)
- [Re.Pack Documentation](https://re-pack.dev/)
- [Module Federation](https://module-federation.io/)
