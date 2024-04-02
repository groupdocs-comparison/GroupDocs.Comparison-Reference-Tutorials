---
title: Saving User Defined Document Metadata in GroupDocs Comparison for .NET
linktitle: Saving User Defined Document Metadata in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 16
url: /net/loading-and-saving-documents/saving-user-defined-document-metadata/
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
    /// This example demonstrates using option for select user metadata
    /// </summary>
    class SetDocumentMetadataUserDefined
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # SetDocumentMetadataUserDefined : using option for select user metadata\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer("SOURCE.docx"))
            {
                comparer.Add("TARGET.docx");
                SaveOptions saveOptions = new SaveOptions()
                {
                    CloneMetadataType = MetadataType.FileAuthor,
                    FileAuthorMetadata = new FileAuthorMetadata
                    {
                        Author = "Tom",
                        Company = "GroupDocs",
                        LastSaveBy = "Jack"
                    }
                };
                comparer.Compare(outputFileName, saveOptions);
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
