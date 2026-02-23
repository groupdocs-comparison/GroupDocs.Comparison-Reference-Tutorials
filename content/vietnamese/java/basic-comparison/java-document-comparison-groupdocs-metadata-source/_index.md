---
categories:
- Java Development
date: '2026-02-23'
description: Tìm hiểu cách so sánh tài liệu trong Java bằng API GroupDocs.Comparison,
  bao gồm so sánh nhiều tệp và tài liệu được bảo mật bằng mật khẩu. Hướng dẫn từng
  bước với mã nguồn, các thực tiễn tốt nhất và khắc phục sự cố.
keywords: Java document comparison tutorial, GroupDocs Java API guide, compare documents
  in java, java compare multiple files, java compare password protected, Java file
  comparison library, how to compare Word documents in Java
lastmod: '2026-02-23'
linktitle: Java Document Comparison Tutorial
tags:
- document-comparison
- groupdocs
- java-tutorial
- api-integration
title: So sánh tài liệu trong Java – Hướng dẫn đầy đủ API GroupDocs
type: docs
url: /vi/java/basic-comparison/java-document-comparison-groupdocs-metadata-source/
weight: 1
---

# so sánh tài liệu trong java – Hướng dẫn đầy đủ API GroupDocs

## Giới thiệu

Bạn đã bao giờ phải so sánh thủ công hai tài liệu từng dòng một, chỉ để bỏ lỡ những khác biệt quan trọng? Bạn không phải là người duy nhất. **so sánh tài liệu trong java** là một thách thức phổ biến, đặc biệt khi bạn cần bảo toàn siêu dữ liệu, xử lý các tệp được bảo vệ bằng mật khẩu, hoặc so sánh nhiều tệp cùng lúc.

**Thực tế là**: hầu hết các nhà phát triển gặp khó khăn vì họ hoặc tự xây dựng từ đầu (mất rất nhiều thời gian) hoặc dùng các công cụ diff cơ bản mà bỏ qua định dạng, siêu dữ liệu và cài đặt bảo mật. Đó là lúc **GroupDocs.Comparison for Java** xuất hiện.

Trong hướng dẫn toàn diện này, bạn sẽ khám phá cách triển khai so sánh tài liệu mạnh mẽ trong các ứng dụng Java của mình. Chúng tôi sẽ bao phủ mọi thứ từ cài đặt cơ bản đến xử lý siêu dữ liệu nâng cao, cộng thêm các ví dụ thực tế mà bạn có thể sử dụng ngay trong môi trường production. Khi hoàn thành, bạn sẽ biết cách:

- Cài đặt GroupDocs.Comparison trong dự án Java của bạn (rất dễ dàng)  
- **so sánh tài liệu trong java** đồng thời bảo toàn tính toàn vẹn của siêu dữ liệu  
- Xử lý các kịch bản **java compare multiple files** và **java compare password protected**  
- Tối ưu hiệu năng cho việc xử lý tài liệu quy mô lớn  

Sẵn sàng biến việc so sánh tài liệu thành việc nhẹ nhàng trong các ứng dụng Java? Hãy cùng bắt đầu!

## Câu trả lời nhanh
- **Thư viện nào cho phép tôi so sánh tài liệu trong java?** GroupDocs.Comparison for Java  
- **Tôi có thể so sánh nhiều tệp cùng lúc không?** Có – chỉ cần thêm bao nhiêu tài liệu mục tiêu tùy ý  
- **Làm sao xử lý tài liệu được bảo vệ bằng mật khẩu?** Sử dụng `LoadOptions` kèm mật khẩu tài liệu  
- **Có cần giấy phép cho môi trường production không?** Giấy phép GroupDocs hợp lệ sẽ loại bỏ watermark và các giới hạn  
- **Yêu cầu phiên bản Java nào?** JDK 8+, khuyến nghị JDK 11+  

## **so sánh tài liệu trong java** là gì?
So sánh tài liệu trong Java có nghĩa là phát hiện chương trình các khác biệt — thay đổi văn bản, chỉnh sửa định dạng, hoặc cập nhật siêu dữ liệu — giữa hai hoặc nhiều tệp bằng một thư viện hiểu cấu trúc tài liệu. GroupDocs.Comparison trừu tượng hoá độ phức tạp, cung cấp một API đơn giản để tạo tài liệu diff, làm nổi bật mọi thay đổi.

