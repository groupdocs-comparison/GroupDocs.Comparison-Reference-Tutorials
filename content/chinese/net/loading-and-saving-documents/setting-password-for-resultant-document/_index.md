---
title: 为 .NET 的 GroupDocs 比较中的结果文档设置密码
linktitle: 为 .NET 的 GroupDocs 比较中的结果文档设置密码
second_title: GroupDocs.Comparison .NET API
description: 了解如何在 GroupDocs Comparison for .NET 中为生成的文档设置密码。增强安全性并保护您的比较文件。
weight: 17
url: /zh/net/loading-and-saving-documents/setting-password-for-resultant-document/
---
## 介绍
在本教程中，我们将指导您完成使用 GroupDocs Comparison for .NET 为生成的文档设置密码的过程。此功能为您比较的文档增加了额外的安全层，确保只有授权的个人才能访问它们。
## 先决条件
在继续之前，请确保您具备以下条件：
1. 适用于 .NET 的 GroupDocs Comparison：确保您的 .NET 环境中安装了 GroupDocs Comparison 库。您可以从以下位置下载：[这里](https://releases.groupdocs.com/comparison/net/).
2. 源文件和目标文件：准备源文件（`SOURCE.docx`）和目标文档（`TARGET.docx`）您想要比较并为结果文档设置密码。

## 导入命名空间
首先，您需要将必要的命名空间导入到 C# 项目中才能使用 GroupDocs 比较功能：
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
指定要保存结果文档的目录并定义输出文件的名称。
## 步骤 2：将文档与密码设置进行比较
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    CompareOptions cOptions = new CompareOptions
    {
        PasswordSaveOption = PasswordSaveOption.User
    };
    SaveOptions sOptions = new SaveOptions()
    {
        Password = "YourPasswordHere"
    };
    comparer.Compare(outputFileName, sOptions, cOptions);
}
```
在这里，我们初始化一个`Comparer`对象与源文档。然后，我们添加要比较的目标文档。我们设置`PasswordSaveOption`到`User`指定密码将应用于生成的文档。在中提供所需的密码`Password`的财产`SaveOptions`目的。
## 第3步：显示成功消息
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
最后显示成功信息，表示文档比对成功，并且所设置的密码的文档已保存到指定目录中。

## 结论
在 GroupDocs Comparison for .NET 中为生成的文档设置密码可为比较文档添加额外的安全层，确保机密性和完整性。通过遵循本教程中概述的步骤，您可以在 .NET 应用程序中轻松实现此功能。
## 常见问题解答
### 我可以比较不同格式的文档吗？
是的，GroupDocs Comparison for .NET 支持比较各种格式的文档，例如 DOCX、PDF、PPTX、XLSX 等。
### 有试用版吗？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).
### 如果遇到任何问题，我如何获得支持？
您可以从 GroupDocs Comparison 社区论坛寻求帮助[这里](https://forum.groupdocs.com/c/comparison/12).
### 我需要许可证才能使用 GroupDocs Comparison for .NET 吗？
是的，您可以从以下位置购买许可证[这里](https://purchase.groupdocs.com/buy)或获得临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).
### 是否有任何适用于 .NET 的 GroupDocs Comparison 的文档？
是的，您可以访问文档[这里](https://tutorials.groupdocs.com/comparison/net/).