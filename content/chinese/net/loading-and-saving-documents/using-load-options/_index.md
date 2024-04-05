---
title: 在 .NET 的 GroupDocs 比较中使用加载选项
linktitle: 在 .NET 的 GroupDocs 比较中使用加载选项
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs Comparison for .NET 中的加载选项来无缝比较具有自定义字体的文档。
type: docs
weight: 13
url: /zh/net/loading-and-saving-documents/using-load-options/
---
## 介绍
欢迎来到我们关于在 .NET 的 GroupDocs Comparison 中使用加载选项的教程！在本教程中，我们将引导您逐步完成使用“加载选项”比较文档的过程。无论您是初学者还是经验丰富的开发人员，本指南都将帮助您将 GroupDocs Comparison 无缝集成到您的 .NET 应用程序中。
## 先决条件
在开始之前，请确保您已设置以下先决条件：
### 1. 安装 .NET 的 GroupDocs Comparison
您可以从以下位置下载 GroupDocs Comparison for .NET 库：[这个链接](https://releases.groupdocs.com/comparison/net/)。请按照文档中提供的安装说明进行操作，以顺利完成设置过程。
### 2. 获取源文件和目标文件
确保您准备好源文档和目标文档以供比较。这些文档可以采用多种格式，例如 DOCX、PDF 或 TXT。
## 导入命名空间
在深入研究代码之前，让我们为应用程序导入必要的命名空间：
```csharp
using System;
using System.IO;
using System.Collections.Generic;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
现在，让我们将提供的示例代码分解为多个步骤：
## 第 1 步：定义自定义字体目录
```csharp
List<string> fontDirectories = new List<string>();
//需要设置字体文件的目录
fontDirectories.Add(Constants.CUSTOM_FONT);
```
在这一步中，我们创建一个字符串类型的列表来保存自定义字体所在的目录。确保更换`Constants.CUSTOM_FONT`与包含自定义字体的实际目录路径。
## 第 2 步：实例化加载选项
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontDirectories = fontDirectories;
```
在这里，我们实例化一个`LoadOptions`对象并为其分配自定义字体目录。此步骤准备加载具有自定义字体的文档所需的选项。
## 第 3 步：比较文档
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx"), loadOptions))
{
    comparer.Add(File.OpenRead("TARGET.docx"));
    comparer.Compare(File.Create(Path.Combine("Your Document Directory", "RESULT.docx")));
}
```
现在，我们创建一个`Comparer`使用源文档和先前定义的加载选项的对象。然后，我们将目标文档添加到比较器中并进行比较。最后，我们将比较后的文档保存到指定目录中。
## 第4步：显示成功消息
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```
比较过程完成后，我们会显示一条成功消息以及保存比较文档的目录。
## 结论
总之，本教程提供了有关在 GroupDocs Comparison for .NET 中使用加载选项的综合指南。通过遵循分步说明，您可以将文档比较功能无缝集成到您的 .NET 应用程序中。
## 常见问题解答
### 问：GroupDocs Comparison 可以处理不同格式的文档吗？
是的，GroupDocs Comparison 支持比较各种格式的文档，例如 DOCX、PDF、TXT 等。
### 问：购买前有试用版吗？
是的，您可以访问 GroupDocs Comparison 的免费试用版：[这个链接](https://releases.groupdocs.com/).
### 问：如何获得 GroupDocs Comparison 的支持？
您可以从 GroupDocs 社区论坛寻求支持[这里](https://forum.groupdocs.com/c/comparison/12).
### 问：我可以在比较文档中使用自定义字体吗？
绝对地！ GroupDocs Comparison 允许您指定自定义字体目录以实现准确的文档呈现。
### 问：临时许可证是否可用于测试目的？
是的，您可以从以下位置获取用于测试和评估目的的临时许可证：[这个链接](https://purchase.groupdocs.com/temporary-license/).