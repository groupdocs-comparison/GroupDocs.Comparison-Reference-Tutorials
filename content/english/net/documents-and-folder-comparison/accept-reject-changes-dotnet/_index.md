---
title: Accept and Reject Changes in GroupDocs Comparison for .NET
linktitle: Accept and Reject Changes in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 10
url: /net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.AdvancedUsage
{
    using GroupDocs.Comparison;
    using GroupDocs.Comparison.Result;
    using GroupDocs.Comparison.Options;
    
    /// <summary>
    /// This example demonstrates how to update changes from path
    /// </summary>
    class AcceptRejectDetectedChangesPath
    {
        public static void Run()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # AcceptRejectDetectedChangesPath : How to update changes from path\n");

            string outputDirectory = "Your Document Directory";
            string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
            string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");

            using (Comparer comparer = new Comparer("SOURCE.docx"))
            {
                comparer.Add("TARGET.docx");
                comparer.Compare();
                ChangeInfo[] changes = comparer.GetChanges();
                // inserted word "Cool" was not be added to result document
                changes[0].ComparisonAction = ComparisonAction.Reject;
                comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
                changes = comparer.GetChanges();
                changes[0].ComparisonAction = ComparisonAction.Accept;
                comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
            }
            Console.WriteLine($"\nChanges updated successfully.\nCheck output in {outputDirectory}.");
        }
    }
}

```
