# Dependency-Parsing

# Hướng dẫn sử dụng MaltParser

Tài liệu này cung cấp hướng dẫn cài đặt, thiết lập và sử dụng MaltParser cho các nhiệm vụ phân tích phụ thuộc (dependency parsing). MaltParser là một công cụ phân tích phụ thuộc ngữ pháp dựa trên học máy.

## Mục lục

1. [Cài đặt](#cài-đặt)
2. [Huấn luyện bộ phân tích](#huấn-luyện-bộ-phân-tích)
3. [Phân tích câu mới](#phân-tích-câu-mới)
4. [Đánh giá bộ phân tích](#đánh-giá-bộ-phân-tích)
5. [Sử dụng dòng lệnh](#sử-dụng-dòng-lệnh)
6. [Xử lý sự cố](#xử-lý-sự-cố)
7. [Tham khảo](#tham-khảo)

## Cài đặt

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

## Huấn luyện bộ phân tích

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

## Đánh giá bộ phân tích

Bạn có thể đánh giá hiệu suất của bộ phân tích đã huấn luyện bằng các chỉ số như Unlabeled Attachment Score (UAS) và Labeled Attachment Score (LAS).

1. **Chuẩn bị dữ liệu kiểm tra:**
   - Đảm bảo dữ liệu kiểm tra của bạn ở định dạng CoNLL.

2. **Đánh giá mô hình:**
   - Sử dụng công cụ đánh giá phù hợp để so sánh kết quả phân tích của bộ phân tích với các chú thích chuẩn (gold-standard) trong dữ liệu kiểm tra.

## Sử dụng dòng lệnh

MaltParser cung cấp nhiều tùy chọn dòng lệnh để huấn luyện, phân tích và cấu hình bộ phân tích. Một số tùy chọn phổ biến bao gồm:

- `-c <tên_mô_hình>`: Chỉ định tên mô hình.
- `-i <file_đầu_vào>`: Chỉ định file đầu vào.
- `-o <file_đầu_ra>`: Chỉ định file đầu ra.
- `-m <chế_độ>`: Chỉ định chế độ (`learn` để huấn luyện, `parse` để phân tích).

Để xem danh sách đầy đủ các tùy chọn, chạy:
```bash
java -jar maltparser-<phiên_bản>.jar -help
