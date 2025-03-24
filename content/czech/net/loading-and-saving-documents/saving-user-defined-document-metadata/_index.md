---
title: Ukládání uživatelem definovaných metadat dokumentu ve srovnání GroupDocs pro .NET
linktitle: Ukládání uživatelem definovaných metadat dokumentu ve srovnání GroupDocs pro .NET
second_title: GroupDocs.Comparison .NET API
description: Naučte se ukládat uživatelsky definovaná metadata dokumentu pomocí GroupDocs Comparison for .NET. Snadno porovnávejte a upravujte metadata pomocí podrobných pokynů.
weight: 16
url: /cs/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---

# Ukládání uživatelem definovaných metadat dokumentu ve srovnání GroupDocs pro .NET

## Úvod
V tomto tutoriálu prozkoumáme, jak uložit uživatelsky definovaná metadata dokumentu pomocí GroupDocs Comparison for .NET. Metadata jsou zásadní pro efektivní organizaci a správu dokumentů. Pomocí GroupDocs Comparison můžete snadno porovnávat a upravovat metadata tak, aby vyhovovala vašim specifickým požadavkům.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1.  GroupDocs Comparison for .NET: Stáhněte a nainstalujte GroupDocs Comparison for .NET z[tady](https://releases.groupdocs.com/comparison/net/).
2. Vývojové prostředí: Ujistěte se, že máte v systému nainstalované vhodné vývojové prostředí, jako je Visual Studio.
3. Zdrojové a cílové dokumenty: Připravte zdrojové a cílové dokumenty, které chcete porovnat a manipulovat s metadaty.

## Importovat jmenné prostory
Nejprve naimportujte potřebné jmenné prostory pro přístup k funkcím, které poskytuje GroupDocs Comparison for .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Krok 1: Definujte výstupní adresář a název souboru
Definujte adresář, kam chcete uložit porovnávaný dokument, a zadejte název výstupního souboru.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Krok 2: Inicializujte Comparer a přidejte dokumenty
 Inicializujte`Comparer` objekt se zdrojovým dokumentem a přidejte cílový dokument pro porovnání.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Krok 3: Zadejte možnosti metadat
 Zadejte možnosti metadat pro uložení do porovnávaného dokumentu. V tomto příkladu jsme nastavili`CloneMetadataType` na`MetadataType.FileAuthor` a poskytnout podrobnosti pro`FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## Krok 4: Porovnejte dokumenty a uložte metadata
Porovnejte dokumenty se zadanými možnostmi metadat a uložte porovnávaný dokument.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Krok 5: Zobrazte zprávu o úspěchu
Zobrazte zprávu o úspěchu s uvedením, že dokumenty byly úspěšně porovnány, a umístění výstupu.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Závěr
V tomto tutoriálu jsme se naučili, jak uložit uživatelsky definovaná metadata dokumentu pomocí GroupDocs Comparison for .NET. Dodržením těchto kroků můžete efektivně porovnávat dokumenty při zachování a manipulaci s metadaty podle vašich požadavků.
## FAQ
### Dokáže GroupDocs Comparison for .NET zpracovat různé formáty dokumentů?
Ano, GroupDocs Comparison podporuje širokou škálu formátů dokumentů včetně DOCX, PDF, PPTX, XLSX a dalších.
### Je k dispozici bezplatná zkušební verze pro GroupDocs Comparison for .NET?
 Ano, máte přístup k bezplatné zkušební verzi[tady](https://releases.groupdocs.com/).
### Mohu upravit možnosti metadat podle svých potřeb?
GroupDocs Comparison rozhodně poskytuje flexibilní možnosti přizpůsobení zpracování metadat během porovnávání dokumentů.
### Nabízí GroupDocs Comparison technickou podporu?
Ano, technickou podporu můžete získat na fóru GroupDocs Comparison[tady](https://forum.groupdocs.com/c/comparison/12).
### Kde si mohu zakoupit licenci pro GroupDocs Comparison for .NET?
 Licenci si můžete zakoupit na webu GroupDocs[tady](https://purchase.groupdocs.com/buy).