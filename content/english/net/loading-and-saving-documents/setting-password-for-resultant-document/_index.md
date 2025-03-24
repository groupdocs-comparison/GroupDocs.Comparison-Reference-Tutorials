---
title: Setting Password for Resultant Document in GroupDocs Comparison for .NET
linktitle: Setting Password for Resultant Document in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Learn how to set a password for resultant documents in GroupDocs Comparison for .NET. Enhance security and protect your compared files.
weight: 17
url: /net/loading-and-saving-documents/setting-password-for-resultant-document/
---
## Introduction
In this tutorial, we'll guide you through the process of setting a password for the resultant document using GroupDocs Comparison for .NET. This feature adds an extra layer of security to your compared documents, ensuring that only authorized individuals can access them.
## Prerequisites
Before you proceed, make sure you have the following:
1. GroupDocs Comparison for .NET: Ensure that you have the GroupDocs Comparison library installed in your .NET environment. You can download it from [here](https://releases.groupdocs.com/comparison/net/).
2. Source and Target Documents: Prepare the source document (`SOURCE.docx`) and the target document (`TARGET.docx`) that you want to compare and set a password for the resultant document.

## Import Namespaces
First, you need to import the necessary namespaces to your C# project to use GroupDocs Comparison functionality:
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
Specify the directory where you want to save the resultant document and define the name for the output file.
## Step 2: Compare Documents with Password Settings
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    CompareOptions cOptions = new CompareOptions
    {
        PasswordSaveOption = PasswordSaveOption.User
    };
    SaveOptions sOptions = new SaveOptions()
    {
        Password = "YourPasswordHere"
    };
    comparer.Compare(outputFileName, sOptions, cOptions);
}
```
Here, we initialize a `Comparer` object with the source document. Then, we add the target document to be compared. We set the `PasswordSaveOption` to `User` to specify that a password will be applied to the resultant document. Provide the desired password in the `Password` property of the `SaveOptions` object.
## Step 3: Display Success Message
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
Finally, we display a success message indicating that the documents have been compared successfully, and the resultant document with the set password has been saved to the specified directory.

## Conclusion
Setting a password for the resultant document in GroupDocs Comparison for .NET adds an extra layer of security to your compared documents, ensuring confidentiality and integrity. By following the steps outlined in this tutorial, you can easily implement this feature in your .NET applications.
## FAQ's
### Can I compare documents in different formats?
Yes, GroupDocs Comparison for .NET supports comparing documents in various formats such as DOCX, PDF, PPTX, XLSX, and more.
### Is there a trial version available?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### How can I get support if I encounter any issues?
You can seek assistance from the GroupDocs Comparison community forum [here](https://forum.groupdocs.com/c/comparison/12).
### Do I need a license to use GroupDocs Comparison for .NET?
Yes, you can purchase a license from [here](https://purchase.groupdocs.com/buy) or obtain a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
### Is there any documentation available for GroupDocs Comparison for .NET?
Yes, you can access the documentation [here](https://tutorials.groupdocs.com/comparison/net/).
