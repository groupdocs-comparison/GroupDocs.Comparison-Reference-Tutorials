---
categories:
- Document Processing
date: '2026-06-10'
description: Lär dig hur du jämför dokument .net med GroupDocs.Comparison. Steg‑för‑steg‑guide
  som täcker installation, kod, jämföra Excel‑filer C#, jämföra PDF‑filer C# och bästa
  praxis.
keywords:
- compare documents .net
- compare excel files c#
- compare pdf files c#
- document comparison best practices
lastmod: '2026-06-10'
schemas:
- author: GroupDocs
  dateModified: '2026-06-10'
  description: Learn how to compare documents .net with GroupDocs.Comparison. Step‑by‑step
    guide covering setup, code, compare excel files c#, compare pdf files c#, and
    best practices.
  headline: compare documents .net – Complete GroupDocs Implementation Guide
  type: TechArticle
- questions:
  - answer: You can add multiple target documents to a single `Comparer` instance
      using repeated `Add()` calls, but processing them sequentially is recommended
      for large batches.
    question: How many documents can I compare at once?
  - answer: Yes—pass the password when constructing the `Comparer` or loading the
      document.
    question: Can GroupDocs.Comparison handle password‑protected files?
  - answer: Over 50 formats, including DOCX, XLSX, PPTX, PDF, JPEG, PNG, TXT, and
      more.
    question: What file formats does GroupDocs.Comparison support?
  - answer: Use `ComparisonSettings` to set `InsertedColor`, `DeletedColor`, and `StyleChangeColor`.
    question: How do I customize the appearance of changes?
  - answer: Absolutely—disable options like `DetectStyleChanges` or `DetectTableChanges`
      in `ComparisonSettings`.
    question: Is it possible to ignore specific change types?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- groupdocs
- automation
title: jämför dokument .net – Komplett GroupDocs-implementeringsguide
type: docs
url: /sv/net/basic-comparison/implement-document-comparison-groupdocs-net/
weight: 1
---

# jämför dokument .net – Komplett GroupDocs-implementeringsguide

Om du behöver **jämföra dokument .net**, har du kommit till rätt ställe. Föreställ dig att öppna två kontrakt som ser identiska ut och omedelbart upptäcka varje förändring—ingen manuell bläddring, inga missade redigeringar. Det är kraften i automatiserad dokumentjämförelse, och med **GroupDocs.Comparison for .NET** kan du göra det på några minuter.

## Snabba svar
- **Vilket bibliotek hanterar dokumentjämförelse i .NET?** GroupDocs.Comparison.
- **Kan jag jämföra Word-, Excel- och PDF-filer?** Ja—över 50 format stöds.
- **Vilken version bör jag använda?** Version 25.4.0 erbjuder bästa prestanda och stabilitet.
- **Behöver jag en licens för produktion?** En kommersiell licens krävs för produktionsdistributioner.
- **Är asynkron bearbetning möjlig?** Absolut—använd `Task.Run` med jämförelses‑API‑et.

## Vad är GroupDocs.Comparison?
GroupDocs.Comparison är ett .NET-bibliotek som programatiskt upptäcker skillnader mellan två eller fler dokument och genererar en markerad resultatfil. Det stöder över 50 format, bearbetar flertusenssidiga filer utan att ladda hela innehållet i minnet, och ger finjusterad kontroll över jämförelsesinställningarna.

## Varför använda GroupDocs.Comparison för jämföra dokument .net?
GroupDocs.Comparison levererar snabb, exakt och skalbar dokumentdiff för .NET-applikationer. Det kan bearbeta stora PDF‑ och Office‑filer på sekunder, bevara formatering och visuell integritet samtidigt som det markerar insättningar, borttagningar och stiländringar. Biblioteket fungerar över .NET Core, .NET 5/6/7 och hela .NET Framework, vilket gör det till ett mångsidigt val för alla projekt.

- **Hastighet:** Bearbetar en 200‑sidig PDF på under 2 sekunder på en standardserver.  
- **Noggrannhet:** Upptäcker text, formatering, tabeller och bilder med 99,9 % precision.  
- **Skalbarhet:** Hanterar batchjobb med tusentals filer med hjälp av streaming‑API:er.  
- **Flexibilitet:** Fungerar med .NET Core 3.1+, .NET 5/6/7 och .NET Framework 4.6.1+.

