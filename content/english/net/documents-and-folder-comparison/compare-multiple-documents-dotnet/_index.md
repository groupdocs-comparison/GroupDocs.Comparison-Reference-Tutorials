---
title: Compare Multiple Documents in GroupDocs Comparison for .NET
linktitle: Compare Multiple Documents in GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: 
type: docs
weight: 13
url: /net/documents-and-folder-comparison/compare-multiple-documents-dotnet/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Comparison.Examples.CSharp.AdvancedUsage
{
    using GroupDocs.Comparison;
    using GroupDocs.Comparison.Options;

    /// <summary>
    /// This class demonstrates comparing of multi documents
    /// </summary>
    class CompareMultipleDocumentsPath
    {
        /// <summary>
        /// This example demonstrates comparing of multi words documents
        /// </summary>
        public static void CompareMultipleWordsDocuments()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # CompareMultipleDocumentsPath-CompareMultipleWordsDocuments : Comparing of multiple words documents\n");
            
            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");

            using (Comparer comparer = new Comparer("SOURCE.docx"))
            {
                comparer.Add("TARGET.docx");
                comparer.Add("TARGET2.docx");
                comparer.Add("TARGET3.docx");

                comparer.Compare(outputFileName);
            }
            Console.WriteLine($"\nWord Documents compared successfully.\nCheck output in {outputDirectory}.");
        }

        /// <summary>
        /// This example demonstrates comparing of multi txt documents
        /// </summary>
        public static void CompareMultipleTxtDocuments()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # CompareMultipleDocumentsPath-CompareMultipleTxtDocuments : Comparing of multiple text documents\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.txt");

            using (Comparer comparer = new Comparer("SOURCE.txt"))
            {
                comparer.Add("TARGET.txt");
                comparer.Add("TARGET2.txt");
                comparer.Add("TARGET3.txt");

                comparer.Compare(File.Create(outputFileName), new SaveOptions(), new CompareOptions());
            }
            Console.WriteLine($"\nText documents compared successfully.\nCheck output in {outputDirectory}.");
        }

        /// <summary>
        /// This example demonstrates comparing of multi email documents
        /// </summary>
        public static void CompareMultipleEmailDocuments()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # CompareMultipleDocumentsPath-CompareMultipleEmailDocuments : Comparing of multiple email documents\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.eml");
            
            using (Comparer comparer = new Comparer("SOURCE.eml"))
            {
                comparer.Add("TARGET.eml");
                comparer.Add("TARGET2.eml");
                comparer.Add("TARGET3.eml");

                comparer.Compare(File.Create(outputFileName), new SaveOptions(), new CompareOptions());
            }
            Console.WriteLine($"\nEmail documents compared successfully.\nCheck output in {outputDirectory}.");
        }

        /// <summary>
        /// This example demonstrates comparing of multi pdf documents
        /// </summary>
        public static void CompareMultiplePdfDocuments()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # CompareMultipleDocumentsPath-CompareMultiplePdfDocuments : Comparing of multiple Pdf documents\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.pdf");

            using (Comparer comparer = new Comparer("SOURCE.pdf"))
            {
                comparer.Add("TARGET.pdf");
                comparer.Add("TARGET2.pdf");
                comparer.Add("TARGET3.pdf");

                comparer.Compare(File.Create(outputFileName), new SaveOptions(), new CompareOptions());
            }
            Console.WriteLine($"\nPDF documents compared successfully.\nCheck output in {outputDirectory}.");
        }

        /// <summary>
        /// This example demonstrates comparing of multi diagram documents
        /// </summary>
        public static void CompareMultipleDiagramDocuments()
        {
            Console.WriteLine("\n--------------------------------------------------------------------------------------------------------------------");
            Console.WriteLine("[Example Advanced Usage] # CompareMultipleDocumentsPath-CompareMultipleDiagramDocuments : Comparing of multiple diagram documents\n");

            string outputDirectory = "Your Document Directory";
            string outputFileName = Path.Combine(outputDirectory, "RESULT.vsdx");

            using (Comparer comparer = new Comparer("SOURCE.vsdx"))
            {
                comparer.Add("TARGET.vsdx");
                comparer.Add("TARGET2.vsdx");
                comparer.Add("TARGET3.vsdx");

                comparer.Compare(File.Create(outputFileName), new SaveOptions(), new CompareOptions() { DiagramMasterSetting = new DiagramMasterSetting() { MasterPath = Constants.DIAGRAM_SETTINGS } });
            }
            Console.WriteLine($"\nDiagram documents compared successfully.\nCheck output in {outputDirectory}.");
        }

    }
}

```
