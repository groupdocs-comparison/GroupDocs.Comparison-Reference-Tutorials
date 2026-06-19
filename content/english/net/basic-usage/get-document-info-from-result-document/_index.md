---
title: "How to Extract Metadata from .NET Comparison Results – Complete Guide"
linktitle: "Extract Document Info from Comparison Results"
second_title: GroupDocs.Comparison .NET API
description: "Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison. Step‑by‑step guide with code examples and practical tips."
keywords:
  - how to extract metadata
  - get document size .net
  - document comparison metadata
  - GroupDocs Comparison document info
weight: 12
url: /net/basic-usage/get-document-info-from-result-document/
date: "2026-06-15"
lastmod: "2026-06-15"
categories: ["Document Comparison"]
tags: ["groupdocs-comparison", "document-metadata", "dotnet-api", "document-properties"]
type: docs
schemas:
- type: TechArticle
  headline: How to Extract Metadata from .NET Comparison Results – Complete Guide
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  dateModified: '2026-06-15'
  author: GroupDocs
- type: HowTo
  name: How to Extract Metadata from .NET Comparison Results – Complete Guide
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  steps:
  - name: Initialize Comparer with Source Document
    text: '`Comparer` is the core class in GroupDocs.Comparison that loads the source
      document and orchestrates comparison operations. Using a `using` block guarantees
      that all unmanaged resources are released automatically. > **Pro Tip:** You
      can pass any `Stream` (file, memory, cloud) to the `Comparer` const'
  - name: Add Target Document for Comparison
    text: The `Add()` method accepts additional streams or file paths, enabling one‑to‑many
      comparisons. > **Important:** The order of added documents influences the way
      changes are highlighted in the final report.
  - name: Retrieve Document Info from Result Document
    text: '`IDocumentInfo` provides a unified view of document metadata such as file
      type, page count, and size across all supported formats. > **Understanding the
      Data:** The returned object works the same for DOCX, PDF, XLSX, and PPTX, so
      you can write format‑agnostic code.'
  - name: Display Document Info
    text: 'Once you have the `IDocumentInfo` instance, you can log, store, or present
      its properties. The three most commonly used properties are: - **FileType**
      – e.g., `DOCX`, `PDF`, `XLSX`. - **PageCount** – total pages or slides. - **Size**
      – file size in bytes (useful for storage calculations).'
- type: FAQPage
  questions:
  - question: Is GroupDocs.Comparison for .NET compatible with various document formats?
    answer: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT,
      and many others, providing consistent metadata extraction across them.
  - question: Can I customize comparison settings without affecting metadata extraction?
    answer: Absolutely. Settings such as sensitivity, change types, and output format
      are independent of the `GetDocumentInfo()` call.
  - question: Is there a trial version I can use for evaluation?
    answer: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/).
      The trial includes full metadata extraction capabilities.
  - question: Where can I get support for implementation questions?
    answer: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12)
      for community help and official support from the GroupDocs team.
  - question: What licensing options are available for production deployments?
    answer: GroupDocs offers developer, site, and OEM licenses. Purchase options are
      listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).
---

# How to Extract Metadata from .NET Comparison Results – Complete Guide

When you're working with document comparisons in .NET applications, you might wonder **how to extract metadata** from the comparison results. Metadata such as file type, page count, and document size can be crucial for audit trails, performance tuning, or simply displaying useful information to end users. This tutorial walks you through retrieving that data efficiently with GroupDocs.Comparison for .NET.

## Quick Answers
- **What is the main class for comparison?** `Comparer` loads the source document and runs the comparison engine.  
- **Which method returns metadata?** `GetDocumentInfo()` on a target document returns an `IDocumentInfo` object.  
- **Can I get the document size in .NET?** Yes – the `Size` property of `IDocumentInfo` returns the size in bytes.  
- **Do I need a license for metadata extraction?** A valid GroupDocs.Comparison license is required for production use; the free trial supports all metadata features.  
- **Is the API compatible with .NET 6?** Absolutely – GroupDocs.Comparison supports .NET Framework 4.6.1+, .NET Core 2.0+, and .NET 5/6+.

The `GetDocumentInfo()` method returns an `IDocumentInfo` object containing document metadata.

## What is metadata extraction in document comparison?
Metadata extraction is the process of retrieving descriptive information—such as file type, page count, and file size—from the documents involved in a comparison operation. GroupDocs.Comparison exposes this data through a unified API, making it easy to log, display, or use for conditional processing.

## Why extract metadata from comparison results?
Extracting metadata lets you create detailed audit logs, route files based on type, and adjust processing strategies for large documents. By knowing the file type, page count, and size you can enforce compliance rules, estimate processing time, and present clear information to users before they start a comparison.

## Prerequisites

