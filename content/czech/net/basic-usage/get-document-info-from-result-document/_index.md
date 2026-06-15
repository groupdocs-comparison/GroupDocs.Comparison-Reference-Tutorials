---
categories:
- Document Comparison
date: '2026-06-15'
description: Naučte se, jak extrahovat metadata z .NET comparison výsledků pomocí
  GroupDocs.Comparison. Praktický průvodce krok za krokem s ukázkami kódu a užitečnými
  tipy.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: Extrahovat informace o dokumentu z výsledků porovnání
schemas:
- author: GroupDocs
  dateModified: '2026-06-15'
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  headline: How to Extract Metadata from .NET Comparison Results – Complete Guide
  type: TechArticle
- description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  name: How to Extract Metadata from .NET Comparison Results – Complete Guide
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
  type: HowTo
- questions:
  - answer: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT,
      and many others, providing consistent metadata extraction across them.
    question: Is GroupDocs.Comparison for .NET compatible with various document formats?
  - answer: Absolutely. Settings such as sensitivity, change types, and output format
      are independent of the `GetDocumentInfo()` call.
    question: Can I customize comparison settings without affecting metadata extraction?
  - answer: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/).
      The trial includes full metadata extraction capabilities.
    question: Is there a trial version I can use for evaluation?
  - answer: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12)
      for community help and official support from the GroupDocs team.
    question: Where can I get support for implementation questions?
  - answer: GroupDocs offers developer, site, and OEM licenses. Purchase options are
      listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).
    question: What licensing options are available for production deployments?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- groupdocs-comparison
- document-metadata
- dotnet-api
- document-properties
title: Jak extrahovat metadata z výsledků .NET Comparison – Kompletní průvodce
type: docs
url: /cs/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# Jak extrahovat metadata z výsledků porovnání .NET – Kompletní průvodce

Když pracujete s porovnáváním dokumentů v .NET aplikacích, můžete se ptát **jak extrahovat metadata** z výsledků porovnání. Metadata jako typ souboru, počet stránek a velikost dokumentu mohou být klíčová pro auditní záznamy, ladění výkonu nebo jednoduše pro zobrazování užitečných informací koncovým uživatelům. Tento tutoriál vás provede efektivním získáváním těchto dat pomocí GroupDocs.Comparison pro .NET.

## Rychlé odpovědi
- **Jaká je hlavní třída pro porovnání?** `Comparer` načte zdrojový dokument a spustí porovnávací engine.  
- **Která metoda vrací metadata?** `GetDocumentInfo()` na cílovém dokumentu vrací objekt `IDocumentInfo`.  
- **Mohu získat velikost dokumentu v .NET?** Ano – vlastnost `Size` objektu `IDocumentInfo` vrací velikost v bajtech.  
- **Potřebuji licenci pro extrakci metadat?** Platná licence GroupDocs.Comparison je vyžadována pro produkční použití; bezplatná zkušební verze podporuje všechny funkce metadat.  
- **Je API kompatibilní s .NET 6?** Naprosto – GroupDocs.Comparison podporuje .NET Framework 4.6.1+, .NET Core 2.0+, a .NET 5/6+.

Metoda `GetDocumentInfo()` vrací objekt `IDocumentInfo` obsahující metadata dokumentu.

## Co je extrakce metadat v porovnání dokumentů?
Extrakce metadat je proces získávání popisných informací – jako je typ souboru, počet stránek a velikost souboru – z dokumentů zapojených do operace porovnání. GroupDocs.Comparison poskytuje tato data prostřednictvím jednotného API, což usnadňuje jejich zaznamenávání, zobrazování nebo použití pro podmíněné zpracování.

## Proč extrahovat metadata z výsledků porovnání?
Extrahování metadat vám umožní vytvářet podrobné auditní záznamy, směrovat soubory podle typu a upravovat strategie zpracování pro velké dokumenty. Díky znalosti typu souboru, počtu stránek a velikosti můžete vynucovat pravidla souladu, odhadovat dobu zpracování a předložit uživatelům jasné informace ještě před zahájením porovnání.

## Předpoklady

