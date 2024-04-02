---
title: Compare Protected Documents from Stream - GroupDocs.Comparison for .NET
linktitle: Compare Protected Documents from Stream - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 18
url: /net/document-comparison/compare-protected-documents-from-stream/
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
    /// This example demonstrates comparing of two password encrypted documents
    /// </summary>
    class CompareDocumentsProtectedStream
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # CompareDocumentsProtectedStream : comparing of two password encrypted documents\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx"_PROTECTED), new LoadOptions() { Password = "1234" }))
            {
                comparer.Add(File.OpenRead("TARGET.docx"_PROTECTED), new LoadOptions() { Password = "5678" });
                comparer.Compare(File.Create(outputFileName));
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
        }
    }
}

```
