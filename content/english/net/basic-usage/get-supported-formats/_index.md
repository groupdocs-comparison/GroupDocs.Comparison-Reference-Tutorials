---
title: Get Supported Formats - GroupDocs.Comparison for .NET
linktitle: Get Supported Formats - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Enhance document accuracy and consistency with GroupDocs.Comparison for .NET. Seamlessly integrate this powerful tool into your .NET applications.
type: docs
weight: 15
url: /net/basic-usage/get-supported-formats/
---
## Introduction
In today's digital age, where information is abundant and constantly evolving, ensuring the accuracy and consistency of documents is paramount. Whether you're a software developer, a legal professional, or anyone dealing with documents regularly, having tools that facilitate document comparison can save you time, effort, and potential errors. GroupDocs.Comparison for .NET is one such tool, offering a comprehensive solution for comparing various document formats within .NET applications.
## Prerequisites
Before diving into the tutorial on using GroupDocs.Comparison for .NET, make sure you have the following prerequisites in place:
### 1. Installing GroupDocs.Comparison for .NET
To begin, you'll need to download and install GroupDocs.Comparison for .NET. You can find the download link [here](https://releases.groupdocs.com/comparison/net/). Follow the installation instructions provided to integrate it into your .NET environment seamlessly.
### 2. Familiarity with .NET Framework
A basic understanding of the .NET framework is essential for implementing GroupDocs.Comparison effectively. If you're new to .NET, consider familiarizing yourself with its concepts and syntax through online tutorials or documentation.
### 3. Integrated Development Environment (IDE)
Ensure you have an IDE installed, such as Visual Studio, to write and execute .NET code effortlessly. GroupDocs.Comparison for .NET seamlessly integrates with popular IDEs, enhancing your development experience.

## Import Namespaces
Before delving into the code examples, it's crucial to import the necessary namespaces to access the functionalities provided by GroupDocs.Comparison for .NET.
```csharp
using System;
using System.Linq;
using System.Collections.Generic;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
```

## Step 1: Initializing the Console Application
First, create a new console application project in your IDE and open the main file.
## Step 2: Importing Necessary Libraries
Import the required namespaces as explained earlier to access GroupDocs.Comparison and essential .NET functionalities.
## Step 3: Retrieving Supported File Formats
Use the provided code snippet to retrieve a list of supported file types for comparison.
```csharp
IEnumerable<FileType> fileTypes = FileType
    .GetSupportedFileTypes()
    .OrderBy(fileType => fileType.Extension);
```
## Step 4: Displaying Supported Formats
Iterate through the list of supported file types and display them in the console.
```csharp
foreach (FileType fileType in fileTypes)
    Console.WriteLine(fileType);
```
## Step 5: Confirmation Message
Finally, display a message indicating successful retrieval of supported file types.
```csharp
Console.WriteLine("\nSupported file types retrieved successfully.");
```

## Conclusion
GroupDocs.Comparison for .NET offers a robust solution for document comparison within .NET applications. By following the steps outlined in this tutorial, you can seamlessly integrate it into your projects and enhance document accuracy and consistency.
## FAQ's
### Is GroupDocs.Comparison for .NET compatible with all .NET frameworks?
Yes, GroupDocs.Comparison for .NET supports various .NET frameworks, ensuring compatibility across different environments.
### Can I customize the comparison process based on my specific requirements?
Absolutely, GroupDocs.Comparison for .NET provides extensive customization options, allowing you to tailor the comparison process to meet your exact needs.
### Is there a free trial available for GroupDocs.Comparison for .NET?
Yes, you can explore the features of GroupDocs.Comparison for .NET through a free trial available [here](https://releases.groupdocs.com/).
### How can I get technical support for GroupDocs.Comparison for .NET?
For technical assistance and support, you can visit the GroupDocs.Comparison forum [here](https://forum.groupdocs.com/c/comparison/12).
### Can I purchase a temporary license for short-term usage?
Yes, you can acquire a temporary license for GroupDocs.Comparison for .NET to meet your short-term project needs. Learn more [here](https://purchase.groupdocs.com/temporary-license/).
