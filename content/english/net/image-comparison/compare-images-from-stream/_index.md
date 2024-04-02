---
title: Compare Images from Stream - GroupDocs.Comparison for .NET
linktitle: Compare Images from Stream - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 11
url: /net/image-comparison/compare-images-from-stream/
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
    public class CompareImageFromStream
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # CompareImageFromStream : comparing of two images without SummaryPage\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.png");

            using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.png")))
            {
	            //If you set the GenerateSummaryPage property to true then the result will be saved in PDF format
                CompareOptions options = new CompareOptions();
	            options.GenerateSummaryPage = false;

                comparer.Add(File.OpenRead("TARGET.png"));
                comparer.Compare(outputFileName, options);
            }
            Console.WriteLine($"\nImages compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
        }
    }
}
```
