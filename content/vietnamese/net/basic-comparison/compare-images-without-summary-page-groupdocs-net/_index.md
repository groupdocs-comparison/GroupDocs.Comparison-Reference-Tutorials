---
categories:
- Image Processing
date: '2026-05-31'
description: Tìm hiểu cách so sánh hình ảnh trong .NET bằng GroupDocs.Comparison đồng
  thời tắt trang tóm tắt. Hướng dẫn này bao gồm cài đặt, mã nguồn, mẹo hiệu năng và
  các trường hợp sử dụng thực tế.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: So sánh hình ảnh .NET không có trang tóm tắt
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  headline: How to Compare Images in .NET – Skip Summary Page
  type: TechArticle
- description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  name: How to Compare Images in .NET – Skip Summary Page
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the gateway to all comparison operations. It implements
      `IDisposable`, so wrapping it in a `using` block guarantees that file handles
      and unmanaged memory are released promptly, even if an exception is thrown.
  - name: Configure CompareOptions for No Summary
    text: Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This
      flag tells the engine to skip the creation of the default HTML report, which
      is the primary source of extra I/O in image‑only scenarios.
  - name: Add Target Image(s) for Comparison
    text: You can call `Add()` multiple times to compare one source against several
      targets in a single batch. Each call can receive its own `CompareOptions` if
      you need per‑image customizations.
  - name: Execute Comparison and Save Results
    text: '`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`.
      The result contains a `Stream` with the diff image, which you can save directly
      to disk, send over a network, or embed in a UI component.'
  type: HowTo
- questions:
  - answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
    question: What is the main advantage of skipping the summary page?
  - answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
    question: Can I still retrieve detailed change metadata without a summary page?
  - answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
    question: Which image formats are supported?
  - answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
    question: How should I handle very large images (e.g., >20 MB)?
  - answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
    question: Is this approach safe for multi‑threaded applications?
  type: FAQPage
tags:
- dotnet
- image-comparison
- groupdocs
- csharp
title: Cách so sánh hình ảnh trong .NET – Bỏ qua trang tóm tắt
type: docs
url: /vi/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Cách so sánh hình ảnh trong .NET – Bỏ qua trang tóm tắt

Khi bạn cần **cách so sánh hình ảnh** một cách lập trình trong ứng dụng .NET, điều cuối cùng bạn muốn là một trang tóm tắt bổ sung làm lãng phí thời gian và dung lượng lưu trữ. Dù bạn đang xây dựng một dây chuyền kiểm soát chất lượng, một quy trình quản lý nội dung, hoặc một bộ kiểm thử hồi quy trực quan tự động, việc bỏ qua trang tóm tắt có thể giảm vài giây cho mỗi lần chạy và giữ dung lượng đĩa gọn nhẹ.

Trong tutorial này bạn sẽ học cách sử dụng **GroupDocs.Comparison for .NET** để so sánh hai hình ảnh một cách hiệu quả, cấu hình thư viện để tắt việc tạo trang tóm tắt, và áp dụng các mẹo tối ưu hiệu năng. Chúng tôi cũng sẽ khám phá lý do tại sao điều này quan trọng, khi nào nên dùng, và cách tránh các lỗi thường gặp.

## Câu trả lời nhanh
- **Cách nhanh nhất để so sánh hình ảnh mà không có trang tóm tắt là gì?** Sử dụng `Comparer` với `CompareOptions` và đặt `GenerateSummaryPage = false`.  
- **Thư viện nào hỗ trợ tính năng này ngay từ đầu?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Tôi có cần giấy phép không?** Có, cần giấy phép thương mại cho môi trường production; dùng thử miễn phí cho phát triển.  
- **Tôi có thể so sánh hơn hai hình ảnh cùng lúc không?** Chắc chắn – gọi `Add()` nhiều lần trước khi `Compare()`.  
- **Phương pháp này có phù hợp cho các job batch quy mô lớn không?** Có, khi kết hợp với xử lý batch và quản lý bộ nhớ hợp lý.

## GroupDocs.Comparison là gì?
`GroupDocs.Comparison` là một thư viện .NET phát hiện sự khác biệt trực quan giữa tài liệu và hình ảnh, tạo ra kết quả bên cạnh nhau hoặc chồng lên nhau. Nó hỗ trợ **hơn 50 định dạng đầu vào và đầu ra**, bao gồm JPEG, PNG, BMP, TIFF và GIF, và có thể xử lý các tệp hàng trăm trang mà không cần tải toàn bộ tệp vào bộ nhớ.

