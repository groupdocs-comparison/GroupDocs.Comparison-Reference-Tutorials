---
title: 接受和拒绝 .NET 的 GroupDocs 比较中的更改
linktitle: 接受和拒绝 .NET 的 GroupDocs 比较中的更改
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs Comparison for .NET 接受和拒绝文档中的更改。轻松简化您的文档工作流程。
weight: 10
url: /zh/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---
## 介绍
在文档管理和协作领域，确保文件的准确性和完整性至关重要。 GroupDocs Comparison for .NET 成为一种强大的解决方案，使开发人员能够轻松接受和拒绝文档中的更改，从而简化工作流程并提高工作效率。本教程将指导您使用 GroupDocs Comparison for .NET 完成接受和拒绝更改的过程，并分解每个步骤以使其清晰且易于实施。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
### 环境设置
1. 安装 .NET SDK：如果尚未安装，请从 .NET 网站下载并安装适合您的操作系统的 .NET SDK。
2. 安装 GroupDocs Comparison for .NET：从提供的 GroupDocs Comparison for .NET 获取最新版本[下载链接](https://releases.groupdocs.com/comparison/net/)并按照安装说明进行操作。
3. 熟悉 C# 编程：本教程假设您对 C# 编程语言及其语法有基本的了解。

## 导入命名空间
首先，将必要的命名空间导入到您的项目中。这些命名空间将提供对文档比较和操作所需的功能的访问。

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## 第 1 步：指定输出目录和文件名
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
确保更换`"Your Document Directory"`以及所需输出目录的路径。
## 第 2 步：初始化比较器并比较文档
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
此代码使用源文档初始化 Comparer 对象，并添加目标文档进行比较。然后，它执行比较过程。
## 第 3 步：检索并操作更改
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
从比较中检索更改并根据需要对其进行操作。在此示例中，更改首先被拒绝，然后被接受。生成的文档将被相应保存。

## 结论
总之，GroupDocs Comparison for .NET 为接受和拒绝文档中的更改提供了无缝解决方案。通过遵循本教程中概述的步骤，开发人员可以有效地将此功能集成到他们的应用程序中，确保文档准确性并增强协作。
## 常见问题解答
### GroupDocs Comparison for .NET 可以比较不同格式的文档吗？
是的，GroupDocs Comparison for .NET 支持比较各种格式的文档，例如 DOCX、PDF、PPTX 等。
### .NET 的 GroupDocs Comparison 是否与 .NET Core 兼容？
是的，GroupDocs Comparison for .NET 与 .NET Framework 和 .NET Core 兼容。
### 我可以自定义比较文档中更改的外观吗？
当然，GroupDocs Comparison for .NET 提供了广泛的选项来自定义更改的外观，包括颜色、样式等。
### GroupDocs Comparison for .NET 支持多页文档比较吗？
是的，GroupDocs Comparison for .NET 支持精确、准确地比较多页文档。
### GroupDocs Comparison for .NET 是否有试用版？
是的，您可以从提供的网站免费试用 GroupDocs Comparison for .NET[关联](https://releases.groupdocs.com/).