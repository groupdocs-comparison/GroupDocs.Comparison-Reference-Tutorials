---
title: Loading Documents from Stream in GroupDocs Comparison for .NET
linktitle: Loading Documents from Stream in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 11
url: /net/loading-and-saving-documents/loading-documents-from-stream/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.AdvancedUsage.Loading
{
    /// <summary>
    /// This example demonstrates comparing of two documents loaded by file stream
    /// </summary>
    class LoadDocumentFromStream
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # LoadDocumentFromStream : comparing of two documents loaded by file stream\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Stream sourceStream = File.OpenRead("SOURCE.docx"))
            using (Stream targetStream = File.OpenRead("TARGET.docx"))
            {
                using (Comparer comparer = new Comparer(sourceStream))
                {
                    comparer.Add(targetStream);
                    comparer.Compare(File.Create(outputFileName));
                }
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