## Tại sao nên bỏ qua trang tóm tắt?
Tắt trang tóm tắt giảm I/O lên tới **70 %** cho các so sánh chỉ có hình ảnh và rút ngắn thời gian xử lý trung bình khoảng **30 %**, theo bộ benchmark của thư viện. Khi bạn chỉ cần hình diff (cho kiểm thử tự động hoặc quyết định QC pass/fail), báo cáo HTML bổ sung không mang lại giá trị nào mà chỉ tiêu tốn không gian đĩa.

## Yêu cầu trước và Cài đặt môi trường

### Những gì bạn cần
- **GroupDocs.Comparison for .NET** phiên bản **25.4.0** trở lên  
- Visual Studio 2019 + hoặc bất kỳ IDE nào hỗ trợ .NET  
- .NET Framework 4.6.1 + **hoặc** .NET Core 2.0 +  
- Kiến thức cơ bản về C# và thao tác file I/O  

### Các bổ sung đề xuất
- Một dự án thử nghiệm nhỏ chứa cặp hình mẫu (ví dụ: `source.png` và `target.png`).  
- Tùy chọn: cấu hình Dependency Injection nếu bạn thích kiến trúc dịch vụ.  

### Tại sao những yêu cầu này lại quan trọng
Phiên bản thư viện được chỉ định bao gồm cờ `GenerateSummaryPage` và các cải tiến hiệu năng mà các phiên bản cũ không có. Sử dụng IDE hiện đại giúp bạn tận dụng quản lý gói NuGet và nhận cảnh báo biên dịch sớm.

## Cách cài đặt GroupDocs.Comparison
GroupDocs.Comparison có thể được thêm vào bất kỳ dự án .NET nào qua NuGet, công cụ này tự động tải về các binary và cập nhật file dự án. Chọn phương pháp phù hợp với quy trình làm việc của bạn: Package Manager Console cho người dùng Visual Studio hoặc .NET CLI cho môi trường dòng lệnh. Cả hai lệnh đều tự động giải quyết phụ thuộc và đảm bảo tham chiếu đúng phiên bản.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Thay `25.4.0` bằng phiên bản chính xác bạn muốn khóa.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Cả hai lệnh đều thêm thư viện vào file dự án và khôi phục các binary cần thiết.

**Pro Tip:** Ghim phiên bản trong file `.csproj` để tránh nâng cấp vô tình có thể thay đổi hành vi API.

## Các lưu ý về giấy phép
GroupDocs.Comparison yêu cầu giấy phép cho bất kỳ triển khai production nào. Bạn có thể bắt đầu với **bản dùng thử miễn phí** cung cấp đầy đủ chức năng, sau đó nâng cấp lên **giấy phép tạm thời** cho giai đoạn thử nghiệm mở rộng, và cuối cùng là **giấy phép thương mại đầy đủ** cho production. Nhớ đặt file `GroupDocs.Comparison.lic` ở thư mục gốc của ứng dụng hoặc chỉ định đường dẫn tới file này bằng mã.

## Cấu hình dự án cơ bản

Tạo một ứng dụng console mới (hoặc tích hợp vào dịch vụ hiện có) và thêm đoạn mã mẫu sau. Đoạn này minh họa cấu hình tối thiểu trước khi bạn triển khai logic so sánh.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define directory paths for input images and output results
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Initialize paths to your source and target images
string sourceImagePath = Path.Combine(documentDirectory, "sourceImage.jpg");
string targetImagePath = Path.Combine(documentDirectory, "targetImage.jpg");

