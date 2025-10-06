---
"description": "了解如何使用 GroupDocs .NET 比较工具接受和拒绝文档中的更改。轻松简化您的文档工作流程。"
"linktitle": "接受和拒绝 .NET GroupDocs 比较中的更改"
"second_title": "GroupDocs.Comparison .NET API"
"title": "接受和拒绝 .NET GroupDocs 比较中的更改"
"url": "/zh/net/documents-and-folder-comparison/accept-reject-changes-dotnet/"
"weight": 10
type: docs
---
# 接受和拒绝 .NET GroupDocs 比较中的更改

## 介绍
在文档管理和协作领域，确保文件的准确性和完整性至关重要。GroupDocs .NET 比较工具是一款强大的解决方案，使开发人员能够轻松地接受和拒绝文档中的更改，从而简化工作流程并提高生产力。本教程将指导您使用 GroupDocs .NET 比较工具接受和拒绝更改的过程，并将每个步骤分解，以便清晰易懂地实施。
## 先决条件
在深入学习本教程之前，请确保您已满足以下先决条件：
### 环境设置
1. 安装 .NET SDK：如果您还没有安装，请从 .NET 网站下载并安装适合您的操作系统的 .NET SDK。
2. 安装 GroupDocs .NET 比较：从提供的 [下载链接](https://releases.groupdocs.com/comparison/net/) 并按照安装说明进行操作。
3. 熟悉 C# 编程：本教程假设您对 C# 编程语言及其语法有基本的了解。

## 导入命名空间
首先，将必要的命名空间导入到您的项目中。这些命名空间将提供对文档比较和操作所需功能的访问。

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## 步骤 1：指定输出目录和文件名
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
确保更换 `"Your Document Directory"` 使用所需输出目录的路径。
## 步骤 2：初始化比较器并比较文档
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
此代码使用源文档初始化 Comparer 对象，并添加目标文档进行比较。然后，执行比较过程。
## 步骤 3：检索和操作更改
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
从比较中检索更改并根据需要进行操作。在此示例中，更改先被拒绝，然后被接受。生成的文档将相应地保存。

## 结论
总而言之，GroupDocs .NET 比较工具提供了一个无缝的解决方案，用于接受和拒绝文档中的更改。通过遵循本教程中概述的步骤，开发人员可以有效地将此功能集成到他们的应用程序中，从而确保文档的准确性并增强协作。
## 常见问题解答
### GroupDocs Compare for .NET 可以比较不同格式的文档吗？
是的，GroupDocs Compare for .NET 支持各种格式的文档比较，例如 DOCX、PDF、PPTX 等。
### .NET 的 GroupDocs 比较是否与 .NET Core 兼容？
是的，GroupDocs Compare for .NET 与 .NET Framework 和 .NET Core 兼容。
### 我可以自定义比较文档中更改的外观吗？
当然，GroupDocs Compare for .NET 提供了广泛的选项来自定义更改的外观，包括颜色、样式等。
### GroupDocs Compare for .NET 是否支持多页文档比较？
是的，GroupDocs Compare for .NET 支持精确、准确的多页文档比较。
### GroupDocs Compare for .NET 有试用版吗？
是的，您可以从提供的 GroupDocs 比较中免费试用 .NET [关联](https://releases。groupdocs.com/).