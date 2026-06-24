---
categories:
- Image Processing
date: '2026-05-31'
description: 了解如何在 .NET 中使用 GroupDocs.Comparison 比较图像并禁用摘要页。本教程涵盖设置、代码、性能技巧以及实际案例。
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: 比较图像 .NET（无摘要）
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
title: 如何在 .NET 中比较图像 – 跳过摘要页
type: docs
url: /zh/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# 在 .NET 中比较图像 – 跳过摘要页面

当您需要在 .NET 应用程序中以编程方式 **how to compare images** 时，最不想看到的就是浪费时间和存储空间的额外摘要页面。无论您是在构建质量控制线、内容管理流水线，还是自动化视觉回归测试套件，跳过摘要页面都可以为每次运行节省数秒，并保持磁盘占用精简。

在本教程中，您将学习如何使用 **GroupDocs.Comparison for .NET** 高效比较两张图像，配置库以抑制摘要生成，并运用最佳实践的性能技巧。我们还将探讨此做法的意义、适用场景以及如何避免常见陷阱。

## 快速答案
- **在不生成摘要页面的情况下比较图像的最快方法是什么？** 使用 `Comparer` 配合 `CompareOptions` 并将 `GenerateSummaryPage = false`。  
- **哪个库开箱即支持此功能？** GroupDocs.Comparison for .NET（v25.4.0 及以上）。  
- **我需要许可证吗？** 是的，生产环境必须使用商业许可证；开发阶段可使用免费试用版。  
- **我可以一次比较多于两张图像吗？** 当然可以——在调用 `Compare()` 之前多次调用 `Add()`。  
- **此方法适用于大规模批处理作业吗？** 适用，只要结合批处理和适当的内存管理即可。

## 什么是 GroupDocs.Comparison？
`GroupDocs.Comparison` 是一个 .NET 库，用于检测文档和图像之间的视觉差异，并生成并排或叠加的对比结果。它支持 **50+ 种输入和输出格式**，包括 JPEG、PNG、BMP、TIFF 和 GIF，并且能够在不将整个文件加载到内存中的情况下处理数百页的文件。

## 为什么要跳过摘要页面？
禁用摘要页面可将仅图像对比的 I/O 减少高达 **70 %**，并将处理时间平均缩短约 **30 %**（依据库的基准套件）。当您只需要差异图像（用于自动化测试或 QC 合格/不合格判定）时，额外的 HTML 报告既无价值，又会占用磁盘空间。

## 前置条件和环境设置

### 您需要的内容
- **GroupDocs.Comparison for .NET** 版本 **25.4.0** 或更高  
- Visual Studio 2019 + 或任意 .NET 兼容的 IDE  
- .NET Framework 4.6.1 + **或** .NET Core 2.0 +  
- 基础的 C# 知识以及对文件 I/O 的了解  

### 推荐的额外内容
- 一个包含一对示例图像的小型测试项目（例如 `source.png` 与 `target.png`）。  
- 可选：如果您倾向于面向服务的架构，可设置依赖注入。  

### 为什么这些前置条件很重要
指定的库版本已包含 `GenerateSummaryPage` 标志以及旧版本缺失的性能改进。使用现代 IDE 可让您利用 NuGet 包管理，并在编译时提前看到警告。

## 如何安装 GroupDocs.Comparison
GroupDocs.Comparison 可以通过 NuGet 添加到任何 .NET 项目，NuGet 会处理二进制文件的下载并更新项目文件。请选择符合您工作流的方式：Visual Studio 用户使用 Package Manager Console，或在命令行环境中使用 .NET CLI。两种命令都会自动解析依赖并确保引用正确的版本。

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(将 `25.4.0` 替换为您计划锁定的确切版本。)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
这两个命令都会将库添加到项目文件并恢复所需的二进制文件。

**专业提示：** 在 `.csproj` 中固定版本，以避免意外升级导致 API 行为变化。

