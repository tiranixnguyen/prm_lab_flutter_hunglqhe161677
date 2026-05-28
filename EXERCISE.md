# PRM Lab Exercises

## Lab 1 - Reflection Questions

### 1. What is the purpose of the `flutter doctor` command?

- **Mục đích:** Lệnh này dùng để kiểm tra "sức khỏe" hệ thống và môi trường phát triển (development environment) của bạn.
- **Chi tiết:** Nó sẽ quét máy tính xem bạn đã cài đặt đủ các công cụ cần thiết chưa (như Flutter SDK, Android Studio, VS Code, Xcode, các công cụ dòng lệnh...) và báo cáo chính xác những gì còn thiếu hoặc bị lỗi để bạn kịp thời sửa chữa trước khi lập trình.

---

### 2. What file acts as the entry point of a Flutter application?

- **File điểm khởi đầu:** Đó chính là file `lib/main.dart`.
- **Chi tiết:** Khi ứng dụng Flutter khởi chạy, compiler sẽ tìm đến hàm `main()` nằm bên trong file này đầu tiên để kích hoạt toàn bộ ứng dụng.

---

### 3. Explain the difference between Hot Reload and Hot Restart.

| Tiêu chí               | Hot Reload (`r`)                                                                                    | Hot Restart (`R`)                                                                            |
| :--------------------- | :-------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------- |
| **Cơ chế**             | Chỉ đẩy các thay đổi của code vào máy ảo Dart VM đang chạy.                                         | Kích hoạt lại toàn bộ ứng dụng và biên dịch lại code.                                        |
| **Trạng thái (State)** | **Giữ nguyên** trạng thái hiện tại (Ví dụ: số đếm trên màn hình đang là 5 thì vẫn giữ nguyên là 5). | **Xóa sạch** và reset trạng thái về ban đầu (Số đếm quay về 0).                              |
| **Tốc độ**             | Siêu nhanh (Dưới 1 giây).                                                                           | Chậm hơn Hot Reload một chút nhưng vẫn nhanh hơn việc chạy lại từ đầu.                       |
| **Khi nào dùng?**      | Khi sửa giao diện (UI), đổi màu sắc, đổi text, sửa lỗi nhỏ.                                         | Khi thay đổi hàm `main()`, thay đổi cấu trúc dữ liệu hoặc trạng thái khởi tạo (`initState`). |

---

### 4. How does `runApp()` build the widget tree?

- **Cách hoạt động:** Hàm `runApp()` nhận vào một Widget gốc (Root Widget) — ví dụ như `const MyApp()` — và gắn nó làm gốc của cây Widget (Widget Tree).
- **Chi tiết:** Flutter sẽ lấy Widget này làm điểm bắt đầu, sau đó đọc tiếp các Widget con nằm bên trong nó (như `MaterialApp`, `Scaffold`, `Center`, `Column`...) để vẽ (render) và sắp xếp chúng theo cấu trúc phân cấp hình cây lên trên màn hình thiết bị.

---

### 5. Describe how Flutter’s architecture enables cross-platform development.

Kiến trúc của Flutter giúp nó chạy mượt mà trên nhiều nền tảng (Android, iOS, Web, Desktop) nhờ vào hai yếu tố cốt lõi:

- **Tự vẽ giao diện (Skia/Impeller Graphics Engine):** Flutter không mượn hay phụ thuộc vào các thành phần giao diện (UI components) gốc của hệ điều hành. Thay vào đó, nó sở hữu một công cụ đồ họa riêng để tự vẽ từng pixel lên màn hình. Nhờ vậy, ứng dụng hiển thị giống hệt nhau trên mọi thiết bị.
- **Biên dịch trực tiếp (AOT Compilation):** Code Dart của bạn sẽ được biên dịch trực tiếp thành mã máy nguyên bản (Native Machine Code) của từng nền tảng (ARM code cho iOS/Android). Điều này giúp ứng dụng đạt hiệu năng cực cao, mượt mà ở mức 60fps hoặc 120fps mà không cần thông qua một "cầu nối" (bridge) trung gian nào như một số framework khác.
