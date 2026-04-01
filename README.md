---

# 🚀 TrayManager.dll – System Tray + Multi-thread Logger

🔥 A lightweight **C++Builder DLL** for building Windows tray applications with a **multi-threaded logger** and **real-time callbacks**.

---

## ✨ Features

### 🖥️ System Tray

* Tray icon with dynamic tooltip
* Balloon notifications
* Click / double-click handling
* Exit callback support
* Pass icon from EXE (no blurry icons)

---

### 🧵 Multi-thread Logger

* Thread-safe logging
* Levels: Debug / Info / Warning / Error
* Non-blocking (high performance)
* Automatic log file creation

---

### 🔁 Real-time Callback

* Receive logs instantly
* Useful for UI display or debugging
* Can forward logs to external systems

---

### 🌐 Unicode Ready

* Uses `PWideChar`
* Full Unicode / Vietnamese support

---

## 📦 SDK Structure

TrayManager_SDK includes:

* **AppTrayBootstrap.pas** → App initialization (1 line setup)
* **TrayManagerSDK.pas** → System tray API
* **LoggerCoreSDK.pas** → Logging API
* **LoggerCoreHelper.pas** → Helper functions
* **SingleInstanceSDK.pas** → Prevent multiple instances
* **TrayManager.dll** → Core engine (**required**)

---

## ⚡ Quick Start

In `.dpr`:

AppAuto_Initialize;

In your main form:

```delphi
procedure ExitApp; stdcall;
begin
  AllowCloseGlobal := True;
  Application.Terminate;
end;

procedure TForm1.FormCreate(Sender: TObject);
begin
  AppTray_Init(Self, 'MyApp', 'App is running', @ExitApp);
end;
```

---

## ⚙️ Architecture

Delphi EXE → Pascal SDK → TrayManager.dll → Windows API

✔ Clean separation between UI and core engine
✔ Easy to reuse across projects
✔ High performance (native DLL processing)

---

## 🚀 Behavior

* 🟢 Normal run → show main form
* ⚫ Startup (Windows) → run in background (tray)

---

## ⚠️ Notes

* `TrayManager.dll` must be in the same folder as the EXE
* Callback must use `stdcall`
* Windows only

---

## 👨‍💻 Author

**Kieu Manh**

---
