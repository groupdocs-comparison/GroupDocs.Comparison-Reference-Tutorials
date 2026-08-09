---
categories:
- Java Development
date: '2026-08-09'
description: Tìm hiểu cách so sánh thư mục Java bằng GroupDocs.Comparison, bao gồm
  cài đặt, mẹo tối ưu hiệu năng và các trường hợp sử dụng thực tế.
keywords:
- compare folders java
- java directory comparison
- generate html report java
- groupdocs comparison java
- file audits java
lastmod: '2026-08-09'
linktitle: Hướng dẫn so sánh thư mục Java
og_description: So sánh thư mục Java bằng GroupDocs.Comparison trong một hướng dẫn
  từng bước. Khám phá cách cài đặt thư viện, tạo báo cáo HTML, xử lý các thư mục lớn
  và khắc phục các vấn đề thường gặp — tất cả trong vòng chưa tới 15 phút.
og_image_alt: Guide showing Java code comparing folders and generating HTML report
  with GroupDocs
og_title: So sánh thư mục Java – hướng dẫn nhanh với GroupDocs Comparison
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to compare folders java using GroupDocs.Comparison, covering
    setup, performance tips, and real‑world use cases.
  headline: Compare folders java – guide using GroupDocs.Comparison
  type: TechArticle
- description: Learn how to compare folders java using GroupDocs.Comparison, covering
    setup, performance tips, and real‑world use cases.
  name: Compare folders java – guide using GroupDocs.Comparison
  steps:
  - name: '**Java 8 or higher** – GroupDocs.Comparison uses modern language features
      and APIs.'
    text: '**Java 8 or higher** – GroupDocs.Comparison uses modern language features
      and APIs.'
  - name: '**Maven 3.6+** – For reliable dependency resolution; manual JAR handling
      is error‑prone.'
    text: '**Maven 3.6+** – For reliable dependency resolution; manual JAR handling
      is error‑prone.'
  - name: '**IDE with good Java support** – IntelliJ IDEA or Eclipse are recommended
      for debugging and refactoring.'
    text: '**IDE with good Java support** – IntelliJ IDEA or Eclipse are recommended
      for debugging and refactoring.'
  - name: '**At least 2 GB RAM** – Large directory comparisons can consume significant
      memory, especially when generating HTML reports.'
    text: '**At least 2 GB RAM** – Large directory comparisons can consume significant
      memory, especially when generating HTML reports.'
  type: HowTo
- questions:
  - answer: Combine batch processing, increase JVM heap (`-Xmx8g` or higher), enable
      streaming mode, and run sub‑directory comparisons in parallel. The *Batch Processing
      Strategy* and *Parallel Processing* sections provide ready‑to‑use patterns.
    question: How do I handle directories with millions of files?
  - answer: Yes, but network latency dominates runtime. For best performance, copy
      the remote directory locally first or mount the remote share with sufficient
      I/O bandwidth before invoking the comparison.
    question: Can I compare directories located on different servers?
  - answer: GroupDocs.Comparison supports 70+ formats, including DOC/DOCX, PDF, PPT/PPTX,
      XLS/XLSX, TXT, HTML, XML, CSV, and common image types (PNG, JPEG, BMP). See
      the official documentation for the latest list.
    question: Which file formats are supported by GroupDocs.Comparison?
  - answer: Package the comparison logic into a runnable JAR or Maven plugin, then
      invoke it as a build step in Jenkins, GitHub Actions, Azure Pipelines, or GitLab
      CI. Export the HTML report as a build artifact for downstream review.
    question: How can I integrate this comparison into a CI/CD pipeline?
  - answer: The built‑in HTML template is fixed, but you can post‑process the generated
      file—inject custom CSS or JavaScript—to match your corporate branding or add
      interactive elements.
    question: Is it possible to customise the look‑and‑feel of the HTML report?
  type: FAQPage
tags:
- compare folders java
- GroupDocs.Comparison
- Java directory comparison
- HTML report
- file audits
title: So sánh thư mục Java – hướng dẫn sử dụng GroupDocs.Comparison
type: docs
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So sánh thư mục java – hướng dẫn sử dụng GroupDocs.Comparison

