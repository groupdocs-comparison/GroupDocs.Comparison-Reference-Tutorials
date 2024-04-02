---
title: Set Metered License - GroupDocs Comparison for .NET
linktitle: Set Metered License - GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 12
url: /net/quick-start/set-metered-license/
---

## Complete Source Code
```csharp
using System;

namespace GroupDocs.Comparison.Examples.CSharp.QuickStart
{
    /// <summary>
    /// This example demonstrates how to set Metered license.
    /// Learn more about Metered license at https://purchase.groupdocs.com/faqs/licensing/metered.
    /// </summary>
    class SetMeteredLicense
    {
        public static void Run()
        {
            string publicKey = "*****";
            string privateKey = "*****";
            Metered metered = new Metered();
            metered.SetMeteredKey(publicKey, privateKey);
            Console.WriteLine("License set successfully.");
        }
    }
}
```
