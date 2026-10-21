# HCM-KS26-CNTT2_Nhap-mon-CNTT_Session7_Ex1
 * 1. Tại sao mở file 500MB bằng Notepad lại bị treo?
Notepad hoạt động bằng cách nạp toàn bộ dữ liệu file vào bộ nhớ RAM trước khi hiển thị. Với file 500MB, quá trình phân pháp ký tự và quản lý chuỗi có thể tốn vài GB RAM. Khi RAM bị quá tải, Windows rơi vào trạng thái Not Responding.

* 2. Tại sao lệnh cat trên PowerShell lại làm đơ Terminal?
Trên PowerShell, cat là alias của Get-Content. Mặc định lệnh này đọc và xả toàn bộ 500MB nội dung ra màn hình cùng lúc. Việc bắt Terminal render hàng triệu dòng text trong vài giây vượt quá khả năng xử lý của bộ đệm console, gây đơ giao diện.

# Phần 2: Giải pháp trên PowerShell
1. Lệnh xem file theo từng trang (Page-by-page):

PowerShell
Get-Content server_log_500MB.log | more
(Đọc file theo dòng và dừng lại ở mỗi trang màn hình. Phím Space để sang trang, Enter để xuống 1 dòng).

* 2. Lệnh chỉ xem 10 dòng cuối cùng:

PowerShell
Get-Content server_log_500MB.log -Tail 10