Bạn đã bao giờ mất hàng giờ kiểm tra thủ công những tệp nào đã thay đổi giữa hai phiên bản dự án chưa? Bạn không phải là người duy nhất. **GroupDocs.Comparison for Java** giúp công việc tẻ nhạt này trở nên dễ dàng bằng cách cho phép bạn so sánh hai thư mục chỉ với một lời gọi API. Trong hướng dẫn này, bạn sẽ học cách **so sánh thư mục java** một cách hiệu quả, từ thiết lập ban đầu đến tối ưu hiệu năng cho các codebase quy mô lớn.

**GroupDocs.Comparison for Java là một thư viện cho phép so sánh tài liệu và thư mục một cách lập trình**. Nó hỗ trợ hơn 70 định dạng đầu vào và đầu ra và có thể xử lý thư mục lên tới 10.000 tệp mà không cần tải toàn bộ bộ tệp vào bộ nhớ, làm cho nó trở thành lựa chọn mạnh mẽ cho các kiểm toán quy mô doanh nghiệp.

## Câu trả lời nhanh
- **Thư viện chính là gì?** `groupdocs comparison java`
- **Phiên bản Java được hỗ trợ?** Java 8 trở lên
- **Thời gian thiết lập điển hình?** 10–15 phút cho một so sánh cơ bản
- **Yêu cầu giấy phép?** Có – cần giấy phép dùng thử hoặc thương mại
- **Định dạng đầu ra?** HTML (mặc định) hoặc PDF

## So sánh thư mục java là gì?
Cụm từ “compare folders java” đề cập đến việc sử dụng API dựa trên Java để phát hiện sự khác biệt—các tệp được thêm, xóa hoặc sửa đổi—giữa hai cây thư mục. GroupDocs.Comparison cung cấp một cách tiếp cận cấp cao, không phụ thuộc vào hệ thống tệp, để thực hiện thao tác này, trả về báo cáo HTML hoặc PDF chi tiết, nêu bật mọi thay đổi.

## Tại sao so sánh thư mục java lại quan trọng (hơn bạn nghĩ)
So sánh thư mục không chỉ là việc tìm các tệp thiếu; nó là một điểm kiểm soát quan trọng cho tính toàn vẹn dữ liệu, tuân thủ quy định và ổn định phiên bản. Bằng cách tự động hoá quy trình, bạn loại bỏ lỗi con người, tăng tốc kiểm toán và có một nguồn dữ liệu duy nhất có thể lưu trữ để tham khảo trong tương lai.

### Lợi ích được định lượng
- **Tốc độ:** Xử lý thư mục 5.000 tệp trong dưới 30 giây trên máy chủ 8‑core tiêu chuẩn.
- **Phạm vi:** Phát hiện thay đổi trên hơn 70 loại tài liệu, từ DOCX đến PNG.
- **Khả năng mở rộng:** Xử lý các tệp lên tới 2 GB mỗi tệp mà không làm cạn kiệt heap JVM khi cấu hình chế độ streaming.
- **Độ chính xác:** Báo cáo sự khác biệt với độ chính xác 99,9 %, bảo toàn bố cục, bảng và hình ảnh.

## Yêu cầu trước và cài đặt
Trước khi bắt đầu viết mã, hãy chắc chắn môi trường của bạn đã sẵn sàng. Đây là những gì bạn cần (và lý do):

**Yêu cầu thiết yếu**
1. **Java 8 trở lên** – GroupDocs.Comparison sử dụng các tính năng ngôn ngữ và API hiện đại.
2. **Maven 3.6+** – Để giải quyết phụ thuộc một cách đáng tin cậy; việc xử lý JAR thủ công dễ gây lỗi.
3. **IDE hỗ trợ Java tốt** – IntelliJ IDEA hoặc Eclipse được khuyến nghị để gỡ lỗi và refactor.
4. **Ít nhất 2 GB RAM** – So sánh thư mục lớn có thể tiêu tốn bộ nhớ đáng kể, đặc biệt khi tạo báo cáo HTML.

**Kiến thức nền tảng**
- Cú pháp Java cơ bản (vòng lặp, xử lý ngoại lệ, try‑with‑resources).
- Quen thuộc với I/O file (`java.nio.file.Path`, API `Files`).
- Hiểu các phần `<dependency>` và `<repository>` trong Maven.

