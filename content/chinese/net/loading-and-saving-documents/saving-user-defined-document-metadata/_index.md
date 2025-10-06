---
"description": "了解如何使用 GroupDocs Compare for .NET 保存用户定义的文档元数据。通过分步说明轻松比较和操作元数据。"
"linktitle": "在 GroupDocs 比较中保存 .NET 的用户定义文档元数据"
"second_title": "GroupDocs.Comparison .NET API"
"title": "在 GroupDocs 比较中保存 .NET 的用户定义文档元数据"
"url": "/zh/net/loading-and-saving-documents/saving-user-defined-document-metadata/"
"weight": 16
type: docs
---
# 在 GroupDocs 比较中保存 .NET 的用户定义文档元数据

## 介绍
在本教程中，我们将探索如何使用 GroupDocs Compare for .NET 保存用户定义的文档元数据。元数据对于高效地组织和管理文档至关重要。使用 GroupDocs Compare，您可以轻松比较和操作元数据，以满足您的特定需求。
## 先决条件
在开始之前，请确保您满足以下先决条件：
1. GroupDocs .NET 比较：从以下位置下载并安装 GroupDocs .NET 比较 [这里](https://releases。groupdocs.com/comparison/net/).
2. 开发环境：确保您的系统上安装了合适的开发环境，例如 Visual Studio。
3. 源文档和目标文档：准备要比较和操作元数据的源文档和目标文档。

## 导入命名空间
首先，导入必要的命名空间以访问 GroupDocs Compare for .NET 提供的功能。
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 步骤 1：定义输出目录和文件名
定义要保存比较文档的目录并指定输出文件名。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## 步骤 2：初始化比较器并添加文档
初始化 `Comparer` 对象与源文档并添加目标文档进行比较。
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## 步骤 3：指定元数据选项
指定比较文档中保存的元数据选项。在本例中，我们设置 `CloneMetadataType` 到 `MetadataType.FileAuthor` 并提供详细信息 `FileAuthorMetadata`。
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
## 步骤 4：比较文档并保存元数据
将文档与指定的元数据选项进行比较并保存比较的文档。
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## 步骤5：显示成功消息
显示成功消息，表明文档已成功比较以及输出位置。
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs Compare for .NET 保存用户定义的文档元数据。按照以下步骤，您可以高效地比较文档，同时根据需要保存和操作元数据。
## 常见问题解答
### GroupDocs Compare for .NET 能处理各种文档格式吗？
是的，GroupDocs Compare 支持多种文档格式，包括 DOCX、PDF、PPTX、XLSX 等。
### GroupDocs Compare for .NET 有免费试用版吗？
是的，您可以免费试用 [这里](https://releases。groupdocs.com/).
### 我可以根据需要自定义元数据选项吗？
当然，GroupDocsComparison 提供了灵活的选项来定制文档比较期间的元数据处理。
### GroupDocs Compare 是否提供技术支持？
是的，您可以从 GroupDocs 比较论坛获得技术支持 [这里](https://forum。groupdocs.com/c/comparison/12).
### 我可以在哪里购买 GroupDocs Compare for .NET 的许可证？
您可以从 GroupDocs 网站购买许可证 [这里](https://purchase。groupdocs.com/buy).