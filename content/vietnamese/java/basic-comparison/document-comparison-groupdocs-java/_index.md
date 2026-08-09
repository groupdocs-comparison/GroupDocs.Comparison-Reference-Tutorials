---
categories:
- Java Development
date: '2026-08-09'
description: Tìm hiểu cách so sánh tài liệu trong Java bằng streams với GroupDocs.Comparison.
  Hướng dẫn này bao gồm cài đặt, mẹo hiệu năng và khắc phục sự cố cho việc so sánh
  java pdf word.
keywords:
- how to compare docs
- java compare pdf word
- groupdocs comparison java
- document comparison java streams
- compare word documents java
lastmod: '2026-08-09'
linktitle: Hướng dẫn So sánh Tài liệu Java
og_description: Tìm hiểu cách so sánh tài liệu trong Java bằng streams với GroupDocs.Comparison.
  Hướng dẫn này bao gồm cài đặt, mẹo hiệu năng và khắc phục sự cố cho việc so sánh
  java pdf word.
og_image_alt: Guide to compare Word documents in Java using streams with GroupDocs.Comparison
og_title: Cách so sánh tài liệu trong Java bằng streams – Hướng dẫn GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to compare docs in Java using streams with GroupDocs.Comparison.
    This guide covers setup, performance tips, and troubleshooting for java compare
    pdf word.
  headline: How to compare docs in Java with streams – GroupDocs guide
  type: TechArticle
- description: Learn how to compare docs in Java using streams with GroupDocs.Comparison.
    This guide covers setup, performance tips, and troubleshooting for java compare
    pdf word.
  name: How to compare docs in Java with streams – GroupDocs guide
  steps:
  - name: '**Free trial** – Ideal for quick evaluation and small‑scale testing.'
    text: '**Free trial** – Ideal for quick evaluation and small‑scale testing.'
  - name: '**Temporary license** – Perfect for development cycles and proof‑of‑concept
      projects.'
    text: '**Temporary license** – Perfect for development cycles and proof‑of‑concept
      projects.'
  - name: '**Full license** – Required for any production deployment that exceeds
      trial limits.'
    text: '**Full license** – Required for any production deployment that exceeds
      trial limits.'
  - name: '**Tune buffer sizes** – Set `java.io.BufferedInputStream` buffer to 64 KB
      for typical 5‑10 MB files; increase to 256 KB for larger PDFs.'
    text: '**Tune buffer sizes** – Set `java.io.BufferedInputStream` buffer to 64 KB
      for typical 5‑10 MB files; increase to 256 KB for larger PDFs.'
  - name: '**Monitor GC** – Use VisualVM or Java Flight Recorder to watch garbage‑collection
      pauses during bulk comparisons.'
    text: '**Monitor GC** – Use VisualVM or Java Flight Recorder to watch garbage‑collection
      pauses during bulk comparisons.'
  - name: '**Connection pooling** – Reuse HTTP connections when streaming files from
      remote storage services.'
    text: '**Connection pooling** – Reuse HTTP connections when streaming files from
      remote storage services.'
  type: HowTo
- questions:
  - answer: There is no hard limit, but documents larger than 100 MB benefit from
      increased JVM heap size and stream‑buffer tuning to avoid `OutOfMemoryError`.
    question: What's the maximum document size GroupDocs.Comparison can handle?
  - answer: Yes. Provide the password when constructing the source or target stream;
      the API will decrypt the file before comparison.
    question: Can I compare password‑protected documents using streams?
  - answer: The engine auto‑detects formats, but for optimal results convert all inputs
      to a common format (e.g., PDF) before comparison when mixing types.
    question: How do I handle different document formats in the same comparison?
  - answer: Yes. Production deployments need a full or temporary GroupDocs.Comparison
      license. Free trials are limited to 30 days and 20 comparisons.
    question: Is a license required for production use?
  - answer: Absolutely. Use `CompareOptions` to set highlight colors, change markers,
      and output format (PDF, DOCX, HTML, etc.).
    question: Can I customize the appearance of the comparison result?
  type: FAQPage
tags:
- document-comparison
- java-streams
- groupdocs
- word-documents
title: Cách so sánh tài liệu trong Java bằng streams – Hướng dẫn GroupDocs
type: docs
url: /vi/java/basic-comparison/document-comparison-groupdocs-java/
weight: 1
---

