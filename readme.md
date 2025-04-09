# wifi-nextjs

A cross-platform utility for controlling Wi-Fi (turning on/off, checking status) in Next.js APIs using Node.js, PowerShell (Windows), and networksetup (macOS).

## ✨ Features

- Turn Wi-Fi ON/OFF using API routes
- Supports macOS and Windows
- Auto-detects Wi-Fi device
- PowerShell automation for elevated commands on Windows
- Built with Next.js API routes

## 📦 Installation

```bash
npm install wifi-nextjs
```

```bash
yarn add wifi-nextjs
```
## 🛠️ Usage

### 1. Import the module

```js
import wifi from "wifi-nextjs";
```

### 2. Use it inside your API routes

#### `pages/api/wifi.js`

```js
export async function POST(request) {
  const { searchParams } = new URL(request.url);
  const command = searchParams.get("command");

  if (command === "on") {
    await wifi.on();
  } else if (command === "off") {
    await wifi.off();
  } else {
    return new Response("Invalid command", { status: 400 });
  }

  return new Response(JSON.stringify({ status: "success" }), {
    headers: { "Content-Type": "application/json" },
  });
}
```

### 3. HTTP Requests

- Turn on Wi-Fi:
  ```bash
  curl -X POST "/api/wifi?command=on"
  ```

- Turn off Wi-Fi:
  ```bash
  curl -X POST "/api/wifi?command=off"
  ```

- Get Wi-Fi status:
  ```bash
  curl /api/wifi
  ```

## 🧪 API Methods

```js
await wifi.on();         // Turn Wi-Fi on
await wifi.off();        // Turn Wi-Fi off
await wifi.toggle();     // Toggle Wi-Fi state
await wifi.isOn();       // Check if Wi-Fi is on
await wifi.device();     // Get Wi-Fi device name
await wifi.restart();    // Restart Wi-Fi
```

## ⚠️ Requirements

- **Windows**: PowerShell (with admin rights for changes)
- **macOS**: `networksetup` utility

## 📄 License

MIT 
