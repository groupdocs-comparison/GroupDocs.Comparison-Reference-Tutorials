---
title: Set License from File - GroupDocs Comparison for .NET
linktitle: Set License from File - GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 10
url: /net/quick-start/set-license-from-file/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.QuickStart
{
    /// <summary>
    /// This example demonstrates how to set license from file.
    /// </summary>
    /// <remarks>
    /// The SetLicense method attempts to set a license from several locations relative to the executable and GroupDocs.Comparison.dll.
    /// You can also use the additional overload to load a license from a stream, this is useful for instance when the 
    /// License is stored as an embedded resource. 
    /// </remarks>
    class SetLicenseFromFile
    {
        public static void Run()
        {
            if (File.Exists(Constants.LicensePath))
            {
                License license = new License();
                license.SetLicense(Constants.LicensePath);
                Console.WriteLine("License set successfully.");
            }
            else
            {
                Console.WriteLine("\nWe do not ship any license with this example. " +
                                  "\nVisit the GroupDocs site to obtain either a temporary or permanent license. " +
                                  "\nLearn more about licensing at https://purchase.groupdocs.com/faqs/licensing. " +
                                  "\nLear how to request temporary license at https://purchase.groupdocs.com/temporary-license.");
            }
        }
    }
}
```