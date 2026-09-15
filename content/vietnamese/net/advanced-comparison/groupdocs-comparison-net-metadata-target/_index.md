---
categories:
- Document Comparison
date: '2026-09-15'
description: Tìm hiểu cách bảo tồn metadata trong quá trình so sánh tài liệu bằng
  GroupDocs.Comparison cho .NET. Hướng dẫn từng bước với các ví dụ C#, các thực tiễn
  tốt nhất và các trường hợp sử dụng thực tế.
keywords:
- how to preserve metadata
- GroupDocs.Comparison metadata preservation
- .NET document comparison
- metadata handling in .NET
lastmod: '2026-09-15'
linktitle: Hướng dẫn Bảo tồn Metadata
og_description: Khám phá cách bảo tồn metadata trong quá trình so sánh tài liệu trên
  .NET bằng GroupDocs.Comparison. Thực hiện theo một hướng dẫn chi tiết với các thực
  tiễn tốt nhất, mẹo khắc phục sự cố và các ví dụ thực tế.
og_image_alt: Developer guide showing metadata preservation with GroupDocs.Comparison
  in a .NET application
og_title: Cách bảo tồn metadata với GroupDocs.Comparison trong .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-15'
  description: Learn how to preserve metadata during document comparison using GroupDocs.Comparison
    for .NET. Step‑by‑step guide with C# examples, best practices, and real‑world
    use cases.
  headline: How to preserve metadata with GroupDocs.Comparison in .NET
  type: TechArticle
- description: Learn how to preserve metadata during document comparison using GroupDocs.Comparison
    for .NET. Step‑by‑step guide with C# examples, best practices, and real‑world
    use cases.
  name: How to preserve metadata with GroupDocs.Comparison in .NET
  steps:
  - name: Initialize your comparer object
    text: '`Comparer` is the core class that orchestrates the comparison process.
      It loads the source file, tracks changes, and generates the output. **Why use
      `using` statements?** They automatically dispose of resources, preventing memory
      leaks when processing large documents. Trust me, you’ll thank yourself'
  - name: Add the target document
    text: '`Comparer.Add` registers the file that contains the modifications you want
      to compare against. **Common mistake**: Confusing source and target. Think of
      it this way—source is your “original,” target is your “updated version.”'
  - name: Set the metadata type (the magic happens here)
    text: '`CloneMetadataType` is a property of `ComparisonOptions` that determines
      which document’s metadata is cloned into the result. **What’s happening?** `CloneMetadataType
      = MetadataType.Target` tells GroupDocs.Comparison: “Hey, I want to keep the
      target document’s metadata in my final result.”'
  type: HowTo
- questions:
  - answer: When you add several target files, GroupDocs.Comparison uses the metadata
      from the **first** target document added. Add the document whose metadata you
      want to keep first in the chain.
    question: Can I preserve metadata from multiple target documents when comparing?
  - answer: Only the metadata that exists in the target will be copied to the output.
      Missing fields are simply omitted; the comparison still succeeds.
    question: What happens if the target document lacks some metadata fields?
  - answer: 'LoadOptions specifies settings such as passwords for opening protected
      documents. Use a `LoadOptions` object with the password, then pass it to the
      `Comparer` constructor: ```csharp var loadOptions = new LoadOptions() { Password
      = "your_password" }; using (var comparer = new Comparer(sourceFile, loadOptions))
      { // comparison logic here } ```'
    question: How do I handle password‑protected documents?
  - answer: The current API preserves **all** metadata from the chosen source (Target
      or Source). For granular control you’d need to extract the properties after
      comparison and re‑apply them manually.
    question: Is there a way to preserve only selected metadata properties?
  - answer: Most common business formats—DOCX, PDF, PPTX, XLSX, and many others—support
      metadata preservation. See the official docs for the full list.
    question: Which document formats support metadata preservation?
  type: FAQPage
tags:
- metadata preservation
- GroupDocs.Comparison
- .NET tutorial
- document management
- C# comparison
title: Cách bảo tồn metadata với GroupDocs.Comparison trong .NET
type: docs
url: /vi/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# Cách bảo tồn siêu dữ liệu với GroupDocs.Comparison trong .NET