## Tại sao nên dùng GroupDocs.Comparison for Java?
- **Hỗ trợ đa dạng định dạng** – DOCX, PDF, XLSX, PPTX, TXT và nhiều hơn nữa  
- **Xử lý siêu dữ liệu** – chọn siêu dữ liệu nguồn, mục tiêu, hoặc không có siêu dữ liệu cho kết quả  
- **Hỗ trợ mật khẩu** – mở các tệp được bảo vệ mà không cần giải mã thủ công  
- **Hiệu năng mở rộng** – xử lý batch, thực thi async, và thiết kế tiết kiệm bộ nhớ  

## Yêu cầu trước

- **Môi trường Java:** JDK 8+ (khuyến nghị JDK 11+), IDE yêu thích, Maven (hoặc Gradle)  
- **Thư viện GroupDocs.Comparison:** Phiên bản 25.2 trở lên (luôn lấy phiên bản mới nhất)  
- **Giấy phép:** Dùng thử miễn phí, giấy phép tạm thời 30 ngày, hoặc giấy phép thương mại  

## Cài đặt GroupDocs.Comparison trong dự án

### Cấu hình Maven

Đầu tiên – thêm repository và dependency của GroupDocs vào `pom.xml`. Đây là phần mà nhiều tutorial làm phức tạp, nhưng thực tế rất đơn giản:

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

