---
title: Saving Documents Metadata Source in GroupDocs Comparison for .NET
linktitle: Saving Documents Metadata Source in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to save document metadata source using GroupDocs Comparison for .NET. Follow our step-by-step guide for seamless document comparison in your .NET.
type: docs
weight: 14
url: /net/loading-and-saving-documents/saving-documents-metadata-source/
---
## Introduction
In the world of software development, efficient document comparison is crucial for various industries, including legal, finance, and education. GroupDocs Comparison for .NET offers a powerful solution for comparing documents in .NET applications seamlessly. This tutorial will guide you through the process of using GroupDocs Comparison for .NET to save document metadata source. By following these steps, you'll be able to harness the full potential of this library to enhance your document comparison tasks.
## Prerequisites
Before diving into the tutorial, ensure you have the following prerequisites set up:
1. Environment Setup: Have a .NET development environment ready on your machine.
2. GroupDocs Comparison Installation: Download and install GroupDocs Comparison for .NET from the [download link](https://releases.groupdocs.com/comparison/net/).
3. Document Files: Prepare the source and target document files that you want to compare.
4. Basic C# Knowledge: Familiarize yourself with C# programming language basics to understand the code snippets provided.

## Import Namespaces
Before proceeding with the comparison process, make sure to import the necessary namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

## Step 1: Define Output Directory and File Name
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
In this step, we define the directory where the compared document will be saved and specify the output file name.
## Step 2: Initialize Comparer Object
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
```
Here, we initialize a `Comparer` object by providing the path to the source document. This object will be used for document comparison.
## Step 3: Add Target Document
```csharp
comparer.Add("TARGET.docx");
```
We add the target document to the comparer object. This is the document against which the source document will be compared.
## Step 4: Compare Documents and Save Metadata Source
```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Source });
```
In this step, we compare the source and target documents using the `Compare` method of the comparer object. Additionally, we specify the output file name and set `CloneMetadataType` to `MetadataType.Source` to save document metadata source.
## Step 5: Display Output Directory
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
Finally, we display a message indicating successful document comparison and provide the output directory where the compared document is saved.

## Conclusion
In conclusion, GroupDocs Comparison for .NET offers a comprehensive solution for document comparison tasks in .NET applications. By following this tutorial, you've learned how to save document metadata source efficiently, enhancing your document comparison process.
## FAQ's
### Can GroupDocs Comparison for .NET compare documents of different formats?
Yes, GroupDocs Comparison supports comparing documents in various formats, including DOCX, PDF, PPTX, and more.
### Is there a trial version available for GroupDocs Comparison for .NET?
Yes, you can access the trial version from [here](https://releases.groupdocs.com/).
### Can I customize the output format of compared documents?
Absolutely, GroupDocs Comparison provides options to customize the output format according to your requirements.
### Is technical support available for GroupDocs Comparison for .NET users?
Yes, you can seek technical assistance from the [support forum](https://forum.groupdocs.com/c/comparison/12).
### Where can I purchase a license for GroupDocs Comparison for .NET?
You can purchase a license from the GroupDocs website [here](https://purchase.groupdocs.com/buy).
