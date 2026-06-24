---
categories:
- C# Development
date: '2026-05-31'
description: Naučte se, jak porovnat dokumenty v C# pomocí GroupDocs.Comparison .NET.
  Podrobný návod krok za krokem s nastavením, ukázkami kódu, tipy na výkon a reálnými
  příklady použití.
keywords:
- how to compare documents
- compare excel files c#
- compare pdf documents c#
- document comparison best practices
lastmod: '2026-05-31'
linktitle: Návod na porovnání dokumentů v C#
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare documents in C# using GroupDocs.Comparison .NET.
    Step‑by‑step guide with setup, code snippets, performance tips, and real‑world
    use cases.
  headline: 'How to Compare Documents in C#: Master GroupDocs.Comparison .NET'
  type: TechArticle
- description: Learn how to compare documents in C# using GroupDocs.Comparison .NET.
    Step‑by‑step guide with setup, code snippets, performance tips, and real‑world
    use cases.
  name: 'How to Compare Documents in C#: Master GroupDocs.Comparison .NET'
  steps:
  - name: Right‑click on your project in Solution Explorer
    text: Right‑click on your project in Solution Explorer
  - name: Select “Manage NuGet Packages”
    text: Select “Manage NuGet Packages”
  - name: Search for “GroupDocs.Comparison”
    text: Search for “GroupDocs.Comparison”
  - name: Click **Install**
    text: Click **Install**
  - name: '**Document Parsing** – Reads the internal structure of both files.'
    text: '**Document Parsing** – Reads the internal structure of both files.'
  - name: '**Content Analysis** – Compares text, formatting, images, tables, and other
      elements.'
    text: '**Content Analysis** – Compares text, formatting, images, tables, and other
      elements.'
  - name: '**Difference Detection** – Identifies additions, deletions, and modifications.'
    text: '**Difference Detection** – Identifies additions, deletions, and modifications.'
  - name: '**Result Generation** – Creates a new document with changes highlighted.'
    text: '**Result Generation** – Creates a new document with changes highlighted.'
  - name: '**Batch Processing** – Reuse the output directory to minimize I/O operations
      when comparing many file pairs.'
    text: '**Batch Processing** – Reuse the output directory to minimize I/O operations
      when comparing many file pairs.'
  - name: '**Asynchronous Operations** – Use `async/await` patterns for UI applications
      to prevent freezing.'
    text: '**Asynchronous Operations** – Use `async/await` patterns for UI applications
      to prevent freezing.'
  type: HowTo
- questions:
  - answer: GroupDocs.Comparison works best when both files share the same format.
      Cross‑format comparison is possible but may lose fidelity; converting one file
      to match the other first yields the most accurate results.
    question: Can I compare documents of different formats (like Word vs PDF)?
  - answer: 'The library supports password‑protected files. Provide the password when
      initializing the `Comparer`:'
    question: How do I handle password‑protected documents?
  - answer: There’s no hard limit, but practical limits depend on available RAM. Files
      up to **100 MB** typically process without issues on a 4 GB RAM server. For
      larger files, consider chunked processing or a server with more memory.
    question: What’s the largest file size GroupDocs.Comparison can handle?
  - answer: Absolutely. The `CompareOptions` class lets you customize the appearance
      of the diff output. Use the `CompareOptions` class to set highlight colors,
      change indicators, and output formatting. The API offers granular control over
      visual diff appearance.
    question: Can I customize how changes are displayed in the output?
  - answer: Each `Comparer` instance should be used by a single thread, but you can
      create multiple instances for concurrent operations. In web scenarios, instantiate
      a new `Comparer` per request.
    question: Is GroupDocs.Comparison thread‑safe for multi‑user applications?
  type: FAQPage
tags:
- document-comparison
- groupdocs
- dotnet
- file-processing
title: 'Jak porovnat dokumenty v C#: Master GroupDocs.Comparison .NET'
type: docs
url: /cs/net/basic-comparison/groupdocs-comparison-net-document-comparison-csharp/
weight: 1
---

# Jak porovnat dokumenty v C#: Master GroupDocs.Comparison .NET

