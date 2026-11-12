# Orbit — Trợ lý tổng, Công việc & Cuộc sống

Bản web prototype cho mô hình một agent tổng và hai agent chuyên trách. Agent Công việc và Agent Cuộc sống giữ phần việc riêng; agent tổng gom báo cáo, chuyển điều chỉnh và trao đổi quyết định chung với người dùng. Map ngày / tuần / tháng giúp nhìn tổng quan.

**Trạng thái:** demo giao diện và luồng xử lý bằng JavaScript trên trình duyệt. Chưa kết nối Claude/GPT, Zalo hoặc app bên ngoài; chưa có agent chạy nền hoặc thông báo khi đóng web. Dữ liệu mẫu và thay đổi được lưu trong `localStorage` theo trình duyệt, chưa đồng bộ thiết bị.

## Chạy local

Cần Node.js 18 trở lên, không cần cài dependency:

```bash
npm start
```

Mở http://localhost:3000. Có thể đổi cổng bằng biến môi trường `PORT`.

Hoặc dùng Python:

```bash
python3 -m http.server 3000 --directory dist
```

## Thử các luồng

- Chọn **Thử một vòng báo cáo** để xem hai agent chuyên trách báo lên Tổng.
- Nhắn `Tuần này ưu tiên content, giảm việc cá nhân` để đổi định hướng của hai agent.
- Nhắn `Tuần này cần viết 10 bài content, tập 3 buổi và tiết kiệm 3 triệu` để thử phân việc theo mảng.
- Nhắn `Dời việc học tiếng Anh sang mai` hoặc `Tao xong phần content rồi` để thử cập nhật có thể hoàn tác.
- Đổi Ngày / Tuần / Tháng, mở báo cáo rộng và xem báo cáo từng agent.

## Mã nguồn

- `dist/index.html`: trang ứng dụng.
- `dist/app.js`, `styles.css`: lớp prototype dashboard ban đầu và tiện ích dữ liệu, modal, icon.
- `dist/agent.js`, `agent.css`: lớp hội thoại và map.
- `dist/proactive.js`, `proactive.css`: tổng quan thời gian, bản tin và lịch chạy thử trong tab.
- `dist/coordinator.js`, `coordinator.css`: phiên bản hiện tại phân vai Tổng / Công việc / Cuộc sống.
- `dist/assets/japan.jpg`: ảnh minh họa Kyoto.
- `server.mjs`: server local phục vụ file tĩnh.

Các lớp hiện được nạp tuần tự để giữ các bản thử giao diện trước đó. Đây là cấu trúc prototype, nên tách module và gom các lớp trước khi phát triển thành sản phẩm thật. Không có API key trong repo. Lịch sử người dùng lưu trong trình duyệt không nằm trong mã nguồn GitHub.

## Hướng phát triển

1. Chốt trách nhiệm, quyền và điều kiện báo lên của từng agent bằng tình huống thực tế.
2. Tách state và nghiệp vụ khỏi giao diện; thêm backend và database.
3. Kết nối model, nguồn công việc / bot Zalo và dữ liệu cá nhân theo từng phạm vi.
4. Thêm scheduler, thông báo, nhật ký hành động, giới hạn ngân sách và xác nhận cho hành động cần duyệt.

## Tham khảo

Thiết kế tham khảo cách phân cấp dashboard của [Square UI — Dashboard 5](https://github.com/zerostaticthemes/square-ui/tree/master/templates/dashboard-5); mã UI ở đây được viết riêng cho prototype, không tích hợp component React từ repo đó. Ảnh Kyoto từ [Unsplash](https://images.unsplash.com/photo-1493976040374-85c8e12f0c0e).