# Cách so sánh tài liệu trong Java bằng streams – Hướng dẫn GroupDocs

Nếu bạn cần **cách so sánh tài liệu** trong một ứng dụng Java—cho dù bạn đang xây dựng nền tảng cộng tác, hệ thống kiểm soát phiên bản, hoặc chỉ đơn giản là theo dõi các thay đổi giữa các phiên bản—hướng dẫn này sẽ giúp bạn. GroupDocs.Comparison cho Java cho phép bạn thực hiện so sánh tài liệu dựa trên stream, có nghĩa là bạn không bao giờ phải ghi các tệp tạm thời vào đĩa. Cách tiếp cận này lý tưởng cho các ứng dụng cloud‑native, các kịch bản lưu trữ từ xa, và môi trường mà việc sử dụng bộ nhớ phải được giữ ở mức thấp.

## Câu trả lời nhanh
- **Thư viện nào được sử dụng?** GroupDocs.Comparison for Java  
- **Có thể so sánh tài liệu mà không lưu chúng vào đĩa không?** Có, bằng cách sử dụng streams  
- **Phiên bản Java nào được yêu cầu?** JDK 8+ (Java 11+ recommended)  
- **Có cần giấy phép cho môi trường production không?** Có, cần giấy phép đầy đủ hoặc tạm thời  
- **Có thể so sánh các định dạng khác không?** Chắc chắn – PDF, Excel, PowerPoint, và nhiều hơn nữa  

## So sánh tài liệu Word trong Java
Cụm từ “compare word documents java” đề cập đến việc phát hiện chương trình các thay đổi về văn bản, định dạng và cấu trúc giữa hai hoặc nhiều tệp Word (.docx hoặc .doc) từ một ứng dụng Java. Khi sử dụng streams, quá trình so sánh diễn ra hoàn toàn trong bộ nhớ, loại bỏ I/O đĩa và đơn giản hoá việc tích hợp với lưu trữ đám mây.

## Tại sao nên sử dụng so sánh dựa trên stream?
So sánh dựa trên stream cho phép bạn làm việc trực tiếp với các input stream, loại bỏ nhu cầu tạo các tệp tạm thời. Cách tiếp cận này giảm I/O đĩa, cải thiện bảo mật bằng cách giữ dữ liệu trong bộ nhớ, và cho phép tích hợp liền mạch với các dịch vụ lưu trữ đám mây, làm cho nó trở nên lý tưởng cho các ứng dụng Java hiện đại, có khả năng mở rộng.

- **Hiệu suất bộ nhớ** – Không cần tải toàn bộ tệp vào RAM.  
- **Hỗ trợ tệp từ xa** – Hoạt động trực tiếp với các tài liệu lưu trữ trên đám mây hoặc trong cơ sở dữ liệu.  
- **Bảo mật** – Loại bỏ các tệp tạm thời trên đĩa, giảm rủi ro phơi bày.  
- **Khả năng mở rộng** – Xử lý nhiều so sánh đồng thời với mức tiêu thụ tài nguyên tối thiểu.  

## Yêu cầu trước và thiết lập môi trường
Trước khi bạn bắt đầu **so sánh tài liệu stream trong Java**, hãy xác nhận môi trường phát triển của bạn đáp ứng các yêu cầu chính xác sau:

* **GroupDocs.Comparison for Java** phiên bản 25.2 hoặc mới hơn (bản phát hành mới nhất bổ sung hỗ trợ hơn 50 định dạng tệp).  
* **JDK** 8 hoặc mới hơn (Java 11+ được khuyến nghị mạnh mẽ để cải thiện hiệu năng và hỗ trợ mô-đun).  
* **IDE** – IntelliJ IDEA, Eclipse, hoặc VS Code với các extension Java.  
* **Công cụ xây dựng** – Maven hoặc Gradle để quản lý phụ thuộc.  
* **Bộ nhớ** – Tối thiểu 2 GB RAM cho quá trình phát triển mượt mà; các tải công việc sản xuất xử lý tài liệu 100 trang thường cấp phát 4 GB.  

