# 🔒 Chính sách bảo mật — Live Meeting Notes (Android)

**Cập nhật:** 22/07/2026

> Bản này áp dụng riêng cho ứng dụng **Android** "Live Meeting Notes"
> (`com.livemeetingnotes.app`). Bản Web/Extension dùng chính sách riêng
> ([PRIVACY.md](PRIVACY.md)) vì hoạt động hoàn toàn khác (không có
> tài khoản, không có server).

---

## 🎯 Tóm tắt

- Ghi âm, ghi chú, file export được lưu **100% trên máy bạn** — không upload
  audio/nội dung ghi chép lên server của chúng tôi.
- Ứng dụng có **tài khoản Google (tùy chọn)** để: đếm số lượt dùng AI miễn phí,
  đồng bộ giấy phép (license) giữa các thiết bị, và xử lý mua Pro qua Google Play.
- Khi bạn dùng tính năng **AI Transcribe/Smart Transcribe**, audio hoặc văn bản
  liên quan được gửi tới **Google Gemini API** để xử lý — đây là lựa chọn của
  bạn (có thể tắt/không dùng tính năng này).
- **Không có** quảng cáo, không có SDK theo dõi hành vi (analytics/tracking),
  không bán dữ liệu cho bên thứ ba.

---

## 📊 Dữ liệu được lưu trữ

### 1. Trên thiết bị của bạn (local)
- Audio recordings (.wav), meeting metadata, nội dung ghi chú, file Word export.
- Cài đặt ứng dụng (API key riêng nếu bạn tự nhập, ngôn ngữ, v.v.).

### 2. Gửi lên server của chúng tôi (Cloudflare Worker), chỉ khi bạn dùng các tính năng liên quan:

| Dữ liệu | Khi nào gửi | Mục đích |
|---|---|---|
| Email tài khoản Google | Khi đăng nhập Google | Đếm lượt dùng AI miễn phí theo tài khoản, tra cứu/đồng bộ license |
| ID token của Google | Khi đăng nhập Google | Xác thực tài khoản (server tự xác minh với Google, không lưu mật khẩu) |
| Định danh thiết bị (device ID) | Khi đăng nhập/kích hoạt license | Giới hạn số thiết bị dùng chung 1 license (chống chia sẻ tài khoản) |
| Purchase token + product ID (Google Play Billing) | Khi bạn mua gói Pro | Xác minh giao dịch thật với Google Play, kích hoạt license — **không truyền qua thông tin thẻ/thanh toán**, việc này do Google Play xử lý toàn bộ |
| License key | Kích hoạt/khôi phục license | Xác định gói bạn đang dùng (Free/Pro) |

### 3. Gửi tới Google Gemini API (bên thứ ba), chỉ khi bạn chủ động dùng tính năng AI:
- Audio ghi âm hoặc văn bản transcript được gửi qua HTTPS tới Gemini API để
  chuyển giọng nói thành văn bản / tóm tắt nội dung.
- Áp dụng khi bạn bấm "Transcribe with Gemini AI" hoặc bật "Smart Transcribe".
- Nếu bạn dùng chung API key với ứng dụng (không tự nhập key riêng), audio/văn
  bản đi qua server của chúng tôi để mượn tạm 1 API key dùng chung, rồi gửi
  thẳng tới Gemini API — server không lưu lại nội dung audio/transcript đó.

### 4. Dữ liệu KHÔNG được thu thập
- ❌ Không thu thập tên, số điện thoại, địa chỉ, vị trí địa lý.
- ❌ Không có SDK quảng cáo, analytics, tracking hành vi.
- ❌ Không bán/chia sẻ dữ liệu cho bên thứ ba ngoài Google (Sign-In, Play
  Billing, Gemini API) — là các dịch vụ cần thiết để vận hành tính năng bạn
  chủ động sử dụng.

---

## 🔐 Quyền truy cập ứng dụng yêu cầu

- **Microphone** — ghi âm cuộc họp (chỉ khi đang recording).
- **Internet** — đồng bộ license, gọi Gemini API (khi dùng AI), xử lý mua Pro.
- **Bộ nhớ trong** — lưu file ghi âm/ghi chú/export cục bộ.

---

## 🗑️ Xóa dữ liệu

- **Trên máy:** gỡ ứng dụng sẽ xóa toàn bộ file local (audio, ghi chú, export).
- **Trên server:** đăng xuất tài khoản Google sẽ xóa dữ liệu license/thiết bị
  đã lưu cục bộ trên máy bạn. Để yêu cầu xóa hẳn dữ liệu (email, license,
  lịch sử thiết bị) khỏi server, liên hệ email hỗ trợ bên dưới.

---

## 📞 Liên hệ

- **Email hỗ trợ:** hungnd.nldc@gmail.com

---

_Cập nhật lần cuối: 22/07/2026_
