---
title: Compare Images from Path - GroupDocs.Comparison for .NET
linktitle: Compare Images from Path - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 10
url: /net/image-comparison/compare-images-from-path/
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
    /// This example demonstrates comparing of two images without SummaryPage
    /// </summary>
    class CompareImageFromPath
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # CompareImageFromPath : comparing of two images without SummaryPage\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.png");

            using (Comparer comparer = new Comparer("SOURCE.png"))
            {
                //If you set the GenerateSummaryPage property to true then the result will be saved in PDF format
                CompareOptions options = new CompareOptions();
                options.GenerateSummaryPage = false;

                comparer.Add("TARGET.png");
                comparer.Compare(outputFileName, options);
            }
            Console.WriteLine($"\nImages compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
        }
    }
}
```