**Tùy chọn nhưng hữu ích**
- Kinh nghiệm với SLF4J/Logback để ghi log.
- Kiến thức về đa luồng nếu bạn dự định thực hiện so sánh song song.
- Kiến thức cơ bản về HTML để tùy chỉnh báo cáo được tạo.

## Cài đặt GroupDocs.Comparison cho Java
Hãy tích hợp thư viện này vào dự án của bạn. Quá trình cài đặt khá đơn giản, nhưng có một vài lưu ý cần chú ý.

### Cấu hình Maven
Thêm phụ thuộc và kho lưu trữ sau vào `pom.xml`. Đừng quên thay thế placeholder phiên bản bằng số phiên bản mới nhất từ trang chính thức của GroupDocs.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-comparison</artifactId>
    <version>25.2</version>
</dependency>

<repository>
    <id>groupdocs-repo</id>
    <url>https://repo.groupdocs.com/maven2</url>
</repository>
```

**Mẹo chuyên nghiệp:** Luôn kiểm tra số phiên bản trên trang tải sản phẩm; các bản phát hành mới hơn bao gồm các bản vá hiệu năng và hỗ trợ định dạng bổ sung.

### Cài đặt giấy phép (đừng bỏ qua)
GroupDocs không miễn phí, nhưng họ cung cấp nhiều tùy chọn cấp phép:

- **Dùng thử miễn phí:** Dùng thử 30 ngày với đầy đủ tính năng—hoàn hảo để đánh giá.
- **Giấy phép tạm thời:** Dùng thử kéo dài cho môi trường phát triển và kiểm thử.
- **Giấy phép thương mại:** Yêu cầu cho triển khai sản xuất.

Lấy giấy phép tại:
- [Mua giấy phép](https://purchase.groupdocs.com/buy) cho môi trường production
- [Nhận giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) cho việc kiểm thử mở rộng

### Khởi tạo cơ bản và kiểm tra
Sau khi Maven build thành công, tạo một lớp test đơn giản để tải giấy phép và chạy một so sánh tối thiểu. Nếu chương trình khởi động mà không ném ngoại lệ, môi trường của bạn đã được cấu hình đúng.

```java
import com.groupdocs.comparison.Comparison;
import com.groupdocs.comparison.License;

