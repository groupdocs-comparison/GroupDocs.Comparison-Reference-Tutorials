---
title: 在 .NET 的 GroupDocs Comparison 中保存用户定义的文档元数据
linktitle: 在 .NET 的 GroupDocs Comparison 中保存用户定义的文档元数据
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs Comparison for .NET 保存用户定义的文档元数据。通过分步说明轻松比较和操作元数据。
weight: 16
url: /zh/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---

# 在 .NET 的 GroupDocs Comparison 中保存用户定义的文档元数据

## 介绍
在本教程中，我们将探讨如何使用 GroupDocs Comparison for .NET 保存用户定义的文档元数据。元数据对于有效组织和管理文档至关重要。通过 GroupDocs Comparison，您可以轻松比较和操作元数据以满足您的特定要求。
## 先决条件
在我们开始之前，请确保您满足以下先决条件：
1. 适用于 .NET 的 GroupDocs Comparison：从以下位置下载并安装适用于 .NET 的 GroupDocs Comparison[这里](https://releases.groupdocs.com/comparison/net/).
2. 开发环境：确保您的系统上安装了合适的开发环境，例如 Visual Studio。
3. 源文档和目标文档：准备要比较和操作元数据的源文档和目标文档。

## 导入命名空间
首先，导入必要的命名空间以访问 GroupDocs Comparison for .NET 提供的功能。
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 第 1 步：定义输出目录和文件名
定义要保存比较文档的目录并指定输出文件名。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## 第 2 步：初始化比较器并添加文档
初始化`Comparer`对象与源文档并添加目标文档进行比较。
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## 步骤 3：指定元数据选项
指定用于保存在比较文档中的元数据选项。在这个例子中，我们设置`CloneMetadataType`到`MetadataType.FileAuthor`并提供详细信息`FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## 第 4 步：比较文档并保存元数据
将文档与指定的元数据选项进行比较并保存比较的文档。
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## 第5步：显示成功消息
显示成功消息，指示文档已成功比较以及输出位置。
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs Comparison for .NET 保存用户定义的文档元数据。通过执行这些步骤，您可以有效地比较文档，同时根据您的要求保留和操作元数据。
## 常见问题解答
### GroupDocs Comparison for .NET 可以处理各种文档格式吗？
是的，GroupDocs Comparison 支持多种文档格式，包括 DOCX、PDF、PPTX、XLSX 等。
### GroupDocs Comparison for .NET 是否有免费试用版？
是的，您可以免费试用[这里](https://releases.groupdocs.com/).
### 我可以根据需要自定义元数据选项吗？
当然，GroupDocs Comparison 提供了灵活的选项来自定义文档比较期间的元数据处理。
### GroupDocs Comparison 是否提供技术支持？
是的，您可以从 GroupDocs Comparison 论坛获得技术支持[这里](https://forum.groupdocs.com/c/comparison/12).
### 在哪里可以购买 GroupDocs Comparison for .NET 的许可证？
您可以从 GroupDocs 网站购买许可证[这里](https://purchase.groupdocs.com/buy).