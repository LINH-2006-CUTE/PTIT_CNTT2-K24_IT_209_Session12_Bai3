# Bài 3: 

## 1. Mục tiêu

- Quản lý hai môi trường triển khai: Staging và Production.
- Tự động chạy job Staging khi push code lên nhánh `develop`.
- Yêu cầu phê duyệt thủ công trước khi job Production chạy khi push code lên nhánh `main`.
- Sử dụng GitHub Environments để kiểm soát luồng triển khai.

## 2. Công nghệ sử dụng

- Git và GitHub
- GitHub Actions
- GitHub Environments
- Ubuntu trên WSL

## 3. Cấu hình workflow

File workflow: `.github/workflows/cd-multi-env.yml`

### 3.1. Môi trường Staging

- Environment: `staging`
- Nhánh kích hoạt: `develop`
- Job: `Deploy to Staging`
- Kết quả: **Success**

### 3.2. Môi trường Production

- Environment: `production`
- Nhánh kích hoạt: `main`
- Job: `Deploy to Production`
- Bật quy tắc `Required reviewers` để yêu cầu phê duyệt thủ công.
- Kết quả: Workflow chuyển sang trạng thái `Waiting` trước khi được phê duyệt.

## 4. Kết quả kiểm thử

| Trường hợp kiểm thử | Kết quả mong đợi | Kết quả thực tế |
|---|---|---|
| Push nhánh `develop` | Job Staging chạy tự động | Thành công |
| Push nhánh `main` | Production chờ phê duyệt | Thành công |
| Chưa phê duyệt Production | Job triển khai chưa được tiếp tục | Thành công |
| Phê duyệt Production | Job Production tiếp tục chạy | Thành công |
| Kiểm tra kết quả cuối cùng | Workflow hoàn tất | `Success` |

## 5. Kết luận

Đã cấu hình và kiểm thử thành công luồng CI/CD đa môi trường bằng GitHub Actions và GitHub Environments. Môi trường Staging chạy theo nhánh `develop`; môi trường Production chạy theo nhánh `main` và yêu cầu phê duyệt trước khi tiếp tục.

**Lưu ý:** Các bước triển khai trong workflow hiện tại được mô phỏng bằng lệnh `echo`, chưa thực hiện triển khai ứng dụng lên máy chủ thực tế.

## 6. Sản phẩm nộp

- File `.github/workflows/cd-multi-env.yml`
- File báo cáo `homework/session_12/ex3/README.md`
- Ảnh chụp màn hình Production ở trạng thái `Waiting` trước khi phê duyệt.
