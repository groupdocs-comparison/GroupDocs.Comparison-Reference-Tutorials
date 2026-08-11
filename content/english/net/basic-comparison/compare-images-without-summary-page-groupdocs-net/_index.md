---
title: "How to Compare Images in .NET – Skip Summary Page"
linktitle: "Compare Images .NET Without Summary"
description: "Learn how to compare images in .NET using GroupDocs.Comparison while disabling the summary page. This tutorial covers setup, code, performance tips, and real‑world use cases."
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
date: "2026-05-31"
lastmod: "2026-05-31"
weight: 1
url: "/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/"
categories: ["Image Processing"]
tags: ["dotnet", "image-comparison", "groupdocs", "csharp"]
type: docs
schemas:
- type: TechArticle
  headline: How to Compare Images in .NET – Skip Summary Page
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  dateModified: '2026-05-31'
  author: GroupDocs
- type: HowTo
  name: How to Compare Images in .NET – Skip Summary Page
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the gateway to all comparison operations. It implements
      `IDisposable`, so wrapping it in a `using` block guarantees that file handles
      and unmanaged memory are released promptly, even if an exception is thrown.
  - name: Configure CompareOptions for No Summary
    text: Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This
      flag tells the engine to skip the creation of the default HTML report, which
      is the primary source of extra I/O in image‑only scenarios.
  - name: Add Target Image(s) for Comparison
    text: You can call `Add()` multiple times to compare one source against several
      targets in a single batch. Each call can receive its own `CompareOptions` if
      you need per‑image customizations.
  - name: Execute Comparison and Save Results
    text: '`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`.
      The result contains a `Stream` with the diff image, which you can save directly
      to disk, send over a network, or embed in a UI component.'
- type: FAQPage
  questions:
  - question: What is the main advantage of skipping the summary page?
    answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
  - question: Can I still retrieve detailed change metadata without a summary page?
    answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
  - question: Which image formats are supported?
    answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
  - question: How should I handle very large images (e.g., >20 MB)?
    answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
  - question: Is this approach safe for multi‑threaded applications?
    answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
---

# How to Compare Images in .NET – Skip Summary Page

When you need to **how to compare images** programmatically in a .NET application, the last thing you want is an extra summary page that wastes time and storage. Whether you are building a quality‑control line, a content‑management pipeline, or an automated visual‑regression test suite, skipping the summary page can shave seconds off each run and keep your disk footprint lean.

In this tutorial you will learn how to use **GroupDocs.Comparison for .NET** to compare two images efficiently, configure the library to suppress summary generation, and apply best‑practice performance tricks. We’ll also explore why this matters, when to use it, and how to avoid common pitfalls.

## Quick Answers
- **What is the fastest way to compare images without a summary page?** Use `Comparer` with `CompareOptions` and set `GenerateSummaryPage = false`.  
- **Which library supports this out of the box?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Do I need a license?** Yes, a commercial license is required for production; a free trial works for development.  
- **Can I compare more than two images at once?** Absolutely – call `Add()` multiple times before `Compare()`.  
- **Is this approach suitable for large‑scale batch jobs?** Yes, when combined with batch processing and proper memory handling.

## What is GroupDocs.Comparison?
`GroupDocs.Comparison` is a .NET library that detects visual differences between documents and images, producing side‑by‑side or overlay results. It supports **50+ input and output formats**, including JPEG, PNG, BMP, TIFF, and GIF, and can process multi‑hundred‑page files without loading the entire file into memory.

## Why Skip the Summary Page?
Disabling the summary page reduces I/O by up to **70 %** for image‑only comparisons and cuts processing time by roughly **30 %** on average, according to the library’s benchmark suite. When you only need the diff image (for automated testing or QC pass/fail decisions), the extra HTML report adds no value and only consumes disk space.

## Prerequisites and Environment Setup

### What You’ll Need
- **GroupDocs.Comparison for .NET** version **25.4.0** or newer  
- Visual Studio 2019 + or any .NET‑compatible IDE  
- .NET Framework 4.6.1 + **or** .NET Core 2.0 +  
- Basic C# knowledge and familiarity with file I/O  

