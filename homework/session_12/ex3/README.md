
# Bài 3: Tách biệt luồng CI/CD đa môi trường với GitHub Environments

## 1. Mục tiêu
- Tạo hai môi trường staging và production trên GitHub.
- Tự động chạy job staging khi push vào nhánh develop.
- Yêu cầu phê duyệt thủ công trước khi job production chạy khi push vào nhánh main.

## 2. Công nghệ sử dụng
- Git và GitHub
- GitHub Actions
- GitHub Environments
- Ubuntu WSL

## 3. Cấu hình workflow
File workflow chính: `.github/workflows/cd-multi-env.yml`

- `deploy-staging`: chạy trên nhánh develop, sử dụng environment staging.
- `deploy-prod`: chạy trên nhánh main, sử dụng environment production.
- Production sử dụng Required reviewers để yêu cầu phê duyệt trước khi triển khai.

## 4. Kết quả kiểm thử
- Staging: sẽ cập nhật kết quả sau khi push nhánh develop và kiểm tra GitHub Actions.
- Production: sẽ cập nhật kết quả sau khi push nhánh main và kiểm tra trạng thái Waiting for review.
- Phê duyệt deployment: sẽ cập nhật kết quả sau khi kiểm tra nút Approve and deploy.

## 5. Sản phẩm nộp
- File `.github/workflows/cd-multi-env.yml`
- Ảnh chụp màn hình Production chờ phê duyệt.