// Output image path for comparison result
string resultImagePath = Path.Combine(outputDirectory, "resultImage.jpg");
```

> **Important:** Luôn sử dụng `Path.Combine()` cho các đường dẫn file. Nó tự động xử lý dấu phân cách đường dẫn theo OS và tránh các lỗi tiềm ẩn khi di chuyển giữa container Windows và Linux.

## Hướng dẫn triển khai từng bước

### Làm thế nào để so sánh hình ảnh mà không có trang tóm tắt?
`Comparer` là lớp chính trong GroupDocs.Comparison điều phối các thao tác so sánh tài liệu và hình ảnh. `CompareOptions` chứa các cài đặt cấu hình kiểm soát cách so sánh được thực hiện, chẳng hạn như có tạo trang tóm tắt hay không. Tải hình nguồn, cấu hình `CompareOptions` để tắt tóm tắt, thêm hình mục tiêu, và gọi `Compare()`. Phương thức trả về một `ComparisonResult` chứa stream hình diff, bạn có thể ghi ra đĩa, gửi qua mạng, hoặc nhúng vào UI. Cách này chỉ tạo ra diff cần thiết, loại bỏ bất kỳ báo cáo HTML hoặc PDF nào.

```csharp
using (Comparer comparer = new Comparer())
{
    // Load source image
    comparer.Add(sourcePath);

    // Configure options – this is where we turn off the summary page
    CompareOptions options = new CompareOptions
    {
        GenerateSummaryPage = false,
        // You can also tweak sensitivity here if needed
        Sensitivity = 0.5
    };

    // Add the target image for comparison
    comparer.Add(targetPath, options);

    // Execute comparison and retrieve the result image stream
    ComparisonResult result = comparer.Compare();

    // Save the diff image
    using (FileStream outStream = new FileStream(outputPath, FileMode.Create))
    {
        result.Save(outStream);
    }
}
```

Mã trên thực hiện toàn bộ quá trình so sánh trong **bốn bước logic** và chỉ ghi hình diff, không tạo HTML hay PDF tóm tắt.

### Bước 1: Khởi tạo đối tượng Comparer
Lớp `Comparer` là cổng vào mọi thao tác so sánh. Nó triển khai `IDisposable`, vì vậy việc bọc trong khối `using` đảm bảo các handle file và bộ nhớ không quản lý được giải phóng kịp thời, ngay cả khi có exception.

### Bước 2: Cấu hình CompareOptions để không tạo tóm tắt
Đặt `GenerateSummaryPage = false` trên instance `CompareOptions`. Cờ này báo cho engine bỏ qua việc tạo báo cáo HTML mặc định, là nguồn I/O thừa trong các kịch bản chỉ so sánh hình ảnh.

### Bước 3: Thêm hình ảnh mục tiêu để so sánh
Bạn có thể gọi `Add()` nhiều lần để so sánh một nguồn với nhiều mục tiêu trong một batch. Mỗi lời gọi có thể nhận một `CompareOptions` riêng nếu cần tùy chỉnh per‑image.

### Bước 4: Thực hiện so sánh và lưu kết quả
`Comparer.Compare()` thực hiện công việc nặng và trả về một `ComparisonResult`. Kết quả chứa một `Stream` với hình diff, bạn có thể lưu trực tiếp ra đĩa, gửi qua mạng, hoặc nhúng vào UI.

## Phương thức sẵn sàng cho sản xuất
Dưới đây là một phương thức đã sẵn sàng để bạn chèn vào bất kỳ dịch vụ .NET nào. Nó bao gồm kiểm tra đường dẫn, xử lý ngoại lệ, và các hook logging tùy chọn.

```csharp
public static void CompareImagesWithoutSummary(string sourcePath, string targetPath, string outputPath)
{
    try
    {
        using (Comparer comparer = new Comparer(sourcePath))
        {
            // Configure options to skip summary generation
            CompareOptions options = new CompareOptions
            {
                GenerateSummaryPage = false
            };
            
            // Add target image and execute comparison
            comparer.Add(targetPath);
            comparer.Compare(outputPath, options);
            
            Console.WriteLine($"Comparison completed successfully. Result saved to: {outputPath}");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error during image comparison: {ex.Message}");
        throw; // Re-throw for proper error handling upstream
    }
}
```

## Những khó khăn thường gặp trong triển khai (và cách tránh chúng)

- **Vấn đề đường dẫn:** Luôn xác minh cả file nguồn và file mục tiêu tồn tại bằng `File.Exists()`. File thiếu sẽ ném `FileNotFoundException` có thể bắt sớm.  
- **Áp lực bộ nhớ:** Hình ảnh lớn (10 MB +) có thể tiêu tốn RAM đáng kể. Xử lý chúng theo batch và cân nhắc giảm độ phân giải nếu không cần độ chính xác pixel‑perfect.  
- **Khóa file:** Đảm bảo không có tiến trình nào khác giữ khóa exclusive trên các file hình ảnh. Điều này đặc biệt quan trọng trong môi trường đa luồng hoặc container.

## Ứng dụng thực tế và các trường hợp sử dụng

### Kiểm soát chất lượng trong sản xuất
Dây chuyền sản xuất chụp ảnh mỗi sản phẩm và so sánh với mẫu chuẩn. Bỏ qua trang tóm tắt cho phép hệ thống quyết định “pass” hoặc “fail” trong vòng vài mili giây, giữ cho dây chuyền chạy nhanh.

### Hệ thống quản lý nội dung
Khi người dùng tải lên tài sản, CMS có thể ngay lập tức phát hiện bản sao hoặc bản gần giống, ngăn ngừa lãng phí lưu trữ và cải thiện độ liên quan tìm kiếm. Hình diff có thể được lưu làm thumbnail để kiểm tra nhanh.

### Kiểm thử UI tự động (Hồi quy trực quan)
Selenium hoặc Playwright có thể chụp screenshot của trang web, sau đó đưa vào routine so sánh này. Hình diff làm nổi bật các thay đổi UI, và vì không tạo tóm tắt nên pipeline CI vẫn nhanh và nhẹ.

### Hình ảnh y tế (với kiểm toán)
Quy trình radiology đôi khi cần đánh dấu thay đổi giữa các scan liên tiếp. Mặc dù bạn vẫn có thể tạo log audit chi tiết, nhưng hình diff có thể được tạo mà không có trang tóm tắt, giảm thời gian xử lý cho các PNG đã chuyển từ DICOM lớn.

## Các cân nhắc về hiệu năng và tối ưu hoá

### Thực hành tốt nhất quản lý bộ nhớ
Xử lý hình ảnh theo **batch 20–50** tùy vào RAM server. Giải phóng mỗi instance `Comparer` ngay lập tức và chỉ gọi `GC.Collect()` nếu bạn thấy spike bộ nhớ trong các job chạy lâu.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Tối ưu hoá I/O đĩa
Đặt các thư mục input, output và tạm thời trên cùng một volume SSD nhanh. Xóa các file tạm ngay sau khi lưu hình diff để tránh tiêu tốn không gian đĩa không cần.

### Cân nhắc về đa luồng và bất đồng bộ
GroupDocs.Comparison an toàn với thread cho các thao tác chỉ đọc, nhưng tránh chia sẻ một instance `Comparer` giữa các thread. Thay vào đó, khởi tạo các task độc lập:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Khắc phục các vấn đề thường gặp

### Lỗi đường dẫn tệp và quyền truy cập
- **Triệu chứng:** `FileNotFoundException` hoặc `UnauthorizedAccessException`.  
- **Giải pháp:** Dùng `Path.GetFullPath()` để debug đường dẫn đã giải quyết, đảm bảo danh tính (application pool hoặc user trong container) có quyền đọc/ghi, và kiểm tra đường dẫn không bị cắt ngắn bởi biến môi trường.

### Tắc nghẽn bộ nhớ và hiệu năng
- **Triệu chứng:** Chạy chậm hoặc `OutOfMemoryException`.  
- **Giải pháp:** Thu nhỏ hình ảnh về độ phân giải chung (ví dụ 1024 × 768) khi không cần so sánh pixel‑perfect. Giám sát bộ nhớ bằng công cụ như dotMemory hoặc Performance Profiler tích hợp.

### Vấn đề về giấy phép
- **Triệu chứng:** Hình diff có watermark hoặc `LicenseException`.  
- **Giải pháp:** Xác nhận file `GroupDocs.Comparison.lic` nằm trong thư mục exe hoặc tải nó bằng mã: `License license = new License(); license.SetLicense("path/to/license.file");`.

## Các tùy chọn cấu hình nâng cao

### Tùy chỉnh độ nhạy của so sánh
Bạn có thể tinh chỉnh cách engine xử lý các biến thể pixel nhỏ (ví dụ artefact nén) bằng cách điều chỉnh thuộc tính `Sensitivity` trên `CompareOptions`. Giá trị thấp hơn làm so sánh chặt chẽ hơn.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Tối ưu hoá định dạng đầu ra
Nếu bạn cần hình diff ở định dạng cụ thể (PNG vs. JPEG), đặt thuộc tính `OutputFormat`:

```csharp
options.OutputFormat = ImageSaveOptions.SaveFormat.Png;
```

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    // Customize highlighting colors if needed
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

## Tích hợp với các framework .NET phổ biến

### Ví dụ dịch vụ ASP.NET Core
Cung cấp một endpoint HTTP nhẹ nhận hai stream hình ảnh, chạy so sánh và trả về hình diff dưới dạng `FileResult`.

```csharp
public interface IImageComparisonService
{
    Task<string> CompareImagesAsync(string sourceImage, string targetImage);
}

public class ImageComparisonService : IImageComparisonService
{
    private readonly ILogger<ImageComparisonService> _logger;
    private readonly string _outputDirectory;

    public ImageComparisonService(ILogger<ImageComparisonService> logger, IConfiguration config)
    {
        _logger = logger;
        _outputDirectory = config.GetValue<string>("ImageComparison:OutputDirectory");
    }

    public async Task<string> CompareImagesAsync(string sourceImage, string targetImage)
    {
        // Your implementation here
        return await Task.FromResult("comparisonResult.jpg");
    }
}
```

### Đăng ký Dependency Injection
Thêm comparer như một service scoped trong `Program.cs` hoặc `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Câu hỏi thường gặp

**Q: Lợi thế chính của việc bỏ qua trang tóm tắt là gì?**  
A: Giảm thời gian xử lý tới 30 % và giảm dung lượng đĩa khoảng 70 % cho các so sánh chỉ có hình ảnh, rất quan trọng cho các pipeline có lưu lượng cao.

**Q: Tôi vẫn có thể lấy metadata chi tiết mà không có trang tóm tắt không?**  
A: Có. Đối tượng `ComparisonResult` cung cấp một collection `Changes` chứa thông tin lập trình về mỗi sự khác biệt được phát hiện.

**Q: Các định dạng hình ảnh nào được hỗ trợ?**  
A: JPEG, PNG, BMP, TIFF, GIF và một số định dạng khác — tổng cộng hơn 50 định dạng.

**Q: Tôi nên xử lý các hình ảnh rất lớn (ví dụ >20 MB) như thế nào?**  
A: Xử lý chúng theo batch nhỏ hơn, tùy chọn giảm độ phân giải, và giám sát bộ nhớ. Sử dụng `Comparer` trong khối `using` để giải phóng tài nguyên kịp thời.

**Q: Phương pháp này có an toàn cho các ứng dụng đa luồng không?**  
A: Có, miễn là mỗi luồng tạo riêng một instance `Comparer`. Chia sẻ một instance duy nhất có thể gây race condition.

## Tài nguyên bổ sung
- [Tài liệu GroupDocs.Comparison](https://docs.groupdocs.com/comparison/net/)
- [Tham chiếu API](https://reference.groupdocs.com/comparison/net/)
- [Tải xuống](https://releases.groupdocs.com/comparison/net/)
- [Mua](https://purchase.groupdocs.com/buy)
- [Dùng thử miễn phí](https://releases.groupdocs.com/comparison/net/)
- [Giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)
- [Diễn đàn hỗ trợ](https://forum.groupdocs.com/c/comparison/)

---

**Last Updated:** 2026-05-31  
**Tested With:** GroupDocs.Comparison 25.4.0 for .NET  
**Author:** GroupDocs

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

```csharp
// Create a Comparer object with the source image path
using (Comparer comparer = new Comparer(sourceImagePath))
{
    // Configuration will follow in subsequent steps
}
```

```csharp
// Set up compare options to avoid generating a summary page
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```

```csharp
// Add the target image to the comparison
comparer.Add(targetImagePath);
```

```csharp
// Execute comparison with configured options and save to result path
comparer.Compare(resultImagePath, options);
```

```csharp
public static void ProcessImageBatch(List<string> imagePairs, int batchSize = 10)
{
    for (int i = 0; i < imagePairs.Count; i += batchSize)
    {
        var batch = imagePairs.Skip(i).Take(batchSize);
        // Process batch and allow garbage collection between batches
        foreach (var pair in batch)
        {
            // Your comparison logic here
        }
        
        // Explicit garbage collection after each batch (use sparingly)
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```

```csharp
public static async Task<bool> CompareImagesAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            CompareImagesWithoutSummary(source, target, output);
            return true;
        }
        catch
        {
            return false;
        }
    });
}
```

## Hướng dẫn liên quan

- [So sánh hình ảnh .NET - So sánh hình ảnh bằng lập trình](/comparison/net/image-comparison/compare-images-from-path/)
- [So sánh hình ảnh .NET - So sánh hình ảnh từ luồng](/comparison/net/image-comparison/compare-images-from-stream/)
- [Hướng dẫn GroupDocs Comparison .NET - Hướng dẫn sử dụng cơ bản đầy đủ](/comparison/net/basic-usage/)