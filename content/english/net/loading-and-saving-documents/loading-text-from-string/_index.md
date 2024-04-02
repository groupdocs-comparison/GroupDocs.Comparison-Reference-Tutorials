---
title: Loading Text from String in GroupDocs Comparison for .NET
linktitle: Loading Text from String in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 12
url: /net/loading-and-saving-documents/loading-text-from-string/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.AdvancedUsage.Loading
{
    using GroupDocs.Comparison;
    using GroupDocs.Comparison.Options;

    /// <summary>
    /// This example demonstrates comparing of two texts loaded by string variables
    /// </summary>
    class LoadTextFromString
	{
		public static void Run()
		{
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # LoadTextFromString : comparing of two texts loaded by string variables\n");

            // Pass text and instantiate LoadOptions object with set LoadText property to true (this indicates that passed string contains text to be compared, not file path)
            using (Comparer comparer = new Comparer("source text", new LoadOptions() { LoadText = true }))
			{
				// Use the same code structure, to pass second text
				comparer.Add("target text", new LoadOptions() { LoadText = true });
				comparer.Compare();
				// Call GetResultString method to get text with comparison result.
				Console.WriteLine("Result string: \n" + comparer.GetResultString());
			}
			Console.WriteLine($"\nTexts compared successfully.");
		}
	}
}
```