Už jste se někdy museli ručně porovnávat dva Word dokumenty a hledat každou drobnou změnu? Pokud jste vývojář pracující s aplikacemi, kde jsou dokumenty hlavní, víte, jak únavné to může být. **Naučit se, jak programově porovnávat dokumenty** vám ušetří nespočet hodin, eliminuje lidské chyby a přinese konzistenci do jakéhokoli pracovního postupu, který se zabývá smlouvami, specifikacemi nebo zprávami.

Porovnávání dokumentů není jen pohodlí – je to základní kámen přesnosti, efektivity a rozumu v právních technologiích, technickém publikování a platformách pro kolaborativní úpravy. V tomto komplexním tutoriálu projdeme vše, co potřebujete vědět k implementaci robustního, vysoce výkonného porovnávání dokumentů pomocí GroupDocs.Comparison pro .NET.

**Co na konci zvládnete:**
- Kompletní nastavení a konfigurace GroupDocs.Comparison .NET
- Načítání a porovnávání dokumentů pomocí cest k souborům (nejčastější scénář)
- Zpracování výsledků porovnání a přizpůsobení výstupu
- Reálné implementační vzory a osvědčené postupy
- Řešení běžných problémů, se kterými se skutečně setkáte

Ponořme se do transformace vašeho pracovního postupu správy dokumentů.

## Rychlé odpovědi
- **Jaký je nejjednodušší způsob, jak porovnat dva Word soubory?** Načtěte oba soubory pomocí `Comparer` a zavolejte `Compare()`.
- **Jaké formáty GroupDocs.Comparison podporuje?** Více než 50 vstupních a výstupních formátů, včetně DOCX, PDF, XLSX, PPTX a běžných typů obrázků.
- **Potřebuji placenou licenci pro vývoj?** Ne – je k dispozici bezplatná zkušební verze s plnou funkčností a vodoznaky.
- **Jak rychlé je typické porovnání?** 1‑3 sekundy pro standardní 10‑stránkové dokumenty; méně než 5 sekund pro 100‑stránkové soubory na typickém serveru.
- **Mohu spouštět porovnání na Linuxu?** Ano – GroupDocs.Comparison je multiplatformní a funguje na Windows, Linuxu i macOS.

## Co je „jak porovnat dokumenty“?
**Jak porovnat dokumenty** označuje automatizovaný proces detekce přidání, odstranění a úprav mezi dvěma verzemi souboru. GroupDocs.Comparison provádí hlubokou strukturální analýzu – text, formátování, obrázky, tabulky a dokonce i sledované změny – takže získáte přesný vizuální rozdíl bez ruční kontroly.

## Proč použít GroupDocs.Comparison pro porovnávání dokumentů v C#?
GroupDocs.Comparison zpracovává **více než 50 formátů souborů** a dokáže zvládnout **více‑stovkové dokumenty** bez načítání celého souboru do paměti, díky své streamovací architektuře. Benchmarky ukazují 30 % snížení využití paměti ve srovnání s konkurenčními knihovnami při zpracování 200‑stránkových PDF a typický čas 2 sekundy pro 100‑stránkové Word soubory na virtuálním stroji s 2 CPU jádry.

## Před začátkem: Co budete potřebovat
Nastavení porovnávání dokumentů v C# je jednoduché, ale ujistěte se, že máte vše připravené, abyste se později vyhnuli frustrujícím překážkám.

### Základní požadavky

**Vývojové prostředí:**
- .NET Core 3.1+ nebo .NET Framework 4.6.1+ (většina moderních aplikací používá .NET Core)
- Visual Studio 2019+ nebo Visual Studio Code (VS Community funguje perfektně)
- Základní znalost C# (pokud umíte pracovat s třídami a metodami, máte vše potřebné)

**Knihovna GroupDocs.Comparison:**
- Verze 25.4.0 (nejnovější stabilní k datu psaní)
- Kompatibilní s Windows, Linux a macOS
- Podporuje **více než 50 vstupních a výstupních formátů** ihned po instalaci

**Testovací dokumenty:**
Budete potřebovat pár ukázkových dokumentů pro experimentování. Word dokumenty (.docx) jsou skvělé pro testování, ale knihovna také zvládá PDF, Excel soubory, PowerPoint prezentace a mnoho dalších.