**Mẹo:** Luôn kiểm tra số phiên bản mới nhất trên [trang phát hành của GroupDocs](https://releases.groupdocs.com/comparison/java/). Các phiên bản mới thường bao gồm cải thiện hiệu năng và sửa lỗi giúp bạn tránh được nhiều rắc rối.

### Đặt giấy phép

Đây là điều mà hầu hết các nhà phát triển không nhận ra: bạn có thể bắt đầu thử nghiệm GroupDocs.Comparison ngay lập tức với bản dùng thử miễn phí. Không cần thẻ tín dụng, không ràng buộc.

**Các lựa chọn của bạn:**
1. **Dùng thử miễn phí** – hoàn hảo cho việc thử nghiệm và các dự án nhỏ. Chỉ cần tải về và bắt đầu viết code!  
2. **Giấy phép tạm thời** – cần thời gian đánh giá lâu hơn? Nhận giấy phép tạm thời 30 ngày [tại đây](https://purchase.groupdocs.com/temporary-license/)  
3. **Giấy phép thương mại** – sẵn sàng cho production? Xem bảng giá [tại đây](https://purchase.groupdocs.com/buy)

Bản dùng thử bao gồm mọi tính năng nhưng sẽ thêm watermark vào các tệp đầu ra. Đối với phát triển và thử nghiệm, điều này thường chấp nhận được.

## Triển khai so sánh tài liệu: Hướng dẫn chi tiết

Bây giờ là phần chính! Chúng ta sẽ xây dựng một giải pháp so sánh tài liệu hoàn chỉnh từng bước. Đừng lo – chúng tôi sẽ giải thích không chỉ “cách làm” mà còn “lý do” cho mỗi quyết định.

### Hiểu về nguồn siêu dữ liệu (Rất quan trọng!)

Trước khi bắt đầu code, hãy nói về một vấn đề khiến nhiều nhà phát triển bối rối: nguồn siêu dữ liệu. Khi bạn **so sánh tài liệu trong java**, bạn cần quyết định siêu dữ liệu (tác giả, ngày tạo, thuộc tính tùy chỉnh, v.v.) của tài liệu nào sẽ được bảo toàn trong kết quả.

GroupDocs.Comparison cung cấp ba tùy chọn:
- **SOURCE** – dùng siêu dữ liệu từ tài liệu gốc  
- **TARGET** – dùng siêu dữ liệu từ tài liệu bạn đang so sánh với  
- **NONE** – loại bỏ toàn bộ siêu dữ liệu khỏi kết quả  

Đối với hầu hết các ứng dụng doanh nghiệp, bạn sẽ muốn sử dụng **SOURCE** để duy trì tính nhất quán.

### Triển khai từng bước

Chúng ta sẽ tạo một utility có thể tái sử dụng trong bất kỳ dự án nào.

#### Bước 1: Nhập các lớp cần thiết

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.enums.MetadataType;
import com.groupdocs.comparison.options.save.SaveOptions;
import java.nio.file.Path;
import java.io.IOException;
```

#### Bước 2: Tạo đối tượng Comparer

Đây là nơi phép màu bắt đầu. Lớp `Comparer` là điểm vào chính cho mọi thao tác so sánh:

```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source.docx")) {
    // All our comparison logic goes here
}
```

**Tại sao dùng try‑with‑resources?** Lớp `Comparer` triển khai `AutoCloseable`, nghĩa là nó sẽ tự động giải phóng tài nguyên khi kết thúc. Điều này ngăn ngừa rò rỉ bộ nhớ – rất quan trọng khi xử lý nhiều tài liệu.

#### Bước 3: Thêm tài liệu mục tiêu để so sánh

```java
comparer.add("YOUR_DOCUMENT_DIRECTORY/target1.docx");
```

**Điều thú vị:** bạn thực sự có thể thêm nhiều tài liệu mục tiêu và so sánh chúng tất cả so với nguồn trong một lần thực thi. Chỉ cần gọi `add()` nhiều lần:

```java
comparer.add("YOUR_DOCUMENT_DIRECTORY/target1.docx");
comparer.add("YOUR_DOCUMENT_DIRECTORY/target2.docx");
comparer.add("YOUR_DOCUMENT_DIRECTORY/target3.docx");
```

#### Bước 4: Cấu hình xử lý siêu dữ liệu và thực thi so sánh

Ở đây chúng ta thiết lập nguồn siêu dữ liệu và chạy quá trình so sánh thực tế:

```java
final Path resultPath = comparer.compare("output/comparison_result.docx",
        new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)
                .build());
```

**Điều gì đang xảy ra?** Chúng ta yêu cầu GroupDocs:
1. So sánh tất cả các tài liệu đã thêm với nguồn  
2. Lưu kết quả vào đường dẫn đã chỉ định  
3. Sử dụng siêu dữ liệu của tài liệu **SOURCE** trong kết quả cuối cùng  

### Ví dụ hoàn chỉnh

Hãy gộp lại thành một phương thức bạn có thể dùng ngay:

```java
public class DocumentComparison {
    
    public static Path compareDocumentsWithMetadata(
            String sourcePath, 
            String targetPath, 
            String outputPath) throws IOException {
        
        try (Comparer comparer = new Comparer(sourcePath)) {
            // Add the target document
            comparer.add(targetPath);
            
            // Configure comparison options
            SaveOptions saveOptions = new SaveOptions.Builder()
                    .setCloneMetadataType(MetadataType.SOURCE)
                    .build();
            
            // Execute comparison and return result path
            return comparer.compare(outputPath, saveOptions);
        }
    }
}
```

## Những lỗi thường gặp và cách tránh

Sau khi hỗ trợ hàng trăm nhà phát triển triển khai so sánh tài liệu, tôi đã thấy các vấn đề lặp lại. Dưới đây là những lỗi lớn (và cách khắc phục):

### Vấn đề đường dẫn tệp

**Vấn đề**: `FileNotFoundException` mặc dù tệp tồn tại  
**Giải pháp**: Luôn sử dụng đường dẫn tuyệt đối hoặc giải quyết đúng các đường dẫn tương đối

```java
// Instead of this:
String sourcePath = "documents/source.docx";

// Do this:
String sourcePath = Paths.get("documents", "source.docx").toAbsolutePath().toString();
```

### Vấn đề quản lý bộ nhớ

**Vấn đề**: Lỗi hết bộ nhớ khi so sánh tài liệu lớn  
**Giải pháp**: Tăng kích thước heap JVM và sử dụng quản lý tài nguyên đúng cách

```bash
# Add these JVM arguments when running your application
-Xmx4g -XX:+UseG1GC
```

### Xử lý siêu dữ liệu không đúng

**Vấn đề**: Mất siêu dữ liệu quan trọng trong quá trình so sánh  
**Giải pháp**: Luôn đặt rõ loại siêu dữ liệu – đừng dựa vào giá trị mặc định

```java
// Always be explicit about metadata handling
SaveOptions saveOptions = new SaveOptions.Builder()
        .setCloneMetadataType(MetadataType.SOURCE)  // Be explicit!
        .build();
```

### Lỗi cấu hình giấy phép

**Vấn đề**: Watermark xuất hiện trong môi trường production  
**Giải pháp**: Xác minh giấy phép đã được tải đúng trước khi tạo đối tượng `Comparer`

```java
// Load license at application startup
License license = new License();
license.setLicense("path/to/your/license.lic");
```

## Thực hành tốt cho môi trường production

Dựa trên kinh nghiệm thực tế, dưới đây là các thực hành giúp giải pháp của bạn trở nên production‑ready:

### Xử lý lỗi có ý nghĩa

Đừng chỉ bắt ngoại lệ – hãy xử lý chúng một cách có ý nghĩa:

```java
public ComparisonResult compareDocuments(String source, String target) {
    try (Comparer comparer = new Comparer(source)) {
        comparer.add(target);
        Path result = comparer.compare("output.docx", 
            new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)
                .build());
        
        return new ComparisonResult(true, result.toString(), null);
        
    } catch (IOException e) {
        logger.error("File access error during comparison", e);
        return new ComparisonResult(false, null, "Unable to access document files");
        
    } catch (Exception e) {
        logger.error("Unexpected error during document comparison", e);
        return new ComparisonResult(false, null, "Document comparison failed");
    }
}
```

### Tối ưu hiệu năng

Đối với các kịch bản khối lượng lớn, hãy cân nhắc các tối ưu sau:

1. **Tái sử dụng đối tượng `Comparer`** khi có thể (nhưng cần chú ý tới tính thread‑safety)  
2. **Xử lý tài liệu theo batch** để tránh quá tải tài nguyên hệ thống  
3. **Sử dụng xử lý bất đồng bộ** cho các tài liệu lớn  
4. **Giám sát việc sử dụng bộ nhớ** và điều chỉnh cài đặt JVM cho phù hợp  

### Các cân nhắc bảo mật

Khi làm việc với tài liệu nhạy cảm:

- **Xác thực loại tệp** trước khi xử lý  
- **Triển khai kiểm soát truy cập** thích hợp  
- **Xóa ngay các tệp tạm** sau khi sử dụng  
- **Xem xét mã hoá** kết quả so sánh  

## Ứng dụng thực tế và các trường hợp sử dụng

Hãy xem cách các nhà phát triển đang áp dụng GroupDocs.Comparison trong môi trường production:

### Đánh giá tài liệu pháp lý

Các công ty luật dùng so sánh tài liệu để theo dõi thay đổi trong hợp đồng và thỏa thuận pháp lý. Tính năng bảo toàn siêu dữ liệu rất quan trọng vì họ cần duy trì nguồn gốc tài liệu.

```java
// Typical legal document comparison workflow
public void reviewContractChanges(String originalContract, String revisedContract) {
    try (Comparer comparer = new Comparer(originalContract)) {
        comparer.add(revisedContract);
        
        SaveOptions options = new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)  // Preserve original metadata
                .build();
        
        Path result = comparer.compare("contract_review.docx", options);
        
        // Send result to legal team for review
        notifyLegalTeam(result);
    }
}
```

### Hệ thống quản lý nội dung (CMS)

Các nền tảng CMS dùng so sánh tài liệu để kiểm soát phiên bản và theo dõi thay đổi:

```java
public class CMSDocumentVersioning {
    
