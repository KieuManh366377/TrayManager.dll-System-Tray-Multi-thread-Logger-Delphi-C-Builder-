# 🚀 TrayManager.dll – System Tray + Multi-thread Logger (Delphi / C++Builder)

> 🔥 Thư viện **C++Builder DLL** giúp bạn tạo ứng dụng chạy nền dưới **System Tray**  
> + Logger đa luồng + Callback realtime

---

## ✨ Tính năng chính

### 🖥️ System Tray Manager
- 🧩 Tạo icon dưới khay hệ thống (System Tray)
- 💬 Tooltip (Hint) động
- 🔔 Hiển thị thông báo (Balloon)
- 🖱️ Xử lý click / double-click
- ❌ Callback khi chọn Exit từ menu tray
- 🎨 Truyền icon từ EXE (tránh icon mờ)

---

### 🧵 Multi-thread Logger Engine
- ⚡ Ghi log đa luồng (thread-safe)
- 🏷️ Hỗ trợ level:
  - 🐞 Debug
  - ℹ️ Info
  - ⚠️ Warning
  - ❌ Error
- 📁 Tự tạo file log
- 🧠 Non-blocking (hiệu năng cao)

---

### 🔁 Realtime Log Callback
- 📡 Nhận log ngay khi được ghi
- 🔌 Dùng để:
  - Hiển thị log lên UI
  - Debug realtime
  - Forward sang hệ thống khác

---

### 🌐 Unicode Ready
- ✅ Sử dụng `PWideChar`
- ✅ Hỗ trợ tiếng Việt đầy đủ

---

## 📦 Cấu trúc SDK

```

TrayManager_SDK/
│
├── AppTrayBootstrap.pas   // 🔥 Entry point (1 dòng là chạy)
├── TrayManagerSDK.pas     // System Tray API (icon, tooltip, balloon, callback)
├── LoggerCoreSDK.pas      // Logger API (multi-thread + callback)
├── LoggerCoreHelper.pas   // Wrapper tiện lợi cho EXE
├── SingleInstanceSDK.pas  // Chống chạy nhiều instance
│
└── TrayManager.dll        // ⚠️ Bắt buộc (core engine)

---

## 🧩 Mô tả các thành phần

| File | Mô tả |
|------|------|
| `AppTrayBootstrap.pas` | Entry point, gom toàn bộ init (tray + startup + UI) |
| `TrayManagerSDK.pas` | Giao tiếp với DLL để quản lý System Tray |
| `LoggerCoreSDK.pas` | API logging đa luồng + callback realtime |
| `LoggerCoreHelper.pas` | Hàm wrapper giúp gọi log dễ hơn |
| `SingleInstanceSDK.pas` | Đảm bảo chỉ chạy 1 instance |
| `TrayManager.dll` | Core engine viết bằng C++Builder |

---

## ⚙️ Cách hoạt động

```

[ Delphi EXE ]
↓
[ SDK (Pascal units) ]
↓
[ TrayManager.dll (C++Builder) ]
↓
[ Windows API (Tray + Thread + File IO) ]

```

👉 Kiến trúc này giúp:
- 🔌 Tách biệt UI và engine
- 🔁 Dễ reuse cho nhiều project
- ⚡ Tối ưu hiệu năng (DLL xử lý nặng)

---

## 🚀 Luồng khởi động

1. `AppAuto_Initialize` (trong `.dpr`)
2. `AppTray_Init` (trong `FormCreate`)
3. DLL khởi tạo:
   - Tray icon
   - Logger thread
   - Callback
4. Ứng dụng chạy:
   - Normal → hiện form
   - Startup → ẩn xuống tray

```