*Mẹo chuyên gia*: Nếu streams là mới đối với bạn, hãy xem lại các hướng dẫn Java 8 `java.io.InputStream` và `java.nio.file.Files` trước khi bắt đầu với mã so sánh.

## Thiết lập dự án và cấu hình

### Cấu hình Maven
Thêm phụ thuộc GroupDocs.Comparison vào `pom.xml` của bạn. Sử dụng phiên bản ổn định mới nhất để hưởng lợi từ các bản vá bảo mật và cải thiện hiệu năng.

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/comparison/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-comparison</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**Lưu ý quan trọng**: Luôn tham chiếu đến số phiên bản mới nhất; các bản phát hành cũ hơn có thể thiếu hỗ trợ cho các định dạng Office mới nhất.

### Các tùy chọn cấu hình giấy phép
GroupDocs.Comparison cung cấp ba lộ trình cấp phép:

1. **Dùng thử miễn phí** – Lý tưởng cho việc đánh giá nhanh và kiểm thử quy mô nhỏ.  
2. **Giấy phép tạm thời** – Hoàn hảo cho các chu kỳ phát triển và dự án chứng minh khái niệm.  
3. **Giấy phép đầy đủ** – Cần thiết cho bất kỳ triển khai sản xuất nào vượt quá giới hạn dùng thử.  

Bắt đầu với dùng thử miễn phí, sau đó nâng cấp lên giấy phép tạm thời khi bạn tích hợp API.

## Cách thực hiện so sánh tài liệu stream trong Java
Tải các tài liệu nguồn và đích dưới dạng stream, đưa chúng vào `Comparer`, và ghi kết quả vào một output stream. Toàn bộ thao tác hoàn thành trong hai dòng mã một khi các stream đã được chuẩn bị, và khối try‑with‑resources đảm bảo đóng đúng cách, ngăn ngừa rò rỉ bộ nhớ và đảm bảo thực thi an toàn đa luồng.

## Các import và thiết lập cần thiết
Điều đầu tiên bạn cần là một định nghĩa rõ ràng về lớp cốt lõi:

Lớp `Comparer` là thành phần cốt lõi của GroupDocs.Comparison, điều phối việc phân tích tài liệu và tạo ra kết quả so sánh.

Sau đó, import các gói cần thiết:

```java
import com.groupdocs.comparison.Comparer;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;
```

## Ví dụ triển khai đầy đủ
Dưới đây là luồng tối thiểu, sẵn sàng cho sản xuất cho so sánh dựa trên stream:

```java
class CompareDocumentsFromStreamFeature {
    public static void run() throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/CompareDocumentsFromStream_result.docx";

        try (InputStream sourceStream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/SOURCE_WORD.docx");
             InputStream targetStream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/TARGET1_WORD.docx");
             OutputStream resultStream = new FileOutputStream(outputFileName)) {
              
            // Initialize the Comparer with the source document stream
            try (Comparer comparer = new Comparer(sourceStream)) {
                comparer.add(targetStream);
                 
                // Perform comparison and output results to a stream
                comparer.compare(resultStream);
            }
        }
    }
}
```

## Hiểu về triển khai
* **Stream nguồn** – Đại diện cho tài liệu cơ sở ("gốc").  
* **Thêm stream đích** – `comparer.add(targetStream)` cho phép bạn so sánh bất kỳ số lượng phiên bản nào so với nguồn.  
* **Kết quả stream đầu ra** – Kết quả so sánh được ghi trực tiếp vào `resultStream`, cho phép bạn kiểm soát hoàn toàn nơi lưu trữ hoặc truyền kết quả.  
* **Quản lý tài nguyên** – Mẫu try‑with‑resources đảm bảo các stream được đóng, loại bỏ lỗi rò rỉ bộ nhớ phổ biến trong các triển khai so sánh tài liệu Java.  

## Cấu hình nâng cao và tùy chỉnh
Mặc dù luồng cơ bản hoạt động cho hầu hết các kịch bản, bạn có thể tinh chỉnh hành vi so sánh để phù hợp với nhu cầu kinh doanh cụ thể.

### Cài đặt độ nhạy của so sánh
Lớp `CompareOptions` cho phép bạn cấu hình độ nhạy và kiểu hiển thị của kết quả so sánh.

