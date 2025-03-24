---
title: Using Load Options in GroupDocs Comparison for .NET
linktitle: Using Load Options in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to use Load Options in GroupDocs Comparison for .NET to compare documents with custom fonts seamlessly.
weight: 13
url: /net/loading-and-saving-documents/using-load-options/
---
## Introduction
Welcome to our tutorial on utilizing Load Options in GroupDocs Comparison for .NET! In this tutorial, we'll walk you through the process of comparing documents using Load Options in a step-by-step manner. Whether you're a beginner or an experienced developer, this guide will help you seamlessly integrate GroupDocs Comparison into your .NET applications.
## Prerequisites
Before we begin, make sure you have the following prerequisites set up:
### 1. Install GroupDocs Comparison for .NET
You can download the GroupDocs Comparison for .NET library from [this link](https://releases.groupdocs.com/comparison/net/). Follow the installation instructions provided in the documentation for a smooth setup process.
### 2. Obtain Source and Target Documents
Ensure you have the source and target documents ready for comparison. These documents could be in various formats such as DOCX, PDF, or TXT.
## Import Namespaces
Before we delve into the code, let's import the necessary namespaces for our application:
```csharp
using System;
using System.IO;
using System.Collections.Generic;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
Now, let's break down the example code provided into multiple steps:
## Step 1: Define Custom Font Directories
```csharp
List<string> fontDirectories = new List<string>();
// Need to set the directory of the file with the font
fontDirectories.Add(Constants.CUSTOM_FONT);
```
In this step, we create a list of string type to hold the directories where custom fonts are located. Ensure to replace `Constants.CUSTOM_FONT` with the actual directory path containing your custom fonts.
## Step 2: Instantiate Load Options
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontDirectories = fontDirectories;
```
Here, we instantiate a `LoadOptions` object and assign the custom font directories to it. This step prepares the options needed for loading the documents with custom fonts.
## Step 3: Compare Documents
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx"), loadOptions))
{
    comparer.Add(File.OpenRead("TARGET.docx"));
    comparer.Compare(File.Create(Path.Combine("Your Document Directory", "RESULT.docx")));
}
```
Now, we create a `Comparer` object using the source document and the previously defined load options. Then, we add the target document to the comparer and perform the comparison. Finally, we save the compared document to a specified directory.
## Step 4: Display Success Message
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```
After the comparison process is complete, we display a success message along with the directory where the compared document is saved.
## Conclusion
In conclusion, this tutorial provided a comprehensive guide on using Load Options in GroupDocs Comparison for .NET. By following the step-by-step instructions, you can seamlessly integrate document comparison functionality into your .NET applications.
## FAQ's
### Q: Can GroupDocs Comparison handle documents of different formats?
Yes, GroupDocs Comparison supports comparing documents in various formats such as DOCX, PDF, TXT, and more.
### Q: Is there a trial version available before purchasing?
Yes, you can access the free trial version of GroupDocs Comparison from [this link](https://releases.groupdocs.com/).
### Q: How can I get support for GroupDocs Comparison?
You can seek support from the GroupDocs community forum [here](https://forum.groupdocs.com/c/comparison/12).
### Q: Can I use custom fonts in the compared documents?
Absolutely! GroupDocs Comparison allows you to specify custom font directories for accurate document rendering.
### Q: Are temporary licenses available for testing purposes?
Yes, you can obtain temporary licenses for testing and evaluation purposes from [this link](https://purchase.groupdocs.com/temporary-license/).
