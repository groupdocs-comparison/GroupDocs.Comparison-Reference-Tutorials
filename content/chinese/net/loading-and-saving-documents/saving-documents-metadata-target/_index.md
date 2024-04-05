---
title: 在 .NET 的 GroupDocs 比较中保存文档元数据目标
linktitle: 在 .NET 的 GroupDocs 比较中保存文档元数据目标
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs Comparison for .NET 保存文档元数据目标。在 .NET 应用程序中进行高效文档比较的简单步骤。
type: docs
weight: 15
url: /zh/net/loading-and-saving-documents/saving-documents-metadata-target/
---
## 介绍
在本教程中，我们将指导您完成使用 GroupDocs Comparison for .NET 保存文档元数据目标的过程。 GroupDocs Comparison for .NET 是一个功能强大的库，允许您比较和合并 .NET 应用程序中的文档。
## 先决条件
在开始之前，请确保您具备以下先决条件：
1.  GroupDocs Comparison for .NET：确保您已下载并安装 GroupDocs Comparison for .NET。您可以从以下位置下载：[这里](https://releases.groupdocs.com/comparison/net/).
2. .NET 开发环境：您的系统上应该设置有 .NET 开发环境。

## 导入命名空间
在开始编码之前，让我们导入必要的名称空间：
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 第 1 步：定义输出目录和文件名
首先，指定要保存比较文档的输出目录以及输出文件的名称。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## 第 2 步：比较文档并保存元数据目标
现在，初始化一个`Comparer`对象与源文档并添加要比较的目标文档。然后，致电`Compare`方法并指定输出文件名以及保存选项以将元数据类型克隆为目标。
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
}
```
## 第3步：显示成功消息
最后，显示一条成功消息，表明文档已成功比较，并提供输出文件的保存路径。
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
恭喜！您已使用 GroupDocs Comparison for .NET 成功保存了文档元数据目标。

## 结论
在本教程中，我们介绍了使用 GroupDocs Comparison for .NET 保存文档元数据目标的过程。通过执行上述步骤，您可以在 .NET 应用程序中高效地比较和保存文档。
## 常见问题解答
### 我可以比较不同格式的文档吗？
是的，GroupDocs Comparison for .NET 支持比较各种格式的文档，例如 DOCX、PDF、PPTX、XLSX 等。
### 有试用版吗？
是的，您可以从以下位置获得免费试用[这里](https://releases.groupdocs.com/).
### 如果遇到任何问题，我如何获得支持？
您可以从 GroupDocs Comparison 社区论坛寻求帮助[这里](https://forum.groupdocs.com/c/comparison/12).
### 我可以自定义比较文档的输出格式吗？
是的，您可以根据您的要求自定义输出格式和其他选项。
### GroupDocs Comparison for .NET 是否适合大规模文档比较任务？
是的，GroupDocs Comparison for .NET 旨在高效处理大规模文档比较任务。