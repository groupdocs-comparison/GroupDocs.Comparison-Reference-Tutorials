---
title: Set Metered License - GroupDocs Comparison for .NET
linktitle: Set Metered License - GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Integrate GroupDocs Comparison for .NET seamlessly into your .NET projects for efficient document comparison workflows.
weight: 12
url: /net/quick-start/set-metered-license/
---
## Introduction
In the realm of .NET development, having robust tools for document comparison is indispensable. GroupDocs Comparison for .NET stands out as a powerful solution for comparing various document formats programmatically. From text documents to spreadsheets and presentations, this library enables developers to efficiently identify differences between files.
## Prerequisites
Before diving into the intricacies of utilizing GroupDocs Comparison for .NET, ensure you have the following prerequisites in place:
1. Knowledge of .NET Development: Familiarity with C# programming and .NET environment is essential to effectively utilize GroupDocs Comparison for .NET.
2. Installation of GroupDocs Comparison Library: Download and install the GroupDocs Comparison for .NET library from the [download link](https://releases.groupdocs.com/comparison/net/).
3. Metered License: Acquire a metered license from GroupDocs to unlock the full potential of the library. You can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
4. Integrated Development Environment (IDE): Have an IDE like Visual Studio installed for seamless development experience.

## Import Namespaces
To begin using GroupDocs Comparison for .NET, import the necessary namespaces into your project. Follow these steps:

```csharp
using System;
```
These namespaces provide access to the essential classes and methods needed for document comparison functionality.
## Setting up a Metered License
Before utilizing the full features of GroupDocs Comparison for .NET, setting up a metered license is crucial. Here's a step-by-step guide to achieve this:
## Step 1: Acquire Public and Private Keys
Firstly, acquire the public and private keys provided by GroupDocs after purchasing a metered license.
## Step 2: Set up the Metered License
Now, use the obtained public and private keys to set up the metered license as demonstrated below:
```csharp
string publicKey = "*****";
string privateKey = "*****";
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```
Replace `"*****"` with your actual public and private keys provided by GroupDocs. This code initializes the metered license with the provided keys, enabling access to the full functionality of GroupDocs Comparison for .NET.

## Conclusion
In conclusion, GroupDocs Comparison for .NET offers a comprehensive solution for document comparison within .NET applications. By following the outlined steps for importing namespaces and setting up a metered license, developers can seamlessly integrate this powerful library into their projects, facilitating efficient document comparison workflows.
## FAQ's
### Can I use GroupDocs Comparison for .NET without a license?
No, a valid license is required to utilize the full functionality of the library. However, you can obtain a temporary license for testing purposes.
### What document formats does GroupDocs Comparison for .NET support?
GroupDocs Comparison for .NET supports a wide range of document formats including DOCX, XLSX, PPTX, PDF, and more.
### Is GroupDocs Comparison for .NET compatible with .NET Core?
Yes, GroupDocs Comparison for .NET is compatible with both .NET Framework and .NET Core environments.
### Can I customize the comparison settings?
Yes, developers have the flexibility to customize various aspects of document comparison such as comparison type, style settings, and comparison scope.
### Where can I seek assistance if I encounter any issues?
You can seek assistance from the GroupDocs Comparison community forum [here](https://forum.groupdocs.com/c/comparison/12).
