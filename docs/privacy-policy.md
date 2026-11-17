[Tiếng Việt](./privacy-policy.md) | [English](./privacy-policy-en.md)

# Chính sách Bảo mật — Family Alarm

**Cập nhật lần cuối:** 17/11/2026

## 1. Cam kết tổng quan

**Family Alarm** được thiết kế theo nguyên tắc **tối thiểu hóa dữ liệu (Data Minimization)**. Ứng dụng **không yêu cầu đăng ký tài khoản cá nhân**, không thu thập họ tên thật, email, số điện thoại, danh bạ, vị trí GPS, tệp cá nhân hay mã định danh quảng cáo, và **không chứa quảng cáo hay SDK theo dõi hành vi bên thứ ba**.

Chính sách này giải thích rõ những thông tin nào được tạo ra, lưu trữ trên thiết bị hoặc đồng bộ lên máy chủ để tính năng báo thức gia đình hoạt động, cùng với [Điều khoản dịch vụ](./terms-of-service.md) của Ứng dụng.

---

## 2. Dữ liệu chúng tôi xử lý & Mục đích sử dụng

### 2.1. Dữ liệu lưu trữ cục bộ trên thiết bị (`SharedPreferences`)
Các dữ liệu sau chỉ nằm trong vùng lưu trữ riêng tư của Ứng dụng trên thiết bị (đã tắt tự động sao lưu Android `allowBackup="false"`):

| Loại dữ liệu | Mục đích sử dụng | Chia sẻ ra ngoài? |
| :--- | :--- | :--- |
| **Mã thiết bị ngẫu nhiên (`deviceId`)** (chuỗi UUID rút gọn, ví dụ `dev_a1b2c3d4e5f6`) | Phân biệt thiết bị trong cùng nhóm gia đình và xử lý yêu cầu tham gia. Không gắn với IMEI hay số seri phần cứng. | Chỉ gửi khi thiết lập/tham gia nhóm Gia đình. |
| **Tên mẫu máy (`Build.MODEL`)** | Hiển thị tên dễ nhận biết trong danh sách thiết bị gia đình (ví dụ `SM-A176B`). | Chỉ chia sẻ với các thiết bị trong cùng nhóm Gia đình. |
| **Báo thức riêng (`Personal Alarms`)** | Lưu giờ, phút, nhãn, ngày lặp, thời lượng và trạng thái bật/tắt của báo thức cá nhân. | **Không bao giờ** gửi lên máy chủ hay thiết bị khác. |
| **Cài đặt cá nhân** (Giao diện Sáng/Tối, màu chủ đề, ngôn ngữ, âm lượng, nhạc chuông đã chọn, rung, thời gian báo lại) | Ghi nhớ tùy chọn hiển thị và cách đổ chuông trên thiết bị của bạn. | **Không** gửi lên máy chủ. |
| **Token xác thực ẩn danh Firebase** (`refreshToken`, `authUid`) | Duy trì phiên kết nối ẩn danh hợp lệ với máy chủ Firebase khi đồng bộ gia đình. | Chỉ trao đổi bảo mật với dịch vụ Google Firebase Auth. |

### 2.2. Dữ liệu đồng bộ lên máy chủ (Chỉ khi dùng tính năng Gia đình có Internet)
Nếu bạn thiết lập nhóm Gia đình ở chế độ trực tuyến hoặc tham gia vào một nhóm qua mã kết nối/QR, các dữ liệu sau sẽ được đồng bộ qua kết nối mã hóa **HTTPS** tới **Google Firebase Realtime Database** (máy chủ khu vực `asia-southeast1` - Singapore):