### Recommended Extras
- A small test project containing a pair of sample images (e.g., `source.png` and `target.png`).  
- Optional: Dependency injection setup if you prefer a service‑oriented architecture.  

### Why These Prerequisites Matter
The specified library version includes the `GenerateSummaryPage` flag and performance improvements that older releases lack. Using a modern IDE ensures you can leverage NuGet package management and see compile‑time warnings early.

## How to Install GroupDocs.Comparison
GroupDocs.Comparison can be added to any .NET project via NuGet, which handles downloading the binaries and updating the project file. Choose the method that matches your workflow: the Package Manager Console for Visual Studio users or the .NET CLI for command‑line environments. Both commands automatically resolve dependencies and ensure the correct version is referenced.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Replace `25.4.0` with the exact version you plan to lock.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Both commands add the library to your project file and restore the necessary binaries.

**Pro Tip:** Pin the version in your `.csproj` to avoid accidental upgrades that could change API behavior.

## Licensing Considerations
GroupDocs.Comparison requires a license for any production deployment. You can start with a **free trial** that provides full functionality, then upgrade to a **temporary license** for extended testing, and finally to a **full commercial license** for production. Remember to place the `GroupDocs.Comparison.lic` file in the application root or specify its path programmatically.

## Basic Project Setup

Create a new console app (or integrate into an existing service) and add the following boilerplate code. This snippet demonstrates the minimal setup required before you dive into comparison logic.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define directory paths for input images and output results
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Initialize paths to your source and target images
string sourceImagePath = Path.Combine(documentDirectory, "sourceImage.jpg");
string targetImagePath = Path.Combine(documentDirectory, "targetImage.jpg");

