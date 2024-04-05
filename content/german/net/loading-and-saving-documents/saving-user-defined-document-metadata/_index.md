---
title: Speichern benutzerdefinierter Dokumentmetadaten im GroupDocs-Vergleich für .NET
linktitle: Speichern benutzerdefinierter Dokumentmetadaten im GroupDocs-Vergleich für .NET
second_title: GroupDocs.Comparison .NET-API
description: Erfahren Sie, wie Sie benutzerdefinierte Dokumentmetadaten mit GroupDocs Compare für .NET speichern. Vergleichen und bearbeiten Sie Metadaten ganz einfach mit Schritt-für-Schritt-Anleitungen.
type: docs
weight: 16
url: /de/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie benutzerdefinierte Dokumentmetadaten mit GroupDocs Compare für .NET speichern. Metadaten sind für die effiziente Organisation und Verwaltung von Dokumenten von entscheidender Bedeutung. Mit GroupDocs Compare können Sie Metadaten ganz einfach vergleichen und bearbeiten, um sie an Ihre spezifischen Anforderungen anzupassen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  GroupDocs-Vergleich für .NET: Laden Sie GroupDocs-Vergleich für .NET herunter und installieren Sie ihn von[Hier](https://releases.groupdocs.com/comparison/net/).
2. Entwicklungsumgebung: Stellen Sie sicher, dass auf Ihrem System eine geeignete Entwicklungsumgebung wie Visual Studio installiert ist.
3. Quell- und Zieldokumente: Bereiten Sie die Quell- und Zieldokumente vor, deren Metadaten Sie vergleichen und bearbeiten möchten.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces, um auf die vom GroupDocs-Vergleich für .NET bereitgestellten Funktionen zuzugreifen.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Schritt 1: Definieren Sie Ausgabeverzeichnis und Dateinamen
Definieren Sie das Verzeichnis, in dem Sie das verglichene Dokument speichern möchten, und geben Sie den Namen der Ausgabedatei an.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Schritt 2: Vergleicher initialisieren und Dokumente hinzufügen
 Initialisieren Sie die`Comparer` Objekt mit dem Quelldokument und fügen Sie das Zieldokument zum Vergleich hinzu.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Schritt 3: Metadatenoptionen angeben
 Geben Sie die Metadatenoptionen zum Speichern im verglichenen Dokument an. In diesem Beispiel setzen wir`CloneMetadataType` Zu`MetadataType.FileAuthor` und geben Sie Einzelheiten dazu an`FileAuthorMetadata`.
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
Zeigt eine Erfolgsmeldung an, die angibt, dass die Dokumente erfolgreich verglichen wurden, und den Ausgabeort.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man benutzerdefinierte Dokumentmetadaten mit GroupDocs Compare für .NET speichert. Wenn Sie diese Schritte befolgen, können Sie Dokumente effizient vergleichen und gleichzeitig Metadaten gemäß Ihren Anforderungen beibehalten und bearbeiten.
## FAQs
### Kann GroupDocs-Vergleich für .NET verschiedene Dokumentformate verarbeiten?
Ja, GroupDocs Compare unterstützt eine Vielzahl von Dokumentformaten, darunter DOCX, PDF, PPTX, XLSX und mehr.
### Gibt es eine kostenlose Testversion für GroupDocs-Vergleich für .NET?
 Ja, Sie können auf die kostenlose Testversion zugreifen[Hier](https://releases.groupdocs.com/).
### Kann ich die Metadatenoptionen an meine Bedürfnisse anpassen?
Absolut, GroupDocs Compare bietet flexible Optionen zur individuellen Anpassung der Metadatenverarbeitung während des Dokumentenvergleichs.
### Bietet GroupDocs Compare technischen Support?
Ja, Sie können technischen Support über das GroupDocs-Vergleichsforum erhalten[Hier](https://forum.groupdocs.com/c/comparison/12).
### Wo kann ich eine Lizenz für GroupDocs-Vergleich für .NET erwerben?
 Sie können eine Lizenz auf der GroupDocs-Website erwerben[Hier](https://purchase.groupdocs.com/buy).