---
title: Get Document Info from Result Document - GroupDocs.Comparison for .NET
linktitle: Get Document Info from Result Document - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 12
url: /net/basic-usage/get-document-info-from-result-document/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using System.Linq;

namespace GroupDocs.Comparison.Examples.CSharp.BasicUsage
{
    using GroupDocs.Comparison;
    using GroupDocs.Comparison.Interfaces;

    /// <summary>
    /// This example demonstrates result document object info extraction
    /// </summary>
    class GetDocumentInfoFromResultDocument
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # GetDocumentInfoFromResultDocument : result document object info extraction\n");

            using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
            {
                comparer.Add(File.OpenRead("TARGET.docx"));
                IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
                Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
            }
            Console.WriteLine($"\nDocument info extracted successfully.");
        }
    }
}



```
