# Dependency-Parsing

# 1. Hướng dẫn sử dụng MaltParser

Tài liệu này cung cấp hướng dẫn cài đặt, thiết lập và sử dụng MaltParser cho các nhiệm vụ phân tích phụ thuộc (dependency parsing). MaltParser là một công cụ phân tích phụ thuộc ngữ pháp dựa trên học máy.


## 1.1 Cài đặt

1. **Tải MaltParser:**
   - Truy cập [trang web MaltParser](http://www.maltparser.org/download.html) và tải về phiên bản mới nhất của file `.jar` của MaltParser.

2. **Cài đặt Java:**
   - MaltParser yêu cầu Java để chạy. Đảm bảo rằng bạn đã cài đặt Java:
     ```bash
     java -version
     ```
   - Nếu Java chưa được cài đặt, tải về và cài đặt từ [trang web chính thức của Java](https://www.java.com/).

3. **Thiết lập MaltParser:**
   - Đặt file `.jar` vừa tải về trong thư mục nơi bạn muốn làm việc với MaltParser.
   - Mở terminal và điều hướng đến thư mục này:
     ```bash
     cd /đường/dẫn/đến/thư_mục/maltparser/
     ```

## 1.2 Huấn luyện bộ phân tích

Để huấn luyện bộ phân tích với MaltParser, bạn cần có một tập dữ liệu huấn luyện ở định dạng CoNLL.

1. **Chuẩn bị dữ liệu huấn luyện:**
   - Đảm bảo rằng dữ liệu huấn luyện của bạn ở định dạng CoNLL chính xác, thường là các file `.conllu` hoặc `.conll`.

2. **Huấn luyện bộ phân tích:**
   - Chạy lệnh sau để huấn luyện bộ phân tích:
     ```bash
     java -jar maltparser-<phiên_bản>.jar -c <tên_mô_hình> -i <dữ_liệu_huấn_luyện>.conllu -m learn
     ```
   - Thay `<phiên_bản>` bằng phiên bản MaltParser bạn đã tải về, `<tên_mô_hình>` bằng tên bạn muốn đặt cho mô hình của mình, và `<dữ_liệu_huấn_luyện>` bằng đường dẫn đến file dữ liệu huấn luyện của bạn.

3. **Kết quả huấn luyện:**
   - Sau khi huấn luyện, một file mô hình (`<tên_mô_hình>.mco`) sẽ được tạo trong thư mục làm việc của bạn.

## Phân tích câu mới

Sau khi đã huấn luyện xong bộ phân tích, bạn có thể sử dụng nó để phân tích các câu mới.

1. **Chuẩn bị dữ liệu đầu vào:**
   - Tạo một file chứa các câu bạn muốn phân tích ở định dạng CoNLL.

2. **Chạy bộ phân tích:**
   - Sử dụng lệnh sau để phân tích các câu:
     ```bash
     java -jar maltparser-<phiên_bản>.jar -c <tên_mô_hình> -i <dữ_liệu_đầu_vào>.conllu -o <dữ_liệu_đầu_ra>.conllu -m parse
     ```
   - Thay `<dữ_liệu_đầu_vào>` bằng đường dẫn đến file đầu vào của bạn và `<dữ_liệu_đầu_ra>` bằng tên file đầu ra mong muốn.

3. **Dữ liệu đầu ra:**
   - Các câu được phân tích sẽ được lưu trong file đầu ra bạn chỉ định.

## 1.3 Đánh giá bộ phân tích

Bạn có thể đánh giá hiệu suất của bộ phân tích đã huấn luyện bằng các chỉ số như Unlabeled Attachment Score (UAS) và Labeled Attachment Score (LAS).

1. **Chuẩn bị dữ liệu kiểm tra:**
   - Đảm bảo dữ liệu kiểm tra của bạn ở định dạng CoNLL.

2. **Đánh giá mô hình:**
   - Sử dụng công cụ đánh giá phù hợp để so sánh kết quả phân tích của bộ phân tích với các chú thích chuẩn (gold-standard) trong dữ liệu kiểm tra.

## 1.4 Sử dụng dòng lệnh

MaltParser cung cấp nhiều tùy chọn dòng lệnh để huấn luyện, phân tích và cấu hình bộ phân tích. Một số tùy chọn phổ biến bao gồm:

- `-c <tên_mô_hình>`: Chỉ định tên mô hình.
- `-i <file_đầu_vào>`: Chỉ định file đầu vào.
- `-o <file_đầu_ra>`: Chỉ định file đầu ra.
- `-m <chế_độ>`: Chỉ định chế độ (`learn` để huấn luyện, `parse` để phân tích).

Để xem danh sách đầy đủ các tùy chọn, chạy:
```bash
java -jar maltparser-<phiên_bản>.jar -help
```

# 2. Hướng dẫn sử dụng MSTParser
Phần tiếp theo cung cấp hướng dẫn cài đặt, thiết lập và sử dụng MSTParser cho các nhiệm vụ phân tích phụ thuộc (dependency parsing) dựa vào đồ thị

## 2.1 Cài đặt

1. **Clone repository**:

    ```bash
    git clone https://github.com/kzn/mstparser.git
    ```

2. **Biên dịch mã nguồn**:

    Điều hướng đến thư mục chứa mã nguồn và chạy lệnh sau để biên dịch:

    ```bash
    cd mstparser
    javac -classpath ".:lib/trove.jar" mstparser/DependencyParser.java
    ```
## 2.2 Huấn luyện bộ phân tích
Để huấn luyện mô hình trên một tập dữ liệu, bạn có thể sử dụng lệnh sau:
```bash
java -cp dist/mstparser.jar mstparser.DependencyParser train train-file:<đường dẫn đến tập huấn luyện> model-name:<tên mô hình>
```

## 2.3 Chạy bộ phân tích đã huấn luyện trên bộ data mới
Sau khi đã huấn luyện mô hình, bạn có thể sử dụng nó để phân tích cú pháp các câu mới:
```bash
java -cp dist/mstparser.jar mstparser.DependencyParser test test-file:<đường dẫn đến tập dữ liệu> model-name:<tên mô hình> output-file:<đường dẫn đến file đầu ra>
```

## 2.4 Đánh giá kết quả bộ phân tích
Để đánh giá kết quả bộ phân tích (giả sử file output là out.txt, file kết quả thật là test.txt), bạn có thể sử dụng lệnh sau
```bash
java -classpath ".:lib/trove.jar" -Xmx1800m mstparser.DependencyParser
eval gold-file:test.txt output-file:out.txt MST
```
## 2.5 Tùy chọn thêm
MSTParser cung cấp nhiều tùy chọn cấu hình để tinh chỉnh quá trình huấn luyện và phân tích cú pháp. Để biết danh sách đầy đủ các tùy chọn và tham số, vui lòng tham khảo tài liệu trong repository GitHub chính thức: https://github.com/travisbrown/mstparser.