### Rychlá kontrola prostředí
Před instalací něčeho ověřte verzi .NET spuštěním následujícího v příkazovém řádku:

```bash
dotnet --version
```

Pokud vidíte číslo verze jako 6.0.x nebo 7.0.x, jste připraveni. Pokud ne, stáhněte si nejnovější .NET SDK z webu Microsoftu.

## Nastavení GroupDocs.Comparison pro .NET (Jednoduše)

Instalace GroupDocs.Comparison je pravděpodobně nejsnadnější část celého tutoriálu. Máte dvě možnosti a obě trvají méně než minutu.

### Možnost 1: Použití NuGet Package Manager (doporučeno)
Otevřete svůj projekt ve Visual Studio a poté:
1. Klikněte pravým tlačítkem na projekt v Solution Explorer
2. Vyberte „Manage NuGet Packages“
3. Vyhledejte „GroupDocs.Comparison“
4. Klikněte na **Install**

Nebo použijte Package Manager Console:

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

### Možnost 2: Použití .NET CLI
Pokud dáváte přednost příkazové řádce (obzvláště užitečné pro CI/CD pipeline):

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

### Správa licencí (nepřeskakujte to)
Zde je něco, co mnohé vývojáře zaskočí: GroupDocs.Comparison není zcela zdarma, ale jsou velkorysí s evaluačními možnostmi.

**Pro vývoj a testování:**
- Bezplatná zkušební verze s plnou funkčností
- Vodoznaky na výstupu (zcela v pořádku pro testování)
- Žádné časové omezení zkušební verze

**Pro produkci:**
- Vyžadována komerční licence
- Dočasné licence k dispozici pro prodloužené hodnocení
- Množstevní slevy pro podnikové aplikace

Tip: Začněte s bezplatnou zkušební verzí. Můžete postavit a otestovat celou implementaci před rozhodnutím o licenci. Většina vývojářů knihovnu považuje za tak užitečnou, že náklady na licenci jsou samozřejmostí.

### Základní ověření nastavení
Ujistěme se, že vše funguje, pomocí rychlého testu. Přidejte tyto using direktivy do vašeho C# souboru:

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
```

Pokud Visual Studio nehlásí chybějící reference, jste připraveni na start.

## Jak porovnat dokumenty pomocí GroupDocs.Comparison
GroupDocs.Comparison provádí rozdíl dokumentů pomocí třídy `Comparer`. Třída `Comparer` řídí porovnání, zatímco její metoda `Compare()` provádí analýzu a vytváří nový dokument zvýrazňující všechny změny. Načtěte svůj zdrojový soubor, přidejte jeden nebo více cílových souborů a zavolejte `Compare()` pro získání výsledku.

Třída `Comparer` je hlavní komponenta, která řídí proces porovnání. Načte oba zdrojové i cílové soubory, analyzuje jejich struktury a vytvoří diff dokument.

### Postup krok za krokem

**Krok 1: Definujte cesty k souborům**  
Použijte `Path.Combine()` pro multiplatformní kompatibilitu; automaticky správně zachází s oddělovači cest, ať už jste na Windows (`\`) nebo Linux/macOS (`/`). Vždy jej používejte místo ručního zadávání cest s lomítky.

```csharp
string YOUR_DOCUMENT_DIRECTORY = @"C:\Documents\TestFiles";
string sourcePath = Path.Combine(YOUR_DOCUMENT_DIRECTORY, "source.docx");
string targetPath = Path.Combine(YOUR_DOCUMENT_DIRECTORY, "target.docx");
```

**Krok 2: Inicializujte Comparer**  
`using` blok zajišťuje, že všechny zdroje jsou uvolněny po dokončení, což zabraňuje únikům paměti – obzvláště důležité při zpracování mnoha dokumentů ve dávce.

```csharp
using (Comparer comparer = new Comparer(sourcePath))
```

**Krok 3: Přidejte cílový dokument(y)**  
GroupDocs.Comparison vám umožňuje porovnat jeden zdroj s více cíli. Zavolejte `Add()` pro každý další soubor, který chcete porovnat se zdrojem.

```csharp
comparer.Add(targetPath);
```

**Krok 4: Spusťte a uložte**  
`Compare()` provádí těžkou práci. Analyzuje oba dokumenty, identifikuje rozdíly a vytvoří nový dokument se zvýrazněnými změnami.

```csharp
string outputFileName = Path.Combine(YOUR_OUTPUT_DIRECTORY, "result.docx");
comparer.Compare(outputFileName);
```

### Co se děje během porovnání?
Když zavoláte `Compare()`, GroupDocs.Comparison provádí několik operací:
1. **Parsing dokumentu** – Načte vnitřní strukturu obou souborů.
2. **Analýza obsahu** – Porovnává text, formátování, obrázky, tabulky a další prvky.
3. **Detekce rozdílů** – Identifikuje přidání, odstranění a úpravy.
4. **Generování výsledku** – Vytvoří nový dokument se zvýrazněnými změnami.

Celý proces obvykle trvá **1‑3 sekundy pro standardní obchodní dokumenty**; velké soubory (100 + stránek) mohou trvat až **5 sekund** na průměrném serveru.

## Praktické aplikace: Kde porovnávání dokumentů vyniká
Pochopení technické implementace je skvělé, ale pojďme si povědět, kde je to ve skutečných aplikacích opravdu užitečné.

### Systémy pro revizi právních dokumentů
Právnické firmy a právní oddělení se neustále zabývají revizemi smluv. Místo ručního přezkoumání každé změny v klauzuli můžete vygenerovat diff dokument, který jasně ukazuje, co bylo přidáno, odebráno nebo upraveno, což dramaticky zrychlí proces revize.

```csharp
// Compare contract versions automatically
string originalContract = @"contracts\initial-agreement.docx";
string revisedContract = @"contracts\revised-agreement.docx";
string comparisonResult = @"output\contract-changes.docx";

