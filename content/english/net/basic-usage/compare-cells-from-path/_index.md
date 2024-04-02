---
title: Compare Cells from Path - GroupDocs.Comparison for .NET
linktitle: Compare Cells from Path - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 10
url: /net/basic-usage/compare-cells-from-path/
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
    class CompareCellsFromPath
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # CompareCellsFromPath : comparing of two cells files\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "result.xlsx");

            using (Comparer comparer = new Comparer("source.xlsx"))
            {
                comparer.Add("target.xlsx");
                comparer.Compare(outputFileName);
            }
            Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
