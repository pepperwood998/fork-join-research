# Mô hình Fork-Join

## Định nghĩa
+ Mô hình được áp dụng để  cài đặt và chạy chương trình một cách song song.
+ Việc thực thi chương trình sẽ được chia thành nhiều nhánh thực thi song song  
(chia nhánh sẽ diễn ra tại một số điểm trong chương trình).
+ Từng nhánh song song đó có thể sẽ được đệ quy chia nhỏ thành các nhiệm vụ con cho tới khi chúng đủ đơn giản.
+ Mô hình này có thể được coi là một "design pattern" cho việc xử lý song song.

## Ý tưởng cơ bản
#### Đoạn mã giả mô tả ý tưởng của mô hình
    Giải(tác vụ):
        if (tác vụ nhỏ):
            Giải trưc tiếp tác vụ, trả về kq
        else:
            Với mỗi [tác_vụ_con] trong tác vụ (fork):
                Giải(tác_vụ_con)
            Tổng hợp, trả về kết quả