Điều chỉnh mức độ mà engine đánh dấu các thay đổi:

```java
// Example of configuring comparison options (pseudo-code for concept)
CompareOptions options = new CompareOptions();
options.setIgnoreFormatting(true);  // Focus on content changes
options.setIgnoreWhitespace(true);  // Ignore spacing differences
```

**Khi nào nên dùng**: Các hợp đồng pháp lý thường yêu cầu độ nhạy tối đa, trong khi các bản nháp hợp tác có thể bỏ qua các chỉnh sửa định dạng nhỏ.

### Xử lý nhiều định dạng tài liệu
GroupDocs.Comparison hỗ trợ hơn 50 định dạng đầu vào và đầu ra, bao gồm:

* Word: `.docx`, `.doc`  
* PDF: `.pdf`  
* Excel: `.xlsx`, `.xls`  
* PowerPoint: `.pptx`, `.ppt`  

Mẫu dựa trên stream tương tự hoạt động cho tất cả các định dạng được hỗ trợ—chỉ cần thay đổi phần mở rộng tệp của các input stream.

## Những lỗi thường gặp và giải pháp
Ngay cả các nhà phát triển dày dặn kinh nghiệm cũng gặp phải những trục trặc khi triển khai **so sánh tài liệu java**. Dưới đây là các vấn đề phổ biến nhất và cách giải quyết chúng.

### Vấn đề 1: Vấn đề vị trí stream
**Vấn đề**: Một stream bị tiêu thụ trong lần so sánh đầu tiên, gây ra lỗi cho các lần gọi tiếp theo.  
**Giải pháp**: Luôn tạo một `InputStream` mới cho mỗi thao tác so sánh. Không tái sử dụng cùng một instance của stream.

### Vấn đề 2: Rò rỉ bộ nhớ
**Vấn đề**: Quên đóng các stream dẫn đến việc heap tăng dần.  
**Giải pháp**: Bao bọc mọi việc sử dụng stream trong khối try‑with‑resources, như trong ví dụ triển khai.

### Vấn đề 3: Vấn đề đường dẫn tệp
**Vấn đề**: Đường dẫn không đúng gây ra `FileNotFoundException`.  
**Giải pháp**: Sử dụng đường dẫn tuyệt đối trong quá trình phát triển và tách chúng ra qua các tệp cấu hình cho môi trường sản xuất.

### Vấn đề 4: Hiệu năng tài liệu lớn
**Vấn đề**: So sánh các tài liệu lớn hơn 50 MB có thể gây timeout.  
**Giải pháp**: Tăng heap JVM (`-Xmx4g`), tinh chỉnh kích thước bộ đệm nội bộ, và cân nhắc chia tài liệu thành các phần logic để xử lý song song.

**Mẹo gỡ lỗi**: Thêm logging quanh mỗi thao tác stream để giám sát số byte đã đọc và nhanh chóng xác định các nút thắt.

## Tối ưu hoá hiệu năng cho sản xuất
Khi bạn đưa tính năng so sánh vào một dịch vụ trực tiếp, hiệu năng và khả năng mở rộng trở nên quan trọng.

### Thực hành tốt quản lý bộ nhớ
1. **Tinh chỉnh kích thước bộ đệm** – Đặt bộ đệm `java.io.BufferedInputStream` thành 64 KB cho các tệp thường 5‑10 MB; tăng lên 256 KB cho các PDF lớn hơn.  
2. **Giám sát GC** – Sử dụng VisualVM hoặc Java Flight Recorder để theo dõi các khoảng dừng của garbage‑collection trong quá trình so sánh hàng loạt.  
3. **Kết nối pool** – Tái sử dụng các kết nối HTTP khi stream các tệp từ các dịch vụ lưu trữ từ xa.

### Các cân nhắc xử lý đồng thời
Các instance của GroupDocs.Comparison là thread‑safe, vì vậy bạn có thể chạy an toàn nhiều so sánh song song bằng cách sử dụng `ExecutorService`.

```java
// Example pattern for concurrent document comparison
ExecutorService executor = Executors.newFixedThreadPool(4);
// Process multiple comparisons concurrently
```

