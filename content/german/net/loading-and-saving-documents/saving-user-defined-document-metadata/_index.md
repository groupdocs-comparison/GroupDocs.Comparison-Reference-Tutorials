---
"description": "Erfahren Sie, wie Sie benutzerdefinierte Dokumentmetadaten mit GroupDocs Comparison für .NET speichern. Vergleichen und bearbeiten Sie Metadaten ganz einfach mit Schritt-für-Schritt-Anleitungen."
"linktitle": "Speichern benutzerdefinierter Dokumentmetadaten im GroupDocs-Vergleich für .NET"
"second_title": "GroupDocs.Comparison .NET-API"
"title": "Speichern benutzerdefinierter Dokumentmetadaten im GroupDocs-Vergleich für .NET"
"url": "/de/net/loading-and-saving-documents/saving-user-defined-document-metadata/"
"weight": 16
---

# Speichern benutzerdefinierter Dokumentmetadaten im GroupDocs-Vergleich für .NET

## Einführung
In diesem Tutorial erfahren Sie, wie Sie benutzerdefinierte Dokumentmetadaten mit GroupDocs Comparison für .NET speichern. Metadaten sind entscheidend für die effiziente Organisation und Verwaltung von Dokumenten. Mit GroupDocs Comparison können Sie Metadaten einfach vergleichen und bearbeiten, um Ihren spezifischen Anforderungen gerecht zu werden.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. GroupDocs-Vergleich für .NET: Laden Sie GroupDocs-Vergleich für .NET herunter und installieren Sie es von [Hier](https://releases.groupdocs.com/comparison/net/).
2. Entwicklungsumgebung: Stellen Sie sicher, dass auf Ihrem System eine geeignete Entwicklungsumgebung wie Visual Studio installiert ist.
3. Quell- und Zieldokumente: Bereiten Sie die Quell- und Zieldokumente vor, deren Metadaten Sie vergleichen und bearbeiten möchten.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces, um auf die von GroupDocs Comparison für .NET bereitgestellten Funktionen zuzugreifen.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Schritt 1: Ausgabeverzeichnis und Dateinamen festlegen
Definieren Sie das Verzeichnis, in dem Sie das verglichene Dokument speichern möchten, und geben Sie den Namen der Ausgabedatei an.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Schritt 2: Comparer initialisieren und Dokumente hinzufügen
Initialisieren Sie den `Comparer` Objekt mit dem Quelldokument und fügen Sie das Zieldokument zum Vergleich hinzu.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Schritt 3: Metadatenoptionen festlegen
Geben Sie die Metadatenoptionen für das Speichern im verglichenen Dokument an. In diesem Beispiel setzen wir `CloneMetadataType` Zu `MetadataType.FileAuthor` und geben Sie Details an für `FileAuthorMetadata`.
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
## Schritt 4: Dokumente vergleichen und Metadaten speichern
Vergleichen Sie die Dokumente mit den angegebenen Metadatenoptionen und speichern Sie das verglichene Dokument.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Schritt 5: Erfolgsmeldung anzeigen
Zeigen Sie eine Erfolgsmeldung an, die angibt, dass die Dokumente erfolgreich verglichen wurden, und geben Sie den Ausgabeort an.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie Sie benutzerdefinierte Dokumentmetadaten mit GroupDocs Comparison für .NET speichern. Mit diesen Schritten können Sie Dokumente effizient vergleichen und gleichzeitig Metadaten entsprechend Ihren Anforderungen beibehalten und bearbeiten.
## Häufig gestellte Fragen
### Kann GroupDocs Comparison für .NET verschiedene Dokumentformate verarbeiten?
Ja, GroupDocs Comparison unterstützt eine breite Palette von Dokumentformaten, darunter DOCX, PDF, PPTX, XLSX und mehr.
### Gibt es eine kostenlose Testversion für GroupDocs Comparison für .NET?
Ja, Sie können auf die kostenlose Testversion zugreifen [Hier](https://releases.groupdocs.com/).
### Kann ich Metadatenoptionen meinen Anforderungen entsprechend anpassen?
Auf jeden Fall. GroupDocs Comparison bietet flexible Optionen zur individuellen Anpassung der Metadatenverarbeitung beim Dokumentvergleich.
### Bietet GroupDocs Comparison technischen Support?
Ja, Sie können technischen Support vom GroupDocs-Vergleichsforum erhalten [Hier](https://forum.groupdocs.com/c/comparison/12).
### Wo kann ich eine Lizenz für GroupDocs Comparison für .NET erwerben?
Sie können eine Lizenz von der GroupDocs-Website erwerben [Hier](https://purchase.groupdocs.com/buy).