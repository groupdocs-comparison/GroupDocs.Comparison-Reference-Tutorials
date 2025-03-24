---
title: Compare Images from Stream - GroupDocs.Comparison for .NET
linktitle: Compare Images from Stream - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to compare images from streams using GroupDocs.Comparison for .NET. Step-by-step guide for seamless integration into .NET applications.
weight: 11
url: /net/image-comparison/compare-images-from-stream/
---
## Introduction
In the realm of .NET development, ensuring accuracy and consistency across documents or images is crucial. GroupDocs.Comparison for .NET provides a robust solution for developers to compare images efficiently. This tutorial will guide you through the process of comparing images from streams using GroupDocs.Comparison for .NET. By following these steps, you'll be able to seamlessly integrate image comparison capabilities into your .NET applications.
## Prerequisites
Before diving into the tutorial, make sure you have the following prerequisites in place:
### 1. Install GroupDocs.Comparison for .NET
Ensure that you have GroupDocs.Comparison for .NET installed in your development environment. You can download the necessary files from the [download link](https://releases.groupdocs.com/comparison/net/).
### 2. Obtain a License
To utilize GroupDocs.Comparison for .NET, you'll need a valid license. You can either purchase a license from [GroupDocs](https://purchase.groupdocs.com/buy) or obtain a temporary license for evaluation purposes from [here](https://purchase.groupdocs.com/temporary-license/).
### 3. Familiarity with .NET Development
Basic knowledge of .NET programming is required to follow along with this tutorial.

## Import Namespaces
Before proceeding with the comparison process, ensure you import the necessary namespaces into your .NET project. 
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Step 1: Define Output Directory and File Name
Firstly, specify the directory where you want to store the comparison result and the name of the output file.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.png");
```
## Step 2: Initialize Comparer
Next, initialize the `Comparer` object by providing the source image stream.
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.png")))
{
```
## Step 3: Add Target Image
Add the target image to the comparison process by providing its stream.
```csharp
comparer.Add(File.OpenRead("TARGET.png"));
```
## Step 4: Configure Comparison Options
Configure the options for image comparison. In this example, we set `GenerateSummaryPage` to false to prevent generating a summary page.
```csharp
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```
## Step 5: Perform Comparison
Execute the comparison process by calling the `Compare` method and providing the output file name and comparison options.
```csharp
comparer.Compare(outputFileName, options);
```
## Step 6: Display Result
Finally, display a message confirming the successful comparison and the location of the output file.
```csharp
Console.WriteLine($"\nImages compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```

## Conclusion
In conclusion, GroupDocs.Comparison for .NET offers a powerful solution for comparing images within .NET applications. By following the step-by-step guide outlined in this tutorial, developers can seamlessly integrate image comparison functionality into their projects, ensuring accuracy and consistency across documents.
## FAQ's
### Can GroupDocs.Comparison for .NET compare images in different formats?
Yes, GroupDocs.Comparison for .NET supports comparing images in various formats, including PNG, JPEG, GIF, BMP, and more.
### Is it possible to customize the comparison settings?
Absolutely, developers can customize comparison settings according to their requirements, such as ignoring small formatting differences or setting tolerance levels.
### Can I compare images stored in memory streams?
Yes, you can compare images from memory streams, as demonstrated in this tutorial.
### Does GroupDocs.Comparison for .NET provide support for document comparison as well?
Yes, GroupDocs.Comparison for .NET supports comparing not only images but also documents in various formats such as Word, Excel, PDF, and more.
### Is there a trial version available for testing purposes?
Yes, you can obtain a free trial version from [here](https://releases.groupdocs.com/).