## Förutsättningar
- **Utvecklingsmiljö:** .NET Core 3.1 eller nyare, eller .NET Framework 4.6.1 +  
- **GroupDocs.Comparison‑bibliotek:** Version 25.4.0 (installerat via NuGet)  
- **Exempelfiler:** Word-, PDF- eller Excel‑dokument för testning  
- **Grundläggande C#‑kunskaper:** Klasser, metoder, `using`‑satser  

### Bra att ha (valfritt)
- Bekantskap med NuGet‑pakethantering  
- Erfarenhet av fil‑I/O och strömmar  
- Förståelse för async/await‑mönster  

## Hur man jämför dokument .net med GroupDocs.Comparison?
För att jämföra två dokument med GroupDocs.Comparison, läs in varje fil i en ström, konfigurera valfria ComparisonSettings och anropa Compare‑metoden på en Comparer‑instans. API‑et returnerar ett resultatsdokument som markerar skillnader, och du kan spara det i vilket stödformat som helst. Detta tillvägagångssätt kräver bara några rader kod samtidigt som du får full kontroll över jämförelseprocessen.

### Steg‑för‑steg‑implementering

### 1️⃣ Smart dokument‑sökvägshantering
Centralisering av filsökvägar förhindrar “file not found”-fel och gör miljöbyten smidiga.

```csharp
public static class Constants
{
    public const string SOURCE_WORD = @"YOUR_DOCUMENT_DIRECTORY\source.docx";
    public const string TARGET_WORD = @"YOUR_DOCUMENT_DIRECTORY\target.docx";

    public static string GetOutputDirectoryPath()
    {
        return @"YOUR_OUTPUT_DIRECTORY";
    }

    public const string RESULT_WORD = "result.docx";
}
```

**Varför detta fungerar:**  
- En plats för att uppdatera sökvägar för dev, test eller produktion.  
- Eliminera hårdkodade strängar spridda i kodbasen.  

### 2️⃣ Kärn‑jämförelselogik
`Comparer`‑klassen är motorn som driver diff‑algoritmen.

```csharp
using (Comparer comparer = new Comparer(Constants.SOURCE_WORD))
{
    // Add the target document for comparison
    comparer.Add(Constants.TARGET_WORD);

    // Perform the comparison and save the result
    string outputFileName = Path.Combine(Constants.GetOutputDirectoryPath(), Constants.RESULT_WORD);
    comparer.Compare(outputFileName);
}
```

**Definitionsankare:**  
`Comparer` är GroupDocs.Comparisons kärnklass som orkestrerar dokumentanalys och producerar det markerade resultatet.

**Hur det hjälper:**  
- Stöder flera mål‑dokument via upprepade `Add()`‑anrop.  
- Genererar en resultfil med förändringar markerade i rött, grönt eller anpassade färger.

### 3️⃣ Avancerade inställningar för Excel och PDF
Du kan finjustera jämförelsen för att ignorera formatering eller fokusera på dataskillnader—perfekt för **compare excel files c#**‑scenarier.

```csharp
CompareOptions compareOptions = new CompareOptions()
{
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    StyleChangeDetection = true
};

using (Comparer comparer = new Comparer(sourcePath))
{
    comparer.Add(targetPath);
    comparer.Compare(outputPath, compareOptions);
}
```

**Definitionsankare:**  
`ComparisonSettings` låter dig aktivera eller inaktivera specifika förändringstyper såsom `DetectStyleChanges` eller `DetectTableChanges`.

### 4️⃣ Hantera flera format
GroupDocs.Comparison upptäcker automatiskt filtypen, men du kan också tvinga ett format när det behövs—idealiskt för **compare pdf files c#**.

```csharp
public static void CompareDocumentsByType(string sourcePath, string targetPath, string outputPath)
{
    string extension = Path.GetExtension(sourcePath).ToLower();
    
    using (Comparer comparer = new Comparer(sourcePath))
    {
        comparer.Add(targetPath);
        
        CompareOptions options = GetOptionsForFormat(extension);
        comparer.Compare(outputPath, options);
    }
}

private static CompareOptions GetOptionsForFormat(string extension)
{
    switch (extension)
    {
        case ".pdf":
            return new CompareOptions { DetectStyleChanges = false };
        case ".xlsx":
            return new CompareOptions { CalculateCoordinates = true };
        default:
            return new CompareOptions();
    }
}
```

