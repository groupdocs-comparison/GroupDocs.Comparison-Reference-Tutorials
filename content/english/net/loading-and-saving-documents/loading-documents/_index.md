---
title: Loading Documents in GroupDocs Comparison for .NET
linktitle: Loading Documents in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 10
url: /net/loading-and-saving-documents/loading-documents/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.AdvancedUsage.Loading
{
    /// <summary>
    /// This example demonstrates comparing of two documents loaded by file path
    /// </summary>
    class LoadDocumentFromLocalDisc
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # LoadDocumentFromLocalDisc : comparing of two documents loaded by file path\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            string sourcePath = "SOURCE.docx";
            using (Comparer comparer = new Comparer(sourcePath))
            {
                string targetPath = "SOURCE.docx";
                comparer.Add("TARGET.docx");
                comparer.Compare(outputFileName);
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
