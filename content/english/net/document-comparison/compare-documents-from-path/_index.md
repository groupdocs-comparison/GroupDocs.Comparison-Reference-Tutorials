---
title: Compare Documents from Path - GroupDocs.Comparison for .NET
linktitle: Compare Documents from Path - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 15
url: /net/document-comparison/compare-documents-from-path/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates comparing of two documents
    /// </summary>
    class CompareDocumentsFromPath
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # CompareDocumentsFromPath : comparing of two documents from path\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer("SOURCE.docx"))
            {
                comparer.Add("TARGET.docx");
                comparer.Compare(outputFileName);
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}
```
