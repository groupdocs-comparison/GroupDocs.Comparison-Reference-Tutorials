---
title: Setting Password for Resultant Document in GroupDocs Comparison for .NET
linktitle: Setting Password for Resultant Document in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 17
url: /net/loading-and-saving-documents/setting-password-for-resultant-document/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.AdvancedUsage
{
    using GroupDocs.Comparison;
    using GroupDocs.Comparison.Options;

    /// <summary>
    /// This example demonstrates how protect result document by password
    /// </summary>
    class SetPasswordForResultantDocument
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SetPasswordForResultantDocument : how protect result document by password\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer("SOURCE.docx"))
            {
                comparer.Add("TARGET.docx");
                CompareOptions cOptions = new CompareOptions
                {
                    PasswordSaveOption = PasswordSaveOption.User
                };
                SaveOptions sOptions = new SaveOptions()
                {
                    Password = "3333"
                };
                comparer.Compare(outputFileName, sOptions, cOptions);
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