    public VersionComparisonResult compareVersions(
            DocumentVersion current, 
            DocumentVersion previous) {
        
        try (Comparer comparer = new Comparer(current.getFilePath())) {
            comparer.add(previous.getFilePath());
            
            String outputName = String.format("comparison_%s_vs_%s.docx", 
                current.getVersionNumber(), 
                previous.getVersionNumber());
            
            Path result = comparer.compare(outputName, 
                new SaveOptions.Builder()
                    .setCloneMetadataType(MetadataType.SOURCE)
                    .build());
            
            return new VersionComparisonResult(result, current, previous);
        }
    }
}
```

### Phân tích tài liệu tài chính

Các tổ chức tài chính sử dụng công cụ này cho tuân thủ quy định và tạo dấu vết kiểm toán:

```java
public AuditResult auditFinancialDocument(String originalReport, String submittedReport) {
    // Compare submitted report against original
    // Metadata preservation is critical for audit compliance
    try (Comparer comparer = new Comparer(originalReport)) {
        comparer.add(submittedReport);
        
        Path auditResult = comparer.compare("audit_comparison.docx",
            new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)
                .build());
        
        return generateAuditReport(auditResult);
    }
}
```

## Tối ưu hiệu năng và mở rộng quy mô

Khi bạn sẵn sàng xử lý khối lượng tài liệu lớn, các chiến lược sau sẽ giúp ứng dụng luôn phản hồi nhanh:

### Quản lý bộ nhớ

Các tài liệu lớn có thể nhanh chóng tiêu thụ bộ nhớ. Đây là cách xử lý hiệu quả:

```java
public class OptimizedDocumentProcessor {
    
