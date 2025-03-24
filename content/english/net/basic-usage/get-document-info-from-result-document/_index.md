---
title: Get Document Info from Result Document - GroupDocs.Comparison for .NET
linktitle: Get Document Info from Result Document - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to retrieve document info from result document using GroupDocs.Comparison for .NET. Easy steps explained for .NET developers.
weight: 12
url: /net/basic-usage/get-document-info-from-result-document/
---

# Get Document Info from Result Document - GroupDocs.Comparison for .NET

## Introduction
In the realm of .NET development, managing and comparing documents is a common requirement. GroupDocs.Comparison for .NET offers a robust solution for this task, allowing developers to seamlessly integrate document comparison functionalities into their applications. This tutorial will guide you through the process of utilizing GroupDocs.Comparison for .NET to retrieve document information from the result document. 
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites:
1. GroupDocs.Comparison for .NET: Install the GroupDocs.Comparison for .NET library. You can download it from [here](https://releases.groupdocs.com/comparison/net/).
2. Development Environment: Set up your .NET development environment, including IDE (such as Visual Studio) and necessary configurations.
3. Document Files: Prepare the source and target document files (e.g., `SOURCE.docx` and `TARGET.docx`) for comparison.

## Import Namespaces
Firstly, you need to import the necessary namespaces to access GroupDocs.Comparison functionalities.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

## Step 1: Initialize Comparer with Source Document
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```
In this step, we initialize a `Comparer` object with the source document (`SOURCE.docx` in this case) using a `using` statement to ensure proper resource disposal.
## Step 2: Add Target Document for Comparison
```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```
Here, we add the target document (`TARGET.docx`) to the comparer object for comparison.
## Step 3: Retrieve Document Info from Result Document
```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```
This step retrieves document information from the result document. It accesses the target document using `FirstOrDefault()` and then calls `GetDocumentInfo()` to obtain information such as file type, number of pages, and document size.
## Step 4: Display Document Info
```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```
Here, we display the retrieved document information including file type, number of pages, and document size in bytes.

## Conclusion
GroupDocs.Comparison for .NET simplifies the process of document comparison in .NET applications. By following this tutorial, you've learned how to retrieve document information from the result document using GroupDocs.Comparison for .NET. Incorporate these techniques into your projects to enhance document management capabilities.
## FAQ's
### Is GroupDocs.Comparison for .NET compatible with various document formats?
Yes, GroupDocs.Comparison for .NET supports a wide range of document formats including DOCX, PDF, PPTX, XLSX, and more.
### Can I customize the document comparison settings?
Absolutely, GroupDocs.Comparison for .NET offers extensive customization options for document comparison to suit your specific requirements.
### Is there a trial version available for evaluation?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### How can I get support for GroupDocs.Comparison for .NET?
You can seek assistance and engage with the community at the GroupDocs.Comparison forum [here](https://forum.groupdocs.com/c/comparison/12).
### What are the licensing options for GroupDocs.Comparison for .NET?
You can explore licensing options and purchase a license from [here](https://purchase.groupdocs.com/buy).
