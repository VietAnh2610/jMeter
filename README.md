# JMeter

## Giới thiệu

JMeter là một công cụ mã nguồn mở được phát triển bởi Apache Software Foundation. Nó được sử dụng để kiểm thử hiệu năng và tải cho các ứng dụng web. JMeter có thể mô phỏng một lượng lớn người dùng truy cập vào dịch vụ web, API hoặc ứng dụng web để phân tích hiệu năng của chúng.

## Tính năng chính

- **Kiểm thử tải và hiệu năng**: JMeter có thể tạo ra nhiều người dùng ảo để kiểm thử khả năng chịu tải và hiệu năng của ứng dụng.
- **Hỗ trợ nhiều giao thức**: JMeter hỗ trợ nhiều giao thức khác nhau như HTTP, HTTPS, FTP, JDBC, SOAP, REST, và nhiều hơn nữa.
- **Dễ dàng sử dụng**: Giao diện đồ họa thân thiện giúp người dùng dễ dàng thiết lập và quản lý các kịch bản kiểm thử.
- **Mở rộng**: JMeter cho phép người dùng viết các plugin để mở rộng chức năng của nó.
- **Báo cáo chi tiết**: JMeter cung cấp các báo cáo chi tiết về kết quả kiểm thử giúp người dùng phân tích và tối ưu hóa ứng dụng.

## Cài đặt

Để cài đặt JMeter, bạn cần làm theo các bước sau:

1. **Tải JMeter**: Truy cập vào trang web chính thức của Apache JMeter và tải phiên bản mới nhất.
2. **Cài đặt JDK**: JMeter yêu cầu Java Development Kit (JDK) để chạy. Đảm bảo rằng bạn đã cài đặt JDK và thiết lập biến môi trường JAVA_HOME.
3. **Giải nén**: Giải nén tập tin JMeter đã tải xuống vào thư mục bạn mong muốn.
4. **Chạy JMeter**: Điều hướng đến thư mục bin trong thư mục JMeter đã giải nén và chạy tập tin `jmeter.bat` (đối với Windows) hoặc `jmeter` (đối với Unix).

## Sử dụng cơ bản

1. **Tạo test plan**: Mở JMeter và tạo một test plan mới.
2. **Thêm thread group**: Thêm một thread group để mô phỏng người dùng ảo.
3. **Thêm sampler**: Thêm sampler để xác định các yêu cầu HTTP hoặc các giao thức khác mà bạn muốn kiểm thử.
4. **Thêm listener**: Thêm listener để thu thập và hiển thị kết quả kiểm thử.
5. **Chạy kiểm thử**: Chạy test plan và theo dõi kết quả trong listener.

### Tạo kịch bản kiểm tra

1. **Mở JMeter**: Khởi động JMeter và tạo một test plan mới.
2. **Thêm Thread Group**:
   - Chuột phải vào Test Plan, chọn `Add` -> `Threads (Users)` -> `Thread Group`.
   - Cấu hình Thread Group với số lượng người dùng là 50, thời gian khởi động là 10 giây và số lần lặp lại là 10.
3. **Thêm HTTP Request Defaults**:
   - Chuột phải vào Thread Group, chọn `Add` -> `Config Element` -> `HTTP Request Defaults`.
   - Cấu hình: Server Name or IP: `vietnamnet.vn`, Protocol: `http`.
4. **Thêm HTTP Request**:
   - Chuột phải vào Thread Group, chọn `Add` -> `Sampler` -> `HTTP Request`.
   - Đặt tên là "Homepage Request" và cấu hình Path: `/`.
5. **Thêm Listener để thu thập kết quả**:
   - Chuột phải vào Thread Group, chọn `Add` -> `Listener` -> `View Results in Table`.
   - Chuột phải vào Thread Group, chọn `Add` -> `Listener` -> `Summary Report`.

## Kết quả kiểm tra

Dưới đây là các thông số thu thập được từ quá trình kiểm tra hiệu năng:

