# Lỗ Hổng Việt Nam · Vulnerability Intelligence Dashboard

Dashboard HTML/CSS/JavaScript thuần, giao diện tiếng Việt, thích hợp triển khai bằng GitHub Pages.

## Trạng thái dữ liệu

**460 danh mục** và **31 loại giao thức** là quy mô mục tiêu do chủ dự án cung cấp, không phải số bản ghi được xác minh trong repository. Trang hiện có 31 nhóm giao thức tham khảo, không phải danh sách chuẩn đã đối chiếu với nguồn 460 danh mục. Khi chưa có tệp dữ liệu, các biểu đồ và số lượng bản ghi hiển thị là 0, tránh tạo số liệu giả.

## Chạy thử

Mở `index.html` bằng trình duyệt, hoặc chạy máy chủ tĩnh:

```bash
python -m http.server 8000
```

Để nạp dữ liệu: nhấn **Nhập JSON**. Hoặc lưu dữ liệu vào `data/vulnerabilities.json` với cấu trúc:

```json
[
  {
    "id": "CVE-YYYY-NNNNN",
    "title": "Tên lỗ hổng đã xác minh",
    "protocol": "HTTP",
    "severity": "high",
    "cvss": 8.1,
    "description": "Mô tả đã kiểm chứng",
    "mitigation": "Khuyến nghị phòng vệ",
    "source": "https://nvd.nist.gov/"
  }
]
```

Mức độ hợp lệ: `critical`, `high`, `medium`, `low`, `none`. Các trường mô tả có thể bỏ trống.

## Các màn hình

- Tổng quan: số liệu trên dữ liệu đã nhập, biểu đồ mức độ và giao thức.
- Danh mục: tìm kiếm, lọc theo giao thức/mức độ, đọc chi tiết.
- 31 giao thức: thư viện phân loại dạng thẻ.
- Phân tích: ma trận mức độ nghiêm trọng và thống kê theo giao thức.
- Nguồn dữ liệu: hướng dẫn JSON và liên kết tới CVE, NVD, CISA KEV, CVSS, EPSS.

## Dữ liệu, bảo mật và giới hạn

Không có backend, không lưu tệp nhập lên máy chủ. Dữ liệu được xử lý cục bộ. Khi xuất CSV, nội dung đầu vào chưa được trung hòa nguy cơ công thức bảng tính, nên chỉ mở tệp từ nguồn tin cậy. Chưa có tính năng xác minh CVE, cập nhật thời gian thực, đồng bộ KEV/EPSS, hay kiểm thử khai thác.

Muốn tự động cập nhật, nên có quy trình thu thập đã kiểm chứng từ các nguồn công khai, chuẩn hóa và xuất JSON tĩnh định kỳ bằng GitHub Actions.

## Triển khai

Trong repository → **Settings → Pages → Build and deployment → Deploy from a branch** → chọn **main** / **/(root)**. Địa chỉ dự kiến sau khi công bố: https://xulytiengviet.github.io/lohong/

## Nguồn tra cứu

- https://www.cve.org/
- https://nvd.nist.gov/
- https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- https://www.first.org/cvss/
- https://www.first.org/epss/

Dự án phục vụ học tập và quản trị an toàn thông tin, không tự động khai thác lỗ hổng.
