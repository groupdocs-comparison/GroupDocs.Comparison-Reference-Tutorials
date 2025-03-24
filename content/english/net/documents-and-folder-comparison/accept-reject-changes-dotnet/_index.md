---
title: Accept and Reject Changes in GroupDocs Comparison for .NET
linktitle: Accept and Reject Changes in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to accept and reject changes in documents using GroupDocs Comparison for .NET. Streamline your document workflows effortlessly.
weight: 10
url: /net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---
## Introduction
In the realm of document management and collaboration, ensuring the accuracy and integrity of files is paramount. GroupDocs Comparison for .NET emerges as a robust solution, empowering developers to effortlessly accept and reject changes within documents, thereby streamlining workflows and enhancing productivity. This tutorial will guide you through the process of accepting and rejecting changes using GroupDocs Comparison for .NET, breaking down each step for clarity and ease of implementation.
## Prerequisites
Before diving into the tutorial, ensure you have the following prerequisites in place:
### Environment Setup
1. Install .NET SDK: If you haven't already, download and install the .NET SDK suitable for your operating system from the .NET website.
2. Install GroupDocs Comparison for .NET: Obtain the latest version of GroupDocs Comparison for .NET from the provided [download link](https://releases.groupdocs.com/comparison/net/) and follow the installation instructions.
3. Familiarity with C# Programming: This tutorial assumes a basic understanding of C# programming language and its syntax.

## Import Namespaces
To begin with, import the necessary namespaces into your project. These namespaces will provide access to the functionalities required for document comparison and manipulation.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Step 1: Specify Output Directory and File Names
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
Ensure to replace `"Your Document Directory"` with the path to your desired output directory.
## Step 2: Initialize Comparer and Compare Documents
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
This code initializes the Comparer object with the source document and adds the target document for comparison. Then, it executes the comparison process.
## Step 3: Retrieve and Manipulate Changes
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Retrieve the changes from the comparison and manipulate them as needed. In this example, changes are rejected first and then accepted. The resulting documents are saved accordingly.

## Conclusion
In conclusion, GroupDocs Comparison for .NET offers a seamless solution for accepting and rejecting changes within documents. By following the steps outlined in this tutorial, developers can efficiently integrate this functionality into their applications, ensuring document accuracy and enhancing collaboration.
## FAQ's
### Can GroupDocs Comparison for .NET compare documents of different formats?
Yes, GroupDocs Comparison for .NET supports comparison between documents of various formats such as DOCX, PDF, PPTX, and more.
### Is GroupDocs Comparison for .NET compatible with .NET Core?
Yes, GroupDocs Comparison for .NET is compatible with both .NET Framework and .NET Core.
### Can I customize the appearance of changes in the compared documents?
Absolutely, GroupDocs Comparison for .NET provides extensive options for customizing the appearance of changes including color, style, and more.
### Does GroupDocs Comparison for .NET support multi-page document comparison?
Yes, GroupDocs Comparison for .NET supports comparison of multi-page documents with precision and accuracy.
### Is there a trial version available for GroupDocs Comparison for .NET?
Yes, you can avail a free trial of GroupDocs Comparison for .NET from the provided [link](https://releases.groupdocs.com/).
