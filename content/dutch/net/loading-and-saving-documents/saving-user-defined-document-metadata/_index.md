---
title: Door de gebruiker gedefinieerde documentmetagegevens opslaan in GroupDocs-vergelijking voor .NET
linktitle: Door de gebruiker gedefinieerde documentmetagegevens opslaan in GroupDocs-vergelijking voor .NET
second_title: GroupDocs.Vergelijking .NET API
description: Leer hoe u door de gebruiker gedefinieerde documentmetagegevens kunt opslaan met GroupDocs Comparison voor .NET. Vergelijk en manipuleer eenvoudig metadata met stapsgewijze instructies.
weight: 16
url: /nl/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## Invoering
In deze zelfstudie onderzoeken we hoe u door de gebruiker gedefinieerde documentmetagegevens kunt opslaan met behulp van GroupDocs Comparison voor .NET. Metadata zijn cruciaal voor het efficiënt organiseren en beheren van documenten. Met GroupDocs Comparison kunt u eenvoudig metadata vergelijken en manipuleren om aan uw specifieke vereisten te voldoen.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  GroupDocs Comparison voor .NET: Download en installeer GroupDocs Comparison voor .NET van[hier](https://releases.groupdocs.com/comparison/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u een geschikte ontwikkelomgeving, zoals Visual Studio, op uw systeem hebt geïnstalleerd.
3. Bron- en doeldocumenten: Bereid de bron- en doeldocumenten voor waarvoor u de metagegevens wilt vergelijken en manipuleren.

## Naamruimten importeren
Importeer eerst de benodigde naamruimten om toegang te krijgen tot de functionaliteiten van GroupDocs Comparison voor .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Stap 1: Definieer de uitvoermap en bestandsnaam
Definieer de map waarin u het vergeleken document wilt opslaan en geef de naam van het uitvoerbestand op.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Stap 2: Initialiseer Comparer en voeg documenten toe
 Initialiseer de`Comparer` object met het brondocument en voeg het doeldocument toe ter vergelijking.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Stap 3: Geef metagegevensopties op
 Geef de metagegevensopties op voor het opslaan in het vergeleken document. In dit voorbeeld stellen we in`CloneMetadataType` naar`MetadataType.FileAuthor` en geef details voor`FileAuthorMetadata`.
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
## Stap 4: Documenten vergelijken en metadata opslaan
Vergelijk de documenten met de opgegeven metadata-opties en sla het vergeleken document op.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Stap 5: Succesbericht weergeven
Geef een succesbericht weer dat aangeeft dat de documenten met succes zijn vergeleken en de uitvoerlocatie.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u door de gebruiker gedefinieerde documentmetagegevens kunt opslaan met behulp van GroupDocs Comparison voor .NET. Door deze stappen te volgen, kunt u documenten efficiënt vergelijken en tegelijkertijd metagegevens behouden en manipuleren volgens uw vereisten.
## Veelgestelde vragen
### Kan GroupDocs Comparison for .NET verschillende documentformaten verwerken?
Ja, GroupDocs Comparison ondersteunt een breed scala aan documentformaten, waaronder DOCX, PDF, PPTX, XLSX en meer.
### Is er een gratis proefversie beschikbaar voor GroupDocs Comparison for .NET?
 Ja, u heeft toegang tot de gratis proefperiode[hier](https://releases.groupdocs.com/).
### Kan ik metadata-opties aanpassen aan mijn behoeften?
Absoluut, GroupDocs Comparison biedt flexibele opties om de verwerking van metagegevens tijdens documentvergelijking aan te passen.
### Biedt GroupDocs Comparison technische ondersteuning?
Ja, u kunt technische ondersteuning krijgen via het GroupDocs-vergelijkingsforum[hier](https://forum.groupdocs.com/c/comparison/12).
### Waar kan ik een licentie kopen voor GroupDocs Comparison voor .NET?
 U kunt een licentie kopen op de GroupDocs-website[hier](https://purchase.groupdocs.com/buy).