**Mẹo hiệu năng**: Thực hiện các bài kiểm tra tải với 100 người dùng đồng thời trên tài liệu 200 trang để thiết lập các con số thông lượng thực tế.

### Chiến lược caching
* **Fingerprint tài liệu** – Tạo hash SHA‑256 cho mỗi tệp đến; bỏ qua so sánh nếu hash trùng với cặp đã xử lý trước đó.  
* **Caching kết quả** – Lưu stream so sánh đã tạo trong Redis hoặc CDN cho các yêu cầu lặp lại.  
* **Caching một phần** – Lưu trữ kết quả phân tích trung gian cho các tệp rất lớn để tránh phân tích lại cùng các phần.

## Các thực hành tốt khi tích hợp
### Chiến lược xử lý lỗi
Định nghĩa một bộ xử lý ngoại lệ trung tâm bắt `ComparisonException` và ghi log stack trace cùng một ID liên quan duy nhất.

```java
try {
    // Document comparison logic
} catch (FileNotFoundException e) {
    // Handle missing files gracefully
    log.error("Document not found: {}", e.getMessage());
} catch (IOException e) {
    // Handle stream processing errors
    log.error("Stream processing failed: {}", e.getMessage());
} catch (Exception e) {
    // Handle unexpected errors
    log.error("Unexpected error during comparison: {}", e.getMessage());
}
```

### Giám sát và logging
Theo dõi các chỉ số quan trọng này trong nền tảng quan sát của bạn:

* **Thời gian xử lý** – Thời gian trung bình cho mỗi lần so sánh, phân theo kích thước tài liệu.  
* **Sử dụng bộ nhớ** – Tiêu thụ heap trong thời gian tải cao nhất.  
* **Tỷ lệ lỗi** – Tần suất `ComparisonException` hoặc `OutOfMemoryError`.  
* **Thông lượng** – Số tài liệu được xử lý mỗi phút.

### Quản lý cấu hình
Tách riêng tất cả các cài đặt (đường dẫn giấy phép, kích thước bộ đệm, giá trị timeout) vào `application.yml` hoặc biến môi trường. Sử dụng các profile riêng cho phát triển, kiểm thử và sản xuất.

## Ứng dụng thực tế và các trường hợp sử dụng
### Chỉnh sửa tài liệu hợp tác
Khi nhiều thành viên trong nhóm tải lên các phiên bản mới, so sánh tải lên với bản cơ sở đã lưu để làm nổi bật các bổ sung và xóa bỏ trong thời gian thực.

### Đánh giá tài liệu pháp lý
Các công ty luật có thể thực hiện các so sánh độ nhạy cao trên hợp đồng, đảm bảo mọi thay đổi điều khoản đều được ghi lại và báo cáo.

### Hệ thống quản lý nội dung
Các nền tảng CMS có thể tự động tạo nhật ký thay đổi mỗi khi tác giả cập nhật tài liệu chính sách.

### Phiên bản tài liệu API
So sánh các phiên bản liên tiếp của tài liệu tham khảo API để tự động tạo changelog cho các nhà phát triển.

## Khắc phục các vấn đề thường gặp
* **ClassNotFoundException** – Xác minh rằng phụ thuộc Maven đã được giải quyết đúng và JAR nằm trong classpath.  
* **OutOfMemoryError** – Tăng heap JVM (`-Xmx`) hoặc bật chia đoạn tài liệu qua tùy chọn `ChunkSize`.  
* **Kết quả so sánh không chính xác** – Đảm bảo cả hai tài liệu sử dụng cùng một mã hóa và bất kỳ phông chữ nhúng nào đều có sẵn cho engine.  
* **Hiệu năng chậm trên các tệp lưu trữ trên mạng** – Lưu tệp từ xa vào bộ nhớ cục bộ trong thời gian so sánh, hoặc sử dụng streaming bất đồng bộ.

## Các bước tiếp theo và tính năng nâng cao
Bạn hiện đã có nền tảng vững chắc cho **so sánh tài liệu java** bằng streams. Hãy cân nhắc khám phá các khả năng cấp độ tiếp theo này:

