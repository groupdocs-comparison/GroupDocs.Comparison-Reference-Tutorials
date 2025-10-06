---
"description": "Naučte se, jak přijímat a odmítat změny v dokumentech pomocí nástroje GroupDocs Comparison pro .NET. Zjednodušte si své pracovní postupy s dokumenty bez námahy."
"linktitle": "Přijetí a odmítnutí změn v porovnání GroupDocs pro .NET"
"second_title": "GroupDocs.Comparison .NET API"
"title": "Přijetí a odmítnutí změn v porovnání GroupDocs pro .NET"
"url": "/cs/net/documents-and-folder-comparison/accept-reject-changes-dotnet/"
"weight": 10
type: docs
---
# Přijetí a odmítnutí změn v porovnání GroupDocs pro .NET

## Zavedení
oblasti správy dokumentů a spolupráce je zajištění přesnosti a integrity souborů prvořadé. GroupDocs Comparison for .NET se jeví jako robustní řešení, které vývojářům umožňuje bez námahy přijímat a odmítat změny v dokumentech, čímž zefektivňuje pracovní postupy a zvyšuje produktivitu. Tento tutoriál vás provede procesem přijímání a odmítání změn pomocí GroupDocs Comparison for .NET a rozebere každý krok pro přehlednost a snadnou implementaci.
## Předpoklady
Než se pustíte do tutoriálu, ujistěte se, že máte splněny následující předpoklady:
### Nastavení prostředí
1. Instalace sady .NET SDK: Pokud jste tak ještě neučinili, stáhněte si a nainstalujte sadu .NET SDK vhodnou pro váš operační systém z webových stránek .NET.
2. Instalace GroupDocs Comparison pro .NET: Získejte nejnovější verzi GroupDocs Comparison pro .NET z poskytnutého [odkaz ke stažení](https://releases.groupdocs.com/comparison/net/) a postupujte podle pokynů k instalaci.
3. Znalost programování v jazyce C#: Tento tutoriál předpokládá základní znalost programovacího jazyka C# a jeho syntaxe.

## Importovat jmenné prostory
Nejprve importujte do projektu potřebné jmenné prostory. Tyto jmenné prostory vám poskytnou přístup k funkcím potřebným pro porovnávání a manipulaci s dokumenty.

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
Ujistěte se, že vyměníte `"Your Document Directory"` s cestou k požadovanému výstupnímu adresáři.
## Krok 2: Inicializace porovnávače a porovnání dokumentů
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Tento kód inicializuje objekt Comparer zdrojovým dokumentem a přidá cílový dokument pro porovnání. Poté provede proces porovnání.
## Krok 3: Načtení a manipulace se změnami
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Načtěte změny z porovnání a upravte je podle potřeby. V tomto příkladu jsou změny nejprve odmítnuty a poté přijaty. Výsledné dokumenty jsou odpovídajícím způsobem uloženy.

## Závěr
Závěrem lze říci, že GroupDocs Comparison pro .NET nabízí bezproblémové řešení pro přijímání a odmítání změn v dokumentech. Dodržováním kroků popsaných v tomto tutoriálu mohou vývojáři efektivně integrovat tuto funkci do svých aplikací, čímž zajistí přesnost dokumentů a vylepší spolupráci.
## Často kladené otázky
### Může GroupDocs Comparison pro .NET porovnávat dokumenty různých formátů?
Ano, GroupDocs Comparison for .NET podporuje porovnávání dokumentů různých formátů, jako jsou DOCX, PDF, PPTX a další.
### Je porovnání GroupDocs pro .NET kompatibilní s .NET Core?
Ano, porovnání GroupDocs pro .NET je kompatibilní s .NET Framework i .NET Core.
### Mohu si přizpůsobit vzhled změn v porovnávaných dokumentech?
Rozhodně, GroupDocs Comparison for .NET nabízí rozsáhlé možnosti pro přizpůsobení vzhledu změn, včetně barvy, stylu a dalších.
### Podporuje GroupDocs Comparison for .NET porovnávání vícestránkových dokumentů?
Ano, GroupDocs Comparison for .NET podporuje porovnávání vícestránkových dokumentů s přesností a správností.
### Je k dispozici zkušební verze nástroje GroupDocs Comparison pro .NET?
Ano, můžete využít bezplatnou zkušební verzi GroupDocs Comparison pro .NET z poskytnuté [odkaz](https://releases.groupdocs.com/).