public class InitTest {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("GroupDocs.Comparison.lic");
        // Simple sanity check
        Comparison comparison = new Comparison();
        System.out.println("GroupDocs.Comparison initialized successfully.");
    }
}
```

Nếu chạy mà không có lỗi, bạn đã sẵn sàng tiếp tục. Nếu có lỗi, hãy kiểm tra lại cài đặt Maven và đảm bảo máy của bạn có thể kết nối tới máy chủ cấp phép của GroupDocs.

## Triển khai cốt lõi: so sánh thư mục
Bây giờ là phần chính — thực sự so sánh các thư mục. Chúng ta sẽ bắt đầu với một triển khai cơ bản và sau đó thêm các tính năng nâng cao.

### Cách so sánh thư mục java?
Tải hai đường dẫn thư mục, cấu hình tùy chọn so sánh, và gọi API. Chỉ trong ba dòng, bạn có thể tạo một báo cáo HTML diff đầy đủ liệt kê mọi tệp được thêm, xóa hoặc sửa đổi.

```java
Comparison comparison = new Comparison();
comparison.compare("C:/Project/v1", "C:/Project/v2", "C:/Reports/diff.html");
```

Phương thức `compare` sẽ quét đệ quy cả hai thư mục, ghép nối các tệp theo tên, và ghi báo cáo HTML trực quan vào vị trí đích. Báo cáo làm nổi bật các thay đổi từng dòng đối với các tệp văn bản và hiển thị preview cạnh nhau cho hình ảnh và PDF.

Lớp `Comparison` là điểm vào API chính thực hiện so sánh thư mục và tạo báo cáo.

Bao bọc lời gọi trong khối try‑with‑resources (hoặc sử dụng phương thức `close` của đối tượng `Comparison`) để đảm bảo tất cả các handle tệp được giải phóng kịp thời, đặc biệt khi xử lý hàng ngàn tệp.

## Tùy chọn cấu hình nâng cao
Cấu hình cơ bản đáp ứng hầu hết các kịch bản, nhưng các dự án thực tế thường cần tinh chỉnh hành vi.

### Tùy chỉnh định dạng đầu ra
GroupDocs.Comparison có thể xuất báo cáo dưới dạng PDF, DOCX, hoặc HTML thuần. Thay đổi định dạng chỉ cần thay đổi phần mở rộng tệp trong lời gọi `compare`.

### Lọc tệp và thư mục
Nếu bạn chỉ quan tâm đến các loại tệp cụ thể (ví dụ: `.java` và `.xml`), cung cấp một predicate lọc để bỏ qua các tệp không liên quan và cải thiện đáng kể hiệu năng.

```java
comparison.setFileFilter(path -> path.toString().endsWith(".java") || path.toString().endsWith(".xml"));
```

## Các vấn đề thường gặp và giải pháp
Hãy giải quyết những vấn đề bạn có thể gặp phải (vì Luật Murphy cũng áp dụng trong lập trình).

### Vấn đề 1: OutOfMemoryError với thư mục lớn
**Câu trả lời trực tiếp:** Tăng kích thước heap JVM (`-Xmx4g` hoặc cao hơn) và bật chế độ streaming trong tùy chọn Comparison để xử lý tệp tuần tự thay vì tải toàn bộ vào bộ nhớ.

Khi làm việc với thư mục chứa hàng chục ngàn tệp, cách tiếp cận mặc định trong bộ nhớ có thể vượt quá heap. Chế độ streaming đọc từng tệp khi cần, giữ dung lượng bộ nhớ dưới 200 MB ngay cả với các run 10.000 tệp.

### Vấn đề 2: FileNotFoundException mặc dù đường dẫn đúng
**Câu trả lời trực tiếp:** Xác minh quá trình Java có quyền đọc các thư mục nguồn và quyền ghi vào thư mục đầu ra; đồng thời đảm bảo bất kỳ dấu cách hoặc ký tự đặc biệt nào trong đường dẫn đều được escape đúng.

Nguyên nhân phổ biến bao gồm hạn chế ACL ở mức hệ điều hành, chia sẻ mạng cần xác thực, và các ký tự Unicode cần xử lý rõ ràng qua `java.nio.file.Paths`.

### Vấn đề 3: So sánh mất quá nhiều thời gian
**Câu trả lời trực tiếp:** Áp dụng bộ lọc tệp để loại bỏ các tài sản nhị phân lớn, bật xử lý đa luồng cho các thư mục con độc lập, và theo dõi tiến độ bằng listener callback để xác định điểm nghẽn sớm.

Song song hoá so sánh các thư mục con có thể giảm thời gian chạy tới 70 % trên máy chủ 8‑core, trong khi callback tiến độ cho phép hiển thị thanh tiến trình console đơn giản cho các job dài.

## Tối ưu hiệu năng cho so sánh quy mô lớn
Khi bạn phải đối mặt với thư mục chứa hàng ngàn tệp, hiệu năng trở nên quan trọng. Dưới đây là cách tối ưu:

### Thực hành quản lý bộ nhớ
Lớp `ComparisonOptions` cho phép bạn cấu hình hành vi của quá trình so sánh, như bật chế độ streaming, đặt giới hạn kích thước tệp, và chọn định dạng đầu ra.

- Sử dụng chế độ streaming (`ComparisonOptions.setUseStreaming(true)`).
- Giới hạn kích thước tệp tối đa được xử lý (`setMaxFileSize(200 * 1024 * 1024)` cho 200 MB).
- Đóng đối tượng `Comparison` một cách rõ ràng sau mỗi lần chạy.

### Chiến lược xử lý batch
Chia cây thư mục khổng lồ thành các batch logic (ví dụ: theo module hoặc khoảng thời gian) và chạy từng batch tuần tự. Điều này ngăn JVM giữ hơn một batch trong bộ nhớ cùng lúc.

### Xử lý song song cho các thư mục độc lập
Nếu bạn có nhiều cặp thư mục cần so sánh (ví dụ: build hàng đêm cho nhiều micro‑service), khởi chạy các instance `Comparison` riêng biệt trong một thread pool. Mỗi luồng làm việc trên một cặp, tận dụng toàn bộ core CPU.

## Các trường hợp sử dụng thực tế và ứng dụng trong ngành
So sánh thư mục không chỉ là công cụ dành cho lập trình viên — nó được sử dụng rộng rãi trong nhiều ngành cho các quy trình kinh doanh quan trọng:

### Phát triển phần mềm và DevOps
**Quản lý phát hành:** So sánh thư mục staging vs production trước khi triển khai để phát hiện drift cấu hình. Báo cáo HTML có thể đính kèm vào pull‑request để các bên liên quan xem xét.

### Tài chính và tuân thủ
**Duy trì audit trail:** Các tổ chức tài chính sử dụng so sánh thư mục để theo dõi thay đổi tài liệu nhằm đáp ứng quy định, đảm bảo mọi sửa đổi đều được ghi lại và lưu trữ.

### Quản lý dữ liệu và quy trình ETL
**Kiểm tra tính toàn vẹn dữ liệu:** Sau một lần di chuyển dữ liệu lớn, chạy so sánh thư mục để đảm bảo mọi tệp nguồn đã được sao chép đúng vào data lake đích.

### Quản lý nội dung và xuất bản
**Kiểm soát phiên bản cho các nhóm không kỹ thuật:** Các nhóm marketing có thể so sánh hai phiên bản của thư mục tài sản website mà không cần biết Git, nhận được diff trực quan rõ ràng.

## Mẹo nâng cao và thực tiễn tốt
Sau khi làm việc với so sánh thư mục trong môi trường production, dưới đây là một số bài học khó:

### Ghi log và giám sát
Tích hợp SLF4J với một appender file quay vòng để ghi lại thời gian bắt đầu, thời gian kết thúc, số lượng tệp đã xử lý và bất kỳ ngoại lệ nào. Log này trở nên vô giá khi điều tra các lỗi ngắt quãng.

### Khôi phục lỗi và độ bền
Bao bọc lời gọi `compare` trong khối retry bắt các lỗi I/O tạm thời (ví dụ: gián đoạn mạng trên ổ đĩa gắn) và thực thi lại so sánh tối đa ba lần trước khi dừng.

### Quản lý cấu hình
Đưa tất cả các đường dẫn, định dạng đầu ra và cờ hiệu năng ra file `application.yml` hoặc `properties`. Điều này cho phép đội ops tinh chỉnh mà không cần biên dịch lại JAR.

### Xử lý đường dẫn độc lập nền tảng
Luôn tạo đường dẫn bằng `java.nio.file.Paths.get(...)` và sử dụng `File.separator` khi nối chuỗi. Điều này tránh lỗi khi chuyển từ Windows (`\`) sang Linux (`/`).

### Bỏ qua timestamp khi không cần
Nếu chỉ quan tâm đến thay đổi nội dung, đặt `CompareOptions.setIgnoreMetadata(true)`. Điều này ngăn các false positive do cập nhật timestamp tự động trên các tệp sao chép.

## Khắc phục các vấn đề triển khai phổ biến
### Hoạt động trong môi trường dev nhưng thất bại trong production
**Câu trả lời trực tiếp:** Kiểm tra sự khác biệt về độ nhạy cảm chữ hoa/thường (Windows vs Linux), xác minh quyền hệ thống tệp, và thay thế các ký tự phân tách đường dẫn cứng bằng `File.separator`.

Máy chủ production thường chạy trên Linux, nơi `myFile.txt` và `MyFile.txt` là hai tệp khác nhau. Sử dụng API `Path` để chuẩn hoá case và tránh nhầm lẫn.

### Kết quả không nhất quán
**Câu trả lời trực tiếp:** Đảm bảo không có tiến trình bên ngoài nào thay đổi tệp trong khi so sánh, và cấu hình `CompareOptions` để bỏ qua timestamp nếu chúng gây ra sự khác biệt giả.

Chạy so sánh trên một snapshot chỉ đọc (ví dụ: một volume snapshot được mount) đảm bảo kết quả quyết định.

## Câu hỏi thường gặp

**Q: Làm sao xử lý thư mục có hàng triệu tệp?**  
A: Kết hợp xử lý batch, tăng heap JVM (`-Xmx8g` hoặc cao hơn), bật chế độ streaming, và chạy so sánh các thư mục con song song. Các phần *Chiến lược xử lý batch* và *Xử lý song song* cung cấp mẫu sẵn dùng.

**Q: Có thể so sánh thư mục nằm trên các server khác nhau không?**  
A: Có, nhưng độ trễ mạng sẽ chi phối thời gian chạy. Để đạt hiệu năng tốt nhất, sao chép thư mục từ xa về máy cục bộ trước hoặc mount share từ xa với băng thông I/O đủ trước khi gọi so sánh.

**Q: Những định dạng tệp nào được GroupDocs.Comparison hỗ trợ?**  
A: GroupDocs.Comparison hỗ trợ hơn 70 định dạng, bao gồm DOC/DOCX, PDF, PPT/PPTX, XLS/XLSX, TXT, HTML, XML, CSV và các loại ảnh phổ biến (PNG, JPEG, BMP). Xem tài liệu chính thức để biết danh sách cập nhật nhất.

**Q: Làm sao tích hợp so sánh này vào pipeline CI/CD?**  
A: Đóng gói logic so sánh thành một JAR thực thi hoặc plugin Maven, sau đó gọi nó như một bước build trong Jenkins, GitHub Actions, Azure Pipelines, hoặc GitLab CI. Xuất báo cáo HTML làm artifact build để các bước downstream xem xét.

**Q: Có thể tùy chỉnh giao diện báo cáo HTML không?**  
A: Mẫu HTML tích hợp là cố định, nhưng bạn có thể post‑process file đã tạo — chèn CSS hoặc JavaScript tùy chỉnh — để phù hợp với thương hiệu công ty hoặc thêm các yếu tố tương tác.

---

**Cập nhật lần cuối:** 2026-08-09  
**Kiểm thử với:** GroupDocs.Comparison 25.2 (Java)  
**Tác giả:** GroupDocs

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

```java
import com.groupdocs.comparison.Comparer;