1. **Thông tin nhóm Gia đình:** Mã nhóm ngẫu nhiên (`familyId`), `deviceId` và tên mẫu máy của Người đại diện & các Thành viên, vai trò truy cập (`REPRESENTATIVE` hoặc `MEMBER`), mã xác thực ẩn danh `authUid`, và mốc thời gian hoạt động gần nhất (`lastSeenMs`) để hiển thị trạng thái *Đã kết nối / Ngoại tuyến*.
2. **Danh sách Báo thức gia đình:** Giờ, phút, nhãn báo thức (tối đa 120 ký tự), ngày lặp trong tuần, thời lượng chuông và trạng thái bật/tắt.
3. **Thông báo thay đổi gần nhất (`lastChangeEvent`):** Tiêu đề, mô tả ngắn sự kiện (ví dụ vừa thêm/sửa báo thức nào) và mốc thời gian để thông báo cho các thiết bị khác trong cùng nhóm.
4. **Dữ liệu ghép nối tạm thời (`pairingCodes`, `joinRequests`):** Mã ghép nối 5 phút và yêu cầu chờ phê duyệt từ thiết bị thành viên.

> **Lưu ý:** Nếu bạn chọn **"Tiếp tục ngoại tuyến"** khi thiết lập, dữ liệu báo thức gia đình sẽ chỉ nằm trên thiết bị của bạn và không tải lên Firebase.

---

## 3. Quyền truy cập hệ thống Android & Cách sử dụng

Ứng dụng chỉ yêu cầu các quyền hệ thống trực tiếp phục vụ chức năng báo thức và đồng bộ:

| Quyền Android | Mục đích thực tế trong Ứng dụng |
| :--- | :--- |
| `INTERNET` & `ACCESS_NETWORK_STATE` | Kiểm tra trạng thái mạng, đồng bộ báo thức gia đình với Firebase Realtime Database và hiển thị trang thông tin pháp lý trên WebUI. |
| `POST_NOTIFICATIONS` | Hiển thị thông báo khi báo thức kêu hoặc khi lịch báo thức gia đình được cập nhật. |
| `SCHEDULE_EXACT_ALARM` / `USE_EXACT_ALARM` | Đặt lịch đổ chuông chính xác đến từng phút theo giờ bạn đã chọn. |
| `USE_FULL_SCREEN_INTENT` | Hiển thị màn hình đổ chuông báo thức ngay cả khi điện thoại đang khóa màn hình. |
| `FOREGROUND_SERVICE` & `FOREGROUND_SERVICE_MEDIA_PLAYBACK` | Duy trì phát nhạc chuông và đếm ngược báo thức ổn định khi đang kêu. |
| `WAKE_LOCK` & `VIBRATE` | Đánh thức màn hình khi đến giờ báo thức và rung theo cài đặt. |
| `RECEIVE_BOOT_COMPLETED` | Khôi phục lịch báo thức và lịch đồng bộ sau khi điện thoại khởi động lại hoặc cập nhật ứng dụng. |
| `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS` *(tùy chọn)* | Giúp hệ thống không trì hoãn báo thức hoặc đồng bộ nền trên một số dòng máy Android. |

Ứng dụng **không** yêu cầu quyền Camera, Micro, Vị trí (GPS), Danh bạ hay Đọc bộ nhớ ngoài.

---

## 4. Dịch vụ bên thứ ba

**Family Alarm** sử dụng dịch vụ hạ tầng đám mây từ **Google Firebase** (**Firebase Authentication** dạng ẩn danh và **Firebase Realtime Database**) để thực hiện việc xác thực phiên thiết bị và đồng bộ dữ liệu nhóm gia đình theo thời gian thực.

