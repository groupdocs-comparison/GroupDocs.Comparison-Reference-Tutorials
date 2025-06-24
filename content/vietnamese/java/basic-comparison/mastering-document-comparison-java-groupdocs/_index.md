---
"date": "2025-05-05"
"description": "Tìm hiểu cách tự động so sánh tài liệu với độ chính xác bằng GroupDocs.Comparison cho Java. Tùy chỉnh kiểu, điều chỉnh độ nhạy và bỏ qua tiêu đề/chân trang một cách dễ dàng."
"title": "So sánh tài liệu chính trong Java bằng API GroupDocs.Comparison"
"url": "/vi/java/basic-comparison/mastering-document-comparison-java-groupdocs/"
"weight": 1
---

# Làm chủ việc so sánh tài liệu trong Java bằng API GroupDocs.Comparison

## Giới thiệu

Bạn có thấy mệt mỏi khi phải so sánh tài liệu theo cách thủ công không? Cho dù là xác định những thay đổi trong tiêu đề, chân trang hay nội dung, việc so sánh tài liệu có thể là một nhiệm vụ khó khăn. Thư viện GroupDocs.Comparison for Java tự động hóa và cải thiện quy trình này một cách chính xác và dễ dàng.

Hướng dẫn toàn diện này sẽ hướng dẫn bạn cách tận dụng GroupDocs.Comparison trong Java để tùy chỉnh kiểu so sánh tài liệu, điều chỉnh cài đặt độ nhạy, bỏ qua so sánh tiêu đề/chân trang, đặt kích thước giấy đầu ra, v.v. Đến cuối hướng dẫn này, bạn sẽ có thể sắp xếp hợp lý quy trình làm việc của mình một cách hiệu quả.

**Những gì bạn sẽ học được:**
- Bỏ qua phần đầu trang và chân trang khi so sánh tài liệu.
- Tùy chỉnh các thay đổi bằng cách điều chỉnh kiểu dáng.
- Điều chỉnh độ nhạy so sánh để phân tích chi tiết.
- Thiết lập kích thước giấy đầu ra trong ứng dụng Java.
- Triển khai các tính năng này vào các tình huống thực tế.

Đảm bảo bạn có đủ các điều kiện tiên quyết cần thiết trước khi bắt đầu thực hành.

## Điều kiện tiên quyết

Để bắt đầu sử dụng GroupDocs.Comparison cho Java, hãy đảm bảo bạn có những điều sau:
1. **Bộ phát triển Java (JDK):** Đảm bảo JDK được cài đặt trên máy của bạn. Bất kỳ phiên bản nào trên 8 đều đủ.
2. **Chuyên gia:** Hướng dẫn này giả định rằng bạn đang sử dụng Maven để quản lý các phụ thuộc của dự án.
3. **Thư viện GroupDocs.Comparison:**
   - Thêm phụ thuộc sau vào `pom.xml`:

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
4. **Giấy phép:** Nhận bản dùng thử miễn phí, giấy phép tạm thời hoặc mua phiên bản đầy đủ từ GroupDocs.

Với những thiết lập này, bạn đã sẵn sàng để bắt đầu triển khai các tính năng so sánh tài liệu trong ứng dụng Java của mình.

## Thiết lập GroupDocs.Comparison cho Java

Đảm bảo rằng môi trường của chúng ta được cấu hình đúng:

### Cài đặt qua Maven

Thêm đoạn mã XML ở trên vào dự án của bạn `pom.xml`Bước này đảm bảo kho lưu trữ và sự phụ thuộc cần thiết được Maven nhận dạng. 

