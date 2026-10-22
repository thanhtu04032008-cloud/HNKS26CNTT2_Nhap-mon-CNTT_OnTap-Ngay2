# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên: Lê Đặng Thanh Tú**
- **Lớp: CNTT2**
- **Link repository:**
- **Hệ điều hành (Windows/macOS): Windows**

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell
gc .\logs\access.log | sls "ERROR" > logs\error_report.txt
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text
[ERROR] Khong tim thay trang /lich-thi (404)

```

## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
(gc .\logs\access.log | sls "WARNING").count
(gc .\logs\payment.log | sls "ERROR").count
```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log: 4
ERROR trong payment.log: 3
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
.\auto_warning.ps1

```

### Nội dung file logs/warning_report.txt

```text
 2 0 2 5 - 1 0 - 1 8   0 9 : 1 9 : 1 3   [ W A R N I N G ]   C o n g   t h a n h   t o a n   p h a n   h o i   c h a m 
 
 2 0 2 5 - 1 0 - 1 8   0 9 : 2 8 : 1 6   [ W A R N I N G ]   N h i e u   l a n   n h a p   s a i   m a   O T P 
 
 2 0 2 5 - 1 0 - 1 8   0 9 : 4 3 : 0 1   [ W A R N I N G ]   S o   d u   v i   g a n   b a n g   h o c   p h i 
 
 2 0 2 5 - 1 0 - 1 8   0 9 : 4 6 : 2 2   [ W A R N I N G ]   S o   d u   v i   g a n   b a n g   h o c   p h i 
 
 2 0 2 5 - 1 0 - 1 8   0 9 : 4 9 : 4 3   [ W A R N I N G ]   S o   d u   v i   g a n   b a n g   h o c   p h i 
 

```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
"=== TONG HOP ACCESS LOG ===" > logs/tong_hop_ngay2.txt
gc .\logs\access.log | sls "ERROR" >> .\logs\tong_hop_ngay2.txt
(gc .\logs\payment.log | sls "WARNING").count >> .\logs\tong_hop_ngay2.txt
```

### Nội dung file logs/tong_hop_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)


5


```

## Bài 5. Câu hỏi ngắn

- **a) lệnh > là để ghi đè cũ còn lệnh >> là để ghi thêm vào cuối file**
- **b) các nội dung sẽ mất hết, chỉ còn các dòng chứa ERROR**
- **c) vì trên máy tính khác sẽ không có file/folder giống máy gốc. Điều này khiên cho câu lệnh bị lỗi**

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
