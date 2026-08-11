---
categories:
- Image Processing
date: '2026-05-31'
description: Lär dig hur du jämför bilder i .NET med GroupDocs.Comparison samtidigt
  som du inaktiverar sammanfattningssidan. Denna handledning täcker installation,
  kod, prestandatips och verkliga användningsfall.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: Jämför bilder .NET utan sammanfattning
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  headline: How to Compare Images in .NET – Skip Summary Page
  type: TechArticle
- description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  name: How to Compare Images in .NET – Skip Summary Page
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
  type: HowTo
- questions:
  - answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
    question: What is the main advantage of skipping the summary page?
  - answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
    question: Can I still retrieve detailed change metadata without a summary page?
  - answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
    question: Which image formats are supported?
  - answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
    question: How should I handle very large images (e.g., >20 MB)?
  - answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
    question: Is this approach safe for multi‑threaded applications?
  type: FAQPage
tags:
- dotnet
- image-comparison
- groupdocs
- csharp
title: Hur man jämför bilder i .NET – Hoppa över sammanfattningssidan
type: docs
url: /sv/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Hur man jämför bilder i .NET – Hoppa över sammanfattningssida

När du behöver **how to compare images** programatiskt i en .NET‑applikation är det sista du vill ha en extra sammanfattningssida som slösar tid och lagring. Oavsett om du bygger en kvalitets‑kontrolllinje, en innehållshanterings‑pipeline eller en automatiserad visuell‑regressionstestsvit, kan hoppa över sammanfattningssidan spara sekunder per körning och hålla ditt diskutrymme smalt.

I den här handledningen kommer du att lära dig hur du använder **GroupDocs.Comparison for .NET** för att jämföra två bilder effektivt, konfigurera biblioteket för att undertrycka generering av sammanfattning och tillämpa bästa praxis‑prestandatrick. Vi kommer också att utforska varför detta är viktigt, när du ska använda det och hur du undviker vanliga fallgropar.

## Snabba svar
- **Vad är det snabbaste sättet att jämföra bilder utan en sammanfattningssida?** Use `Comparer` with `CompareOptions` and set `GenerateSummaryPage = false`.  
- **Vilket bibliotek stöder detta direkt?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Behöver jag en licens?** Yes, a commercial license is required for production; a free trial works for development.  
- **Kan jag jämföra mer än två bilder samtidigt?** Absolutely – call `Add()` multiple times before `Compare()`.  
- **Är detta tillvägagångssätt lämpligt för storskaliga batchjobb?** Yes, when combined with batch processing and proper memory handling.

## Vad är GroupDocs.Comparison?
`GroupDocs.Comparison` är ett .NET‑bibliotek som upptäcker visuella skillnader mellan dokument och bilder och producerar sida‑vid‑sida‑ eller överlagringsresultat. Det stöder **50+ in‑ och utdataformat**, inklusive JPEG, PNG, BMP, TIFF och GIF, och kan bearbeta fler‑hundra‑sidiga filer utan att läsa in hela filen i minnet.

## Varför hoppa över sammanfattningssidan?
Att inaktivera sammanfattningssidan minskar I/O med upp till **70 %** för bild‑endast jämförelser och kortar ner behandlingstiden med ungefär **30 %** i genomsnitt, enligt bibliotekets benchmark‑svit. När du bara behöver diff‑bilden (för automatiserad testning eller QC‑godkännande‑/avslag‑beslut) tillför den extra HTML‑rapporten inget värde och tar bara upp diskutrymme.

## Förutsättningar och miljöinställning

### Vad du behöver
- **GroupDocs.Comparison for .NET** version **25.4.0** or newer  
- Visual Studio 2019 + or any .NET‑compatible IDE  
- .NET Framework 4.6.1 + **or** .NET Core 2.0 +  
- Grundläggande kunskap i C# och bekantskap med fil‑I/O  

### Rekommenderade extrafunktioner
- Ett litet testprojekt som innehåller ett par exempelbilder (t.ex. `source.png` och `target.png`).  
- Valfritt: Dependency injection‑inställning om du föredrar en service‑orienterad arkitektur.  

### Varför dessa förutsättningar är viktiga
Den angivna biblioteksversionen innehåller flaggan `GenerateSummaryPage` och prestandaförbättringar som äldre versioner saknar. Att använda ett modernt IDE säkerställer att du kan utnyttja NuGet‑pakethantering och se kompileringsvarningar tidigt.

## Hur man installerar GroupDocs.Comparison
GroupDocs.Comparison kan läggas till i vilket .NET‑projekt som helst via NuGet, vilket hanterar nedladdning av binärfilerna och uppdatering av projektfilen. Välj den metod som matchar ditt arbetsflöde: Package Manager Console för Visual Studio‑användare eller .NET CLI för kommandorads‑miljöer. Båda kommandona löser automatiskt beroenden och säkerställer att rätt version refereras.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Ersätt `25.4.0` med den exakta version du planerar att låsa.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Båda kommandona lägger till biblioteket i din projektfil och återställer de nödvändiga binärfilerna.

