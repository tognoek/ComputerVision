# Ghi chú
- Em có chạy và để mất thông số của lần cuối cùng nạp trên hệ thống.
- Em tìm được lại thông số với số điểm Private là tốt nhất.
- Cost lần cuối: 0.36887
- Cost mà code chạy ra: 0.43613. Epchos = 100, Batch_size = 4. Đầy là lần có Private tốt nhất.
- Đáp án em nạp là mô hình lấy lần cuối chứ không phải lần tốt nhất.
- Mô hình em còn nhiều thiếu sót mong thầy góp ý.
# Khống chế radom của numpy
- state = 2904
# Các hàm kích hoạt
- Linear 
- ReLU
- Linear kết hợp với ReLU
# Hàm mất mát
- MeanSquaredError
    # Điểm chung
    - Tất cả các hàm đều viết 2 phương thức
    - Lan truyền xuyên. Dùng để tính toán giá trị từ trái qua phải có nghĩa là dựa đoán giá trị theo công thức cho trước hoặc là bạn tự tạo thêm.
    - Lan truyền ngược. Dùng để tính toán lại W và b của quá trình lan truyền xuôi giúp tôi uy thuật toán tốt hơn.
    # Điểm khác
    - Mỗi hàm đều có một phương trình khác nhau.
    - Ví dụ ở lan truyền xuôi
    - Hàm Liner theo công thức W * X + b. W là trọng số đầu vào, X là đầu vào và b là giá trị cộng thêm có thể bằng 0 cũng được.
    - Hàm ReLU sẽ là max(X, 0). X là đầu vào.
    - Các công thức được học và tìm kiếm trên mạng.
# Dữ liệu
- Đọc dữ liệu từ file csv.
- Cấu hình lại dữ liệu thời gian.
- Một sô trường có 2 giá trị một bảng là 1 từ Trung và 1 chữ số thì em viết hàm để lấy mỗi chữ số.
- Loại bỏ các giá trị lỗi như: ?NAME và các từ Trung Quốc thành nan
- Với các giá trị nan em cho lấy giá trị trung bình của cột đó.
- Ghép file X và y lại theo ID để tránh việc X có id mà y thì không. Đồng bộ dữ liệu.
- Tách ra để tạo X và y như ban đầu nhưng đẹp hơn.
- Chuyển về array của numpy và dùng scaler để transform dữ liệu.
- Với tệp kiểm thử cũng tương tự chỉ là không đồng bộ dữ liệu tại đây là file kiểm thử.
- Với tệp y thì em chia cho 100 tại số lớn quá dễ đến việc tính toán của numpy báo lỗi. Khi dự đoán xong em nhân lại 100 để cho về nguyên hình.
- Em có tách dữ liệu ra để làm train và test nhưng em chỉ dùng phần train có nghĩa là dùng phẩn 80% để làn train và test luôn. Vứt 20% đi mất rồi.
# Mô hình NeuralNetwork
- Khởi tạo các lớp ẩn lớp cuối đề nhận giá trị và xác định hàm mất mát.
- Lớp ẩn em dùng LinearAndReLU.
- Lớp cuối em dùng Liner để tính toán.
- Hàm mất mát là MeanSquaredError.
- Mô hình NeuralNetwork cũng có lân truyền xuôi và lan truyền ngược.
- Em viết lan truyền xuôi và sau khi lan truyền xuôi em gọi luôn lan truyền ngược của các lớp ẩn dựa vào độ mất mát được tính bở hàm mất mát.
- Hàm train có tác dụng:
  - Nhận vào đầu vào, số lần lặp và số tệp dữ liệu mỗi lần học cho NeuralNetwork.
  - Em xóa trộn giá trị đầu vào mỗi lần lặp để cho mô hình có tính ngẫu nhiên.
  - Gửi vào lan truyền xuôi tệp dữ liệu với kích cỡ batch được truyền vào.
  - Mỗi 10 lần em dùng chính dữ liệu đầu vào để kiểm tra xem mô hình xem thử độ hiệu quả trong quá trình học tập.
  - Có thể tách tệp ra thành 2 phần là train và test. Nhưng do bài em nạp em dùng phần train cho việc kiểm tra luôn nên em để vậy.
  - Nếu nhưng mức độ học tập tốt hơn thì em lưu lần học đó để xuất ra trọng số . 
  - Hiện tại mô hình em đang dùng lần train cuối dùng để dùng làm mô hình chuẩn.
  - Có vẻ em quên dùng mô hình tốt nhất để dự đoán giá nhà rồi.
  - Mỗi 30 lần em lại chỉnh lại tốc độ học của mô hình. Giảm xuống tý.
# Main
- Ở đầy em chỉ khởi tạo ra mô hình NeuralNetwork với số hidden_layer, epochs và btach_size.
- Sau đó train mô hình vừa tạo với tệp dữ liệu.
- Dùng mô hình để dự đoán giá nhà cho tệp thử nghiệm.
- Sau đó lưu tại vào các thư mục.
# Cảm ơn thầy đã đọc tới đây.
