---
title: Saving Documents Metadata Source in GroupDocs Comparison for .NET
linktitle: Saving Documents Metadata Source in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 14
url: /net/loading-and-saving-documents/saving-documents-metadata-source/
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
    /// This example demonstrates using option for select metadata 
    /// </summary>
    class SetDocumentMetadataSource
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SetDocumentMetadataSource : using option for select metadata\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer("SOURCE.docx"))
            {
                comparer.Add("TARGET.docx");
                comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Source });
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