**Pro Tip:** Fäst versionen i din `.csproj` för att undvika oavsiktliga uppgraderingar som kan ändra API‑beteende.

## Licensöverväganden
GroupDocs.Comparison kräver en licens för alla produktionsdistributioner. Du kan börja med en **free trial** som ger full funktionalitet, sedan uppgradera till en **temporary license** för utökad testning, och slutligen till en **full commercial license** för produktion. Kom ihåg att placera `GroupDocs.Comparison.lic`‑filen i applikationens rot eller ange dess sökväg programatiskt.

## Grundläggande projektinställning
Skapa en ny konsolapp (eller integrera i en befintlig tjänst) och lägg till följande grundkod. Detta kodsnutt demonstrerar den minsta uppsättningen som krävs innan du dyker in i jämförelselogiken.

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

> **Viktigt:** Always use `Path.Combine()` for file paths. It automatically handles OS‑specific path separators and avoids subtle bugs when moving between Windows and Linux containers.

## Steg‑för‑steg implementationsguide

### Hur jämför jag bilder utan en sammanfattningssida?
`Comparer` är den primära klassen i GroupDocs.Comparison som orkestrerar dokument‑ och bildjämförelseoperationer. `CompareOptions` innehåller konfigurationsinställningar som styr hur jämförelsen utförs, t.ex. om en sammanfattningssida ska genereras. Läs in källbilden, konfigurera `CompareOptions` för att inaktivera sammanfattningen, lägg till målbilden och anropa `Compare()`. Metoden returnerar ett `ComparisonResult` som innehåller diff‑bildströmmen, som du kan skriva till disk, skicka över ett nätverk eller bädda in i en UI‑komponent. Detta tillvägagångssätt säkerställer att endast den väsentliga diffen produceras, utan extra HTML‑ eller PDF‑rapporter.

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

Koden ovan utför hela jämförelsen i **fyra logiska steg** och skriver endast diff‑bilden, utan någon HTML‑ eller PDF‑sammanfattning.

### Steg 1: Initiera Comparer‑objektet
`Comparer`‑klassen är porten till alla jämförelseoperationer. Den implementerar `IDisposable`, så att omsluta den i ett `using`‑block garanterar att filhandtag och ohanterat minne frigörs omedelbart, även om ett undantag kastas.

### Steg 2: Konfigurera CompareOptions för ingen sammanfattning
Sätt `GenerateSummaryPage = false` på `CompareOptions`‑instansen. Denna flagga instruerar motorn att hoppa över skapandet av standard‑HTML‑rapporten, vilket är den primära källan till extra I/O i bild‑endast scenarier.

### Steg 3: Lägg till målbild(er) för jämförelse
Du kan anropa `Add()` flera gånger för att jämföra en källa mot flera mål i ett enda batch. Varje anrop kan få sin egen `CompareOptions` om du behöver anpassningar per bild.

### Steg 4: Utför jämförelse och spara resultat
`Comparer.Compare()` utför det tunga arbetet och returnerar ett `ComparisonResult`. Resultatet innehåller en `Stream` med diff‑bilden, som du kan spara direkt till disk, skicka över ett nätverk eller bädda in i en UI‑komponent.

## Komplett produktionsklar metod
Nedan är en färdig‑till‑användning‑metod som du kan lägga in i vilken .NET‑tjänst som helst. Den inkluderar sökvägsvalidering, undantagshantering och valfria loggningskrokar.

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

## Vanliga implementeringsfallgropar (och hur man undviker dem)

- **Sökvägsproblem:** Always verify that both source and target files exist with `File.Exists()`. A missing file will throw a `FileNotFoundException` that can be caught early.  
- **Minnetryck:** Large images (10 MB +) can consume significant RAM. Process them in batches and consider down‑scaling if pixel‑perfect accuracy isn’t required.  
- **Fil lås:** Ensure no other process holds an exclusive lock on the image files. This is especially important in multi‑threaded or containerized environments.  

## Praktiska tillämpningar och användningsfall

### Kvalitetskontroll i tillverkning
En produktionslinje fångar bilder av varje objekt och jämför dem mot en guldstandard. Att hoppa över sammanfattningssidan låter systemet besluta “pass” eller “fail” inom millisekunder, vilket håller linjen i hög hastighet.

### Innehållshanteringssystem
När användare laddar upp tillgångar kan CMS omedelbart upptäcka dubbletter eller nästan‑dubbletter, vilket förhindrar lagringsuppblåsthet och förbättrar sökrelevans. Diff‑bilden kan lagras som en miniatyr för snabb visuell inspektion.