    private final ExecutorService executor = Executors.newFixedThreadPool(
        Runtime.getRuntime().availableProcessors());
    
    public CompletableFuture<Path> compareDocumentsAsync(
            String source, 
            String target, 
            String output) {
        
        return CompletableFuture.supplyAsync(() -> {
            try (Comparer comparer = new Comparer(source)) {
                comparer.add(target);
                return comparer.compare(output, 
                    new SaveOptions.Builder()
                        .setCloneMetadataType(MetadataType.SOURCE)
                        .build());
            }
        }, executor);
    }
}
```

### Xử lý batch

Đối với việc so sánh nhiều tài liệu, xử lý batch là người bạn đồng hành:

```java
public List<ComparisonResult> processBatch(List<DocumentPair> documentPairs) {
    return documentPairs.parallelStream()
        .map(this::compareDocumentPair)
        .collect(Collectors.toList());
}

private ComparisonResult compareDocumentPair(DocumentPair pair) {
    try (Comparer comparer = new Comparer(pair.getSourcePath())) {
        comparer.add(pair.getTargetPath());
        Path result = comparer.compare(pair.getOutputPath(),
            new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)
                .build());
        return new ComparisonResult(pair, result, true);
    } catch (Exception e) {
        return new ComparisonResult(pair, null, false, e.getMessage());
    }
}
```

## Hướng dẫn khắc phục sự cố

Khi có lỗi (và chúng đôi khi xảy ra), đây là danh sách kiểm tra để debug:

### Lỗi “Comparison Failed”

**Nguyên nhân phổ biến nhất:**
1. Định dạng tệp không được hỗ trợ  
2. Tài liệu nguồn bị hỏng  
3. Bộ nhớ không đủ  
4. Vấn đề quyền truy cập tệp  

**Các bước debug:**

```java
// Add comprehensive logging to identify the issue
logger.debug("Starting comparison: source={}, target={}", sourcePath, targetPath);

