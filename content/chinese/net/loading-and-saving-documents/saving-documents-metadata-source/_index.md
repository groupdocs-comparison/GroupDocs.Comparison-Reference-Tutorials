---
title: 在 .NET 的 GroupDocs Comparison 中保存文档元数据源
linktitle: 在 .NET 的 GroupDocs Comparison 中保存文档元数据源
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs Comparison for .NET 保存文档元数据源。按照我们的分步指南在 .NET 中进行无缝文档比较。
weight: 14
url: /zh/net/loading-and-saving-documents/saving-documents-metadata-source/
---

# 在 .NET 的 GroupDocs Comparison 中保存文档元数据源

## 介绍
在软件开发领域，有效的文档比较对于各个行业（包括法律、金融和教育）至关重要。 GroupDocs Comparison for .NET 提供了一个强大的解决方案，用于无缝比较 .NET 应用程序中的文档。本教程将指导您完成使用 GroupDocs Comparison for .NET 保存文档元数据源的过程。通过执行这些步骤，您将能够充分利用该库的潜力来增强您的文档比较任务。
## 先决条件
在深入学习本教程之前，请确保您已设置以下先决条件：
1. 环境设置：在您的计算机上准备好 .NET 开发环境。
2.  GroupDocs Comparison 安装：从以下位置下载并安装 GroupDocs Comparison for .NET[下载链接](https://releases.groupdocs.com/comparison/net/).
3. 文档文件：准备要比较的源文档文件和目标文档文件。
4. 基本 C# 知识：熟悉 C# 编程语言基础知识，以理解提供的代码片段。

## 导入命名空间
在继续进行比较过程之前，请确保导入必要的命名空间：
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

## 第 1 步：定义输出目录和文件名
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
在此步骤中，我们定义保存比较文档的目录并指定输出文件名。
## 第 2 步：初始化比较器对象
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
```
在这里，我们初始化一个`Comparer`通过提供源文档的路径来获取对象。该对象将用于文档比较。
## 第三步：添加目标文档
```csharp
comparer.Add("TARGET.docx");
```
我们将目标文档添加到比较器对象中。这是将与源文档进行比较的文档。
## 步骤 4：比较文档并保存元数据源
```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Source });
```
在此步骤中，我们使用以下方法比较源文档和目标文档`Compare`比较器对象的方法。此外，我们指定输出文件名并设置`CloneMetadataType`到`MetadataType.Source`保存文档元数据源。
## 第5步：显示输出目录
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
最后，我们显示一条消息，指示文档比较成功，并提供保存比较文档的输出目录。

## 结论
总之，GroupDocs Comparison for .NET 为 .NET 应用程序中的文档比较任务提供了全面的解决方案。通过学习本教程，您已了解如何有效保存文档元数据源，从而增强文档比较过程。
## 常见问题解答
### GroupDocs Comparison for .NET 可以比较不同格式的文档吗？
是的，GroupDocs Comparison 支持比较各种格式的文档，包括 DOCX、PDF、PPTX 等。
### GroupDocs Comparison for .NET 是否有试用版？
是的，您可以访问试用版[这里](https://releases.groupdocs.com/).
### 我可以自定义比较文档的输出格式吗？
当然，GroupDocs Comparison 提供了根据您的要求自定义输出格式的选项。
### .NET 用户的 GroupDocs Comparison 是否可以获得技术支持？
是的，您可以向以下机构寻求技术帮助[支持论坛](https://forum.groupdocs.com/c/comparison/12).
### 在哪里可以购买 GroupDocs Comparison for .NET 的许可证？
您可以从 GroupDocs 网站购买许可证[这里](https://purchase.groupdocs.com/buy).