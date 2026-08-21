---
categories:
- Document Processing
date: '2026-07-01'
description: 了解如何使用 GroupDocs.Comparison 读取文件元数据 C#，高效提取文件大小流并获取文档属性流。
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: 提取文档信息 .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  headline: Read File Metadata C# – Extract Document Information from Streams
  type: TechArticle
- description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  name: Read File Metadata C# – Extract Document Information from Streams
  steps:
  - name: Initialize the Comparer Object with Stream
    text: The following snippet creates a `Comparer` instance from a read‑only `FileStream`.
      Using a `using` block guarantees that the stream is closed and the comparer
      disposed, preventing file locks.
  - name: Extract Document Information
    text: Calling `GetDocumentInfo()` returns an `IDocumentInfo` object that holds
      all the metadata you need. The method reads only the necessary parts of the
      file header, so even a 500‑page PDF is processed in a fraction of a second.
  - name: Display and Use Document Information
    text: You can now access `FileType`, `PageCount`, and `Size` properties. In production
      you might store these values in a database, expose them via an API, or use them
      to decide whether to accept an upload.
  type: HowTo
- questions:
  - answer: Yes. The library supports **over 50 file formats**, including DOCX, PDF,
      XLSX, PPTX, and many image types, making it suitable for virtually any document
      workflow.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. A free trial is available at [the website](https://releases.groupdocs.com/),
      allowing you to evaluate all features without a license.
    question: Can I try GroupDocs.Comparison for .NET before purchasing?
  - answer: You can get help in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12),
      where the community and product team respond to questions promptly.
    question: Where can I find support for GroupDocs.Comparison for .NET?
  - answer: Yes. Temporary licenses can be obtained from [the licensing page](https://purchase.groupdocs.com/temporary-license/),
      ideal for development and QA environments.
    question: Are temporary licenses available for testing?
  - answer: Definitely. It offers enterprise‑grade performance, extensive format support,
      and robust error handling, all of which are essential for large‑scale production
      systems.
    question: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- metadata-extraction
title: 读取文件元数据 C# – 从流中提取文档信息
type: docs
url: /zh/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# 读取文件元数据 C# – 从流中提取文档信息

## 介绍

在 C# 中读取文件元数据而不加载整个文档是现代 .NET 应用的常见需求。**Read file metadata C#** 让您能够验证上传、显示文档详情，并在保持低内存使用的同时做出处理决策。GroupDocs.Comparison for .NET 提供了一个快速的基于流的 API，直接从 `Stream` 中提取文件类型、页数、大小等属性。接下来的章节将说明此功能的重要性、如何设置以及可直接放入任何 .NET 项目的逐步代码示例。

## 快速答案
- **“read file metadata C#” 是什么意思？** 它指的是通过 .NET 流检索文档的属性（类型、页数、大小），而无需加载完整内容。  
- **哪个库处理此操作？** GroupDocs.Comparison for .NET 提供 `GetDocumentInfo()` 方法用于快速提取元数据。  
- **我需要许可证吗？** 免费试用可用于开发；生产环境需要商业许可证。  
- **我可以在大 PDF 上使用吗？** 可以——流式方法能够在不占用大量内存的情况下处理数百页的文件。  
- **它兼容 .NET 6+ 吗？** 完全兼容，库针对 .NET Standard 2.0，能够在 .NET 6、.NET 7 和 .NET Core 上运行。

## 什么是 read file metadata C#？
`Read file metadata C#` 指的是使用能够处理流的 C# 代码获取文档的描述性信息——如格式、页数和字节大小。此技术避免将整个文件加载到内存中，对于大型 PDF、DOCX 文件或批量操作尤为有价值。

## 为什么使用 GroupDocs 从流中提取元数据？
GroupDocs.Comparison 支持 **50+ 输入和输出格式**，并且能够从最大 **2 GB** 的文件中提取元数据，同时将内存使用保持在 **10 MB** 以下。库仅读取必要的头部区域，在标准服务器上对典型的 100 页 PDF 能在 **150 ms** 以内返回结果。这些量化的优势转化为更快的上传验证、更低的云成本以及更流畅的用户体验。

## 前置条件和设置

### 1. 安装 GroupDocs.Comparison for .NET
从 [官方下载页面](https://releases.groupdocs.com/comparison/net/) 下载最新包。如果更喜欢使用 NuGet，请运行：

```
Install-Package GroupDocs.Comparison
```

### 2. 基础 .NET 开发知识  
您应熟悉 C# 以及 .NET I/O 模型。使用 `Stream`、`FileStream` 和 `MemoryStream` 对下面的示例至关重要。

### 3. 开发环境  
Visual Studio、VS Code 或 JetBrains Rider 都受支持。确保项目目标为 .NET 6 或更高，以获得最佳性能。

## 如何从流中读取文件元数据 C#？

使用 `FileStream` 加载文档，实例化 `Comparer`，并调用 `GetDocumentInfo()`。整个操作仅需两行代码，即可返回包含文件类型、页数和大小的 `IDocumentInfo` 对象。库内部只读取必要的头部字节，即使是大型 PDF 也能快速处理且不会占用大量内存。  
`Comparer` 是负责文档分析的主要 GroupDocs.Comparison 类。  
`GetDocumentInfo()` 返回包含基本元数据的 `IDocumentInfo` 对象。

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### 步骤 1：使用流初始化 Comparer 对象

以下代码片段从只读 `FileStream` 创建 `Comparer` 实例。使用 `using` 块可确保流被关闭、Comparer 被释放，从而防止文件锁定。

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### 步骤 2：提取文档信息

调用 `GetDocumentInfo()` 返回包含所有所需元数据的 `IDocumentInfo` 对象。该方法仅读取文件头的必要部分，即使是 500 页的 PDF 也能在瞬间完成处理。

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### 步骤 3：显示并使用文档信息

现在您可以访问 `FileType`、`PageCount` 和 `Size` 属性。在生产环境中，您可能会将这些值存入数据库、通过 API 暴露，或用来决定是否接受上传。

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## 常见使用场景和实现模式

### 文件上传验证

当用户上传文档时，您可以立即验证其类型和页数，再决定是否将其写入存储。这可防止不需要的格式和超大文件进入系统。

```csharp
// Example: Validating uploaded documents before processing
public bool ValidateUploadedDocument(Stream documentStream)
{
    using (Comparer comparer = new Comparer(documentStream))
    {
        IDocumentInfo info = comparer.Source.GetDocumentInfo();
        
        // Check if it's a supported format
        if (info.FileType == FileType.Unknown)
            return false;
            
        // Ensure it's not too large (e.g., max 50 pages)
        if (info.PageCount > 50)
            return false;
            
        return true;
    }
}
```

### 批量文档分析

需要处理文件夹中的文档吗？先提取元数据，再将文件路由到不同的流水线——例如，大 PDF 交给异步工作者处理，而单页文件则直接在线处理。

```csharp
// Example: Categorizing documents by complexity
public void CategorizeDocuments(string[] filePaths)
{
    foreach (string path in filePaths)
    {
        using (Comparer comparer = new Comparer(File.OpenRead(path)))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            
            if (info.PageCount == 1)
            {
                // Fast processing for single-page documents
                ProcessSimpleDocument(path);
            }
            else
            {
                // More thorough processing for complex documents
                ProcessComplexDocument(path);
            }
        }
    }
}
```

## 常见问题及解决方案

### 文件访问和锁定问题

**问题**：“The file is being used by another process.”  
**解决方案**：将流包装在 `using` 语句中，如有必要，使用指数退避的重试策略。

```csharp
// Example: Retry logic for locked files
public IDocumentInfo GetDocumentInfoWithRetry(string filePath, int maxRetries = 3)
{
    for (int attempt = 0; attempt < maxRetries; attempt++)
    {
        try
        {
            using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
            {
                return comparer.Source.GetDocumentInfo();
            }
        }
        catch (IOException) when (attempt < maxRetries - 1)
        {
            Thread.Sleep(100); // Wait a bit before retrying
        }
    }
    throw new Exception($"Could not access file after {maxRetries} attempts");
}
```

### 不支持的文件格式处理

**问题**：API 对未知格式抛出异常。  
**解决方案**：检查 `FileType` 属性；如果返回 `Unknown`，则向调用方返回友好的错误信息并记录该事件。

```csharp
// Example: Safe file type checking
using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
{
    IDocumentInfo info = comparer.Source.GetDocumentInfo();
    
    if (info.FileType == FileType.Unknown)
    {
        Console.WriteLine("Unsupported file format detected");
        return; // or handle appropriately
    }
    
    // Process normally
    ProcessSupportedDocument(info);
}
```

### 大文件内存管理

**问题**：处理超大文档时内存激增。  
**解决方案**：基于流的方法已经将内存使用降到最低，但仍应在完成后立即调用 `Dispose()` 释放 `Comparer`，并避免长时间持有 `IDocumentInfo` 的引用。

## 性能考虑与最佳实践

### 流管理最佳实践

1. **始终使用 `using` 语句** – 确保及时释放资源。  
2. **在重复使用时重置流位置** – 如果需要读取同一流两次，调用 `stream.Seek(0, SeekOrigin.Begin)`。  
3. **选择合适的流类型** – `FileStream` 用于磁盘文件，`MemoryStream` 用于内存数据，`NetworkStream` 用于远程来源。

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### 何时优先使用此方法而非完整文档加载

**优先使用基于流的元数据提取的情况**：

- 只需要高级别的细节（类型、页数、大小）。  
- 正在验证上传或构建文档目录。  
- 性能和低内存占用至关重要。

**切换到完整文档处理的情况**：

- 需要比较内容、提取文本或渲染页面。  
- 需要深度分析（例如 OCR、水印检测）。

## 生产环境高级技巧

### 强健的错误处理策略

将所有操作包装在捕获 `GroupDocs.Comparison.Exceptions.ComparisonException` 的 try‑catch 块中。`ComparisonException` 是库在文档处理期间出现错误时抛出的异常。记录错误细节，返回统一的错误响应，并在 `finally` 代码块中确保 `Comparer` 被释放。

```csharp
public DocumentInfoResult GetDocumentInfoSafely(Stream documentStream)
{
    try
    {
        using (Comparer comparer = new Comparer(documentStream))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            return new DocumentInfoResult 
            { 
                Success = true, 
                Info = info 
            };
        }
    }
    catch (Exception ex)
    {
        return new DocumentInfoResult 
        { 
            Success = false, 
            ErrorMessage = ex.Message 
        };
    }
}
```

### 与日志和监控的集成

注入日志框架（如 Serilog 或 NLog），并输出处理时间、文件大小、成功/失败计数等指标。这些数据有助于及早发现性能回退。

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## 常见问题

**问：GroupDocs.Comparison for .NET 是否兼容不同的文档格式？**  
**答：是的。库支持 **超过 50 种文件格式**，包括 DOCX、PDF、XLSX、PPTX 以及多种图像类型，几乎适用于任何文档工作流。**

**问：我可以在购买前试用 GroupDocs.Comparison for .NET 吗？**  
**答：当然可以。免费试用可在 [官方网站](https://releases.groupdocs.com/) 获得，允许您在无需许可证的情况下评估所有功能。**

**问：在哪里可以找到 GroupDocs.Comparison for .NET 的支持？**  
**答：您可以在 [GroupDocs.Comparison 论坛](https://forum.groupdocs.com/c/comparison/12) 获得帮助，社区和产品团队会及时响应问题。**

**问：是否提供临时许可证用于测试？**  
**答：是的。临时许可证可从 [授权页面](https://purchase.groupdocs.com/temporary-license/) 获取，适用于开发和 QA 环境。**

**问：GroupDocs.Comparison for .NET 适合企业部署吗？**  
**答：绝对适合。它提供企业级性能、广泛的格式支持以及强健的错误处理，这些都是大规模生产系统必不可少的要素。**

---

**最后更新：** 2026-07-01  
**已测试：** GroupDocs.Comparison 23.10 for .NET  
**作者：** GroupDocs

## 相关教程

- [获取文档属性 C# .NET - 提取文件元数据](/comparison/net/basic-usage/get-document-info-from-path/)
- [文档元数据管理 .NET - GroupDocs.Comparison 完整指南](/comparison/net/metadata-management/)
- [文档比较 .NET 教程 - 使用 GroupDocs 保留元数据](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)