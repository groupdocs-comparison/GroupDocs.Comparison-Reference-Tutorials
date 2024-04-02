---
title: Compare Documents Settings in GroupDocs Comparison for .NET
linktitle: Compare Documents Settings in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 11
url: /net/documents-and-folder-comparison/compare-documents-settings-dotnet/
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
    /// This example demonstrates using some of compare settings
    /// </summary>
    class CompareDocumentsSettingsStream
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # CompareDocumentsSettingsStream : Using some of compare settings\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
            {
                comparer.Add(File.OpenRead("TARGET.docx"));
                CompareOptions compareOptions = new CompareOptions()
                {
                    InsertedItemStyle = new StyleSettings()
                    {
                        HighlightColor = System.Drawing.Color.Red,
                        FontColor = System.Drawing.Color.Green,
                        IsUnderline = true
                    }
                };
                comparer.Compare(File.Create(outputFileName), compareOptions);
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
        }
    }
}

```
