---
title: Přijmout a odmítnout změny v porovnání GroupDocs pro .NET
linktitle: Přijmout a odmítnout změny v porovnání GroupDocs pro .NET
second_title: GroupDocs.Comparison .NET API
description: Naučte se přijímat a odmítat změny v dokumentech pomocí GroupDocs Comparison for .NET. Zjednodušte své pracovní postupy s dokumenty bez námahy.
weight: 10
url: /cs/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---

# Přijmout a odmítnout změny v porovnání GroupDocs pro .NET

## Úvod
V oblasti správy dokumentů a spolupráce je prvořadé zajištění přesnosti a integrity souborů. GroupDocs Comparison for .NET se ukazuje jako robustní řešení, které umožňuje vývojářům bez námahy přijímat a odmítat změny v dokumentech, čímž zefektivňuje pracovní postupy a zvyšuje produktivitu. Tento výukový program vás provede procesem přijímání a odmítání změn pomocí GroupDocs Comparison for .NET, přičemž každý krok rozebere pro srozumitelnost a snadnou implementaci.
## Předpoklady
Než se pustíte do výukového programu, ujistěte se, že máte splněny následující předpoklady:
### Nastavení prostředí
1. Nainstalujte .NET SDK: Pokud jste tak ještě neučinili, stáhněte si a nainstalujte .NET SDK vhodnou pro váš operační systém z webu .NET.
2.  Nainstalujte GroupDocs Comparison for .NET: Získejte nejnovější verzi GroupDocs Comparison for .NET z poskytnutého[odkaz ke stažení](https://releases.groupdocs.com/comparison/net/) a postupujte podle pokynů k instalaci.
3. Znalost programování v C#: Tento tutoriál předpokládá základní pochopení programovacího jazyka C# a jeho syntaxe.

## Importovat jmenné prostory
Nejprve importujte potřebné jmenné prostory do svého projektu. Tyto jmenné prostory budou poskytovat přístup k funkcím potřebným pro porovnávání dokumentů a manipulaci s nimi.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Krok 1: Zadejte výstupní adresář a názvy souborů
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 Zajistěte výměnu`"Your Document Directory"` s cestou k požadovanému výstupnímu adresáři.
## Krok 2: Inicializujte nástroj Comparer a porovnejte dokumenty
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Tento kód inicializuje objekt Comparer se zdrojovým dokumentem a přidá cílový dokument pro porovnání. Poté provede proces porovnání.
## Krok 3: Načtení a manipulace se změnami
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Získejte změny z porovnání a upravte je podle potřeby. V tomto příkladu jsou změny nejprve odmítnuty a poté přijaty. Výsledné dokumenty se odpovídajícím způsobem uloží.

## Závěr
Na závěr, GroupDocs Comparison for .NET nabízí bezproblémové řešení pro přijímání a odmítání změn v dokumentech. Podle kroků uvedených v tomto kurzu mohou vývojáři efektivně integrovat tuto funkci do svých aplikací, zajistit přesnost dokumentů a zlepšit spolupráci.
## FAQ
### Může GroupDocs Comparison for .NET porovnávat dokumenty různých formátů?
Ano, GroupDocs Comparison for .NET podporuje srovnání mezi dokumenty různých formátů, jako jsou DOCX, PDF, PPTX a další.
### Je GroupDocs Comparison for .NET kompatibilní s .NET Core?
Ano, GroupDocs Comparison for .NET je kompatibilní s .NET Framework i .NET Core.
### Mohu upravit vzhled změn v porovnávaných dokumentech?
Rozhodně, GroupDocs Comparison for .NET poskytuje rozsáhlé možnosti pro přizpůsobení vzhledu změn, včetně barvy, stylu a dalších.
### Podporuje GroupDocs Comparison for .NET porovnání vícestránkových dokumentů?
Ano, GroupDocs Comparison for .NET podporuje porovnávání vícestránkových dokumentů s přesností a přesností.
### Je k dispozici zkušební verze pro GroupDocs Comparison pro .NET?
 Ano, můžete využít bezplatnou zkušební verzi GroupDocs Comparison for .NET z poskytnutého[odkaz](https://releases.groupdocs.com/).