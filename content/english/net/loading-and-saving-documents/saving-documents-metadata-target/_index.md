---
title: Saving Documents Metadata Target in GroupDocs Comparison for .NET
linktitle: Saving Documents Metadata Target in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to save documents metadata target using GroupDocs Comparison for .NET. Easy steps for efficient document comparison in your .NET applications.
weight: 15
url: /net/loading-and-saving-documents/saving-documents-metadata-target/
---
## Introduction
In this tutorial, we'll guide you through the process of saving document metadata target using GroupDocs Comparison for .NET. GroupDocs Comparison for .NET is a powerful library that allows you to compare and merge documents in your .NET applications.
## Prerequisites
Before you begin, make sure you have the following prerequisites:
1. GroupDocs Comparison for .NET: Ensure you have downloaded and installed GroupDocs Comparison for .NET. You can download it from [here](https://releases.groupdocs.com/comparison/net/).
2. .NET Development Environment: You should have a .NET development environment set up on your system.

## Import Namespaces
Before we start coding, let's import the necessary namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Step 1: Define Output Directory and File Name
First, specify the output directory where you want to save the compared documents and the name of the output file.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Step 2: Compare Documents and Save Metadata Target
Now, initialize a `Comparer` object with the source document and add the target document(s) you want to compare. Then, call the `Compare` method and specify the output file name along with the save options to clone metadata type as target.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
}
```
## Step 3: Display Success Message
Finally, display a success message indicating that the documents have been compared successfully and provide the path where the output file is saved.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
Congratulations! You have successfully saved documents metadata target using GroupDocs Comparison for .NET.

## Conclusion
In this tutorial, we've covered the process of saving documents metadata target using GroupDocs Comparison for .NET. By following the steps outlined above, you can efficiently compare and save documents in your .NET applications.
## FAQ's
### Can I compare documents of different formats?
Yes, GroupDocs Comparison for .NET supports comparing documents of various formats such as DOCX, PDF, PPTX, XLSX, and more.
### Is there a trial version available?
Yes, you can get a free trial from [here](https://releases.groupdocs.com/).
### How can I get support if I encounter any issues?
You can seek assistance from the GroupDocs Comparison community forum [here](https://forum.groupdocs.com/c/comparison/12).
### Can I customize the output format of compared documents?
Yes, you can customize the output format and other options according to your requirements.
### Is GroupDocs Comparison for .NET suitable for large-scale document comparison tasks?
Yes, GroupDocs Comparison for .NET is designed to handle large-scale document comparison tasks efficiently.
