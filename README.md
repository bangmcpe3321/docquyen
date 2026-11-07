# Độc quyền — Quyền lực & cái giá

Game mô phỏng kinh tế bằng tiếng Việt về **độc quyền trong kinh tế thị trường**: nó hình thành thế nào, ai được lợi, ai trả giá, và cạnh tranh giữ vai trò gì.

Bạn nhận một quán trà nhỏ ở Đà Nẵng năm 2019. Qua 12 chương và 12 năm, mỗi quyết định đổi sáu chỉ số, mở hoặc khoá những nhánh về sau, và dẫn tới một trong sáu kết cục.

**Chơi ngay:** mở `index.html`, hoặc vào thẳng [`docquyen.html`](docquyen.html).

---

## Nội dung

- **12 chương** tình huống: nhà cung cấp giữ giá, đề nghị mua lại 70% cổ phần, đối thủ phá giá, bài báo điều tra, vốn nhà nước, đình công, thuật toán nền tảng, bữa tối cấu kết, điều tra chống độc quyền, dự thảo hiến chương thị trường.
- **6 chỉ số sống** (0–100): Vốn · Thị phần · Uy tín thương hiệu · Niềm tin người tiêu dùng · Quan hệ chính quyền · Áp lực pháp lý.
- **18 thẻ kiến thức** mở sau các quyết định quan trọng, lưu lại trong **Sổ tay**: cạnh tranh, độc quyền tư nhân, độc quyền nhà nước, lợi nhuận độc quyền, thôn tính – sáp nhập, thao túng giá, luật chống độc quyền, cartel, đổi mới, chia tách…
- **6 kết thúc**, mỗi kết thúc có màn riêng với lời bình, tóm tắt hành trình và bài học kinh tế:

| Kết thúc | Điều kiện khái quát |
|---|---|
| Đế chế độc quyền | Thị phần áp đảo, thị trường không còn lựa chọn |
| Bị chia tách | Áp lực pháp lý chạm ngưỡng, cơ quan cạnh tranh can thiệp |
| Phá sản | Vốn cạn trong khi thị phần và niềm tin cùng xuống |
| Dẫn đầu nhờ đổi mới | Thương hiệu và niềm tin cao, không cần thống trị thị phần |
| Bị tẩy chay | Người tiêu dùng quay lưng vì che giấu hoặc thao túng |
| Kết thúc bí mật | Cùng thị trường ký hiến chương: hạ tầng mở, giá minh bạch |

Tiến trình được lưu bằng `localStorage`. Đã mở bao nhiêu kết thúc được đếm ở màn hình chính (x/6).

## Nhiều người chơi

- **Chuyền máy 2–4 người**: mỗi người chọn kín, có màn hình "Chuyển cho …" để giữ bí mật, rồi công bố đồng thời.
- **Online 2 người qua WebRTC**: trao đổi mã kết nối bằng copy/paste, không cần máy chủ. Nên chạy qua HTTP server (xem bên dưới).
- Tuỳ chọn thêm vai **Cơ quan quản lý** với bốn hành động: điều tra, bảo vệ người tiêu dùng, hỗ trợ doanh nghiệp nhỏ, chờ đợi.

Trong chế độ nhiều người, **thị phần là tổng không đổi** (zero-sum), còn **Niềm tin người tiêu dùng** và **Áp lực pháp lý** là chỉ số dùng chung của cả thị trường. Hành động gồm: chiến tranh giá, đổi mới, thôn tính, đề nghị sáp nhập, vận động chính sách, cấu kết giữ giá, mở hạ tầng hợp tác. Cấu kết bị phát hiện sẽ bị phạt cả nhóm.

Kết thúc được xét cho từng doanh nghiệp, kèm một kết cục chung của thị trường: một người thống trị · cả nhóm bị phạt vì cấu kết · cạnh tranh lành mạnh · thị trường đồng thuận · thị trường mong manh.

## Chạy locally

Mở trực tiếp `index.html` bằng trình duyệt hiện đại là đủ cho chơi đơn và chuyền máy. Để WebRTC ổn định hơn:

```bash
python -m http.server 8000
# rồi mở http://localhost:8000
```

Tham số URL hữu ích: `?fresh=1` xoá tiến trình đã lưu, `?resume=1` vào thẳng ván đang chơi.

## Cấu trúc

```text
.
├── index.html      # Trang giới thiệu + nút vào game
├── docquyen.html   # Toàn bộ game: HTML, CSS, JS, dữ liệu truyện trong một file
├── README.md
└── LICENSE
```

Game là **một file HTML duy nhất**, không thư viện ngoài, không bước build. Dữ liệu truyện nằm trong object `STORY` ở đầu `<script>` nên có thể sửa nội dung mà không chạm vào engine.

## Công nghệ

- HTML5 · CSS3 · JavaScript thuần (ES6)
- WebRTC DataChannel cho chế độ online
- `localStorage` cho tiến trình, thẻ kiến thức và kết thúc đã mở
- Tôn trọng `prefers-reduced-motion`

## Giấy phép

Mã nguồn phát hành theo **MIT License** — xem [`LICENSE`](LICENSE).
