---
title: Get Supported Formats - GroupDocs.Comparison for .NET
linktitle: Get Supported Formats - GroupDocs.Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 15
url: /net/basic-usage/get-supported-formats/
---

## Complete Source Code
```csharp
using System;
using System.Linq;
using System.Collections.Generic;

namespace GroupDocs.Comparison.Examples.CSharp.BasicUsage
{
    using GroupDocs.Comparison;
    using GroupDocs.Comparison.Result;

    /// <summary>
    /// This example demonstrates file types support
    /// </summary>
    internal class GetSupportedFormats
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Basic Usage] # GetSupportedFormats : list of the file types support\n");

            IEnumerable<FileType> fileTypes = FileType
                    .GetSupportedFileTypes()
                    .OrderBy(fileType => fileType.Extension);
            foreach (FileType fileType in fileTypes)
                Console.WriteLine(fileType);
            Console.WriteLine("\nSupported file types retrieved successfully.");
        }
    }
}
```
