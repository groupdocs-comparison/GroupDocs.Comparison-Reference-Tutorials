---
title: 页面预览后清理资源
linktitle: 页面预览后清理资源
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs.Comparison for .NET 逐步比较文档。通过高效的文档管理增强您的 .NET 应用程序。
type: docs
weight: 13
url: /zh/net/document-comparison/clean-resources-after-page-previews/
---
## 介绍
在 .NET 开发领域，有效管理和比较文档对于从律师事务所到教育机构的各种应用程序至关重要。幸运的是，借助 GroupDocs.Comparison for .NET 等工具，开发人员可以轻松简化比较文档的过程。在本教程中，我们将逐步探索如何利用 GroupDocs.Comparison for .NET 来比较文档。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
1.  GroupDocs.Comparison for .NET：从以下位置下载并安装该库[这里](https://releases.groupdocs.com/comparison/net/).
2. .NET 开发环境：确保您的计算机上设置了有效的 .NET 开发环境。
3. 文档样本：准备要比较的源文档和目标文档。

## 导入命名空间
在您的 .NET 项目中，首先导入必要的命名空间以访问 GroupDocs.Comparison for .NET 的功能。

```csharp
using System;
using System.IO;
```

## 第 1 步：定义输出目录和文件名
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```
## 第 2 步：初始化比较器并添加文档
```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
{
    comparer.Add("TARGET.pptx");
```
## 第 3 步：执行比较并生成输出
```csharp
    comparer.Compare(File.Create(outputFileName));
```
## 第 4 步：生成文档预览
```csharp
    Document document = new Document(File.OpenRead(outputFileName));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    previewOptions.ReleasePageStream = UserReleaseStreamMethod;
    document.GeneratePreview(previewOptions);
}
```
## 第5步：显示成功消息
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

## 结论
总之，GroupDocs.Comparison for .NET 提供了一个强大的解决方案，可以在 .NET 应用程序中轻松比较文档。通过遵循本教程中概述的步骤，开发人员可以将文档比较功能无缝集成到他们的项目中，从而提高生产力和效率。
## 常见问题解答
### GroupDocs.Comparison for .NET 是否与不同的文档格式兼容？
是的，GroupDocs.Comparison for .NET 支持多种文档格式，包括 DOCX、PPTX、XLSX、PDF 等。
### 我可以自定义比较文档的输出格式吗？
当然，GroupDocs.Comparison for .NET 可以根据您的要求灵活地选择输出格式。
### 是否有可用于测试目的的试用版？
是的，您可以通过免费试用版探索 GroupDocs.Comparison for .NET 的功能[这里](https://releases.groupdocs.com/).
### 对于与 GroupDocs.Comparison for .NET 相关的任何问题或查询，如何获得支持？
您可以从 GroupDocs.Comparison 社区论坛寻求帮助[这里](https://forum.groupdocs.com/c/comparison/12).
### 在哪里可以购买 GroupDocs.Comparison for .NET 的许可证？
您可以从以下位置购买 GroupDocs.Comparison for .NET 的许可证：[这个链接](https://purchase.groupdocs.com/buy).