### Mua lại giấy phép
- **Dùng thử miễn phí:** Tải xuống phiên bản dùng thử từ [Tải xuống GroupDocs](https://releases.groupdocs.com/comparison/java/).
- **Giấy phép tạm thời:** Yêu cầu cấp giấy phép tạm thời thông qua [Hỗ trợ GroupDocs](https://purchase.groupdocs.com/temporary-license/) để đánh giá đầy đủ các tính năng.
- **Mua:** Để sử dụng lâu dài, hãy mua giấy phép qua [Mua GroupDocs](https://purchase.groupdocs.com/buy).

Sau khi lấy và thiết lập tệp giấy phép theo tài liệu của GroupDocs, hãy khởi tạo GroupDocs.Comparison như sau:

```java
// Ví dụ khởi tạo cơ bản
com.groupdocs.comparison.License license = new com.groupdocs.comparison.License();
license.setLicense("path/to/your/license/file.lic");
```

## Hướng dẫn thực hiện

### Tính năng 1: Bỏ qua so sánh Header/Footer

**Tổng quan:** Tiêu đề và chân trang thường chứa thông tin như số trang hoặc tiêu đề tài liệu, những thông tin này có thể không liên quan đến việc so sánh thay đổi nội dung.

#### Thiết lập tùy chọn

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import java.io.FileOutputStream;

public class IgnoreHeaderFooterExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/IgnoreHeaderFooter_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_with_footer.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target_with_footer.docx");

            // Đặt tùy chọn so sánh để bỏ qua phần đầu trang và phần chân trang
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setHeaderFootersComparison(false)
                    .build();

            final Path resultPath = comparer.compare(resultStream, new SaveOptions(), compareOptions);
        }
    }
}
```

#### Giải thích
- **`CompareOptions.Builder().setHeaderFootersComparison(false)`**:Thiết lập này hướng dẫn thư viện bỏ qua việc so sánh phần đầu trang và phần chân trang.
- **`try-with-resources`:** Đảm bảo tất cả các luồng đều được đóng lại đúng cách sau khi sử dụng.

### Tính năng 2: Thiết lập kích thước giấy đầu ra

**Tổng quan:** Tùy chỉnh kích thước giấy đầu ra là rất quan trọng để tạo ra các tài liệu thân thiện với máy in. Sau đây là cách bạn có thể điều chỉnh trong quá trình so sánh tài liệu.

#### Các bước thực hiện

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.enums.PaperSize;

public class SetOutputPaperSizeExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/SetOutputPaperSize_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // Đặt kích thước giấy là A6
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setPaperSize(PaperSize.A6)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Giải thích
- **`CompareOptions.Builder().setPaperSize(PaperSize.A6)`**: Đặt kích thước giấy đầu ra thành A6.

### Tính năng 3: Điều chỉnh độ nhạy so sánh

**Tổng quan:** Tinh chỉnh độ nhạy so sánh giúp xác định ngay cả những thay đổi nhỏ. Sau đây là cách bạn có thể điều chỉnh:

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;

public class AdjustComparisonSensitivityExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/AdjustComparisonSensitivity_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // Đặt độ nhạy thành 100
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setSensitivityOfComparison(100)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Giải thích
- **`CompareOptions.Builder().setSensitivityOfComparison(100)`**: Điều chỉnh mức độ nhạy cảm để phát hiện những thay đổi.

### Tính năng 4: Tùy chỉnh Thay đổi Kiểu (Sử dụng Luồng)

**Tổng quan:** Phân biệt giữa văn bản được chèn, xóa và thay đổi giúp việc so sánh trực quan hơn. Sau đây là cách bạn tùy chỉnh kiểu bằng luồng:

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.save.SaveOptions;
import com.groupdocs.comparison.options.style.StyleSettings;

import java.awt.Color;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;

public class CustomizeChangesStylesStreamExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/CustomizeChangesStylesStream_result.docx";

        try (InputStream sourceFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source_word.docx");
             InputStream targetFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");
             OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer(sourceFile)) {

            comparer.add(targetFile);

            // Tùy chỉnh thay đổi kiểu dáng
            StyleSettings insertedStyle = new StyleSettings();
            insertedStyle.setHighlightColor(Color.GREEN); // Màu xanh lá cây cho phần chèn
            StyleSettings deletedStyle = new StyleSettings();
            deletedStyle.setHighlightColor(Color.RED); // Màu đỏ để xóa
            StyleSettings changedStyle = new StyleSettings();
            changedStyle.setHighlightColor(Color.BLUE); // Màu xanh cho những thay đổi

            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setInsertedItemStyle(insertedStyle)
                    .setDeletedItemStyle(deletedStyle)
                    .setChangedItemStyle(changedStyle)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Giải thích
- **Cài đặt phong cách tùy chỉnh**: Sử dụng `StyleSettings` để xác định màu nổi bật cho phần chèn (xanh lá cây), phần xóa (đỏ) và phần thay đổi (xanh lam).
- **`CompareOptions.Builder()`:** Áp dụng các kiểu này trong quá trình so sánh.

## Phần kết luận

Bằng cách tận dụng GroupDocs.Comparison cho Java, bạn có thể tự động so sánh tài liệu với độ chính xác. Hướng dẫn này đề cập đến cách bỏ qua tiêu đề/chân trang, đặt kích thước giấy đầu ra, điều chỉnh độ nhạy và tùy chỉnh các kiểu thay đổi. Việc triển khai các tính năng này sẽ hợp lý hóa quy trình làm việc của bạn và nâng cao khả năng phân tích tài liệu trong các ứng dụng Java.

## Câu hỏi thường gặp

### 1. Tôi có thể bỏ qua phần đầu trang và chân trang khi so sánh trong GroupDocs cho Java không?  

Có, sử dụng `setHeaderFootersComparison(false)` TRONG `CompareOptions` để loại trừ phần đầu trang và phần chân trang khỏi mục so sánh.

### 2. Làm thế nào để thiết lập kích thước trang in đầu ra trong Java bằng GroupDocs?  

Áp dụng `setPaperSize(PaperSize.A6)` hoặc các kích thước khác trong `CompareOptions` để tùy chỉnh kích thước giấy của tài liệu cuối cùng.

### 3. Có thể tinh chỉnh độ nhạy so sánh được không?  

Có, sử dụng `setSensitivityOfComparison()` TRONG `CompareOptions` để điều chỉnh độ nhạy, phát hiện những thay đổi nhỏ hoặc lớn cho phù hợp.

### 4. Tôi có thể định dạng văn bản được chèn, xóa và thay đổi trong khi so sánh không?  

Hoàn toàn, tùy chỉnh kiểu dáng thông qua `StyleSettings` cho các loại thay đổi khác nhau và áp dụng chúng trong `CompareOptions`.

### 5. Cần có những điều kiện tiên quyết nào để bắt đầu sử dụng GroupDocs Comparison trong Java?  

Cài đặt JDK, quản lý các phần phụ thuộc bằng Maven, xin giấy phép và thêm thư viện GroupDocs.Comparison vào dự án của bạn.