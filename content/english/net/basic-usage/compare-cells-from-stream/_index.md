---
title: Compare Cells from Stream - GroupDocs.Comparison for .NET
linktitle: Compare Cells from Stream - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 11
url: /net/basic-usage/compare-cells-from-stream/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates comparing of two cells files
    /// </summary>
    class CompareCellsFromStream
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # CompareCellsFromStream : comparing of two cells files\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "result.xlsx");

            using (Comparer comparer = new Comparer(File.OpenRead("source.xlsx")))
            {
                comparer.Add(File.OpenRead("target.xlsx"));
                comparer.Compare(File.Create(outputFileName));
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