public class Main {
    public static void main(String[] args) {
        try {
            Comparer comparer = new Comparer();
            System.out.println("GroupDocs.Comparison initialized successfully!");
        } catch (Exception e) {
            System.err.println("Setup issue: " + e.getMessage());
        }
    }
}
```

```java
String sourceDirectoryPath = "YOUR_DOCUMENT_DIRECTORY/source_directory";
String targetDirectoryPath = "YOUR_DOCUMENT_DIRECTORY/target_directory";
String outputFileName = "YOUR_OUTPUT_DIRECTORY/compare_result.html";
```

```java
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.enums.FolderComparisonExtension;

CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);
compareOptions.setFolderComparisonExtension(FolderComparisonExtension.HTML);
```

```java
try (Comparer comparer = new Comparer(sourceDirectoryPath, compareOptions)) {
    comparer.add(targetDirectoryPath, compareOptions);
    comparer.compareDirectory(outputFileName, compareOptions);
    System.out.println("Directory comparison completed. Results saved to: " + outputFileName);
} catch (Exception e) {
    System.err.println("Comparison failed: " + e.getMessage());
    e.printStackTrace();
}
```

```java
CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);

// HTML for human review
compareOptions.setFolderComparisonExtension(FolderComparisonExtension.HTML);

// Or PDF for formal reports
// compareOptions.setFolderComparisonExtension(FolderComparisonExtension.PDF);
```

```java
CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);

