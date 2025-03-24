---
title: Saving User Defined Document Metadata in GroupDocs Comparison for .NET
linktitle: Saving User Defined Document Metadata in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to save user-defined document metadata using GroupDocs Comparison for .NET. Easily compare and manipulate metadata with step-by-step instructions.
weight: 16
url: /net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## Introduction
In this tutorial, we will explore how to save user-defined document metadata using GroupDocs Comparison for .NET. Metadata is crucial for organizing and managing documents efficiently. With GroupDocs Comparison, you can easily compare and manipulate metadata to meet your specific requirements.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
1. GroupDocs Comparison for .NET: Download and install GroupDocs Comparison for .NET from [here](https://releases.groupdocs.com/comparison/net/).
2. Development Environment: Make sure you have a suitable development environment such as Visual Studio installed on your system.
3. Source and Target Documents: Prepare the source and target documents that you want to compare and manipulate metadata for.

## Import Namespaces
First, import the necessary namespaces to access the functionalities provided by GroupDocs Comparison for .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Step 1: Define Output Directory and File Name
Define the directory where you want to save the compared document and specify the output file name.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Step 2: Initialize Comparer and Add Documents
Initialize the `Comparer` object with the source document and add the target document for comparison.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Step 3: Specify Metadata Options
Specify the metadata options for saving in the compared document. In this example, we set `CloneMetadataType` to `MetadataType.FileAuthor` and provide details for `FileAuthorMetadata`.
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
## Step 4: Compare Documents and Save Metadata
Compare the documents with specified metadata options and save the compared document.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Step 5: Display Success Message
Display a success message indicating that the documents have been compared successfully and the output location.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Conclusion
In this tutorial, we've learned how to save user-defined document metadata using GroupDocs Comparison for .NET. By following these steps, you can efficiently compare documents while preserving and manipulating metadata according to your requirements.
## FAQ's
### Can GroupDocs Comparison for .NET handle various document formats?
Yes, GroupDocs Comparison supports a wide range of document formats including DOCX, PDF, PPTX, XLSX, and more.
### Is there a free trial available for GroupDocs Comparison for .NET?
Yes, you can access the free trial [here](https://releases.groupdocs.com/).
### Can I customize metadata options according to my needs?
Absolutely, GroupDocs Comparison provides flexible options to customize metadata handling during document comparison.
### Does GroupDocs Comparison offer technical support?
Yes, you can get technical support from the GroupDocs Comparison forum [here](https://forum.groupdocs.com/c/comparison/12).
### Where can I purchase a license for GroupDocs Comparison for .NET?
You can purchase a license from the GroupDocs website [here](https://purchase.groupdocs.com/buy).
