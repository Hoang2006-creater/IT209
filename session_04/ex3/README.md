# Bài tập 3: Cấu hình SSH Ed25519 và kết nối GitHub

## 1. Mục tiêu

* Tạo cặp khóa SSH sử dụng thuật toán Ed25519.
* Cấu hình khóa SSH để xác thực với GitHub.
* Kiểm tra kết nối SSH đến GitHub.
* Cấu hình remote repository bằng giao thức SSH.
* Push mã nguồn từ repository local lên GitHub.

## 2. Tạo khóa SSH Ed25519

Sử dụng PowerShell để tạo khóa SSH:

```powershell
ssh-keygen -t ed25519 -C "EMAIL_GITHUB_CUA_BAN"
```

Sau khi chạy lệnh, chọn vị trí mặc định:

```text
C:\Users\ADMIN\.ssh\id_ed25519
```

Sau khi tạo thành công, thư mục `.ssh` chứa hai tệp:

```text
id_ed25519
id_ed25519.pub
```

Trong đó:

* `id_ed25519`: khóa private, không được chia sẻ hoặc nộp lên GitHub.
* `id_ed25519.pub`: khóa public, được sử dụng để thêm vào tài khoản GitHub.

## 3. Lấy SSH Public Key

Kiểm tra khóa public bằng lệnh:

```powershell
Get-Content $HOME\.ssh\id_ed25519.pub
```

Khóa public được thêm vào GitHub tại:

**GitHub → Settings → SSH and GPG keys → New SSH key**

## 4. Kiểm tra kết nối SSH với GitHub

Sử dụng lệnh:

```powershell
ssh -T git@github.com
```

Kết nối thành công khi GitHub xác thực tài khoản thông qua SSH.

## 5. Cấu hình GitHub Remote

Repository local được liên kết với GitHub bằng remote `origin`:

```powershell
git remote add origin git@github.com:Hoang2006-creater/IT209.git
```

Kiểm tra remote:

```powershell
git remote -v
```

Kết quả:

```text
origin  git@github.com:Hoang2006-creater/IT209.git (fetch)
origin  git@github.com:Hoang2006-creater/IT209.git (push)
```

## 6. Push project lên GitHub

Đẩy nhánh `main` lên GitHub:

```powershell
git push -u origin main
```

Sau khi push thành công, repository local đã được liên kết và đồng bộ với repository GitHub.

## 7. URL Repository GitHub

Repository GitHub:

https://github.com/Hoang2006-creater/IT209

## 8. Lưu ý bảo mật

Không nộp hoặc công khai khóa private:

```text
id_ed25519
```

Chỉ sử dụng khóa public:

```text
id_ed25519.pub
```

Khóa private phải được giữ bí mật và không được commit vào repository GitHub.

## 9. Kết luận

Đã hoàn thành quá trình tạo khóa SSH Ed25519, cấu hình khóa public trên GitHub, kiểm tra kết nối SSH, cấu hình remote repository và push project lên GitHub bằng giao thức SSH.