## 许可考虑事项
GroupDocs.Comparison 在任何生产部署中都需要许可证。您可以先使用提供完整功能的 **免费试用**，随后升级为 **临时许可证** 进行扩展测试，最终购买 **完整商业许可证** 用于生产。请记得将 `GroupDocs.Comparison.lic` 文件放置在应用根目录，或通过代码显式指定其路径。

## 基本项目设置

创建一个新的控制台应用（或集成到现有服务），并添加以下模板代码。此代码片段演示了在进入比较逻辑之前所需的最小设置。

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

> **重要提示：** 始终使用 `Path.Combine()` 处理文件路径。它会自动适配操作系统的路径分隔符，避免在 Windows 与 Linux 容器之间迁移时出现细微错误。

## 步骤式实现指南

### 如何在不生成摘要页面的情况下比较图像？
`Comparer` 是 GroupDocs.Comparison 中负责文档和图像对比的核心类。`CompareOptions` 保存控制比较行为的配置设置，例如是否生成摘要页面。加载源图像，配置 `CompareOptions` 以禁用摘要，添加目标图像，然后调用 `Compare()`。该方法返回一个包含差异图像流的 `ComparisonResult`，您可以将其写入磁盘、通过网络发送或嵌入 UI 组件。此方式仅生成必要的差异图像，省去任何额外的 HTML 或 PDF 报告。

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

上述代码在 **四个逻辑步骤** 中完成整个比较，并仅写入差异图像，省略所有 HTML 或 PDF 摘要。

### 步骤 1：初始化 Comparer 对象
`Comparer` 类是所有比较操作的入口。它实现了 `IDisposable`，因此在 `using` 块中使用可确保即使抛出异常也能及时释放文件句柄和非托管内存。

### 步骤 2：为无摘要配置 CompareOptions
在 `CompareOptions` 实例上设置 `GenerateSummaryPage = false`。此标志指示引擎跳过默认 HTML 报告的生成，这是图像仅对比场景中主要的额外 I/O 来源。

### 步骤 3：添加目标图像进行比较
您可以多次调用 `Add()`，在单批次中将一个源图像与多个目标图像进行比较。每次调用都可以传入独立的 `CompareOptions`，以实现针对单张图像的自定义设置。

### 步骤 4：执行比较并保存结果
`Comparer.Compare()` 执行核心比较工作并返回 `ComparisonResult`。该结果包含一个 `Stream`，其中是差异图像，您可以直接保存到磁盘、发送网络或嵌入 UI。

## 完整的生产就绪方法

下面提供了一个可直接放入任意 .NET 服务的完整方法示例。它包括路径校验、异常处理以及可选的日志钩子。

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

## 常见实现陷阱（以及如何规避）

- **路径问题：** 始终使用 `File.Exists()` 验证源文件和目标文件是否存在。缺失的文件会抛出 `FileNotFoundException`，可提前捕获。  
- **内存压力：** 大尺寸图像（10 MB 以上）会占用大量 RAM。请分批处理，并在不需要像素级精度时考虑降采样。  
- **文件锁定：** 确保没有其他进程对图像文件持有独占锁。这在多线程或容器化环境中特别重要。  

## 实际应用场景与用例

### 制造业质量控制
生产线对每件产品拍摄图像并与金标准进行对比。跳过摘要页面可让系统在毫秒级内做出“合格”或“不合格”判断，保持高速流水线运转。

### 内容管理系统
用户上传资产时，CMS 可即时检测重复或相似文件，防止存储膨胀并提升搜索相关性。差异图像可作为缩略图供快速目视检查。

### 自动化 UI 测试（视觉回归）
Selenium 或 Playwright 捕获网页截图后，将其传入本比较例程。差异图像突出 UI 变更，且因未生成摘要，CI 流水线保持快速轻量。

### 医学影像（带审计）
放射科工作流有时需要标记连续扫描之间的变化。即使仍需生成详细审计日志，差异图像本身也可在不生成摘要页面的情况下快速产出，降低大规模 DICOM 转 PNG 的处理时间。