using (Comparer comparer = new Comparer(originalContract))
{
    comparer.Add(revisedContract);
    comparer.Compare(comparisonResult);
}
```

### Správa technické dokumentace
Pokud spravujete API dokumentaci, uživatelské příručky nebo specifikace, porovnání vám pomůže:
- Sledovat změny mezi verzemi dokumentace
- Identifikovat, kdy je potřeba aktualizovat screenshoty nebo ukázky kódu
- Zajistit konzistenci napříč více formáty dokumentů

### Kolaborativní tvorba obsahu
Když na stejném whitepaperu, zprávě nebo návrhu pracuje více autorů, porovnání vám pomůže:
- Sloučit individuální příspěvky
- Detekovat konfliktní úpravy
- Udržet jasný auditní záznam změn

### Zajištění kvality při generování dokumentů
Pro aplikace, které automaticky generují faktury, smlouvy nebo zprávy, slouží porovnání jako kontrolní brána:
- Ověřit vygenerované dokumenty vůči hlavní šabloně
- Zachytit chyby při naplňování dat dříve, než se dostanou k zákazníkům
- Zajistit shodu formátování napříč typy výstupů

## Úvahy o výkonu: Jak to udělat rychlé a efektivní
Porovnávání dokumentů může být náročné na zdroje, zejména u velkých souborů. Zde je, jak udržet aplikaci responzivní a efektivní.

### Nejlepší postupy pro správu paměti
**Vždy používejte `using` bloky**

```csharp
// Good: Resources are automatically disposed
using (Comparer comparer = new Comparer(sourcePath))
{
    comparer.Add(targetPath);
    comparer.Compare(outputPath);
} // Comparer is disposed here automatically

