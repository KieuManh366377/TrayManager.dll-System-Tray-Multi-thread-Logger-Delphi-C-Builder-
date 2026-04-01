---

# 🚀 TrayManager.dll – System Tray + Multi-thread Logger (Delphi / C++Builder)

> 🔥 Thư viện **C++Builder DLL** giúp bạn tạo ứng dụng chạy nền dưới **System Tray** + **Logger đa luồng + Callback realtime**

---

## ✨ Tính năng chính

### 🖥️ System Tray Manager

* 🧩 Tạo icon dưới khay hệ thống (System Tray)
* 💬 Tooltip (Hint) động
* 🔔 Hiển thị thông báo (Balloon)
* 🖱️ Xử lý click / double-click
* ❌ Callback khi chọn Exit từ menu tray
* 🎨 Hỗ trợ truyền icon từ EXE (tránh icon mờ)

---

### 🧵 Multi-thread Logger Engine

* ⚡ Ghi log đa luồng (thread-safe)
* 🏷️ Hỗ trợ level:

  * 🐞 Debug
  * ℹ️ Info
  * ⚠️ Warning
  * ❌ Error
* 📁 Tự tạo file log
* 🧠 Tối ưu hiệu năng (non-blocking)

---

### 🔁 Realtime Log Callback

* 📡 Nhận log ngay khi được ghi
* 🔌 Dùng để:

  * Hiển thị log lên UI
  * Debug realtime
  * Forward sang hệ thống khác

---

### 🌐 Unicode Ready

* ✅ Toàn bộ dùng `PWideChar`
* ✅ Hỗ trợ tiếng Việt đầy đủ

---

## 📦 Cấu trúc SDK

```
TrayManager_SDK/
│
├── AppTrayBootstrap.pas   // 🔥 Entry point (1 dòng là chạy)
├── TrayManagerSDK.pas     // Tray API
├── LoggerCoreSDK.pas      // Logger API
├── LoggerCoreHelper.pas   // Helper
├── SingleInstanceSDK.pas  // Chống chạy nhiều instance
│
└── TrayManager.dll        // ⚠️ Bắt buộc
```

---

## ⚡ Sử dụng nhanh (30 giây)

### 1. Trong `.dpr`

```delphi
begin
  Application.Initialize;
  Application.MainFormOnTaskbar := True;

  if not CheckSingleInstance(simFocus) then
    Halt;

  AppAuto_Initialize;

  Application.CreateForm(TForm1, Form1);
  Application.Run;
end.
```

---

### 2. Trong `Form`

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

procedure TForm1.FormCloseQuery(Sender: TObject; var CanClose: Boolean);
begin
  CanClose := AllowCloseGlobal;
end;
```

---

## 🧪 Logger sử dụng

### ✔️ Khởi tạo

```delphi
InitLogger('Log');
```

---

### ✔️ Ghi log đơn giản

```delphi
WriteLog('Hello');
```

---

### ✔️ Ghi log có level

```delphi
WriteLogEx('Có lỗi', Ord(llError));
```

---

### ✔️ Wrapper tiện lợi

```delphi
Log('Debug test', llDebug);
Log('Thông tin', llInfo);
Log('Cảnh báo', llWarn);
Log('Lỗi nghiêm trọng', llError);
```

---

### ✔️ Callback realtime

```delphi
procedure MyLogCallback(const Msg: PWideChar); stdcall;
begin
  // hiển thị lên memo hoặc debug
end;

SetLogCallback(@MyLogCallback);
```

---

## 🎯 Ứng dụng thực tế

* 🔄 App chạy nền (background service UI)
* 📊 Tool monitoring
* 🧾 Logger cho hệ thống lớn
* 🖥️ App ẩn dưới tray (giống OneDrive, Zalo…)
* 🔧 Dev tools nội bộ

---

## ⚠️ Lưu ý quan trọng

* ❗ `TrayManager.dll` phải nằm cùng thư mục EXE
* ❗ Callback phải là `stdcall`
* ❗ Chỉ hỗ trợ Windows

---

## 🧠 Kiến trúc

* ⚙️ Core viết bằng **C++Builder (DLL)**
* 🧩 EXE (Delphi / C++Builder) gọi qua SDK
* 🔌 Tách biệt UI và engine → dễ reuse

---

## 💡 Triết lý thiết kế

> 🔥 **Simple – Fast – Reusable – No Over-Engineering**

* Không phụ thuộc framework nặng
* Fail fast nếu thiếu DLL
* Code gọn, dễ copy project mới

---

## 📸 Demo

* Tray icon + Balloon
* Logger hiển thị realtime trên UI

---

## 👨‍💻 Author

**Kieu Manh**

---

public)
