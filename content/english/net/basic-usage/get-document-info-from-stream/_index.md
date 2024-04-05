---
title: Get Document Info from Stream - GroupDocs.Comparison for .NET
linktitle: Get Document Info from Stream - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to efficiently compare documents in .NET using GroupDocs.Comparison, enhancing your document processing workflows seamlessly.
type: docs
weight: 14
url: /net/basic-usage/get-document-info-from-stream/
---
## Introduction
In the world of .NET development, efficiently comparing documents is a crucial task, whether you're working with Word documents, PDFs, or any other file format. GroupDocs.Comparison for .NET provides a robust solution for document comparison, allowing developers to streamline this process seamlessly. In this tutorial, we'll delve into the fundamentals of using GroupDocs.Comparison for .NET to compare documents, step by step. By the end, you'll have a solid understanding of how to leverage this powerful tool to enhance your document processing workflows.
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites:
### 1. Installation of GroupDocs.Comparison for .NET
Download and install GroupDocs.Comparison for .NET from the [download link](https://releases.groupdocs.com/comparison/net/).
### 2. Basic Knowledge of C# and .NET Development
Familiarize yourself with C# programming language and .NET framework basics to effectively follow along with the examples provided.

## Import Namespaces
Before we begin with the examples, make sure to import the necessary namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

## Step 1: Initialize Comparer Object
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```
In this step, we initialize a `Comparer` object by providing the source document file path as a parameter to its constructor.
## Step 2: Extract Document Info
```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```
Here, we retrieve the document information using the `GetDocumentInfo()` method, which returns an `IDocumentInfo` object containing details like file type, page count, and size.
## Step 3: Display Document Info
```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```
In this step, we print out the extracted document information including file type, page count, and size using the `Console.WriteLine()` method.

Finally, we wrap up by closing the `Comparer` object within a `using` block to ensure proper resource disposal.

## Conclusion
In this tutorial, we've covered the basics of using GroupDocs.Comparison for .NET to extract document information from a stream. By following the step-by-step guide, you've learned how to initialize the `Comparer` object, retrieve document info, and display it in your .NET applications. With this knowledge, you can now efficiently integrate document comparison functionality into your projects, enhancing productivity and efficiency.
## FAQ's
### Is GroupDocs.Comparison for .NET compatible with different document formats?
Yes, GroupDocs.Comparison for .NET supports various document formats including Word documents, PDFs, Excel sheets, and more.
### Can I try GroupDocs.Comparison for .NET before purchasing?
Yes, you can explore the capabilities of GroupDocs.Comparison for .NET with a free trial available at [here](https://releases.groupdocs.com/).
### Where can I find support for GroupDocs.Comparison for .NET?
You can seek assistance and join discussions in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12).
### Are temporary licenses available for GroupDocs.Comparison for .NET?
Yes, temporary licenses are available for testing and evaluation purposes. You can obtain one from [here](https://purchase.groupdocs.com/temporary-license/).
### Is GroupDocs.Comparison for .NET suitable for enterprise use?
Absolutely, GroupDocs.Comparison for .NET offers enterprise-level features and scalability, making it ideal for businesses of all sizes.
