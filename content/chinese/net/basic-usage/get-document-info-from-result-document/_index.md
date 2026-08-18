---
categories:
- Document Comparison
date: '2026-06-15'
description: 了解如何使用 GroupDocs.Comparison 从 .NET 比较结果中提取元数据。一步一步的指南，附带代码示例和实用技巧。
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: 从比较结果中提取文档信息
schemas:
- author: GroupDocs
  dateModified: '2026-06-15'
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  headline: How to Extract Metadata from .NET Comparison Results – Complete Guide
  type: TechArticle
- description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  name: How to Extract Metadata from .NET Comparison Results – Complete Guide
  steps:
  - name: Initialize Comparer with Source Document
    text: '`Comparer` is the core class in GroupDocs.Comparison that loads the source
      document and orchestrates comparison operations. Using a `using` block guarantees
      that all unmanaged resources are released automatically. > **Pro Tip:** You
      can pass any `Stream` (file, memory, cloud) to the `Comparer` const'
  - name: Add Target Document for Comparison
    text: The `Add()` method accepts additional streams or file paths, enabling one‑to‑many
      comparisons. > **Important:** The order of added documents influences the way
      changes are highlighted in the final report.
  - name: Retrieve Document Info from Result Document
    text: '`IDocumentInfo` provides a unified view of document metadata such as file
      type, page count, and size across all supported formats. > **Understanding the
      Data:** The returned object works the same for DOCX, PDF, XLSX, and PPTX, so
      you can write format‑agnostic code.'
  - name: Display Document Info
    text: 'Once you have the `IDocumentInfo` instance, you can log, store, or present
      its properties. The three most commonly used properties are: - **FileType**
      – e.g., `DOCX`, `PDF`, `XLSX`. - **PageCount** – total pages or slides. - **Size**
      – file size in bytes (useful for storage calculations).'
  type: HowTo
- questions:
  - answer: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT,
      and many others, providing consistent metadata extraction across them.
    question: Is GroupDocs.Comparison for .NET compatible with various document formats?
  - answer: Absolutely. Settings such as sensitivity, change types, and output format
      are independent of the `GetDocumentInfo()` call.
    question: Can I customize comparison settings without affecting metadata extraction?
  - answer: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/).
      The trial includes full metadata extraction capabilities.
    question: Is there a trial version I can use for evaluation?
  - answer: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12)
      for community help and official support from the GroupDocs team.
    question: Where can I get support for implementation questions?
  - answer: GroupDocs offers developer, site, and OEM licenses. Purchase options are
      listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).
    question: What licensing options are available for production deployments?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- groupdocs-comparison
- document-metadata
- dotnet-api
- document-properties
title: 如何从 .NET 比较结果中提取元数据 – 完整指南
type: docs
url: /zh/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# 如何从 .NET 比较结果中提取元数据 – 完整指南

当您在 .NET 应用程序中进行文档比较时，可能会想了解 **如何提取元数据**。元数据如文件类型、页数和文档大小对于审计日志、性能调优或仅仅向最终用户显示有用信息都至关重要。本教程将指导您如何使用 GroupDocs.Comparison for .NET 高效检索这些数据。

## 快速答案
- **比较的主要类是什么？** `Comparer` 加载源文档并运行比较引擎。  
- **哪个方法返回元数据？** 对目标文档调用 `GetDocumentInfo()` 会返回 `IDocumentInfo` 对象。  
- **我可以在 .NET 中获取文档大小吗？** 可以——`IDocumentInfo` 的 `Size` 属性返回字节数。  
- **提取元数据需要许可证吗？** 生产环境需要有效的 GroupDocs.Comparison 许可证；免费试用版支持所有元数据功能。  
- **API 与 .NET 6 兼容吗？** 完全兼容——GroupDocs.Comparison 支持 .NET Framework 4.6.1+、.NET Core 2.0+ 和 .NET 5/6+。

`GetDocumentInfo()` 方法返回包含文档元数据的 `IDocumentInfo` 对象。

## 什么是文档比较中的元数据提取？
元数据提取是从比较操作中涉及的文档中检索描述性信息（如文件类型、页数和文件大小）的过程。GroupDocs.Comparison 通过统一的 API 暴露这些数据，便于记录、显示或用于条件处理。

## 为什么要从比较结果中提取元数据？
提取元数据可以帮助您创建详细的审计日志、根据类型路由文件，并针对大文档调整处理策略。了解文件类型、页数和大小后，您可以执行合规规则、估算处理时间，并在用户开始比较之前向其展示清晰的信息。

## 前提条件