### Automatiserad UI‑testning (visuell regression)
Selenium eller Playwright kan fånga skärmbilder av en webbsida och sedan mata dem till denna jämförelseslinga. Diff‑bilden markerar UI‑förändringar, och eftersom ingen sammanfattning genereras förblir CI‑pipeline snabb och lättviktig.

### Medicinsk bildbehandling (med revision)
Radiologiska arbetsflöden behöver ibland flagga förändringar mellan på varandra följande skanningar. Även om du fortfarande kan generera en detaljerad revisionslogg, kan diff‑bilden själv produceras utan en sammanfattningssida, vilket minskar behandlingstiden för stora DICOM‑konverterade PNG‑filer.

## Prestandaöverväganden och optimering

### Bästa praxis för minneshantering
Bearbeta bilder i **batchar på 20–50** beroende på server‑RAM. Frigör varje `Comparer`‑instans omedelbart och anropa `GC.Collect()` endast om du märker minnesspikar under långvariga jobb.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Optimering av disk‑I/O
Placera dina in‑, ut‑ och temporära kataloger på samma snabba SSD‑volym. Radera temporära filer omedelbart efter att diff‑bilden har sparats för att undvika onödig disk‑användning.

### Trådning och async‑överväganden
GroupDocs.Comparison är trådsäker för skriv‑skyddade operationer, men undvik att dela en enda `Comparer`‑instans mellan trådar. Skapa istället oberoende uppgifter:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Felsökning av vanliga problem

### Fel med fil‑sökväg och behörigheter
- **Symptom:** `FileNotFoundException` or `UnauthorizedAccessException`.  
- **Lösning:** Use `Path.GetFullPath()` to debug the resolved path, ensure the application pool identity (or Docker container user) has read/write rights, and double‑check that the path isn’t truncated by environment variables.

### Minnes- och prestandaflaskhalsar
- **Symptom:** Slow runs or `OutOfMemoryException`.  
- **Lösning:** Resize images to a common resolution (e.g., 1024 × 768) when exact pixel comparison isn’t required. Monitor memory with tools like dotMemory or the built‑in Performance Profiler.

### Licensproblem
- **Symptom:** Watermarked diff image or `LicenseException`.  
- **Lösning:** Confirm that `GroupDocs.Comparison.lic` is located in the executable directory or explicitly load it via `License license = new License(); license.SetLicense("path/to/license.file");`.

## Avancerade konfigurationsalternativ

### Anpassning av jämförelsesensitivitet
Du kan finjustera hur motorn behandlar mindre pixelvariationer (t.ex. komprimeringsartefakter) genom att justera `Sensitivity`‑egenskapen på `CompareOptions`. Lägre värden gör jämförelsen striktare.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Optimering av utdataformat
Om du behöver diff‑bilden i ett specifikt format (PNG vs. JPEG), sätt `OutputFormat`‑egenskapen:

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

## Integration med populära .NET‑ramverk

### ASP.NET Core‑tjänsteexempel
Exponera en lättviktig HTTP‑endpoint som accepterar två bild‑strömmar, kör jämförelsen och returnerar diff‑bilden som ett `FileResult`.

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

### Registrering av dependency injection
Lägg till comparer som en scoped‑tjänst i `Program.cs` eller `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Vanliga frågor

**Q: Vad är den största fördelen med att hoppa över sammanfattningssidan?**  
A: Det minskar behandlingstiden med upp till 30 % och minskar diskutrymmet med ungefär 70 % för bild‑endast jämförelser, vilket är kritiskt för hög‑genomströmning pipelines.

**Q: Kan jag fortfarande hämta detaljerad förändringsmetadata utan en sammanfattningssida?**  
A: Ja. `ComparisonResult`‑objektet exponerar en `Changes`‑samling som innehåller programmatisk information om varje upptäckt skillnad.

**Q: Vilka bildformat stöds?**  
A: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.

**Q: Hur bör jag hantera mycket stora bilder (t.ex. >20 MB)?**  
A: Bearbeta dem i mindre batchar, eventuellt ner­skala dem och övervaka minnesanvändning. Att använda `Comparer` i ett `using`‑block säkerställer att resurser frigörs omedelbart.

**Q: Är detta tillvägagångssätt säkert för flertrådade applikationer?**  
A: Ja, så länge varje tråd skapar sin egen `Comparer`‑instans. Att dela en enda instans kan leda till race‑förhållanden.

## Ytterligare resurser

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

## Relaterade handledningar

- [Image Comparison .NET - Compare Images Programmatically](/comparison/net/image-comparison/compare-images-from-path/)
- [Image Comparison .NET - Compare Images from Stream](/comparison/net/image-comparison/compare-images-from-stream/)
- [GroupDocs Comparison .NET Tutorial - Complete Basic Usage Guide](/comparison/net/basic-usage/)