1. **GroupDocs.Comparison pro .NET** – Nainstalujte knihovnu z [oficiální stránky vydání](https://releases.groupdocs.com/comparison/net/).  
   Také můžete procházet všechna vydání na [stránce vydání GroupDocs](https://releases.groupdocs.com/).  
2. **Vývojové prostředí** – Visual Studio, VS Code nebo jakékoli IDE podporující .NET 6+.  
3. **Ukázkové dokumenty** – Dva soubory (např. `SOURCE.docx` a `TARGET.docx`) pro testování. API pracuje s více než **50 formáty dokumentů**.

## Importovat jmenné prostory

Následující direktivy `using` vám poskytují přístup k jádru porovnávacího enginu, utilitám pro práci se soubory a rozhraním metadat.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

Tyto importy jsou vyžadovány před vytvořením jakýchkoli objektů GroupDocs.

## Jak extrahovat metadata z výsledků porovnání?

Třída `Comparer` načte zdrojový dokument a řídí proces porovnání.

Pro získání metadat nejprve načtěte zdrojový dokument pomocí instance `Comparer`, poté přidejte cílový(é) dokument(y). Po inicializaci porovnávacího enginu zavolejte `GetDocumentInfo()` na každém cíli, abyste získali objekt `IDocumentInfo`, který obsahuje vlastnosti jako typ souboru, počet stránek a velikost. Tento přístup funguje jednotně napříč všemi podporovanými formáty.

### Krok 1: Inicializovat Comparer se zdrojovým dokumentem

`Comparer` je hlavní třída v GroupDocs.Comparison, která načte zdrojový dokument a řídí operace porovnání. Použití bloku `using` zajišťuje automatické uvolnění všech neřízených zdrojů.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Tip:** Můžete předat libovolný `Stream` (soubor, paměť, cloud) do konstruktoru `Comparer`, nejen cestu k souboru.

### Krok 2: Přidat cílový dokument pro porovnání

Metoda `Add()` přijímá další streamy nebo cesty k souborům, což umožňuje porovnání jeden‑na‑mnoho.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Důležité:** Pořadí přidaných dokumentů ovlivňuje způsob zvýraznění změn ve finální zprávě.

### Krok 3: Získat informace o dokumentu z výsledného dokumentu

`IDocumentInfo` poskytuje jednotný pohled na metadata dokumentu, jako je typ souboru, počet stránek a velikost, napříč všemi podporovanými formáty.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Porozumění datům:** Vrácený objekt funguje stejně pro DOCX, PDF, XLSX a PPTX, takže můžete psát kód nezávislý na formátu.

### Krok 4: Zobrazit informace o dokumentu

Jakmile máte instanci `IDocumentInfo`, můžete její vlastnosti zaznamenávat, ukládat nebo zobrazovat.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

Nejběžněji používané tři vlastnosti jsou:

- **FileType** – např. `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – celkový počet stránek nebo snímků.  
- **Size** – velikost souboru v bajtech (užitečné pro výpočty úložiště).

## Jak získat velikost dokumentu v .NET?

Vlastnost `Size` vrací velikost souboru v bajtech.

Velikost dokumentu lze získat přímo z instance `IDocumentInfo` pomocí její vlastnosti `Size`. Tato vlastnost vrací přesný počet bajtů původního souboru, což vám umožní převést jej na kilobajty nebo megabajty pro zobrazení či výpočty úložiště. Odráží velikost zdrojového souboru, nikoli žádnou zpracovanou verzi.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Poznámka:** Hodnota `Size` odráží velikost původního souboru, nikoli velikost po jakémkoli interním zpracování nebo kompresi.

## Běžné případy použití a praktické aplikace

- **Dávkové zpracování:** Použijte typ souboru k nasměrování DOCX souborů do workflow specifického pro Word a PDF do pipeline optimalizované pro PDF.  
- **Správa úložiště:** Automaticky archivujte dokumenty větší než 10 MB do chladného úložiště.  
- **Zpětná vazba uživatelům:** Zobrazte počet stránek a velikost před porovnáním, aby uživatelé měli realistická očekávání ohledně doby zpracování.  
- **Zajištění kvality:** Ověřte, že nahrané soubory jsou kompletní porovnáním očekávaného a skutečného počtu stránek.

## Odstraňování běžných problémů

- **Chyby přístupu k souboru:** Ověřte oprávnění ke čtení a během vývoje používejte absolutní cesty.  
- **Paměťové zatížení při velkých souborech:** Upřednostněte streamování (`File.OpenRead`) před načítáním celého souboru do paměti.  
- **Výjimky NullReferenceException:** `FirstOrDefault()` může vrátit `null`, pokud nebyl přidán žádný cíl; vždy zkontrolujte před přístupem k `GetDocumentInfo()`.  

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

- **Omezená metadata pro prostý text:** Formáty jako `.txt` nemusí poskytovat smysluplný `PageCount`. Ošetřete chybějící hodnoty.

## Úvahy o výkonu

- **Správa streamů:** Vždy obalte streamy do `using` bloků, aby se rychle uvolnily souborové handly.  
- **Cache:** Ukládejte často přistupovaná metadata do cache, aby se předešlo opakované extrakci.  
- **Dávkové operace:** Zpracovávejte dokumenty ve skupinách, abyste snížili režii a zvýšili propustnost.

## Nejlepší postupy pro produkční použití

- **Robustní ošetření chyb:** Zabalte extrakci metadat do bloků try‑catch, aby se poškozené nebo nepodporované soubory zpracovávaly elegantně.  
- **Komplexní logování:** Zaznamenávejte typ dokumentu, velikost a počet stránek pro každé porovnání, aby se usnadnilo odstraňování problémů a auditní soulad.  
- **Bezpečnostní hygiena:** Vyhněte se zveřejňování úplných cest k souborům nebo interních detailů serveru v UI zprávách.  
- **Uvolňování zdrojů:** Okamžitě uvolňujte instance `Comparer`, zejména ve webových službách zpracovávajících mnoho souběžných požadavků.

## Pokročilé scénáře

### Více cílových dokumentů

Pokud porovnáváte jeden zdroj s několika cíli, iterujte přes kolekci `Targets` a z každého extrahujte metadata.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Podmíněné zpracování na základě metadat

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Ukládání metadat do databáze

Uložte `FileType`, `PageCount` a `Size` do relační tabulky, aby bylo možné vytvářet reporty a analytiku napříč tisíci porovnáními.

## Často kladené otázky

**Q: Je GroupDocs.Comparison pro .NET kompatibilní s různými formáty dokumentů?**  
A: Ano, podporuje **více než 50 formátů** včetně DOCX, PDF, PPTX, XLSX, TXT a mnoha dalších, poskytuje konzistentní extrakci metadat napříč nimi.

**Q: Mohu přizpůsobit nastavení porovnání, aniž by to ovlivnilo extrakci metadat?**  
A: Naprosto. Nastavení jako citlivost, typy změn a výstupní formát jsou nezávislé na volání `GetDocumentInfo()`.

**Q: Existuje zkušební verze, kterou mohu použít pro hodnocení?**  
A: Ano, stáhněte si bezplatnou zkušební verzi ze [stránky vydání GroupDocs](https://releases.groupdocs.com/). Zkušební verze zahrnuje plnou funkčnost extrakce metadat.

**Q: Kde mohu získat podporu pro otázky implementace?**  
A: Použijte [fórum GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12) pro komunitní pomoc a oficiální podporu od týmu GroupDocs.

**Q: Jaké licenční možnosti jsou k dispozici pro produkční nasazení?**  
A: GroupDocs nabízí vývojářské, site a OEM licence. Možnosti nákupu jsou uvedeny na [stránce nákupu GroupDocs](https://purchase.groupdocs.com/buy).

---

**Poslední aktualizace:** 2026-06-15  
**Testováno s:** GroupDocs.Comparison 6.0 for .NET  
**Autor:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Související tutoriály

- [Správa metadat dokumentu .NET – Kompletní průvodce pro GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Získání vlastností dokumentu C# .NET – Extrakce metadat souboru](/comparison/net/basic-usage/get-document-info-from-path/)
- [Zachování metadat cíle s GroupDocs.Comparison – .NET tutoriál](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)