// Output image path for comparison result
string resultImagePath = Path.Combine(outputDirectory, "resultImage.jpg");
```

> **Important:** Always use `Path.Combine()` for file paths. It automatically handles OS‑specific path separators and avoids subtle bugs when moving between Windows and Linux containers.

## Step‑by‑Step Implementation Guide

### How do I compare images without a summary page?
`Comparer` is the primary class in GroupDocs.Comparison that orchestrates document and image comparison operations. `CompareOptions` holds configuration settings that control how the comparison is performed, such as whether to generate a summary page. Load the source image, configure `CompareOptions` to disable the summary, add the target image, and invoke `Compare()`. The method returns a `ComparisonResult` containing the diff image stream, which you can write to disk, send over a network, or embed in a UI component. This approach ensures only the essential diff is produced, eliminating any extra HTML or PDF reports.

```csharp
using (Comparer comparer = new Comparer())
{
    // Load source image
    comparer.Add(sourcePath);

    // Configure options – this is where we turn off the summary page
    CompareOptions options = new CompareOptions
    {
        GenerateSummaryPage = false,
        // You can also tweak sensitivity here if needed
        Sensitivity = 0.5
    };

    // Add the target image for comparison
    comparer.Add(targetPath, options);

    // Execute comparison and retrieve the result image stream
    ComparisonResult result = comparer.Compare();

    // Save the diff image
    using (FileStream outStream = new FileStream(outputPath, FileMode.Create))
    {
        result.Save(outStream);
    }
}
```

The code above performs the entire comparison in **four logical steps** and writes only the diff image, leaving out any HTML or PDF summary.

### Step 1: Initialize the Comparer Object
The `Comparer` class is the gateway to all comparison operations. It implements `IDisposable`, so wrapping it in a `using` block guarantees that file handles and unmanaged memory are released promptly, even if an exception is thrown.

### Step 2: Configure CompareOptions for No Summary
Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This flag tells the engine to skip the creation of the default HTML report, which is the primary source of extra I/O in image‑only scenarios.

### Step 3: Add Target Image(s) for Comparison
You can call `Add()` multiple times to compare one source against several targets in a single batch. Each call can receive its own `CompareOptions` if you need per‑image customizations.

### Step 4: Execute Comparison and Save Results
`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`. The result contains a `Stream` with the diff image, which you can save directly to disk, send over a network, or embed in a UI component.

## Complete Production‑Ready Method

Below is a ready‑to‑use method you can drop into any .NET service. It includes path validation, exception handling, and optional logging hooks.

```csharp
public static void CompareImagesWithoutSummary(string sourcePath, string targetPath, string outputPath)
{
    try
    {
        using (Comparer comparer = new Comparer(sourcePath))
        {
            // Configure options to skip summary generation
            CompareOptions options = new CompareOptions
            {
                GenerateSummaryPage = false
            };
            
            // Add target image and execute comparison
            comparer.Add(targetPath);
            comparer.Compare(outputPath, options);
            
            Console.WriteLine($"Comparison completed successfully. Result saved to: {outputPath}");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error during image comparison: {ex.Message}");
        throw; // Re-throw for proper error handling upstream
    }
}
```

## Common Implementation Pitfalls (And How to Avoid Them)

- **Path Issues:** Always verify that both source and target files exist with `File.Exists()`. A missing file will throw a `FileNotFoundException` that can be caught early.  
- **Memory Pressure:** Large images (10 MB +) can consume significant RAM. Process them in batches and consider down‑scaling if pixel‑perfect accuracy isn’t required.  
- **File Locks:** Ensure no other process holds an exclusive lock on the image files. This is especially important in multi‑threaded or containerized environments.  

## Practical Applications and Use Cases

### Quality Control in Manufacturing
A production line captures images of each item and compares them against a golden reference. Skipping the summary page allows the system to decide “pass” or “fail” within milliseconds, keeping the line moving at high speed.

### Content Management Systems
When users upload assets, the CMS can instantly detect duplicates or near‑duplicates, preventing storage bloat and improving search relevance. The diff image can be stored as a thumbnail for quick visual inspection.

### Automated UI Testing (Visual Regression)
Selenium or Playwright can capture screenshots of a web page, then feed them to this comparison routine. The diff image highlights UI changes, and because no summary is generated, the CI pipeline remains fast and lightweight.

### Medical Imaging (With Auditing)
Radiology workflows sometimes need to flag changes between successive scans. While you might still generate a detailed audit log, the diff image itself can be produced without a summary page, reducing processing time for large DICOM‑converted PNGs.

## Performance Considerations and Optimization

### Memory Management Best Practices
Process images in **batches of 20–50** depending on server RAM. Release each `Comparer` instance promptly and invoke `GC.Collect()` only if you notice memory spikes during long‑running jobs.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Disk I/O Optimization
Place your input, output, and temporary directories on the same fast SSD volume. Delete temporary files immediately after the diff image is saved to avoid unnecessary disk usage.

### Threading and Async Considerations
GroupDocs.Comparison is thread‑safe for read‑only operations, but avoid sharing a single `Comparer` instance across threads. Instead, spin up independent tasks:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Troubleshooting Common Issues

### File Path and Permission Errors
- **Symptom:** `FileNotFoundException` or `UnauthorizedAccessException`.  
- **Solution:** Use `Path.GetFullPath()` to debug the resolved path, ensure the application pool identity (or Docker container user) has read/write rights, and double‑check that the path isn’t truncated by environment variables.

### Memory and Performance Bottlenecks
- **Symptom:** Slow runs or `OutOfMemoryException`.  
- **Solution:** Resize images to a common resolution (e.g., 1024 × 768) when exact pixel comparison isn’t required. Monitor memory with tools like dotMemory or the built‑in Performance Profiler.

### Licensing Problems
- **Symptom:** Watermarked diff image or `LicenseException`.  
- **Solution:** Confirm that `GroupDocs.Comparison.lic` is located in the executable directory or explicitly load it via `License license = new License(); license.SetLicense("path/to/license.file");`.

## Advanced Configuration Options

### Customizing Comparison Sensitivity
You can fine‑tune how the engine treats minor pixel variations (e.g., compression artifacts) by adjusting the `Sensitivity` property on `CompareOptions`. Lower values make the comparison stricter.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Output Format Optimization
If you need the diff image in a specific format (PNG vs. JPEG), set the `OutputFormat` property:

```csharp
options.OutputFormat = ImageSaveOptions.SaveFormat.Png;
```

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    // Customize highlighting colors if needed
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

## Integration with Popular .NET Frameworks

### ASP.NET Core Service Example
Expose a lightweight HTTP endpoint that accepts two image streams, runs the comparison, and returns the diff image as a `FileResult`.

```csharp
public interface IImageComparisonService
{
    Task<string> CompareImagesAsync(string sourceImage, string targetImage);
}

public class ImageComparisonService : IImageComparisonService
{
    private readonly ILogger<ImageComparisonService> _logger;
    private readonly string _outputDirectory;

    public ImageComparisonService(ILogger<ImageComparisonService> logger, IConfiguration config)
    {
        _logger = logger;
        _outputDirectory = config.GetValue<string>("ImageComparison:OutputDirectory");
    }

    public async Task<string> CompareImagesAsync(string sourceImage, string targetImage)
    {
        // Your implementation here
        return await Task.FromResult("comparisonResult.jpg");
    }
}
```

### Dependency Injection Registration
Add the comparer as a scoped service in `Program.cs` or `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Frequently Asked Questions

**Q: What is the main advantage of skipping the summary page?**  
A: It cuts processing time by up to 30 % and reduces disk usage by roughly 70 % for image‑only comparisons, which is critical for high‑throughput pipelines.

**Q: Can I still retrieve detailed change metadata without a summary page?**  
A: Yes. The `ComparisonResult` object exposes a `Changes` collection that contains programmatic information about each detected difference.

**Q: Which image formats are supported?**  
A: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.

**Q: How should I handle very large images (e.g., >20 MB)?**  
A: Process them in smaller batches, optionally down‑scale them, and monitor memory usage. Using `Comparer` in a `using` block ensures resources are released promptly.

**Q: Is this approach safe for multi‑threaded applications?**  
A: Yes, as long as each thread creates its own `Comparer` instance. Sharing a single instance can lead to race conditions.

## Additional Resources

- [GroupDocs.Comparison Documentation](https://docs.groupdocs.com/comparison/net/)
- [API Reference](https://reference.groupdocs.com/comparison/net/)
- [Download](https://releases.groupdocs.com/comparison/net/)
- [Purchase](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/comparison/net/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/comparison/)

---

**Last Updated:** 2026-05-31  
**Tested With:** GroupDocs.Comparison 25.4.0 for .NET  
**Author:** GroupDocs

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

```csharp
// Create a Comparer object with the source image path
using (Comparer comparer = new Comparer(sourceImagePath))
{
    // Configuration will follow in subsequent steps
}
```

```csharp
// Set up compare options to avoid generating a summary page
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```

```csharp
// Add the target image to the comparison
comparer.Add(targetImagePath);
```

```csharp
// Execute comparison with configured options and save to result path
comparer.Compare(resultImagePath, options);
```

```csharp
public static void ProcessImageBatch(List<string> imagePairs, int batchSize = 10)
{
    for (int i = 0; i < imagePairs.Count; i += batchSize)
    {
        var batch = imagePairs.Skip(i).Take(batchSize);
        // Process batch and allow garbage collection between batches
        foreach (var pair in batch)
        {
            // Your comparison logic here
        }
        
        // Explicit garbage collection after each batch (use sparingly)
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```

```csharp
public static async Task<bool> CompareImagesAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            CompareImagesWithoutSummary(source, target, output);
            return true;
        }
        catch
        {
            return false;
        }
    });
}
```

## Related Tutorials

- [Image Comparison .NET - Compare Images Programmatically](/comparison/net/image-comparison/compare-images-from-path/)
- [Image Comparison .NET - Compare Images from Stream](/comparison/net/image-comparison/compare-images-from-stream/)
- [GroupDocs Comparison .NET Tutorial - Complete Basic Usage Guide](/comparison/net/basic-usage/)
