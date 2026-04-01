
# 🚀 TrayManager.dll – System Tray + Multi-thread Logger

🔥 Thư viện DLL viết bằng C++Builder giúp tạo ứng dụng chạy nền dưới System Tray, kèm Logger đa luồng và callback realtime.

---

## ✨ Tính năng

### 🖥️ System Tray

* Tạo icon dưới khay hệ thống
* Tooltip (hint) động
* Hiển thị thông báo (balloon)
* Xử lý click / double-click
* Callback khi chọn Exit
* Truyền icon từ EXE (không bị mờ)

### 🧵 Logger

* Ghi log đa luồng (thread-safe)
* Hỗ trợ Debug / Info / Warn / Error
* Không block (hiệu năng cao)
* Tự tạo file log

### 🔁 Callback realtime

* Nhận log ngay khi ghi
* Dùng để hiển thị UI hoặc debug

### 🌐 Unicode

* Dùng PWideChar
* Hỗ trợ tiếng Việt đầy đủ

---

## 📦 Cấu trúc

TrayManager_SDK gồm các thành phần:

* AppTrayBootstrap.pas → khởi tạo toàn bộ ứng dụng
* TrayManagerSDK.pas → quản lý system tray
* LoggerCoreSDK.pas → API logging
* LoggerCoreHelper.pas → helper gọi log
* SingleInstanceSDK.pas → chống chạy nhiều instance
* TrayManager.dll → core engine (bắt buộc)

---

## ⚡ Sử dụng nhanh

Trong file .dpr:

AppAuto_Initialize;

Trong Form:

procedure ExitApp; stdcall;
begin
AllowCloseGlobal := True;
Application.Terminate;
end;

procedure TForm1.FormCreate(Sender: TObject);
begin
AppTray_Init(Self, 'MyApp', 'App đang chạy', @ExitApp);
end;

---

## ⚙️ Kiến trúc

Delphi EXE → Pascal SDK → TrayManager.dll → Windows API

✔ Tách biệt UI và engine
✔ Dễ tái sử dụng
✔ Hiệu năng cao

---

## 🚀 Hoạt động

* Chạy bình thường → hiển thị form
* Chạy cùng Windows → ẩn xuống tray

---

## ⚠️ Lưu ý

* TrayManager.dll phải cùng thư mục EXE
* Callback phải dùng stdcall
* Chỉ hỗ trợ Windows

---

## 👨‍💻 Author

Kieu Manh

---