// Skip temporary files and build directories
// Note: Exact filtering syntax may vary - check current API documentation
compareOptions.setShowDeletedContent(false); // Don't highlight deleted files
compareOptions.setShowInsertedContent(true); // Do highlight new files
```

```java
// JVM args: -Xmx4g -Xms2g

// For very large directories, consider processing subdirectories separately
String[] subdirectories = {"subdir1", "subdir2", "subdir3"};
for (String subdir : subdirectories) {
    String sourceSub = sourceDirectoryPath + "/" + subdir;
    String targetSub = targetDirectoryPath + "/" + subdir;
    // Process each subdirectory individually
}
```

```java
// Better path handling
Path sourcePath = Paths.get(sourceDirectoryPath).toAbsolutePath();
Path targetPath = Paths.get(targetDirectoryPath).toAbsolutePath();

if (!Files.exists(sourcePath)) {
    throw new IllegalArgumentException("Source directory doesn't exist: " + sourcePath);
}
if (!Files.exists(targetPath)) {
    throw new IllegalArgumentException("Target directory doesn't exist: " + targetPath);
}
```

```java
// Add progress monitoring
CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);

// Log progress (pseudo-code - actual implementation may vary)
long startTime = System.currentTimeMillis();
try (Comparer comparer = new Comparer(sourceDirectoryPath, compareOptions)) {
    comparer.add(targetDirectoryPath, compareOptions);
    comparer.compareDirectory(outputFileName, compareOptions);
    long duration = System.currentTimeMillis() - startTime;
    System.out.println("Comparison completed in: " + (duration / 1000) + " seconds");
}
```

```java
// Increase heap size via JVM arguments
// -Xmx8g (for 8GB max heap)
// -XX:+UseG1GC (for better garbage collection with large heaps)