* **Quy tắc phát hiện thay đổi tùy chỉnh** – Định nghĩa các quy tắc chuyên ngành để bỏ qua các thay đổi định dạng không quan trọng.  
* **Xử lý batch** – Xây dựng một microservice nhận danh sách các cặp tài liệu và xử lý chúng song song.  
* **Phân loại tăng cường bằng machine‑learning** – Sử dụng mô hình ML để phân loại các thay đổi (ví dụ: “điều khoản pháp lý được thêm” vs. “sửa lỗi chính tả”).  
* **Phơi bày REST API** – Đóng gói logic so sánh trong một controller Spring Boot để dễ dàng tiêu thụ bởi các ứng dụng front‑end.

## Kết luận
Bạn bây giờ đã biết **cách so sánh tài liệu** trong Java bằng cách sử dụng GroupDocs.Comparison với streams. Phương pháp này cung cấp xử lý thân thiện với bộ nhớ, hoạt động liền mạch với lưu trữ từ xa, và mở rộng để xử lý nhiều người dùng đồng thời. Bắt đầu với ví dụ tối thiểu, sau đó lặp lại hướng tới các tính năng nâng cao phù hợp với yêu cầu dự án của bạn.

## Câu hỏi thường gặp
**Q: Kích thước tài liệu tối đa mà GroupDocs.Comparison có thể xử lý là bao nhiêu?**  
A: Không có giới hạn cứng, nhưng các tài liệu lớn hơn 100 MB sẽ hưởng lợi từ việc tăng kích thước heap JVM và tinh chỉnh bộ đệm stream để tránh `OutOfMemoryError`.

**Q: Tôi có thể so sánh các tài liệu được bảo vệ bằng mật khẩu bằng streams không?**  
A: Có. Cung cấp mật khẩu khi tạo stream nguồn hoặc đích; API sẽ giải mã tệp trước khi so sánh.

**Q: Làm thế nào để tôi xử lý các định dạng tài liệu khác nhau trong cùng một lần so sánh?**  
A: Engine tự động phát hiện định dạng, nhưng để có kết quả tối ưu, hãy chuyển tất cả đầu vào sang một định dạng chung (ví dụ: PDF) trước khi so sánh khi kết hợp các loại.

**Q: Có cần giấy phép cho việc sử dụng trong môi trường sản xuất không?**  
A: Có. Các triển khai sản xuất cần giấy phép GroupDocs.Comparison đầy đủ hoặc tạm thời. Các phiên bản dùng thử miễn phí giới hạn 30 ngày và 20 lần so sánh.

**Q: Tôi có thể tùy chỉnh giao diện của kết quả so sánh không?**  
A: Chắc chắn. Sử dụng `CompareOptions` để đặt màu nổi bật, dấu thay đổi và định dạng đầu ra (PDF, DOCX, HTML, v.v.).

---
**Cập nhật lần cuối:** 2026-08-09  
**Kiểm tra với:** GroupDocs.Comparison 25.2 for Java  
**Tác giả:** GroupDocs  
---

**Tài nguyên bổ sung**

- [Tài liệu GroupDocs.Comparison Java](https://docs.groupdocs.com/comparison/java/)
- [Tham chiếu API Java đầy đủ](https://reference.groupdocs.com/comparison/java/)
- [Bản phát hành GroupDocs](https://releases.groupdocs.com/comparison/java/)
- [Mua giấy phép GroupDocs](https://purchase.groupdocs.com/buy)
- [Bắt đầu dùng thử miễn phí](https://releases.groupdocs.com/comparison/java/)
- [Nhận giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)
- [Diễn đàn GroupDocs](https://forum.groupdocs.com/c/comparison)

## Hướng dẫn liên quan
- [so sánh pdf java – Hướng dẫn So sánh Tài liệu Java – Hướng dẫn đầy đủ về Tải và So sánh Tài liệu](/comparison/java/document-loading/)
- [Cách sử dụng GroupDocs: So sánh Tài liệu Java bằng Streams – Hướng dẫn đầy đủ](/comparison/java/advanced-comparison/java-groupdocs-comparison-multi-stream-document-guide/)
- [GroupDocs Comparison Java – So sánh Tài liệu Word được bảo vệ bằng mật khẩu](/comparison/java/advanced-comparison/groupdocs-compare-protected-word-documents-java/)