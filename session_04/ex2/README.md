# Bài 2: Quản lý nhánh và Giải quyết xung đột

## 1. Tạo nhánh feature

Tạo nhánh `feature-update` từ nhánh `main`:

```bash
git checkout -b feature-update
```

Sau đó cập nhật file `README.md` trên nhánh `feature-update` và commit:

```bash
git add README.md
git commit -m "Update README on feature branch"
```

## 2. Cập nhật nhánh main

Chuyển về nhánh `main`:

```bash
git checkout main
```

Cập nhật cùng dòng trong file `README.md` và commit:

```bash
git add README.md
git commit -m "Update README on main branch"
```

## 3. Tạo Merge Conflict

Thực hiện merge nhánh `feature-update` vào `main`:

```bash
git merge feature-update
```

Git phát hiện xung đột trong file `README.md`.

## 4. Giải quyết xung đột thủ công

Mở file `README.md` và tìm các ký hiệu conflict:

```text
<<<<<<< HEAD
=======
>>>>>>> feature-update
```

Sau đó xóa các ký hiệu đánh dấu conflict và chỉnh sửa nội dung thành phiên bản mong muốn.

Sau khi giải quyết xong, lưu file và kiểm tra:

```bash
git status
```

## 5. Hoàn thành Merge

Đưa file đã giải quyết conflict vào Staging Area:

```bash
git add README.md
```

Tạo merge commit:

```bash
git commit -m "Resolve merge conflict"
```

## 6. Kiểm tra lịch sử nhánh

Sử dụng:

```bash
git log --graph --oneline
```

Kết quả cho thấy nhánh `feature-update` được tách ra từ `main`, sau đó hai nhánh có các commit riêng và được hợp nhất bằng một merge commit.

## 7. Kết luận

Đã hoàn thành việc tạo và chuyển đổi giữa các nhánh Git, cố ý tạo Merge Conflict trên cùng một dòng của `README.md`, xử lý conflict thủ công và hoàn thành merge commit.
