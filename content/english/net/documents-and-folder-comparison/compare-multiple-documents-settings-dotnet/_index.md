---
title: Compare Multiple Documents Settings in GroupDocs Comparison for .NET
linktitle: Compare Multiple Documents Settings in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 14
url: /net/documents-and-folder-comparison/compare-multiple-documents-settings-dotnet/
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
    /// This example demonstrates comparing of multi documents from stream
    /// </summary>
    class CompareMultipleDocumentsSettingsStream
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # CompareMultipleDocumentsSettingsStream : comparing of multi documents from stream\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
            {
                comparer.Add(File.OpenRead("TARGET.docx"));
                comparer.Add(File.OpenRead("TARGET2.docx"));
                comparer.Add(File.OpenRead("TARGET3.docx"));
                CompareOptions compareOptions = new CompareOptions()
                {
                    InsertedItemStyle = new StyleSettings()
                    {
                        FontColor = System.Drawing.Color.Yellow
                    }
                };
                comparer.Compare(File.Create(outputFileName), compareOptions);
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
