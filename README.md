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

## Các khái niệm đi kèm
1. Thread-pool/Fork-join-pool  
Xét đến công việc riêng của một tác vụ con, thì công việc đó được thực thi tuần tự, lệnh này tới lệnh kia. Nhưng các tác vụ con lại được thực thi song song với nhau, nên người ta sẽ sử dụng thread-pool để thực thi các tác vụ đó.  

    Trong mô hình này thread-pool sẽ được gọi là fork-join-pool. Công việc của nó tương tự như thread-pool, phân chia công việc cho các luồng thực thi. Luồng nào thực thi xong, nó lấy các tác vụ khác.


    Khác với thread-pool là ở đây cơ chế  lấy tác vụ được cài đặt qua thuật toán "work-stealing"

2. Work stealing  
Là một cơ chế  lập lịch cho chương trình đa luồng

+ Trong bộ lập lịch này, mỗi đơn vị xử  lý (core/processor) sẽ có một hàng đợi để chứa công việc cần thực hiện.  
+ Khi một công việc được thực thi, nó có thể  sỉnh ra công việc mới (fork) mà có thể  được chạy song song với việc chính.  
+ Công việc mới này ban đầu sẽ được cho vào hàng đợi của đơn vị xử lý hiện tại.
+ Nếu một đơn vị xử  lý mà thực hiện hết việc của nó, nó sẽ xem và "cướp" công việc từ hàng đợi của một đơn vị xử lý khác


## Đường dẫn tham khảo
[Fork-join/Fork-join-framework trong Java](https://gpcoder.com/3573-su-dung-fork-join-framework-voi-forkjoinpool-trong-java/ "Boi Việt Nam")  
[Fork-join Model](https://en.wikipedia.org/wiki/Fork%E2%80%93join_model "Fork-join wiki")  
[Work-stealing](https://en.wikipedia.org/wiki/Work_stealing "Work-stealing")