| Label     | # Samples | Average (ms) | Median (ms) | 90% Line (ms) | 95% Line (ms) | 99% Line (ms) | Min (ms) | Max (ms) | Error % | Throughput (requests/sec) | Received KB/sec | Sent KB/sec |
|-----------|-----------|--------------|-------------|---------------|---------------|---------------|----------|----------|---------|---------------------------|-----------------|-------------|
| vnnetPage | 2000      | 2871         | 2049        | 6517          | 7437          | 8210          | 136      | 27597    | 0.00%   | 3.9/sec                   | 509.29          | 0.87        |
| TOTAL     | 2000      | 2871         | 2049        | 6517          | 7437          | 8210          | 136      | 27597    | 0.00%   | 3.9/sec                   | 509.29          | 0.87        |

![image](https://github.com/VietAnh2610/jMeter/assets/129382437/d36d3b55-111a-40f1-ac49-28066c72fb67)
![image](https://github.com/VietAnh2610/jMeter/assets/129382437/abeb7661-fcde-4f8b-a1c6-c38ae5f2fcb3)
![image](https://github.com/VietAnh2610/jMeter/assets/129382437/bd9744e5-1688-4e70-b3ea-7fb5a515a423)

### Phân tích kết quả

1. **Số lượng mẫu thử (Samples)**: 
   - Tổng số mẫu thử là 2000, nghĩa là đã có 2000 yêu cầu được gửi đi.

2. **Thời gian phản hồi trung bình (Average)**:
   - Thời gian phản hồi trung bình của các yêu cầu là 2871 ms.

3. **Thời gian phản hồi trung vị (Median)**:
   - Thời gian phản hồi trung vị là 2049 ms, nghĩa là 50% số yêu cầu có thời gian phản hồi dưới 2049 ms và 50% còn lại có thời gian phản hồi trên 2049 ms.

4. **90% Line**:
   - Thời gian phản hồi của 90% yêu cầu là 6517 ms hoặc ít hơn, và 10% còn lại có thời gian phản hồi cao hơn 6517 ms.

5. **95% Line**:
   - Thời gian phản hồi của 95% yêu cầu là 7437 ms hoặc ít hơn, và 5% còn lại có thời gian phản hồi cao hơn 7437 ms.

6. **99% Line**:
   - Thời gian phản hồi của 99% yêu cầu là 8210 ms hoặc ít hơn, và chỉ 1% số yêu cầu có thời gian phản hồi cao hơn 8210 ms.

7. **Thời gian phản hồi nhỏ nhất (Min)**:
   - Thời gian phản hồi nhỏ nhất là 136 ms, cho thấy yêu cầu nhanh nhất đã hoàn thành trong thời gian này.

8. **Thời gian phản hồi lớn nhất (Max)**:
   - Thời gian phản hồi lớn nhất là 27597 ms, cho thấy yêu cầu chậm nhất đã mất gần 28 giây để hoàn thành.

9. **Tỷ lệ lỗi (Error %)**:
   - Không có lỗi nào xảy ra trong quá trình kiểm tra (tỷ lệ lỗi là 0.00%).

10. **Thông lượng (Throughput)**:
    - Thông lượng trung bình là 3.9 requests/giây, nghĩa là trung bình có khoảng 3.9 yêu cầu được xử lý mỗi giây.

11. **Dung lượng nhận (Received KB/sec)**:
    - Tốc độ nhận dữ liệu trung bình là 509.29 KB/giây.

12. **Dung lượng gửi (Sent KB/sec)**:
    - Tốc độ gửi dữ liệu trung bình là 0.87 KB/giây.

### Kết luận

Trang web vietnamnet.vn có hiệu năng khá tốt khi thời gian phản hồi trung bình là 2871 ms và không có yêu cầu nào bị lỗi (tỷ lệ lỗi là 0.00%). Thông lượng của trang web là 3.9 requests/giây. Tuy nhiên, thời gian phản hồi tối đa lên đến 27597 ms, cho thấy có một số yêu cầu có thời gian phản hồi rất cao, có thể cần kiểm tra thêm để tìm hiểu nguyên nhân và tối ưu hóa hiệu năng.


 