### 5️⃣ Strömning av stora filer
När du bearbetar massiva dokument undviker strömning att hela filen laddas in i minnet.

```csharp
// For files over 50MB, consider this approach
using (var sourceStream = File.OpenRead(sourcePath))
using (var targetStream = File.OpenRead(targetPath))
using (var comparer = new Comparer(sourceStream))
{
    comparer.Add(targetStream);
    comparer.Compare(outputStream);
}
```

### 6️⃣ Robust felhantering
Låt aldrig en korrupt fil krascha din tjänst; omslut anrop i try‑catch‑block och logga användbar information.

```csharp
try
{
    using (Comparer comparer = new Comparer(sourcePath))
    {
        comparer.Add(targetPath);
        comparer.Compare(outputPath);
    }
}
catch (FileNotFoundException ex)
{
    Console.WriteLine($"Document not found: {ex.FileName}");
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine($"Access denied: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"Comparison failed: {ex.Message}");
}
```

## Bästa praxis för dokumentjämförelse
- **Validera indatafiler** innan du anropar API‑et för att tidigt fånga osupporterade format.  
- **Använd `Path.Combine`** för plattformsoberoende sökvägskonstruktion (se Fallgropar #1).  
- **Aktivera endast nödvändiga förändringstyper** för att förbättra prestanda (t.ex. inaktivera stilupptäckt för datacentrerade Excel‑blad).  
- **Disposera `Comparer`‑objekt** omedelbart för att frigöra inhemska resurser.  

## Vanliga fallgropar och hur man undviker dem

### Fallgrop #1: Problem med sökvägsseparatorer
**Lösning:** Bygg alltid sökvägar med `Path.Combine()` och `Path.DirectorySeparatorChar`.

```csharp
// Wrong - will break on different operating systems
string path = "C:/Documents/source.docx";

// Right - works everywhere
string path = Path.Combine("C:", "Documents", "source.docx");
```

### Fallgrop #2: Minnesutarmning vid stora filer
**Lösning:** Byt till strömningsläge för filer större än 50 MB.

```csharp
// For files over 50MB, consider this approach
using (var sourceStream = File.OpenRead(sourcePath))
using (var targetStream = File.OpenRead(targetPath))
using (var comparer = new Comparer(sourceStream))
{
    comparer.Add(targetStream);
    comparer.Compare(outputStream);
}
```

### Fallgrop #3: Ignorera undantag
**Lösning:** Implementera omfattande try‑catch‑block och logga stackspår.

```csharp
try
{
    using (Comparer comparer = new Comparer(sourcePath))
    {
        comparer.Add(targetPath);
        comparer.Compare(outputPath);
    }
}
catch (FileNotFoundException ex)
{
    Console.WriteLine($"Document not found: {ex.FileName}");
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine($"Access denied: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"Comparison failed: {ex.Message}");
}
```

## Strategier för prestandaoptimering

### Minneshantering
Återanvänd `Comparer`‑instanser när det är möjligt och anropa `Dispose()` efter varje jämförelse.

```csharp
// Always dispose of resources properly
using (var comparer = new Comparer(sourcePath))
{
    comparer.Add(targetPath);
    comparer.Compare(outputPath);
    
    // Comparer is automatically disposed here
}

// For batch processing, clear resources between comparisons
for (int i = 0; i < documentPairs.Count; i++)
{
    using (var comparer = new Comparer(documentPairs[i].Source))
    {
        comparer.Add(documentPairs[i].Target);
        comparer.Compare(documentPairs[i].Output);
    }
    
    // Force garbage collection every 10 documents if needed
    if (i % 10 == 0)
    {
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```

### Asynkron bearbetning
Kör jämförelser på bakgrundstrådar för att hålla UI responsivt.

```csharp
public async Task<bool> CompareDocumentsAsync(string sourcePath, string targetPath, string outputPath)
{
    return await Task.Run(() =>
    {
        try
        {
            using (var comparer = new Comparer(sourcePath))
            {
                comparer.Add(targetPath);
                comparer.Compare(outputPath);
                return true;
            }
        }
        catch
        {
            return false;
        }
    });
}
```

## Integration med populära .NET‑ramverk

### ASP.NET Core Web API‑integration
Exponera en REST‑endpoint som accepterar två filer och returnerar diff‑resultatet.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentComparisonController : ControllerBase
{
    [HttpPost("compare")]
    public async Task<IActionResult> CompareDocuments([FromForm] IFormFile sourceFile, [FromForm] IFormFile targetFile)
    {
        if (sourceFile == null || targetFile == null)
            return BadRequest("Both source and target files are required.");

        var tempFolder = Path.GetTempPath();
        var sourcePath = Path.Combine(tempFolder, sourceFile.FileName);
        var targetPath = Path.Combine(tempFolder, targetFile.FileName);
        var outputPath = Path.Combine(tempFolder, $"comparison_{Guid.NewGuid()}.pdf");

        try
        {
            // Save uploaded files
            using (var stream = new FileStream(sourcePath, FileMode.Create))
                await sourceFile.CopyToAsync(stream);
            
            using (var stream = new FileStream(targetPath, FileMode.Create))
                await targetFile.CopyToAsync(stream);

            // Perform comparison
            using (var comparer = new Comparer(sourcePath))
            {
                comparer.Add(targetPath);
                comparer.Compare(outputPath);
            }

            // Return the result file
            var fileBytes = await System.IO.File.ReadAllBytesAsync(outputPath);
            return File(fileBytes, "application/pdf", "comparison_result.pdf");
        }
        finally
        {
            // Clean up temp files
            File.Delete(sourcePath);
            File.Delete(targetPath);
            File.Delete(outputPath);
        }
    }
}
```

### Blazor‑komponent‑integration
Skapa en återanvändbar komponent som visar sid‑vid‑sid jämförelse i webbläsaren.

```csharp
@using GroupDocs.Comparison
@inject IJSRuntime JSRuntime

<div class="document-comparison">
    <InputFile OnChange="HandleFileSelection" multiple />
    <button @onclick="CompareDocuments" disabled="@(!CanCompare)">Compare Documents</button>
    
    @if (comparisonResult != null)
    {
        <div class="result">
            <a href="@comparisonResult" download="comparison_result.pdf">Download Result</a>
        </div>
    }
</div>

@code {
    private List<IBrowserFile> selectedFiles = new();
    private string comparisonResult;
    
    private bool CanCompare => selectedFiles.Count == 2;

    private async Task HandleFileSelection(InputFileChangeEventArgs e)
    {
        selectedFiles = e.GetMultipleFiles(2).ToList();
    }

    private async Task CompareDocuments()
    {
        if (selectedFiles.Count != 2) return;

        // Implementation similar to Web API example
        // Save files, compare, and generate result
    }
}
```

## Verkliga användningsfall

### Scenario 1: Juridisk kontraktsgranskning
Advokatbyråer kan automatiskt markera tillägg, borttagningar och formateringsändringar över kontraktsrevisioner.

```csharp
public class ContractReviewService
{
    public ContractComparisonResult ReviewContract(string originalContract, string revisedContract)
    {
        var outputPath = Path.Combine(Path.GetTempPath(), $"contract_review_{DateTime.Now:yyyyMMddHHmmss}.docx");
        
        var compareOptions = new CompareOptions
        {
            ShowDeletedContent = true,
            ShowInsertedContent = true,
            StyleChangeDetection = true,
            WordsSeparatorChars = new[] { ' ', '.', ',', '!', '?' }
        };

        using (var comparer = new Comparer(originalContract))
        {
            comparer.Add(revisedContract);
            comparer.Compare(outputPath, compareOptions);
        }

        return new ContractComparisonResult
        {
            OutputPath = outputPath,
            HasChanges = File.Exists(outputPath),
            ComparisonDate = DateTime.Now
        };
    }
}
```

### Scenario 2: Versionskontroll för kalkylblad
Finansavdelningar kan upptäcka förändringar i Excel‑modeller utan att manuellt öppna varje fil.

```csharp
public class DocumentVersionControl
{
    public void TrackDocumentChanges(string documentPath, string repositoryPath)
    {
        var versions = Directory.GetFiles(repositoryPath, "*.docx").OrderBy(f => f);
        var latestVersion = versions.LastOrDefault();

        if (latestVersion != null)
        {
            var comparisonPath = Path.Combine(repositoryPath, $"changes_{DateTime.Now:yyyyMMdd}.docx");
            
            using (var comparer = new Comparer(latestVersion))
            {
                comparer.Add(documentPath);
                comparer.Compare(comparisonPath);
            }

            // Archive the comparison for future reference
            ArchiveComparison(comparisonPath);
        }
    }

    private void ArchiveComparison(string comparisonPath)
    {
        // Implementation for archiving comparison results
        var archivePath = Path.Combine(Path.GetDirectoryName(comparisonPath), "archive", Path.GetFileName(comparisonPath));
        Directory.CreateDirectory(Path.GetDirectoryName(archivePath));
        File.Move(comparisonPath, archivePath);
    }
}
```

## Felsökningsguide

### Problem 1: “Filformat stöds inte”
**Lösning:** Verifiera filändelsen mot den stödlista (50+ format) och konvertera osupporterade typer till PDF först.

```csharp
private static readonly HashSet<string> SupportedFormats = new HashSet<string>(StringComparer.OrdinalIgnoreCase)
{
    ".docx", ".doc", ".pdf", ".xlsx", ".xls", ".pptx", ".ppt", ".txt", ".rtf"
};

public static bool IsFormatSupported(string filePath)
{
    var extension = Path.GetExtension(filePath);
    return SupportedFormats.Contains(extension);
}
```

### Problem 2: Minnesproblem med stora filer
**Lösning:** Aktivera strömning och bearbeta filer i delar.

```csharp
public static void CompareLargeDocuments(string sourcePath, string targetPath, string outputPath)
{
    var fileInfo = new FileInfo(sourcePath);
    
    if (fileInfo.Length > 50 * 1024 * 1024) // 50MB threshold
    {
        // Use streaming approach
        using (var sourceStream = File.OpenRead(sourcePath))
        using (var targetStream = File.OpenRead(targetPath))
        using (var outputStream = File.Create(outputPath))
        using (var comparer = new Comparer(sourceStream))
        {
            comparer.Add(targetStream);
            comparer.Compare(outputStream);
        }
    }
    else
    {
        // Standard approach for smaller files
        using (var comparer = new Comparer(sourcePath))
        {
            comparer.Add(targetPath);
            comparer.Compare(outputPath);
        }
    }
}
```

### Problem 3: Tomt jämförelsresultat
**Lösning:** Öka känsligheten genom att växla `DetectFormattingChanges` eller `DetectStyleChanges`.

```csharp
var compareOptions = new CompareOptions
{
    DetectStyleChanges = true,
    DiagramMasterSetting = new DiagramMasterSetting
    {
        UseSourceMaster = true,
        CloneSourceMaster = true
    },
    OriginalSize = new Size(600, 800),
    HeaderFootersComparison = true,
    PaperSize = PaperSize.A4
};
```

## Vanliga frågor

**Q: Hur många dokument kan jag jämföra samtidigt?**  
A: Du kan lägga till flera mål‑dokument till en enda `Comparer`‑instans med upprepade `Add()`‑anrop, men det rekommenderas att bearbeta dem sekventiellt för stora batcher.

**Q: Kan GroupDocs.Comparison hantera lösenordsskyddade filer?**  
A: Ja—ange lösenordet när du konstruerar `Comparer` eller laddar dokumentet.

```csharp
using (var comparer = new Comparer(sourcePath, new LoadOptions("password")))
{
    comparer.Add(targetPath, new LoadOptions("targetPassword"));
    comparer.Compare(outputPath);
}
```

**Q: Vilka filformat stöder GroupDocs.Comparison?**  
A: Över 50 format, inklusive DOCX, XLSX, PPTX, PDF, JPEG, PNG, TXT och fler.

**Q: Hur anpassar jag utseendet på förändringar?**  
A: Använd `ComparisonSettings` för att sätta `InsertedColor`, `DeletedColor` och `StyleChangeColor`.

```csharp
var compareOptions = new CompareOptions
{
    InsertedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Green,
        FontColor = Color.DarkGreen
    },
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

**Q: Är det möjligt att ignorera specifika förändringstyper?**  
A: Absolut—inaktivera alternativ som `DetectStyleChanges` eller `DetectTableChanges` i `ComparisonSettings`.

```csharp
var compareOptions = new CompareOptions
{
    DetectStyleChanges = false, // Ignore formatting changes
    HeaderFootersComparison = false, // Skip headers/footers
    WordsSeparatorChars = new[] { ' ', '\n', '\r', '\t' } // Define word boundaries
};
```

**Q: Kan jag jämföra dokument lagrade i molnlagring?**  
A: Ja—ladda ner strömmarna lokalt eller jämför direkt från en `MemoryStream`.

```csharp
using (var sourceStream = await DownloadFromCloudAsync(sourceUrl))
using (var targetStream = await DownloadFromCloudAsync(targetUrl))
using (var comparer = new Comparer(sourceStream))
{
    comparer.Add(targetStream);
    comparer.Compare(outputStream);
}
```

**Q: Hur kör jag GroupDocs.Comparison i en Docker‑container?**  
A: Inkludera nödvändiga inhemska beroenden i din Dockerfile och kopiera licensfilen till containern.

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:6.0
# Install necessary fonts and libraries for document processing
RUN apt-get update && apt-get install -y libfontconfig1 libfreetype6
```

**Q: Vilken licensiering krävs för produktion?**  
A: En kommersiell GroupDocs.Comparison‑licens är obligatorisk för produktionsdistributioner. Alternativ inkluderar utvecklar-, site- och OEM‑licenser.

**Q: Hur hanterar jag jämförelsesfel på ett smidigt sätt?**  
A: Omslut jämförelsesamtalet i ett try‑catch‑block, logga undantaget och returnera ett användarvänligt felmeddelande.

```csharp
public async Task<ComparisonResult> CompareDocumentsWithRetry(string source, string target, int maxRetries = 3)
{
    for (int attempt = 1; attempt <= maxRetries; attempt++)
    {
        try
        {
            using (var comparer = new Comparer(source))
            {
                comparer.Add(target);
                var outputPath = GenerateOutputPath();
                comparer.Compare(outputPath);
                
                return new ComparisonResult { Success = true, OutputPath = outputPath };
            }
        }
        catch (Exception ex) when (attempt < maxRetries)
        {
            _logger.LogWarning($"Comparison attempt {attempt} failed: {ex.Message}. Retrying...");
            await Task.Delay(TimeSpan.FromSeconds(attempt * 2)); // Exponential backoff
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, $"Comparison failed after {maxRetries} attempts");
            return new ComparisonResult { Success = false, Error = ex.Message };
        }
    }
    
    return new ComparisonResult { Success = false, Error = "Max retries exceeded" };
}
```

## Viktiga resurser och dokumentation
- **Fullständig dokumentation:** [GroupDocs Comparison .NET Docs](https://docs.groupdocs.com/comparison/net/)
- **API‑referensguide:** [GroupDocs API Reference for .NET](https://reference.groupdocs.com/comparison/net/)
- **Community‑supportforum:** [GroupDocs Forum](https://forum.groupdocs.com/c/comparison/)
- **Senaste versioner – nedladdningar:** [Releases Page](https://releases.groupdocs.com/comparison/net/)
- **Gratis provversion – nedladdning:** [Try Free Version](https://releases.groupdocs.com/comparison/net/)
- **Ansök om tillfällig licens:** [Apply for Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Köp full licens:** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)
- **Versioner:** [Releases](https://releases.groupdocs.com/comparison/net/)
- **Tillfällig licens‑sida:** [Temporary License Page](https://purchase.groupdocs.com/temporary-license/)
- **Köpsida:** [Purchase Page](https://purchase.groupdocs.com/buy)

---

**Senast uppdaterad:** 2026-06-10  
**Testad med:** GroupDocs.Comparison 25.4.0 för .NET  
**Författare:** GroupDocs

```plaintext
Install-Package GroupDocs.Comparison -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

```csharp
using GroupDocs.Comparison;
```

## Relaterade handledningar
- [GroupDocs Comparison .NET Snabbstart – Komplett installationsguide](/comparison/net/quick-start/)
- [GroupDocs Comparison .NET Licensinställning – Komplett FileStream‑guide](/comparison/net/licensing-configuration/set-license-file-stream-groupdocs-comparison-dotnet/)
- [Dokumentjämförelsesalternativ .NET – Komplett konfigurationsguide](/comparison/net/comparison-options/)