Trong hướng dẫn này, bạn sẽ học **cách bảo tồn siêu dữ liệu** khi so sánh hai tài liệu bằng GroupDocs.Comparison cho .NET. Bảo tồn siêu dữ liệu là cần thiết cho tuân thủ pháp lý, ghi chép kiểm toán và quy trình làm việc hợp tác, và thư viện cung cấp cho bạn kiểm soát chi tiết về tài liệu nào sẽ giữ lại siêu dữ liệu trong kết quả so sánh.

## Giới thiệu

Bạn đã bao giờ so sánh hai tài liệu mà lại mất các siêu dữ liệu quan trọng trong quá trình không? Bạn không phải là người duy nhất. Khi bạn cần **bảo tồn siêu dữ liệu mục tiêu** trong khi so sánh tài liệu trong một ứng dụng .NET, nhiệm vụ có thể cảm thấy khó khăn—nhưng không nhất thiết phải như vậy.

GroupDocs.Comparison cho .NET cho phép bạn quyết định siêu dữ liệu của tài liệu nào sẽ tồn tại trong kết quả so sánh. Dù bạn đang xây dựng hệ thống quản lý tài liệu, xử lý hợp đồng pháp lý, hay quản lý nội dung hợp tác, bạn luôn muốn siêu dữ liệu từ tài liệu nguồn phù hợp.

## Câu trả lời nhanh
- **“Bảo tồn siêu dữ liệu mục tiêu” có nghĩa là gì?** Nó giữ lại siêu dữ liệu (tác giả, ngày tạo, thuộc tính tùy chỉnh, v.v.) từ tài liệu bạn chỉ định là mục tiêu khi tạo kết quả so sánh.  
- **Phiên bản GroupDocs.Comparison nào được yêu cầu?** Phiên bản 25.4.0 hoặc mới hơn.  
- **Tôi có thể sử dụng với .NET Core không?** Có – .NET Core 2.0+ hoặc .NET Framework 4.6.1+.  
- **Cần giấy phép cho môi trường sản xuất không?** Cần giấy phép thương mại cho môi trường sản xuất; bản dùng thử miễn phí đủ cho việc học.  
- **Tính năng này có hoạt động với PDF và DOCX không?** Có – tất cả các định dạng Office và PDF chính đều hỗ trợ bảo tồn siêu dữ liệu.

## Tại sao việc bảo tồn siêu dữ liệu lại quan trọng

Trước khi đi vào mã, hãy nói về lý do tại sao việc bảo tồn siêu dữ liệu mục tiêu lại quan trọng. Siêu dữ liệu tài liệu không chỉ là “đẹp mắt”—nó thường được yêu cầu pháp lý hoặc quan trọng đối với kinh doanh:

- **Tài liệu pháp lý** – cần giữ lại các dấu hiệu bảo mật luật sư‑khách hàng.  
- **Tệp công ty** – phải giữ các thẻ tuân thủ và chuỗi phê duyệt.  
- **Bài báo học thuật** – ghi nhận tác giả và lịch sử sửa đổi là thiết yếu.  
- **Tài liệu kỹ thuật** – kiểm soát phiên bản và trạng thái xem xét là quan trọng.

Nếu không xử lý đúng, bạn có thể vô tình loại bỏ thông tin đã mất nhiều tháng để thiết lập. Đó là lúc tùy chọn **bảo tồn siêu dữ liệu mục tiêu** tỏa sáng.

## Yêu cầu trước

### Thư viện và phiên bản yêu cầu
- **GroupDocs.Comparison cho .NET**: Phiên bản 25.4.0 hoặc mới hơn (các phiên bản trước có tùy chọn siêu dữ liệu hạn chế).  
- **.NET Framework**: 4.6.1 hoặc cao hơn, hoặc .NET Core 2.0+.