1. **GroupDocs.Comparison for .NET** – Install the library from the [official releases page](https://releases.groupdocs.com/comparison/net/).  
   You can also browse all releases at the [GroupDocs releases page](https://releases.groupdocs.com/).  
2. **Development Environment** – Visual Studio, VS Code, or any IDE that supports .NET 6+.  
3. **Sample Documents** – Two files (e.g., `SOURCE.docx` and `TARGET.docx`) for testing. The API works with over **50 document formats**.

## Import Namespaces

The following `using` directives give you access to the core comparison engine, file handling utilities, and the metadata interfaces.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

These imports are required before you instantiate any GroupDocs objects.

## How to Extract Metadata from Comparison Results?

The `Comparer` class loads the source document and orchestrates the comparison process.

To retrieve metadata, first load the source document with a `Comparer` instance, then add the target document(s). After the comparison engine is initialized, call `GetDocumentInfo()` on each target to obtain an `IDocumentInfo` object that contains properties such as file type, page count, and size. This approach works uniformly across all supported formats.

### Step 1: Initialize Comparer with Source Document

`Comparer` is the core class in GroupDocs.Comparison that loads the source document and orchestrates comparison operations. Using a `using` block guarantees that all unmanaged resources are released automatically.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Pro Tip:** You can pass any `Stream` (file, memory, cloud) to the `Comparer` constructor, not just a file path.

### Step 2: Add Target Document for Comparison

The `Add()` method accepts additional streams or file paths, enabling one‑to‑many comparisons.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Important:** The order of added documents influences the way changes are highlighted in the final report.

### Step 3: Retrieve Document Info from Result Document

`IDocumentInfo` provides a unified view of document metadata such as file type, page count, and size across all supported formats.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Understanding the Data:** The returned object works the same for DOCX, PDF, XLSX, and PPTX, so you can write format‑agnostic code.

### Step 4: Display Document Info

Once you have the `IDocumentInfo` instance, you can log, store, or present its properties.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

The three most commonly used properties are:

- **FileType** – e.g., `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – total pages or slides.  
- **Size** – file size in bytes (useful for storage calculations).

## How to Get Document Size in .NET?

The `Size` property returns the file size in bytes.

The document size can be accessed directly from the `IDocumentInfo` instance via its `Size` property. This property returns the exact number of bytes of the original file, allowing you to convert it to kilobytes or megabytes for display or storage calculations. It reflects the source file size, not any processed version.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Note:** The `Size` value reflects the original file size, not the size after any internal processing or compression.

## Common Use Cases and Practical Applications

- **Batch Processing:** Use file type to route DOCX files to a Word‑specific workflow and PDFs to a PDF‑optimized pipeline.  
- **Storage Management:** Archive documents larger than 10 MB to a cold‑storage bucket automatically.  
- **User Feedback:** Show page count and size before comparison to set realistic expectations for processing time.  
- **Quality Assurance:** Verify that uploaded files are complete by comparing expected versus actual page counts.

## Troubleshooting Common Issues

- **File Access Errors:** Verify read permissions and use absolute paths during development.  
- **Memory Pressure with Large Files:** Prefer streaming (`File.OpenRead`) over loading the whole file into memory.  
- **Null Reference Exceptions:** `FirstOrDefault()` may return `null` if no target was added; always check before accessing `GetDocumentInfo()`.  

```csharp
var target = comparer.Targets.FirstOrDefault();
if (target != null)
{
    var info = target.GetDocumentInfo();
    // Use info safely
}
else
{
    Console.WriteLine("No target document was added.");
}
```

- **Limited Metadata for Plain Text:** Formats like `.txt` may not expose a meaningful `PageCount`. Guard against missing values.

## Performance Considerations

- **Stream Management:** Always wrap streams in `using` statements to release file handles promptly.  
- **Caching:** Store frequently accessed metadata in a cache to avoid repeated extraction.  
- **Batch Operations:** Process documents in groups to reduce overhead and improve throughput.

## Best Practices for Production Use

- **Robust Error Handling:** Enclose metadata extraction in try‑catch blocks to handle corrupted or unsupported files gracefully.  
- **Comprehensive Logging:** Log document type, size, and page count for each comparison to aid troubleshooting and audit compliance.  
- **Security Hygiene:** Avoid exposing full file paths or internal server details in UI messages.  
- **Resource Disposal:** Dispose of `Comparer` instances promptly, especially in web services handling many concurrent requests.

## Advanced Scenarios

### Multiple Target Documents

If you compare one source against several targets, iterate through the `Targets` collection and extract metadata from each.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Conditional Processing Based on Metadata

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Storing Metadata in a Database

Persist `FileType`, `PageCount`, and `Size` in a relational table to enable reporting and analytics across thousands of comparisons.

## Frequently Asked Questions

**Q: Is GroupDocs.Comparison for .NET compatible with various document formats?**  
A: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT, and many others, providing consistent metadata extraction across them.

**Q: Can I customize comparison settings without affecting metadata extraction?**  
A: Absolutely. Settings such as sensitivity, change types, and output format are independent of the `GetDocumentInfo()` call.

**Q: Is there a trial version I can use for evaluation?**  
A: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/). The trial includes full metadata extraction capabilities.

**Q: Where can I get support for implementation questions?**  
A: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12) for community help and official support from the GroupDocs team.

**Q: What licensing options are available for production deployments?**  
A: GroupDocs offers developer, site, and OEM licenses. Purchase options are listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).

---

**Last Updated:** 2026-06-15  
**Tested With:** GroupDocs.Comparison 6.0 for .NET  
**Author:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Related Tutorials

- [Document Metadata Management .NET - Complete Guide for GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Get Document Properties C# .NET - Extract File Metadata](/comparison/net/basic-usage/get-document-info-from-path/)
- [Preserve Target Metadata with GroupDocs.Comparison – .NET Tutorial](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)