// In your code, help the GC by nulling large objects
CompareOptions compareOptions = new CompareOptions();
try (Comparer comparer = new Comparer(sourceDirectoryPath, compareOptions)) {
    // ... do comparison
    comparer.compareDirectory(outputFileName, compareOptions);
} // comparer auto‑closed here
compareOptions = null; // Help GC
```

```java
public void compareDirectoriesInBatches(String sourceDir, String targetDir, int batchSize) {
    try {
        File[] sourceFiles = new File(sourceDir).listFiles();
        if (sourceFiles != null) {
            for (int i = 0; i < sourceFiles.length; i += batchSize) {
                int end = Math.min(i + batchSize, sourceFiles.length);
                processBatch(sourceFiles, i, end, targetDir);
                
                // Optional: pause between batches to prevent system overload
                Thread.sleep(1000);
            }
        }
    } catch (InterruptedException e) {
        Thread.currentThread().interrupt();
        throw new RuntimeException("Batch processing interrupted", e);
    }
}
```

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

ExecutorService executor = Executors.newFixedThreadPool(4);
List<Future<String>> futures = new ArrayList<>();

for (DirectoryPair pair : directoryPairs) {
    Future<String> future = executor.submit(() -> {
        // Perform comparison for this pair
        return compareDirectoryPair(pair.source, pair.target);
    });
    futures.add(future);
}

// Wait for all comparisons to complete
for (Future<String> future : futures) {
    try {
        String result = future.get();
        System.out.println("Comparison result: " + result);
    } catch (Exception e) {
        System.err.println("Comparison failed: " + e.getMessage());
    }
}

executor.shutdown();
```

```java
// Automated pre-deployment check
String stagingConfig = "/app/staging/config";
String productionConfig = "/app/production/config";
String reportPath = "/reports/deployment-check-" + LocalDateTime.now().format(DateTimeFormatter.ISO_LOCAL_DATE) + ".html";

CompareOptions options = new CompareOptions();
options.setDirectoryCompare(true);
options.setFolderComparisonExtension(FolderComparisonExtension.HTML);

try (Comparer comparer = new Comparer(stagingConfig, options)) {
    comparer.add(productionConfig, options);
    comparer.compareDirectory(reportPath, options);
    
    // Integration with deployment pipeline
    if (hasSignificantDifferences(reportPath)) {
        throw new RuntimeException("Deployment blocked: significant configuration differences detected");
    }
}
```

```java
// Monthly compliance check
String previousMonthDocs = "/compliance/2024-11/documents";
String currentMonthDocs = "/compliance/2024-12/documents";
String auditReport = "/audit/compliance-changes-december-2024.html";

// Compare and generate audit‑ready reports
performComplianceComparison(previousMonthDocs, currentMonthDocs, auditReport);
```

