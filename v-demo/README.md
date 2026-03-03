# Vite Inter-Window Communication Demo

Demo này minh họa cách kết nối lại giữa **Trang chính (Parent)** và **Popup (Child)** sau khi Trang chính bị **F5 (Reload)**.

## Cách chạy thử:

1.  Mở trình duyệt tại: `http://localhost:5173/`
2.  Nhấn nút **⚡ Mở Popup lần đầu**.
3.  Quay lại trang chính, bấm **F5 (Reload)** trang web.
4.  Để ý mục **Log nhận được** ở cả 2 trang:
    *   Trang chính load xong sẽ bắn tin nhắn `WHO_IS_ALIVE`.
    *   Popup nhận được sẽ trả lời `PONG`.
    *   Kết nối được tự động khôi phục (Handshake) mà không cần mở tab mới.

## Kỹ thuật sử dụng:
- **`BroadcastChannel`**: Dùng để đồng bộ trạng thái (Handshake) "không dây" giữa 2 cửa sổ cùng Origin.
- **`window.name`**: (Dự phòng) Giúp trang chính lấy lại tham chiếu (`Reference`) của popup cũ nếu cần dùng `postMessage` trực tiếp.

## Lưu ý:
- Nếu popup bị đóng hẳn, trang chính sẽ báo `Chưa kết nối popup ❌`.
- Nếu trang chính reload, nó sẽ tự động tìm lại "người thân" đang mở.
