---
title: Compare Protected Documents from Path - GroupDocs.Comparison for .NET
linktitle: Compare Protected Documents from Path - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 17
url: /net/document-comparison/compare-protected-documents-from-path/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.BasicUsage
{
    using GroupDocs.Comparison;
    using GroupDocs.Comparison.Options;
    /// <summary>
    /// This example demonstrates comparing of two documents with passwords
    /// </summary>
    class CompareDocumentsProtectedPath
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # CompareDocumentsProtectedPath : comparing of two documents with passwords\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer("SOURCE.docx"_PROTECTED, new LoadOptions(){ Password = "1234" }))
            {
                comparer.Add("TARGET.docx"_PROTECTED, new LoadOptions() { Password = "5678" });
                comparer.Compare(outputFileName);
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
        }
    }
}
```