try (Comparer comparer = new Comparer(sourcePath)) {
    logger.debug("Comparer initialized successfully");
    
    comparer.add(targetPath);
    logger.debug("Target document added successfully");
    
    Path result = comparer.compare(outputPath, saveOptions);
    logger.info("Comparison completed successfully: result={}", result);
    
    return result;
} catch (Exception e) {
    logger.error("Comparison failed", e);
    throw new DocumentComparisonException("Failed to compare documents", e);
}
```

### Vấn đề hiệu năng

Nếu quá trình so sánh mất quá nhiều thời gian:

1. **Kiểm tra kích thước tài liệu** – các tệp trên 100 MB có thể cần xử lý đặc biệt  
2. **Giám sát bộ nhớ** – tăng heap nếu cần  
3. **Kiểm tra hiệu năng I/O** – lưu trữ chậm có thể là nút thắt  
4. **Xem xét định dạng tài liệu** – một số định dạng phức tạp hơn để xử lý  

### Rò rỉ bộ nhớ

Dấu hiệu có thể có rò rỉ bộ nhớ:

- Hiệu năng ứng dụng giảm dần theo thời gian  
- `OutOfMemoryError` sau khi xử lý nhiều tài liệu  
- Hoạt động garbage collection cao  

**Giải pháp**: Luôn dùng try‑with‑resources và theo dõi ứng dụng bằng các công cụ profiling.

## Xử lý tệp được bảo vệ bằng mật khẩu

Nếu bạn cần **java compare password protected** tài liệu, hãy dùng `LoadOptions` khi mở nguồn hoặc mục tiêu:

```java
LoadOptions loadOptions = new LoadOptions("your_password");
try (Comparer comparer = new Comparer("protected_document.docx", loadOptions)) {
    // Process password‑protected document
}
```

## Cách java compare password protected documents

Các tệp được bảo vệ bằng mật khẩu phổ biến trong các ngành có quy định nghiêm ngặt. Bằng cách truyền mật khẩu qua `LoadOptions`, bạn giữ luồng so sánh không thay đổi đồng thời cho phép thư viện giải mã tệp một cách an toàn. Nhớ không bao giờ hard‑code mật khẩu; lưu chúng trong vault an toàn hoặc biến môi trường và truyền vào lúc runtime.

## Cách xử lý tài liệu lớn java

Khi tài liệu vượt vài trăm megabyte, bạn có thể gặp chậm trễ hoặc tiêu thụ bộ nhớ cao. Để giảm thiểu:

- **Tăng heap JVM** (`-Xmx`), đặc biệt cho các job batch.  
- **Bật streaming** nếu có – GroupDocs.Comparison đã xử lý tệp theo khối, nhưng bạn cũng có thể giảm áp lực bộ nhớ bằng cách không tải toàn bộ tệp vào bộ nhớ.  
- **Chạy so sánh bất đồng bộ** (xem ví dụ async ở trên) để UI luôn phản hồi.  
- **Chia các PDF rất lớn** thành các phần logic trước khi so sánh nếu logic nghiệp vụ cho phép.

## Tích hợp với Spring Boot

Đối với các nhà phát triển xây dựng microservice, hãy gói logic so sánh trong một Spring service bean:

```java
@Service
public class DocumentComparisonService {
    
    public ComparisonResult compareDocuments(String source, String target) {
        try (Comparer comparer = new Comparer(source)) {
            comparer.add(target);
            Path result = comparer.compare("output.docx",
                new SaveOptions.Builder()
                    .setCloneMetadataType(MetadataType.SOURCE)
                    .build());
            return new ComparisonResult(result);
        }
    }
}
```

## Câu hỏi thường gặp

**Hỏi:** Có thể so sánh hơn hai tài liệu cùng lúc không?  
**Đáp:** Chắc chắn! Thêm nhiều tài liệu mục tiêu bằng `comparer.add()` trước khi thực thi so sánh.

**Hỏi:** GroupDocs.Comparison hỗ trợ những định dạng tệp nào?  
**Đáp:** Hỗ trợ DOCX, PDF, XLSX, PPTX, TXT và nhiều định dạng khác. Xem danh sách đầy đủ trong tài liệu chính thức.

**Hỏi:** Làm sao xử lý tài liệu được bảo vệ bằng mật khẩu?  
**Đáp:** Sử dụng lớp `LoadOptions` để cung cấp mật khẩu khi tạo đối tượng `Comparer` (xem ví dụ ở trên).

**Hỏi:** GroupDocs.Comparison có thread‑safe không?  
**Đáp:** Một đối tượng `Comparer` không thread‑safe, nhưng bạn có thể tạo nhiều đối tượng và chạy chúng song song trong các luồng khác nhau.

**Hỏi:** Làm sao cải thiện hiệu năng cho tài liệu lớn?  
**Đáp:** Tăng heap JVM (`-Xmx`), xử lý bất đồng bộ, batch, và tái sử dụng đối tượng `Comparer` khi thích hợp.

## Tài nguyên bổ sung

- [Tài liệu GroupDocs.Comparison](https://docs.groupdocs.com/comparison/java/) – tham chiếu API chi tiết và các ví dụ  
- [Diễn đàn cộng đồng GroupDocs](https://forum.groupdocs.com/) – nhận hỗ trợ từ các nhà phát triển khác  

---

**Cập nhật lần cuối:** 2026-02-23  
**Kiểm thử với:** GroupDocs.Comparison 25.2  
**Tác giả:** GroupDocs  

---