## 性能考量与优化

### 内存管理最佳实践
根据服务器 RAM 将图像分 **20–50** 张一批处理。及时释放每个 `Comparer` 实例，并仅在发现内存峰值时才调用 `GC.Collect()`。

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### 磁盘 I/O 优化
将输入、输出及临时目录放置在同一高速 SSD 卷上。差异图像保存后立即删除临时文件，以避免不必要的磁盘占用。

### 线程与异步注意事项
GroupDocs.Comparison 对只读操作是线程安全的，但请避免在多个线程间共享同一个 `Comparer` 实例。应为每个任务创建独立实例：

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## 常见问题排查

### 文件路径与权限错误
- **症状：** `FileNotFoundException` 或 `UnauthorizedAccessException`。  
- **解决方案：** 使用 `Path.GetFullPath()` 调试解析后的路径，确保应用池身份（或 Docker 容器用户）拥有读写权限，并检查路径是否被环境变量截断。

### 内存与性能瓶颈
- **症状：** 运行缓慢或出现 `OutOfMemoryException`。  
- **解决方案：** 在不需要像素级比较时将图像统一缩放至常规分辨率（如 1024 × 768），并使用 dotMemory 或内置性能分析器监控内存。

### 许可证问题
- **症状：** 差异图像带水印或抛出 `LicenseException`。  
- **解决方案：** 确认 `GroupDocs.Comparison.lic` 位于可执行文件目录，或通过 `License license = new License(); license.SetLicense("path/to/license.file");` 显式加载。

## 高级配置选项

### 自定义比较灵敏度
通过在 `CompareOptions` 上调整 `Sensitivity` 属性，可微调引擎对细微像素差异（如压缩伪影）的容忍度。值越低，比较越严格。

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### 输出格式优化
若需要特定格式的差异图像（PNG 与 JPEG），请设置 `OutputFormat` 属性：

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

## 与流行 .NET 框架的集成

### ASP.NET Core 服务示例
暴露一个轻量级 HTTP 端点，接受两段图像流，执行比较并以 `FileResult` 返回差异图像。

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

### 依赖注入注册
在 `Program.cs` 或 `Startup.cs` 中将比较器注册为 scoped 服务：

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## 常见问答

**问：跳过摘要页面的主要优势是什么？**  
答：可将图像仅对比的处理时间缩短最高 30 %，磁盘使用量降低约 70 %，这对高吞吐量流水线至关重要。

**问：在不生成摘要页面的情况下还能获取详细的变更元数据吗？**  
答：可以。`ComparisonResult` 对象提供 `Changes` 集合，包含每个检测到的差异的程序化信息。

**问：支持哪些图像格式？**  
答：JPEG、PNG、BMP、TIFF、GIF 等，累计超过 50 种格式。

**问：如何处理非常大的图像（例如 >20 MB）？**  
答：分批处理，必要时降采样，并监控内存使用。使用 `using` 块包装 `Comparer` 可确保资源及时释放。

**问：此方法对多线程应用安全么？**  
答：安全，只要每个线程创建自己的 `Comparer` 实例。共享单实例可能导致竞争条件。

## 其他资源

- [GroupDocs.Comparison Documentation](https://docs.groupdocs.com/comparison/net/)
- [API Reference](https://reference.groupdocs.com/comparison/net/)
- [Download](https://releases.groupdocs.com/comparison/net/)
- [Purchase](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/comparison/net/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/comparison/)

---

**最后更新：** 2026-05-31  
**测试环境：** GroupDocs.Comparison 25.4.0 for .NET  
**作者：** GroupDocs

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

## 相关教程

- [Image Comparison .NET - Compare Images Programmatically](/comparison/net/image-comparison/compare-images-from-path/)
- [Image Comparison .NET - Compare Images from Stream](/comparison/net/image-comparison/compare-images-from-stream/)
- [GroupDocs Comparison .NET Tutorial - Complete Basic Usage Guide](/comparison/net/basic-usage/)