1. **GroupDocs.Comparison for .NET** – 从 [official releases page](https://releases.groupdocs.com/comparison/net/) 安装库。  
   您也可以在 [GroupDocs releases page](https://releases.groupdocs.com/) 浏览所有发行版。  
2. **开发环境** – Visual Studio、VS Code 或任何支持 .NET 6+ 的 IDE。  
3. **示例文档** – 用于测试的两个文件（例如 `SOURCE.docx` 和 `TARGET.docx`）。API 支持超过 **50 种文档格式**。

## 导入命名空间

以下 `using` 指令让您可以访问核心比较引擎、文件处理工具以及元数据接口。

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

在实例化任何 GroupDocs 对象之前，需要先导入这些。

## 如何从比较结果中提取元数据？

`Comparer` 类加载源文档并协调比较过程。

要检索元数据，首先使用 `Comparer` 实例加载源文档，然后添加目标文档。比较引擎初始化后，对每个目标调用 `GetDocumentInfo()`，即可获得包含文件类型、页数和大小等属性的 `IDocumentInfo` 对象。此方法在所有受支持的格式中均可统一使用。

### 步骤 1：使用源文档初始化 Comparer

`Comparer` 是 GroupDocs.Comparison 中的核心类，用于加载源文档并协调比较操作。使用 `using` 块可确保所有非托管资源自动释放。

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **技巧提示：** 您可以向 `Comparer` 构造函数传入任意 `Stream`（文件、内存、云），而不仅限于文件路径。

### 步骤 2：为比较添加目标文档

`Add()` 方法接受额外的流或文件路径，实现一对多比较。

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **重要提示：** 添加文档的顺序会影响最终报告中更改的高亮方式。

### 步骤 3：从结果文档检索文档信息

`IDocumentInfo` 在所有受支持的格式中提供统一的文档元数据视图，如文件类型、页数和大小。

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **了解数据：** 返回的对象在 DOCX、PDF、XLSX 和 PPTX 中表现相同，您可以编写与格式无关的代码。

### 步骤 4：显示文档信息

获取 `IDocumentInfo` 实例后，您可以记录、存储或展示其属性。

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

最常用的三个属性是：

- **FileType** – 例如 `DOCX`、`PDF`、`XLSX`。  
- **PageCount** – 总页数或幻灯片数。  
- **Size** – 文件大小（字节），用于存储计算。

## 如何在 .NET 中获取文档大小？

`Size` 属性返回文件的字节大小。

可以直接通过 `IDocumentInfo` 实例的 `Size` 属性访问文档大小。该属性返回原始文件的精确字节数，您可以将其转换为千字节或兆字节用于显示或存储计算。它反映的是源文件大小，而非任何处理后的版本。

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **注意：** `Size` 值反映的是原始文件大小，而不是任何内部处理或压缩后的大小。

## 常见使用场景与实际应用

- **批量处理：** 使用文件类型将 DOCX 文件路由到 Word 专用工作流，将 PDF 路由到 PDF 优化管道。  
- **存储管理：** 自动将大于 10 MB 的文档归档到冷存储桶。  
- **用户反馈：** 在比较前显示页数和大小，以设定对处理时间的合理预期。  
- **质量保证：** 通过比较预期页数与实际页数，验证上传文件的完整性。

## 常见问题排查

- **文件访问错误：** 验证读取权限，并在开发期间使用绝对路径。  
- **大文件内存压力：** 优先使用流（`File.OpenRead`）而不是将整个文件加载到内存中。  
- **空引用异常：** 如果未添加目标，`FirstOrDefault()` 可能返回 `null`；在访问 `GetDocumentInfo()` 前务必检查。  

```csharp
var target = comparer.Targets.FirstOrDefault();
if (target != null)
{
    var info = target.GetDocumentInfo();
    // Use info safely
}
else
{
    Console.WriteLine("No target document was added.");
}
```

- **纯文本元数据受限：** 像 `.txt` 这样的格式可能不提供有意义的 `PageCount`。请防范缺失值。

## 性能考虑因素

- **流管理：** 始终在 `using` 语句中包装流，以及时释放文件句柄。  
- **缓存：** 将经常访问的元数据存入缓存，避免重复提取。  
- **批量操作：** 将文档分组处理，以降低开销并提升吞吐量。

## 生产环境最佳实践

- **健壮的错误处理：** 将元数据提取放在 try‑catch 块中，以优雅地处理损坏或不受支持的文件。  
- **全面日志记录：** 为每次比较记录文档类型、大小和页数，以帮助排查问题并满足审计合规。  
- **安全卫生：** 避免在 UI 消息中泄露完整文件路径或内部服务器细节。  
- **资源释放：** 及时释放 `Comparer` 实例，尤其在处理大量并发请求的 Web 服务中。

## 高级场景

### 多目标文档

如果将一个源文档与多个目标进行比较，可遍历 `Targets` 集合并从每个目标提取元数据。

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### 基于元数据的条件处理

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### 将元数据存入数据库

将 `FileType`、`PageCount` 和 `Size` 持久化到关系表中，以实现对数千次比较的报告和分析。

## 常见问题

**Q: GroupDocs.Comparison for .NET 是否兼容多种文档格式？**  
A: 是的，它支持 **50+ 种格式**，包括 DOCX、PDF、PPTX、XLSX、TXT 等众多格式，提供一致的元数据提取。

**Q: 我可以自定义比较设置而不影响元数据提取吗？**  
A: 完全可以。诸如灵敏度、变更类型和输出格式等设置与 `GetDocumentInfo()` 调用相互独立。

**Q: 是否有可用于评估的试用版？**  
A: 有，您可以从 [GroupDocs releases page](https://releases.groupdocs.com/) 下载免费试用版。试用版包含完整的元数据提取功能。

**Q: 我可以在哪里获取实现问题的支持？**  
A: 请使用 [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12) 获取社区帮助和 GroupDocs 团队的官方支持。

**Q: 生产部署有哪些许可选项？**  
A: GroupDocs 提供开发者、站点和 OEM 许可证。购买选项列在 [GroupDocs purchase page](https://purchase.groupdocs.com/buy) 上。

---

**最近更新:** 2026-06-15  
**测试环境:** GroupDocs.Comparison 6.0 for .NET  
**作者:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## 相关教程

- [文档元数据管理 .NET - GroupDocs.Comparison 完整指南](/comparison/net/metadata-management/)
- [获取文档属性 C# .NET - 提取文件元数据](/comparison/net/basic-usage/get-document-info-from-path/)
- [使用 GroupDocs.Comparison 保留目标元数据 – .NET 教程](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)