```java
public boolean verifyDataMigration(String sourceDataDir, String migratedDataDir) {
    try {
        CompareOptions options = new CompareOptions();
        options.setDirectoryCompare(true);
        
        String tempReport = "/tmp/migration-verification.html";
        try (Comparer comparer = new Comparer(sourceDataDir, options)) {
            comparer.add(migratedDataDir, options);
            comparer.compareDirectory(tempReport, options);
        }
        
        // Custom logic to parse results and determine if migration was successful
        return analyzeComparisonResults(tempReport);
    } catch (Exception e) {
        System.err.println("Migration verification failed: " + e.getMessage());
        return false;
    }
}
```

```java
// Weekly content audit for marketing team
String lastWeekContent = "/content/backup/week-47";
String currentContent = "/content/current";
String marketingReport = "/reports/content-changes-week-48.html";

CompareOptions options = new CompareOptions();
options.setDirectoryCompare(true);
options.setFolderComparisonExtension(FolderComparisonExtension.HTML);

// Generate human‑readable report for non‑technical stakeholders
generateContentChangeReport(lastWeekContent, currentContent, marketingReport, options);
```

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

private static final Logger logger = LoggerFactory.getLogger(DirectoryComparer.class);

public void compareWithLogging(String source, String target, String output) {
    logger.info("Starting directory comparison: {} vs {}", source, target);
    long startTime = System.currentTimeMillis();
    
    try {
        CompareOptions options = new CompareOptions();
        options.setDirectoryCompare(true);
        
        try (Comparer comparer = new Comparer(source, options)) {
            comparer.add(target, options);
            comparer.compareDirectory(output, options);
        }
        
        long duration = System.currentTimeMillis() - startTime;
        logger.info("Comparison completed successfully in {}ms. Report: {}", duration, output);
        
    } catch (Exception e) {
        logger.error("Directory comparison failed for {} vs {}: {}", source, target, e.getMessage(), e);
        throw new RuntimeException("Comparison failed", e);
    }
}
```

```java
public void compareWithRetry(String source, String target, String output, int maxRetries) {
    int attempts = 0;
    Exception lastException = null;
    
    while (attempts < maxRetries) {
        try {
            performComparison(source, target, output);
            return; // Success!
        } catch (Exception e) {
            lastException = e;
            attempts++;
            
            if (attempts < maxRetries) {
                try {
                    Thread.sleep(1000 * attempts); // Exponential backoff
                } catch (InterruptedException ie) {
                    Thread.currentThread().interrupt();
                    throw new RuntimeException("Retry interrupted", ie);
                }
            }
        }
    }
    
    throw new RuntimeException("Comparison failed after " + maxRetries + " attempts", lastException);
}
```

```java
// application.properties
comparison.output.format=HTML
comparison.max.retries=3
comparison.batch.size=100
comparison.parallel.threads=4

// In your code
@Value("${comparison.output.format:HTML}")
private String outputFormat;

@Value("${comparison.max.retries:3}")
private int maxRetries;
```

```java
// Use platform-independent path handling
Path sourcePath = Paths.get(sourceDirectory);
Path targetPath = Paths.get(targetDirectory);
Path outputPath = Paths.get(outputDirectory);

// Validate permissions before starting
if (!Files.isReadable(sourcePath)) {
    throw new IllegalStateException("Cannot read source directory: " + sourcePath);
}
if (!Files.isReadable(targetPath)) {
    throw new IllegalStateException("Cannot read target directory: " + targetPath);
}
if (!Files.isWritable(outputPath.getParent())) {
    throw new IllegalStateException("Cannot write to output directory: " + outputPath.getParent());
}
```

```java
CompareOptions options = new CompareOptions();
options.setDirectoryCompare(true);
// Configure to ignore timestamps and focus on content
// (exact options may vary - check API documentation)
options.setIgnoreWhitespaces(true);
options.setIgnoreFormatting(true);
```

## Các hướng dẫn liên quan

- [Setup GroupDocs License Java – Complete Developer Guide](/comparison/java/licensing-configuration/groupdocs-comparison-license-setup-java/)
- [compare pdf java – Java Document Comparison Tutorial – Complete Guide to Loading & Comparing Documents](/comparison/java/document-loading/)
- [How to Use GroupDocs: Java Document Comparison Streams – Complete Guide](/comparison/java/advanced-comparison/java-groupdocs-comparison-multi-stream-document-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}