### Cài đặt môi trường
- Visual Studio (hoặc bất kỳ IDE C# nào bạn thích).  
- Kiến thức cơ bản về C# (không quá phức tạp, hứa!).  
- Hai tài liệu mẫu để thử nghiệm (Word *.docx* hoạt động tốt).

### Kiến thức cần thiết
Bạn không cần phải là chuyên gia GroupDocs, nhưng nên thoải mái với:

- Câu lệnh `using` của C# và xử lý tệp.  
- Các khái niệm cơ bản về xử lý tài liệu.  
- Hiểu về siêu dữ liệu (tác giả, tiêu đề, thuộc tính tùy chỉnh, v.v.).

Sẵn sàng? Hãy thiết lập.

## Cài đặt GroupDocs.Comparison cho .NET

Cài đặt GroupDocs.Comparison rất đơn giản, nhưng có một vài lưu ý cần chú ý.

### Các tùy chọn cài đặt

**NuGet Package Manager Console** (phương pháp dễ nhất):  
```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```  

**.NET CLI** (nếu bạn thích dòng lệnh):  
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```  

**Mẹo chuyên nghiệp**: Luôn chỉ định phiên bản để tránh các thay đổi gây lỗi không mong muốn trong dự án của bạn.

### Cách lấy giấy phép

Đây là nơi nhiều nhà phát triển gặp khó khăn ban đầu. GroupDocs.Comparison không miễn phí, nhưng bạn có các tùy chọn:

- **Dùng thử miễn phí** – đầy đủ chức năng trong 30 ngày, hoàn hảo để đánh giá.  
- **Giấy phép tạm thời** – thời gian đánh giá kéo dài nếu bạn cần thêm thời gian.  
- **Giấy phép thương mại** – cho sử dụng trong môi trường sản xuất (có nhiều mức giá).  

Đừng lo về giấy phép ngay bây giờ nếu bạn chỉ đang học—phiên bản dùng thử bao gồm tất cả các tính năng **bảo tồn siêu dữ liệu mục tiêu**.

### Xác minh cài đặt cơ bản

Hãy chắc chắn mọi thứ hoạt động bằng một bài kiểm tra đơn giản:  
```csharp
using System.IO;
using GroupDocs.Comparison;

string sourceFilePath = "source.docx";
string targetFilePath = "target.docx";

// Initialize the Comparer object.
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // Add the target document for comparison.
    comparer.Add(targetFilePath);
}
```  

Nếu đoạn mã này biên dịch không lỗi, bạn đã sẵn sàng. Nếu có lỗi, hãy kiểm tra lại việc cài đặt gói và các câu lệnh `using`.

## Cách bảo tồn siêu dữ liệu mục tiêu

Tải các tệp nguồn và mục tiêu của bạn, sau đó yêu cầu API giữ lại siêu dữ liệu của tệp mục tiêu trong kết quả cuối cùng.

**Câu trả lời trực tiếp (40‑70 từ):**  
Để bảo tồn siêu dữ liệu mục tiêu, khởi tạo một `Comparer` với tài liệu nguồn, thêm tài liệu mục tiêu bằng `Add`, đặt `CloneMetadataType = MetadataType.Target` trên `ComparisonOptions`, và cuối cùng gọi `Compare`. Điều này yêu cầu GroupDocs.Comparison sao chép tác giả, ngày tạo, thuộc tính tùy chỉnh và tất cả các siêu dữ liệu khác từ tệp mục tiêu vào kết quả được tạo.

### Hiểu luồng siêu dữ liệu

Trong một quá trình so sánh điển hình:

1. **Tài liệu nguồn** cung cấp nội dung cơ bản.  
2. **Tài liệu mục tiêu** cung cấp các thay đổi để so sánh.  
3. **Tài liệu đầu ra** kết hợp cả hai, nhưng siêu dữ liệu của tài liệu nào thắng?

Mặc định, GroupDocs.Comparison sử dụng siêu dữ liệu của tài liệu nguồn. Để **bảo tồn siêu dữ liệu mục tiêu**, bạn cần chỉ định rõ ràng cho API.

### Thực hiện từng bước

#### Bước 1: Khởi tạo đối tượng comparer của bạn

`Comparer` là lớp cốt lõi điều phối quá trình so sánh. Nó tải tệp nguồn, theo dõi các thay đổi và tạo ra tệp đầu ra.  
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```  

**Tại sao sử dụng câu lệnh `using`?** Chúng tự động giải phóng tài nguyên, ngăn ngừa rò rỉ bộ nhớ khi xử lý tài liệu lớn. Tin tôi đi, bạn sẽ cảm ơn mình sau khi làm việc với các tệp Word 50 MB.

#### Bước 2: Thêm tài liệu mục tiêu

`Comparer.Add` đăng ký tệp chứa các sửa đổi mà bạn muốn so sánh.  
```csharp
comparer.Add(targetFilePath);
```  

**Nhầm lẫn thường gặp**: Nhầm lẫn nguồn và mục tiêu. Hãy nghĩ như sau—nguồn là “bản gốc,” mục tiêu là “phiên bản cập nhật.”

