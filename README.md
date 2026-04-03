# BÁO CÁO BÀI TẬP: TRIỂN KHAI & KHAI THÁC BAGISTO HEADLESS API

---

## I. THÔNG TIN SINH VIÊN
*   **Họ và tên:** Vu Minh Thanh
*   **MSSV:** 23810310236
*   **Lớp:** Công nghệ Thông tin
*   **Học phần:** Phát triển hệ thống Web / Thương mại điện tử

---

## II. PHẦN 1: CÀI ĐẶT HỆ THỐNG
Hệ thống được cài đặt dựa trên nền tảng **Bagisto** phiên bản mới nhất và tích hợp gói **Headless Extension**.

### Các bước thực hiện:
1.  **Cài đặt Extension:**
    ```bash
    composer require bagisto/bagisto-headless
    ```
2.  **Chạy Migration:** Cập nhật các bảng dữ liệu cần thiết cho API.
    ```bash
    php artisan migrate
    ```
3.  **Kích hoạt API:** Truy cập `Admin Panel -> Configuration -> Headless` để cấu hình quyền truy cập.

### Minh chứng:
> **Hình 1:** Danh sách 03 sản phẩm mang tên "Vu Minh Thanh" trong Admin Panel.

<img width="1920" height="1020" alt="Screenshot 2026-04-03 195723" src="https://github.com/user-attachments/assets/e964423e-279e-4de5-bec1-271117518bd8" />

---

## III. PHẦN 2: KHAI THÁC GRAPHQL API
<img width="1920" height="1020" alt="Screenshot 2026-04-03 195609" src="https://github.com/user-attachments/assets/c57a3b16-3f73-4771-aa3a-a2859dd23d42" />

## IV. PHẦN 3: Xây dựng frontend cơ bản
<img width="1920" height="1020" alt="Screenshot 2026-04-03 200550" src="https://github.com/user-attachments/assets/57fbe787-8418-4c57-bc29-52915c0deeb2" />
## V. Câu hỏi bắt buộc
1. So sánh sự khác biệt về Payload (REST vs GraphQL)
Trong bài làm của em, sự khác biệt về lưu lượng dữ liệu là rất lớn. Với REST API, khi lấy sản phẩm, server sẽ trả về toàn bộ dữ liệu (Over-fetching) bao gồm cả những trường em không dùng tới như cân nặng, thuế, tồn kho... làm tăng kích thước gói tin.

Ngược lại, với GraphQL, em chỉ yêu cầu các trường id, name, price, description và url_key. Payload trả về chỉ chứa đúng các trường này, giúp giảm dung lượng dữ liệu truyền tải qua mạng, tăng tốc độ tải trang và tiết kiệm băng thông đáng kể cho người dùng.

2. Hành động thay đổi giá sản phẩm (Query hay Mutation)?
Để thay đổi giá của một sản phẩm, em sẽ sử dụng Mutation.

Giải thích:
Trong chuẩn GraphQL, các hành động được phân chia theo mục đích sử dụng. Query chỉ dùng cho việc đọc dữ liệu (Read-only) và không làm thay đổi trạng thái hệ thống. Trong khi đó, Mutation được thiết kế để thực hiện các thay đổi dữ liệu (Write operations) như Thêm, Sửa, Xóa. Vì thay đổi giá sản phẩm là một hành động tác động vào cơ sở dữ liệu, nên việc sử dụng Mutation là bắt buộc để đảm bảo tính nhất quán và bảo mật của API.
