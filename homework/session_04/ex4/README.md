# Bài 4: Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## 1. Mục tiêu

* Sử dụng `.gitignore` để bỏ qua file chứa thông tin nhạy cảm.
* Gỡ file `credentials.txt` khỏi Git nhưng không xóa file vật lý trên máy.
* Sử dụng `git commit --amend` để sửa thông điệp của commit gần nhất.

## 2. Tạo file credentials.txt

Tạo file `credentials.txt` và commit nhầm file này lên Git:

```bash
touch credentials.txt
git add credentials.txt
git commit -m "Add credentials file"
```

## 3. Cấu hình .gitignore

Thêm `credentials.txt` vào `.gitignore`:

```text
credentials.txt
```

Kiểm tra:

```bash
cat .gitignore
```

Kết quả:

```text
credentials.txt
```

## 4. Gỡ file khỏi Git tracking

Sử dụng lệnh:

```bash
git rm --cached credentials.txt
```

Lệnh `--cached` chỉ gỡ file khỏi vùng theo dõi của Git và không xóa file vật lý khỏi thư mục làm việc.

Sau khi thực hiện, file `credentials.txt` vẫn tồn tại trên máy.

## 5. Sửa commit gần nhất bằng amend

Thực hiện:

```bash
git add .gitignore
git commit --amend -m "Add gitignore and remove credentials tracking"
```

Lệnh `--amend` dùng để thay thế commit gần nhất bằng một commit mới có nội dung/thông điệp đã được chỉnh sửa.

## 6. Kiểm tra trạng thái

```bash
git status
```

Kết quả mong đợi:

* `credentials.txt` không còn được Git theo dõi.
* File `credentials.txt` vẫn tồn tại trong thư mục làm việc.
* Không còn thay đổi chưa commit liên quan đến `credentials.txt`.

## 7. Kiểm tra lịch sử commit

```bash
git log -n 1
```

Kết quả mong đợi:

```text
Add gitignore and remove credentials tracking
```

Điều này chứng minh commit gần nhất đã được sửa bằng `git commit --amend`.

## 8. Kiểm tra file vật lý

```bash
ls -la
```

File `credentials.txt` vẫn tồn tại trong thư mục làm việc.

## 9. Kết luận

Đã hoàn thành yêu cầu bài tập:

* Tạo `.gitignore` để bỏ qua `credentials.txt`.
* Sử dụng `git rm --cached credentials.txt` để gỡ file khỏi Git tracking.
* Không sử dụng lệnh xóa file vật lý.
* File `credentials.txt` vẫn được giữ lại trên máy.
* Sử dụng `git commit --amend` để sửa thông điệp commit gần nhất.