#### Bước 3: Đặt loại siêu dữ liệu (đây là phần quan trọng)

`CloneMetadataType` là thuộc tính của `ComparisonOptions` xác định siêu dữ liệu của tài liệu nào sẽ được sao chép vào kết quả.  
```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```  

**Điều gì đang xảy ra?** `CloneMetadataType = MetadataType.Target` yêu cầu GroupDocs.Comparison: “Này, tôi muốn giữ siêu dữ liệu của tài liệu mục tiêu trong kết quả cuối cùng.”

## Ví dụ làm việc đầy đủ

Dưới đây là toàn bộ mã trong một chương trình có thể chạy:  
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;

class Program
{
    static void Main(string[] args)
    {
        try
        {
            string sourceFile = "original_document.docx";
            string targetFile = "updated_document.docx";
            string outputFile = "comparison_result.docx";
            
            using (Comparer comparer = new Comparer(sourceFile))
            {
                comparer.Add(targetFile);
                
                // Preserve target document metadata
                comparer.Compare(outputFile, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
                
                Console.WriteLine($"Comparison completed! Check {outputFile}");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error during comparison: {ex.Message}");
        }
    }
}
```  

## Những sai lầm thường gặp cần tránh

- **Vấn đề đường dẫn tệp** – luôn sử dụng đường dẫn đầy đủ hoặc đảm bảo các tệp của bạn nằm trong thư mục làm việc:  
```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```  

- **Quản lý bộ nhớ** – đối với tài liệu lớn, luôn bao bọc các đối tượng `Comparer` trong câu lệnh `using`.  

- **Tương thích phiên bản** – các phiên bản GroupDocs.Comparison khác nhau cung cấp các tùy chọn siêu dữ liệu khác nhau—hãy dùng phiên bản 25.4.0 hoặc mới hơn để có kết quả tốt nhất.

## Các kịch bản siêu dữ liệu nâng cao

### Khi nào nên sử dụng siêu dữ liệu mục tiêu so với nguồn

| Kịch bản | Ưu tiên siêu dữ liệu **mục tiêu** | Ưu tiên siêu dữ liệu **nguồn** |
|----------|-----------------------------------|---------------------------------|
| Cần cập nhật thông tin tác giả | ✅ | ❌ |
| Tài liệu gốc có ưu tiên pháp lý | ❌ | ✅ |
| Thuộc tính tùy chỉnh chỉ được thêm trong tệp mới hơn | ✅ | ❌ |
| Bạn muốn giữ lịch sử của tài liệu “master” | ❌ | ✅ |

### Xử lý nhiều tài liệu mục tiêu

Bạn có thể so sánh với nhiều mục tiêu đồng thời vẫn bảo tồn siêu dữ liệu từ tài liệu mục tiêu đầu tiên bạn thêm:  
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    comparer.Add(targetFilePath1);
    comparer.Add(targetFilePath2);
    comparer.Add(targetFilePath3);
    
    // Metadata will come from the first target document
    comparer.Compare(outputFileName, new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target 
    });
}
```  

## Ứng dụng thực tế và các trường hợp sử dụng

### Quản lý tài liệu pháp lý

Các công ty luật thường cần so sánh các phiên bản hợp đồng trong khi bảo tồn các dấu hiệu siêu dữ liệu cụ thể:  
```csharp
// Preserve client metadata from updated contract
using (Comparer comparer = new Comparer("original_contract.docx"))
{
    comparer.Add("client_revised_contract.docx");
    
    comparer.Compare("final_contract_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Keep client's metadata
    });
}
```  

### Hợp tác học thuật và nghiên cứu

Khi nhiều nhà nghiên cứu hợp tác, bạn muốn bảo tồn thông tin tác giả mới nhất:  
```csharp
// Keep metadata from the researcher's latest submission
using (Comparer comparer = new Comparer("draft_paper.docx"))
{
    comparer.Add("researcher_updates.docx");
    
    comparer.Compare("paper_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Preserve researcher metadata
    });
}
```  

### Quy trình tuân thủ doanh nghiệp

Trong các ngành công nghiệp được quy định, duy trì siêu dữ liệu tuân thủ là rất quan trọng:  
```csharp
// Preserve compliance tags from updated policy document
using (Comparer comparer = new Comparer("old_policy.docx"))
{
    comparer.Add("compliance_approved_policy.docx");
    
    comparer.Compare("policy_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Keep compliance metadata
    });
}
```  

## Khắc phục các vấn đề thường gặp

### Lỗi “File not found”

Vấn đề phổ biến nhất. Gỡ lỗi bằng các kiểm tra rõ ràng:  
```csharp
string sourceFile = "source.docx";

// Always check if files exist before comparison
if (!File.Exists(sourceFile))
{
    Console.WriteLine($"Source file not found: {Path.GetFullPath(sourceFile)}");
    return;
}

// Same for target files
if (!File.Exists(targetFile))
{
    Console.WriteLine($"Target file not found: {Path.GetFullPath(targetFile)}");
    return;
}
```  

### Vấn đề bộ nhớ với tài liệu lớn

Đối với tài liệu lớn hơn 10 MB, hãy xem xét các tối ưu sau:  
```csharp
// Use explicit disposal for large documents
using (var comparer = new Comparer(sourceFile))
{
    comparer.Add(targetFile);
    
    var saveOptions = new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target 
    };
    
    comparer.Compare(outputFile, saveOptions);
    
    // Explicitly clean up
    GC.Collect();
    GC.WaitForPendingFinalizers();
}
```  

### Vấn đề quyền truy cập và cho phép

Khi làm việc với các tệp được bảo vệ hoặc chia sẻ trên mạng:  
```csharp
try
{
    using (var comparer = new Comparer(sourceFile))
    {
        comparer.Add(targetFile);
        comparer.Compare(outputFile, new SaveOptions() 
        { 
            CloneMetadataType = MetadataType.Target 
        });
    }
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine("Access denied. Check file permissions.");
    Console.WriteLine($"Details: {ex.Message}");
}
catch (IOException ex)
{
    Console.WriteLine("File I/O error occurred.");
    Console.WriteLine($"Details: {ex.Message}");
}
```  

## Các cân nhắc về hiệu năng và thực hành tốt nhất

### Quản lý bộ nhớ

GroupDocs.Comparison có thể tiêu thụ tới **300 MB RAM** khi xử lý một PDF 100 trang. Sử dụng câu lệnh `using` để đảm bảo giải phóng và giải phóng bộ nhớ kịp thời.  
```csharp
// Good - automatic resource cleanup
using (var comparer = new Comparer(sourceFile))
{
    // comparison logic here
}

// Bad - potential memory leaks
var comparer = new Comparer(sourceFile);
// ... comparison logic
// comparer.Dispose(); // Easy to forget!
```  

- **Xử lý tài liệu theo lô** – nếu bạn đang so sánh nhiều tệp, hãy xử lý chúng theo nhóm nhỏ để giảm mức sử dụng bộ nhớ.

### Các hoạt động async để cải thiện độ phản hồi

Đối với ứng dụng desktop hoặc web, bao bọc quá trình so sánh trong một phương thức async:  
```csharp
public async Task<bool> CompareDocumentsAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            using (var comparer = new Comparer(source))
            {
                comparer.Add(target);
                comparer.Compare(output, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
                return true;
            }
        }
        catch
        {
            return false;
        }
    });
}
```  

### Hướng dẫn về kích thước tệp

- **Nhỏ (< 1 MB)** – xử lý trực tiếp.  
- **Trung bình (1‑10 MB)** – hiển thị tiến độ để giao diện người dùng phản hồi tốt.  
- **Lớn (> 10 MB)** – luôn sử dụng xử lý async và cân nhắc gọi GC rõ ràng như trên.

## Tích hợp với hệ thống lớn hơn

### Tích hợp ASP.NET Core

Dưới đây là một controller đã sẵn sàng sử dụng, nhận hai tệp tải lên, thực hiện so sánh và trả về kết quả trong khi **bảo tồn siêu dữ liệu mục tiêu**:  
```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentComparisonController : ControllerBase
{
    [HttpPost("compare-with-target-metadata")]
    public async Task<IActionResult> CompareWithTargetMetadata(
        IFormFile sourceFile, 
        IFormFile targetFile)
    {
        var tempSource = Path.GetTempFileName();
        var tempTarget = Path.GetTempFileName();
        var outputPath = Path.GetTempFileName();
        
        try
        {
            // Save uploaded files temporarily
            await sourceFile.CopyToAsync(new FileStream(tempSource, FileMode.Create));
            await targetFile.CopyToAsync(new FileStream(tempTarget, FileMode.Create));
            
            // Perform comparison with target metadata preservation
            using (var comparer = new Comparer(tempSource))
            {
                comparer.Add(tempTarget);
                comparer.Compare(outputPath, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
            }
            
            // Return comparison result
            var resultBytes = await System.IO.File.ReadAllBytesAsync(outputPath);
            return File(resultBytes, "application/vnd.openxmlformats-officedocument.wordprocessingml.document", 
                       "comparison_result.docx");
        }
        finally
        {
            // Clean up temporary files
            if (System.IO.File.Exists(tempSource)) System.IO.File.Delete(tempSource);
            if (System.IO.File.Exists(tempTarget)) System.IO.File.Delete(tempTarget);
            if (System.IO.File.Exists(outputPath)) System.IO.File.Delete(outputPath);
        }
    }
}
```  

## Câu hỏi thường gặp

**H: Tôi có thể bảo tồn siêu dữ liệu từ nhiều tài liệu mục tiêu khi so sánh không?**  
Đ: Khi bạn thêm nhiều tệp mục tiêu, GroupDocs.Comparison sẽ sử dụng siêu dữ liệu từ tài liệu mục tiêu **đầu tiên** được thêm. Hãy thêm tài liệu mà bạn muốn giữ siêu dữ liệu trước tiên trong chuỗi.

**H: Điều gì xảy ra nếu tài liệu mục tiêu thiếu một số trường siêu dữ liệu?**  
Đ: Chỉ những siêu dữ liệu tồn tại trong tài liệu mục tiêu sẽ được sao chép vào đầu ra. Các trường thiếu sẽ bị bỏ qua; quá trình so sánh vẫn thành công.

**H: Làm thế nào để xử lý tài liệu được bảo vệ bằng mật khẩu?**  
Đ: `LoadOptions` chỉ định các cài đặt như mật khẩu để mở tài liệu được bảo vệ.  
Sử dụng một đối tượng `LoadOptions` với mật khẩu, sau đó truyền nó vào hàm khởi tạo của `Comparer`:  
```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```  

**H: Có cách nào để chỉ bảo tồn một số thuộc tính siêu dữ liệu được chọn không?**  
Đ: API hiện tại bảo tồn **tất cả** siêu dữ liệu từ nguồn đã chọn (Target hoặc Source). Để kiểm soát chi tiết, bạn cần trích xuất các thuộc tính sau khi so sánh và áp dụng lại thủ công.

**H: Định dạng tài liệu nào hỗ trợ bảo tồn siêu dữ liệu?**  
Đ: Hầu hết các định dạng kinh doanh phổ biến—DOCX, PDF, PPTX, XLSX và nhiều định dạng khác—hỗ trợ bảo tồn siêu dữ liệu. Xem tài liệu chính thức để biết danh sách đầy đủ.

**H: Truy cập [Diễn đàn Hỗ trợ GroupDocs](https://forum.groupdocs.com/c/comparison) để nhận trợ giúp từ cộng đồng, hoặc liên hệ trực tiếp với bộ phận hỗ trợ của GroupDocs nếu bạn có giấy phép thương mại.**

## Tài nguyên bổ sung

- **Tài liệu chính thức**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **Tham chiếu API**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **Tải phiên bản mới nhất**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **Dùng thử miễn phí**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **Các tùy chọn mua**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)

---

**Cập nhật lần cuối:** 2026-09-15  
**Kiểm tra với:** GroupDocs.Comparison 25.4.0 for .NET  
**Tác giả:** GroupDocs  

## Hướng dẫn liên quan

- [Hướng dẫn GroupDocs Comparison NET - Hướng dẫn đầy đủ về So sánh tài liệu với Siêu dữ liệu](/comparison/net/metadata-management/guide-groupdocs-comparison-net-metadata-setting/)  
- [Cách trích xuất siêu dữ liệu từ kết quả so sánh .NET – Hướng dẫn đầy đủ](/comparison/net/basic-usage/get-document-info-from-result-document/)  
- [So sánh tài liệu .NET - Cách lưu siêu dữ liệu mục tiêu](/comparison/net/loading-and-saving-documents/saving-documents-metadata-target/)