- Toàn bộ lưu lượng mạng giữa Ứng dụng và Firebase đều đi qua giao thức bảo mật **HTTPS / TLS**.
- Tham khảo chính sách quyền riêng tư của Google tại: [https://policies.google.com/privacy](https://policies.google.com/privacy)

Chúng tôi **không** bán, **không** cho thuê và **không** chia sẻ dữ liệu của bạn với nhà quảng cáo, môi giới dữ liệu hay bên thứ ba nào khác ngoài hạ tầng đồng bộ nêu trên.

---

## 5. Thời gian lưu giữ & Xóa dữ liệu

1. **Dữ liệu cục bộ trên máy:** Tồn tại cho đến khi bạn sử dụng chức năng **Đặt lại thiết lập gia đình**, xóa dữ liệu ứng dụng trong Cài đặt Android, hoặc gỡ cài đặt Ứng dụng.
2. **Mã ghép nối & Yêu cầu tham gia:** Mã ghép nối chỉ có hiệu lực **5 phút** và được xóa khỏi Firebase sau khi hết hạn hoặc ngay khi Người đại diện chấp thuận/từ chối yêu cầu.
3. **Khi thành viên rời nhóm hoặc bị xóa:**
   - Khi Người đại diện xóa một thiết bị trong mục **Thiết bị**, bản ghi thành viên và yêu cầu tham gia của thiết bị đó bị xóa ngay khỏi Firebase.
   - Khi thiết bị Thành viên chọn **Thiết đặt → Đặt lại thiết lập gia đình** (khi đang có Internet), thiết bị đó tự động gửi lệnh xóa thông tin thành viên của chính mình khỏi nhóm trên Firebase và xóa toàn bộ phiên cục bộ.
4. **Nhóm gia đình trên máy chủ:** Nếu thiết bị Người đại diện gỡ cài đặt ứng dụng mà không xóa các thành viên khác trước, dữ liệu lịch báo thức chung gắn với `familyId` đó có thể vẫn tồn tại trên máy chủ để phục vụ các thành viên còn lại, hoặc được dọn dẹp theo chính sách quản trị/yêu cầu hỗ trợ qua email liên hệ.

---

## 6. Quyền của người dùng

Bạn có toàn quyền kiểm soát dữ liệu của mình:

- **Xem và chỉnh sửa:** Xem trực tiếp danh sách thiết bị đã liên kết, vai trò truy cập, các báo thức gia đình và báo thức riêng ngay trong Ứng dụng.
- **Thu hồi quyền hệ thống:** Tắt bất kỳ quyền Android nào trong **Thiết đặt → Quyền ứng dụng** hoặc trong Cài đặt hệ thống của điện thoại.
- **Xóa và ngắt kết nối:** Rời nhóm gia đình hoặc xóa thiết bị thành viên bất cứ lúc nào.
- **Yêu cầu hỗ trợ / Xóa dữ liệu nhóm:** Nếu bạn muốn yêu cầu xóa hoàn toàn một `familyId` cũ trên máy chủ hoặc có thắc mắc về bảo mật, hãy gửi email tới `[email-ho-tro@tenmien.com]`.

---

## 7. Quyền riêng tư của trẻ em

Family Alarm là công cụ báo thức dành cho hộ gia đình và không chủ động thu thập thông tin định danh cá nhân của bất kỳ ai, kể cả trẻ em. Việc kết nối thiết bị của trẻ em vào nhóm gia đình do cha mẹ hoặc người giám hộ (**Người đại diện**) trực tiếp thực hiện và quản lý tại nhà. Nếu bạn là phụ huynh/người giám hộ và muốn yêu cầu gỡ dữ liệu nhóm liên quan, vui lòng liên hệ với chúng tôi qua email bên dưới.

---

## 8. Thay đổi Chính sách Bảo mật

Jexopy có thể cập nhật Chính sách Bảo mật này khi bổ sung tính năng mới hoặc theo yêu cầu pháp lý / Google Play. Phiên bản mới nhất sẽ được cập nhật kèm ngày hiệu lực ở phần đầu tài liệu.

---

## 9. Liên hệ

Mọi câu hỏi hoặc yêu cầu liên quan đến quyền riêng tư, xin vui lòng liên hệ:

- **Nhà phát triển:** JexOpy
- **Email:** superhien65@gmail.com
- **Trang thông tin:** [https://jexopy.github.io/FamilyAlarm/](https://jexopy.github.io/FamilyAlarm/)