// Avoid: Manual disposal required (and often forgotten)
Comparer comparer = new Comparer(sourcePath);
comparer.Add(targetPath);
comparer.Compare(outputPath);
comparer.Dispose(); // Easy to forget, causes memory leaks
```

**Monitorujte zpracování velkých souborů**
Pro dokumenty větší než **50 MB** nebo **500 + stránek** zvažte:
- Spouštění porovnání během mimošpičkových hodin
- Implementaci zpětné vazby o průběhu pro uživatele
- Rozdělení velmi velkých souborů na logické sekce, pokud je to možné

### Optimalizace pro různé typy souborů
- **Textově těžké dokumenty (Word, PDF)** – Obecně rychlé, **1‑5 sekund** pro typické obchodní soubory.
- **Obrázkově těžké prezentace** – Pomalejší kvůli vizuálním diff algoritmům, **10‑30 sekund** pro velké prezentace.
- **Tabulky s komplexními vzorci** – Výkon se liší podle složitosti výpočtů; pro nejlepší rychlost udržujte vzorce jednoduché.

### Praktické tipy pro výkon
1. **Dávkové zpracování** – Znovu použijte výstupní adresář pro minimalizaci I/O operací při porovnávání mnoha párů souborů.
2. **Asynchronní operace** – Používejte vzory `async/await` pro UI aplikace, aby nedocházelo k zamrznutí.
3. **Cache** – Ukládejte výsledky porovnání pro identické páry dokumentů, abyste se vyhnuli opakovanému zpracování.

## Řešení běžných problémů (ušetřete čas)
Každý vývojář se s těmito problémy setká. Zde jsou řešení, která skutečně potřebujete.

### Chyby „Soubor nenalezen“
**Problém** – Nejčastější problém na začátku.

```csharp
// This will fail if the path is wrong
using (Comparer comparer = new Comparer(@"C:\NonExistent\file.docx"))
```

**Řešení** – Ověřte existenci souboru před voláním compareru:

```csharp
if (!File.Exists(sourcePath))
{
    Console.WriteLine($"Source file not found: {sourcePath}");
    return;
}

