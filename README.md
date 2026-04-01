OK 👍 đây là bản **siêu gọn – copy lên GitHub là đẹp ngay**:

---

````md
# 🚀 TrayManager.dll – System Tray + Multi-thread Logger

> 🔥 DLL C++Builder giúp tạo app chạy nền (System Tray) + Logger đa luồng + Callback realtime

---

## ✨ Features

### 🖥️ System Tray
- Icon + Tooltip
- Balloon notification
- Click / Double-click
- Exit callback
- Truyền icon từ EXE (không mờ)

### 🧵 Logger
- Multi-thread (thread-safe)
- Levels: Debug / Info / Warn / Error
- Non-blocking, hiệu năng cao
- Tự tạo file log

### 🔁 Callback
- Nhận log realtime
- Hiển thị UI / debug / forward

### 🌐 Unicode
- Dùng `PWideChar`
- Hỗ trợ tiếng Việt

---

## 📦 SDK

```text
TrayManager_SDK/
├── AppTrayBootstrap.pas
├── TrayManagerSDK.pas
├── LoggerCoreSDK.pas
├── LoggerCoreHelper.pas
├── SingleInstanceSDK.pas
└── TrayManager.dll   (required)
````

---

## ⚡ Quick Start

### DPR

```delphi
AppAuto_Initialize;
```

### Form

```delphi
procedure ExitApp; stdcall;
begin
  AllowCloseGlobal := True;
  Application.Terminate;
end;

procedure TForm1.FormCreate(Sender: TObject);
begin
  AppTray_Init(Self, 'MyApp', 'App đang chạy', @ExitApp);
end;
```

---

## ⚙️ Architecture

```text
Delphi EXE
   ↓
Pascal SDK
   ↓
TrayManager.dll
   ↓
Windows API
```

---

## 🚀 Behavior

* 🟢 Run normally → hiện form
* ⚫ Run with Windows → chạy nền (tray)

---

## ⚠️ Note

* `TrayManager.dll` phải cùng thư mục EXE
* Callback phải `stdcall`
* Windows only

---

## 👨‍💻 Author

Kieu Manh



Nếu muốn “ngầu hơn” nữa mình sẽ làm bản có **badge + banner + tiếng Anh** 👍
```
