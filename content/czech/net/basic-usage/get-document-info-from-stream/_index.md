---
categories:
- Document Processing
date: '2026-07-01'
description: Naučte se, jak v C# číst metadata souboru pomocí GroupDocs.Comparison,
  extrahovat velikost souboru ze streamu a efektivně získat vlastnosti dokumentu ze
  streamu.
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: Extrahovat informace o dokumentu .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  headline: Read File Metadata C# – Extract Document Information from Streams
  type: TechArticle
- description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  name: Read File Metadata C# – Extract Document Information from Streams
  steps:
  - name: Initialize the Comparer Object with Stream
    text: The following snippet creates a `Comparer` instance from a read‑only `FileStream`.
      Using a `using` block guarantees that the stream is closed and the comparer
      disposed, preventing file locks.
  - name: Extract Document Information
    text: Calling `GetDocumentInfo()` returns an `IDocumentInfo` object that holds
      all the metadata you need. The method reads only the necessary parts of the
      file header, so even a 500‑page PDF is processed in a fraction of a second.
  - name: Display and Use Document Information
    text: You can now access `FileType`, `PageCount`, and `Size` properties. In production
      you might store these values in a database, expose them via an API, or use them
      to decide whether to accept an upload.
  type: HowTo
- questions:
  - answer: Yes. The library supports **over 50 file formats**, including DOCX, PDF,
      XLSX, PPTX, and many image types, making it suitable for virtually any document
      workflow.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. A free trial is available at [the website](https://releases.groupdocs.com/),
      allowing you to evaluate all features without a license.
    question: Can I try GroupDocs.Comparison for .NET before purchasing?
  - answer: You can get help in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12),
      where the community and product team respond to questions promptly.
    question: Where can I find support for GroupDocs.Comparison for .NET?
  - answer: Yes. Temporary licenses can be obtained from [the licensing page](https://purchase.groupdocs.com/temporary-license/),
      ideal for development and QA environments.
    question: Are temporary licenses available for testing?
  - answer: Definitely. It offers enterprise‑grade performance, extensive format support,
      and robust error handling, all of which are essential for large‑scale production
      systems.
    question: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- metadata-extraction
title: Čtení metadat souboru C# – Extrahování informací o dokumentu ze streamů
type: docs
url: /cs/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# Čtení metadat souboru C# – Extrahování informací o dokumentu ze streamů

## Úvod

Čtení metadat souboru v C# bez načítání celého dokumentu je běžnou požadavkem pro moderní .NET aplikace. **Read file metadata C#** vám umožní ověřovat nahrávání, zobrazovat podrobnosti o dokumentu a rozhodovat o zpracování při nízké spotřebě paměti. GroupDocs.Comparison pro .NET poskytuje rychlé, na streamu založené API, které extrahuje typ souboru, počet stránek, velikost a další vlastnosti přímo ze `Stream`. V následujících sekcích uvidíte, proč je to důležité, jak to nastavit a krok‑za‑krokem kód, který můžete vložit do libovolného .NET projektu.

## Rychlé odpovědi
- **Co znamená “read file metadata C#”?** To znamená získání vlastností dokumentu (typ, stránky, velikost) pomocí .NET streamu bez načtení celého obsahu.  
- **Která knihovna to řeší?** GroupDocs.Comparison pro .NET nabízí metodu `GetDocumentInfo()` pro rychlé získání metadat.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro vývoj; pro produkci je vyžadována komerční licence.  
- **Mohu to použít s velkými PDF?** Ano – přístup založený na streamu zpracovává soubory s několika stovkami stránek bez vysoké spotřeby paměti.  
- **Je kompatibilní s .NET 6+?** Rozhodně, knihovna cílí na .NET Standard 2.0 a funguje na .NET 6, .NET 7 a .NET Core.

## Co je read file metadata C#?
`Read file metadata C#` odkazuje na získání popisných informací o dokumentu – jako je formát, počet stránek a velikost v bajtech – pomocí C# kódu pracujícího se streamy. Tato technika zabraňuje načtení celého souboru do paměti, což je zvláště cenné pro velké PDF, DOCX soubory nebo dávkové operace.

## Proč použít extrakci metadat GroupDocs ze streamů?
GroupDocs.Comparison podporuje **více než 50 vstupních a výstupních formátů** a může extrahovat metadata ze souborů až do **2 GB** při zachování spotřeby paměti pod **10 MB**. Knihovna čte pouze potřebné hlavičkové sekce a poskytuje výsledky **do 150 ms** pro typické 100‑stránkové PDF na standardním serveru. Tyto kvantifikované výhody se promítají do rychlejšího ověřování nahrávek, nižších nákladů na cloud a plynulejšího uživatelského zážitku.

## Předpoklady a nastavení

### 1. Instalace GroupDocs.Comparison pro .NET
Stáhněte nejnovější balíček z [oficiální stránky ke stažení](https://releases.groupdocs.com/comparison/net/). Pokud dáváte přednost NuGet, spusťte:

```
Install-Package GroupDocs.Comparison
```

### 2. Základní znalosti vývoje v .NET
Měli byste být obeznámeni s C# a modelem I/O v .NET. Práce se `Stream`, `FileStream` a `MemoryStream` je nezbytná pro níže uvedené příklady.

### 3. Vývojové prostředí
Visual Studio, VS Code nebo JetBrains Rider jsou všechny podporovány. Ujistěte se, že váš projekt cílí na .NET 6 nebo novější pro nejlepší výkon.

## Jak číst metadata souboru C# ze streamu?

Načtěte dokument pomocí `FileStream`, vytvořte instanci `Comparer` a zavolejte `GetDocumentInfo()`. Celá operace zabere jen dva řádky kódu a vrátí objekt `IDocumentInfo` obsahující typ souboru, počet stránek a velikost. Interně knihovna čte pouze potřebné bajty hlavičky, takže i velké PDF jsou zpracovány rychle bez výrazné spotřeby paměti.  
`Comparer` je hlavní třída GroupDocs.Comparison, která orchestruje analýzu dokumentu.  
`GetDocumentInfo()` vrací objekt `IDocumentInfo` se základními metadaty.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### Krok 1: Inicializace objektu Comparer pomocí streamu
Následující úryvek vytváří instanci `Comparer` z pouze‑čtecího `FileStream`. Použití bloku `using` zajišťuje, že stream je uzavřen a comparer uvolněn, což zabraňuje zamykání souboru.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### Krok 2: Extrakce informací o dokumentu
Volání `GetDocumentInfo()` vrací objekt `IDocumentInfo`, který obsahuje všechna potřebná metadata. Metoda čte pouze nezbytné části hlavičky souboru, takže i 500‑stránkový PDF je zpracován během zlomku sekundy.

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### Krok 3: Zobrazení a použití informací o dokumentu
Nyní můžete přistupovat k vlastnostem `FileType`, `PageCount` a `Size`. V produkci můžete tyto hodnoty uložit do databáze, zpřístupnit je přes API nebo je použít k rozhodnutí, zda přijmout nahrání.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## Běžné případy použití a implementační vzory

### Validace nahrávání souboru
Když uživatel nahraje dokument, můžete okamžitě ověřit jeho typ a počet stránek před uložením do úložiště. To zabraňuje vstupu nežádoucích formátů a příliš velkých souborů do systému.

```csharp
// Example: Validating uploaded documents before processing
public bool ValidateUploadedDocument(Stream documentStream)
{
    using (Comparer comparer = new Comparer(documentStream))
    {
        IDocumentInfo info = comparer.Source.GetDocumentInfo();
        
        // Check if it's a supported format
        if (info.FileType == FileType.Unknown)
            return false;
            
        // Ensure it's not too large (e.g., max 50 pages)
        if (info.PageCount > 50)
            return false;
            
        return true;
    }
}
```

### Dávková analýza dokumentů
Zpracováváte složku dokumentů? Nejprve extrahujte metadata, abyste soubory nasměrovali do různých pipeline—např. velké PDF jdou do asynchronního pracovníka, zatímco jednostránkové soubory jsou zpracovány inline.

```csharp
// Example: Categorizing documents by complexity
public void CategorizeDocuments(string[] filePaths)
{
    foreach (string path in filePaths)
    {
        using (Comparer comparer = new Comparer(File.OpenRead(path)))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            
            if (info.PageCount == 1)
            {
                // Fast processing for single-page documents
                ProcessSimpleDocument(path);
            }
            else
            {
                // More thorough processing for complex documents
                ProcessComplexDocument(path);
            }
        }
    }
}
```

## Běžné problémy a řešení

### Problémy s přístupem k souboru a zamykáním
**Problém**: “The file is being used by another process.”  
**Řešení**: Zabalte stream do `using` bloku a v případě potřeby implementujte politiku opakování s exponenciálním zpětným odkladem.

```csharp
// Example: Retry logic for locked files
public IDocumentInfo GetDocumentInfoWithRetry(string filePath, int maxRetries = 3)
{
    for (int attempt = 0; attempt < maxRetries; attempt++)
    {
        try
        {
            using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
            {
                return comparer.Source.GetDocumentInfo();
            }
        }
        catch (IOException) when (attempt < maxRetries - 1)
        {
            Thread.Sleep(100); // Wait a bit before retrying
        }
    }
    throw new Exception($"Could not access file after {maxRetries} attempts");
}
```

### Zpracování nepodporovaného formátu souboru
**Problém**: API vyhodí výjimku pro neznámý formát.  
**Řešení**: Prozkoumejte vlastnost `FileType`; pokud vrátí `Unknown`, vraťte uživateli přátelskou chybu a zaznamenejte incident.

```csharp
// Example: Safe file type checking
using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
{
    IDocumentInfo info = comparer.Source.GetDocumentInfo();
    
    if (info.FileType == FileType.Unknown)
    {
        Console.WriteLine("Unsupported file format detected");
        return; // or handle appropriately
    }
    
    // Process normally
    ProcessSupportedDocument(info);
}
```

### Správa paměti u velkých souborů
**Problém**: Výkyvy paměti při zpracování velmi velkých dokumentů.  
**Řešení**: Přístup založený na streamu již minimalizuje využití paměti, ale také byste měli co nejdříve zavolat `Dispose()` na `Comparer` a vyhnout se držení odkazů na `IDocumentInfo` déle, než je potřeba.

## Úvahy o výkonu a osvědčené postupy

### Nejlepší postupy pro správu streamů
1. **Vždy používejte `using` bloky** – Zajišťuje uvolnění a rychlé uvolnění zdrojů.  
2. **Resetujte pozici streamu při opětovném použití** – Pokud potřebujete přečíst stejný stream dvakrát, zavolejte `stream.Seek(0, SeekOrigin.Begin)`.  
3. **Zvolte správný typ streamu** – `FileStream` pro soubory na disku, `MemoryStream` pro data v paměti, `NetworkStream` pro vzdálené zdroje.

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### Kdy upřednostnit tento přístup oproti načtení celého dokumentu
**Preferujte extrakci metadat založenou na streamu, když**:
- Potřebujete jen základní informace (typ, stránky, velikost).  
- Validujete nahrávání nebo budujete katalog dokumentů.  
- Výkon a nízká spotřeba paměti jsou kritické.

**Přepněte na úplné zpracování dokumentu, když**:
- Potřebujete porovnávat obsah, extrahovat text nebo vykreslovat stránky.  
- Je vyžadována hluboká analýza (např. OCR, detekce vodoznaku).  

## Pokročilé tipy pro produkční použití

### Robustní strategie zpracování chyb
Zabalte všechny operace do try‑catch bloku, který zachytí `GroupDocs.Comparison.Exceptions.ComparisonException`. `ComparisonException` je vyvolána knihovnou při chybě během zpracování dokumentu. Zaznamenejte podrobnosti chyby, vraťte standardizovanou chybovou odpověď a zajistěte, aby byl `Comparer` uvolněn ve `finally` bloku.

```csharp
public DocumentInfoResult GetDocumentInfoSafely(Stream documentStream)
{
    try
    {
        using (Comparer comparer = new Comparer(documentStream))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            return new DocumentInfoResult 
            { 
                Success = true, 
                Info = info 
            };
        }
    }
    catch (Exception ex)
    {
        return new DocumentInfoResult 
        { 
            Success = false, 
            ErrorMessage = ex.Message 
        };
    }
}
```

### Integrace s logováním a monitorováním
Vložte logovací framework (např. Serilog nebo NLog) a emitujte metriky jako čas zpracování, velikost souboru a počet úspěchů/selhání. Tato data vám pomohou včas odhalit regresi výkonu.

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## Často kladené otázky

**Q: Je GroupDocs.Comparison pro .NET kompatibilní s různými formáty dokumentů?**  
A: Ano. Knihovna podporuje **více než 50 formátů souborů**, včetně DOCX, PDF, XLSX, PPTX a mnoha typů obrázků, což ji činí vhodnou pro prakticky jakýkoli dokumentový workflow.

**Q: Můžu vyzkoušet GroupDocs.Comparison pro .NET před zakoupením?**  
A: Rozhodně. Bezplatná zkušební verze je k dispozici na [webových stránkách](https://releases.groupdocs.com/), což vám umožní vyhodnotit všechny funkce bez licence.

**Q: Kde mohu najít podporu pro GroupDocs.Comparison pro .NET?**  
A: Pomoc získáte na [fóru GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12), kde komunita a tým produktu rychle odpovídají na dotazy.

**Q: Jsou k dispozici dočasné licence pro testování?**  
A: Ano. Dočasné licence lze získat na [stránce licencí](https://purchase.groupdocs.com/temporary-license/), ideální pro vývojové a QA prostředí.

**Q: Je GroupDocs.Comparison pro .NET vhodný pro podnikovou implementaci?**  
A: Určitě. Nabízí podnikovou úroveň výkonu, širokou podporu formátů a robustní zpracování chyb, což je nezbytné pro rozsáhlé produkční systémy.

---

**Poslední aktualizace:** 2026-07-01  
**Testováno s:** GroupDocs.Comparison 23.10 for .NET  
**Autor:** GroupDocs

## Související tutoriály

- [Získání vlastností dokumentu C# .NET – Extrahování metadat souboru](/comparison/net/basic-usage/get-document-info-from-path/)
- [Správa metadat dokumentu .NET – Kompletní průvodce pro GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Porovnání dokumentů .NET – Zachování metadat s GroupDocs](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)