if (!File.Exists(targetPath))
{
    Console.WriteLine($"Target file not found: {targetPath}");
    return;
}
```

### Problémy s oprávněními a přístupem
**Problém** – Aplikace nemůže číst nebo zapisovat soubory.

**Řešení**:
- Spusťte aplikaci s dostatečnými oprávněními.
- Ujistěte se, že soubory nejsou zamčeny jinými programy (zejména Excel).
- Ověřte oprávnění pro zápis do výstupního adresáře.

### Nepodporované formáty souborů
**Problém** – Ne všechny typy souborů jsou podporovány stejně.

**Plně podporováno** – Microsoft Office (Word, Excel, PowerPoint), PDF, prostý text, většina formátů obrázků.

**Omezená podpora** – Komplexní CAD výkresy, specializované proprietární formáty.

### Problémy s pamětí u velkých souborů
**Problém** – Pády nebo zpomalení u obrovských dokumentů.

**Řešení**:
- Zvyšte limity paměti aplikace.
- Zpracovávejte velké soubory po částech.
- Použijte streamovací porovnání pro velmi velké soubory (k dispozici v enterprise edici).

## Pokročilé vzory použití
Jakmile budete mít základní porovnání pod kontrolou, tyto vzory učiní vaši implementaci robustnější.

### Porovnání více dokumentů

```csharp
using (Comparer comparer = new Comparer(sourceDocument))
{
    // Add multiple targets
    comparer.Add(document1);
    comparer.Add(document2);
    comparer.Add(document3);
    
    // Single comparison shows differences from all targets
    comparer.Compare(outputPath);
}
```

### Nejlepší postupy pro zpracování chyb

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
    Console.WriteLine($"File not found: {ex.FileName}");
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

### Integrace s File Watchers
Pro automatické porovnání při změně souborů:

```csharp
FileSystemWatcher watcher = new FileSystemWatcher(@"C:\Documents\Watch");
watcher.Changed += (sender, e) => {
    // Trigger comparison when files change
    CompareDocuments(e.FullPath, referenceDocument);
};
```

## Často kladené otázky
**Q: Mohu porovnávat dokumenty různých formátů (např. Word vs PDF)?**  
A: GroupDocs.Comparison funguje nejlépe, když oba soubory mají stejný formát. Porovnání napříč formáty je možné, ale může dojít ke ztrátě věrnosti; převod jednoho souboru tak, aby odpovídal druhému, poskytne nejpřesnější výsledky.

**Q: Jak zacházet s dokumenty chráněnými heslem?**  
A: Knihovna podporuje soubory chráněné heslem. Zadejte heslo při inicializaci `Comparer`:

```csharp
LoadOptions loadOptions = new LoadOptions() { Password = "your-password" };
using (Comparer comparer = new Comparer(sourcePath, loadOptions))
```

**Q: Jaká je maximální velikost souboru, kterou GroupDocs.Comparison zvládne?**  
A: Neexistuje pevný limit, ale praktické limity závisí na dostupné RAM. Soubory do **100 MB** se obvykle zpracovávají bez problémů na serveru s 4 GB RAM. Pro větší soubory zvažte zpracování po částech nebo server s více pamětí.

**Q: Mohu přizpůsobit, jak jsou změny zobrazeny ve výstupu?**  
A: Rozhodně. Třída `CompareOptions` vám umožňuje přizpůsobit vzhled diff výstupu. Použijte třídu `CompareOptions` k nastavení barev zvýraznění, indikátorů změn a formátování výstupu. API nabízí detailní kontrolu nad vzhledem vizuálního rozdílu.

**Q: Je GroupDocs.Comparison thread‑safe pro víceuživatelské aplikace?**  
A: Každá instance `Comparer` by měla být používána jedním vláknem, ale můžete vytvořit více instancí pro souběžné operace. Ve webových scénářích vytvořte novou `Comparer` pro každý požadavek.

**Q: Jak přesné je porovnání u komplexních dokumentů s tabulkami a obrázky?**  
A: Velmi přesné. Engine analyzuje strukturu dokumentu – ne jen prostý text – takže tabulky, obrázky, formátování a dokonce i sledované změny jsou detekovány a správně zvýrazněny.

**Q: Můžu to integrovat s cloudovými úložišti jako Azure Blob nebo AWS S3?**  
A: Ano, ale nejprve budete muset soubory stáhnout lokálně. GroupDocs.Comparison pracuje s lokálními cestami k souborům, takže stáhněte blob, spusťte porovnání a poté výsledek nahrajte zpět do cloudu.

## Důležité zdroje
- **Oficiální dokumentace**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)
- **API reference**: [Complete API Documentation](https://reference.groupdocs.com/comparison/net/)
- **Stáhnout knihovnu**: [Get GroupDocs.Comparison](https://releases.groupdocs.com/comparison/net/)
- **Možnosti licencování**: [Purchase Information](https://purchase.groupdocs.com/buy)
- **Bezplatná zkušební verze**: [Start Your Evaluation](https://releases.groupdocs.com/comparison/net/)
- **Dočasná licence**: [Extended Evaluation License](https://purchase.groupdocs.com/temporary-license/)
- **Komunitní podpora**: [GroupDocs Forum](https://forum.groupdocs.com/c/comparison/)

---

**Poslední aktualizace:** 2026-05-31  
**Testováno s:** GroupDocs.Comparison 25.4.0 for .NET  
**Autor:** GroupDocs

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define constants for document paths
string YOUR_DOCUMENT_DIRECTORY = @"C:\Documents\TestFiles";
string sourcePath = Path.Combine(YOUR_DOCUMENT_DIRECTORY, "source.docx");
string targetPath = Path.Combine(YOUR_DOCUMENT_DIRECTORY, "target.docx");
string YOUR_OUTPUT_DIRECTORY = @"C:\Documents\Output";
string outputFileName = Path.Combine(YOUR_OUTPUT_DIRECTORY, "result.docx");

// Initialize the Comparer with the source document path
using (Comparer comparer = new Comparer(sourcePath))
{
    // Add the target document to be compared against the source
    comparer.Add(targetPath);
    
    // Perform the comparison and save the result to the output file
    comparer.Compare(outputFileName);
}

Console.WriteLine($"Comparison complete! Check your results at: {outputFileName}");
```

## Související tutoriály
- [GroupDocs Comparison .NET Quick Start - Kompletní průvodce nastavením](/comparison/net/quick-start/)
- [Document Comparison .NET Tutorial - Kompletní průvodce načítáním a ukládáním](/comparison/net/loading-and-saving-documents/)
- [GroupDocs Comparison .NET License Setup - Kompletní průvodce FileStream](/comparison/net/licensing-configuration/set-license-file-stream-groupdocs-comparison-dotnet/)