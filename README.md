# Nhà phố 3 tầng 5 × 18 m – Mô hình 3D

Trang web tĩnh hiển thị mô hình 3D nhà phố 3 tầng (mặt tiền 5 m, sâu 18 m), viết bằng HTML + [three.js](https://threejs.org/). Không cần build, không cần cài đặt.

## Tính năng

- Xoay, phóng to / thu nhỏ mô hình bằng chuột hoặc cảm ứng
- Chọn xem **Tất cả**, **Tầng 1**, **Tầng 2**, **Tầng 3**
- Chọn từng **phòng** để camera zoom vào
- Đổi **góc nhìn**: Mặt tiền, Phối cảnh, Bên hông, Trên xuống
- Thanh trượt làm mờ tường ngoài, bật / tắt mái, bật / tắt nhãn phòng
- Nút **🖼 Xem ảnh** ở góc trên bên phải: hiện ảnh minh họa theo mục đang chọn

## Cấu trúc thư mục

```
3d-house/
├── index.html
├── README.md
└── images/
    ├── tat-ca.jpg              ← mục Tất cả
    ├── tang-1/
    │   ├── tong-quan.jpg       ← bấm "Cả tầng" hoặc không chọn phòng
    │   ├── sanh.jpg
    │   ├── phong-khach.jpg
    │   ├── cau-thang.jpg
    │   ├── phong-ngu-1.jpg
    │   ├── wc1.jpg
    │   └── bep-an.jpg
    ├── tang-2/
    │   ├── tong-quan.jpg
    │   ├── phong-tho.jpg
    │   ├── phong-du-tru.jpg
    │   ├── cau-thang.jpg
    │   ├── phong-ngu-2.jpg
    │   ├── wc2.jpg
    │   └── phong-ngu-3.jpg
    └── tang-3/
        ├── tong-quan.jpg
        ├── phong-trong-1.jpg
        ├── phong-trong-2.jpg
        ├── cau-thang.jpg
        ├── phong-trong-3.jpg
        ├── wc.jpg
        └── phong-trong-4.jpg
```

## Cách thêm ảnh

1. Đặt ảnh vào thư mục `images/` với **đúng tên** như trên.
2. Mở trang, chọn tầng / phòng rồi bấm **🖼 Xem ảnh**.

Nếu file ảnh chưa có, trang sẽ báo tên file cần thêm, ví dụ:
`Chưa có ảnh. Hãy thêm file: images/tang-1/sanh.jpg`

### Quy tắc đặt tên

- Chữ thường, không dấu, không khoảng trắng (`tang-1.jpg`, không phải `Tầng 1.jpg`).
- Phân biệt hoa thường trên GitHub Pages / Vercel: `Sanh.jpg` và `sanh.jpg` là hai file khác nhau.
- Nên giữ mỗi ảnh dưới khoảng 500 KB để tải nhanh trên điện thoại.

### Đổi tên file hoặc dùng đuôi khác

Mở `index.html`, tìm `const PICS=` và sửa đường dẫn cho khớp. Ví dụ dùng `.png` hoặc `.webp`:

```js
{main:'images/tang-1/tong-quan.png', rooms:['images/tang-1/sanh.webp', ...]}
```

Thứ tự trong `rooms` trùng với thứ tự nút **Phòng** trên trang:

| Tầng | Thứ tự phòng |
|------|--------------|
| 1 | Sảnh, Phòng khách, Cầu thang, Phòng ngủ 1, WC1, Bếp + ăn |
| 2 | Phòng thờ, Phòng dự trữ, Cầu thang, Phòng ngủ 2, WC2, Phòng ngủ 3 |
| 3 | Phòng trống 1, Phòng trống 2, Cầu thang, Phòng trống 3, WC, Phòng trống 4 |

> Tầng 3 hiện chưa đặt tên phòng. Khi đã có tên thật, đổi tên file và sửa `PICS` cho khớp.

## Chạy trên máy

Mở thẳng `index.html` bằng trình duyệt. Cần có mạng để tải thư viện three.js từ CDN. Nếu trình duyệt chặn đọc ảnh khi mở file trực tiếp, chạy server tĩnh:

```bash
npx serve .
# hoặc
python3 -m http.server 8000
```

## Đưa lên mạng

Đây là trang tĩnh, không cần cấu hình build.

- **Vercel:** kéo thả thư mục vào vercel.com, hoặc import repo GitHub.
- **GitHub Pages:** đẩy lên repo, vào *Settings → Pages*, chọn nhánh `main` và thư mục `/ (root)`. Gói GitHub Free chỉ dùng được với repo **public**.

Lưu ý: link sau khi đăng là công khai, ai có link đều xem được.

## Ghi chú

- Các thư mục `tang-1`, `tang-2`, `tang-3` có file `.gitkeep` để Git giữ thư mục rỗng. Có ảnh thật rồi thì xóa file này cũng được.
- Kích thước trong mô hình tính bằng mét. Tầng 1: sảnh dài 2.2 m, phòng khách dài 3.9 m.