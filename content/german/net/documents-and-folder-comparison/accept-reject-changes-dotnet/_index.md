---
title: Änderungen im GroupDocs-Vergleich für .NET akzeptieren und ablehnen
linktitle: Änderungen im GroupDocs-Vergleich für .NET akzeptieren und ablehnen
second_title: GroupDocs.Comparison .NET-API
description: Erfahren Sie, wie Sie mit GroupDocs Compare für .NET Änderungen in Dokumenten akzeptieren und ablehnen. Optimieren Sie Ihre Dokumenten-Workflows mühelos.
weight: 10
url: /de/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---
## Einführung
Im Bereich Dokumentenmanagement und Zusammenarbeit ist die Sicherstellung der Genauigkeit und Integrität der Dateien von größter Bedeutung. GroupDocs Compare für .NET erweist sich als robuste Lösung, die es Entwicklern ermöglicht, Änderungen in Dokumenten mühelos zu akzeptieren und abzulehnen, wodurch Arbeitsabläufe optimiert und die Produktivität gesteigert werden. Dieses Tutorial führt Sie durch den Prozess des Akzeptierens und Ablehnens von Änderungen mithilfe von GroupDocs Compare für .NET und schlüsselt jeden Schritt auf, um Klarheit und eine einfache Implementierung zu gewährleisten.
## Voraussetzungen
Bevor Sie mit dem Tutorial beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
### Umgebungseinrichtung
1. Installieren Sie das .NET SDK: Falls Sie es noch nicht getan haben, laden Sie das für Ihr Betriebssystem geeignete .NET SDK von der .NET-Website herunter und installieren Sie es.
2.  Installieren Sie GroupDocs-Vergleich für .NET: Beziehen Sie die neueste Version von GroupDocs-Vergleich für .NET von der bereitgestellten Website[Download-Link](https://releases.groupdocs.com/comparison/net/) und befolgen Sie die Installationsanweisungen.
3. Vertrautheit mit der C#-Programmierung: Dieses Tutorial setzt ein grundlegendes Verständnis der Programmiersprache C# und ihrer Syntax voraus.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namensräume in Ihr Projekt. Diese Namensräume bieten Zugriff auf die für den Dokumentenvergleich und die Dokumentenbearbeitung erforderlichen Funktionen.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Schritt 1: Geben Sie das Ausgabeverzeichnis und die Dateinamen an
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 Stellen Sie sicher, dass Sie es ersetzen`"Your Document Directory"` mit dem Pfad zu Ihrem gewünschten Ausgabeverzeichnis.
## Schritt 2: Comparer initialisieren und Dokumente vergleichen
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Dieser Code initialisiert das Comparer-Objekt mit dem Quelldokument und fügt das Zieldokument zum Vergleich hinzu. Anschließend wird der Vergleichsprozess ausgeführt.
## Schritt 3: Änderungen abrufen und bearbeiten
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Rufen Sie die Änderungen aus dem Vergleich ab und bearbeiten Sie sie nach Bedarf. In diesem Beispiel werden Änderungen zunächst abgelehnt und dann übernommen. Die resultierenden Dokumente werden entsprechend gespeichert.

## Abschluss
Zusammenfassend bietet GroupDocs-Vergleich für .NET eine nahtlose Lösung zum Akzeptieren und Ablehnen von Änderungen in Dokumenten. Durch Befolgen der in diesem Tutorial beschriebenen Schritte können Entwickler diese Funktionalität effizient in ihre Anwendungen integrieren und so die Dokumentengenauigkeit sicherstellen und die Zusammenarbeit verbessern.
## FAQs
### Kann GroupDocs Compare für .NET Dokumente unterschiedlicher Formate vergleichen?
Ja, GroupDocs-Vergleich für .NET unterstützt den Vergleich zwischen Dokumenten verschiedener Formate wie DOCX, PDF, PPTX und mehr.
### Ist GroupDocs-Vergleich für .NET mit .NET Core kompatibel?
Ja, der GroupDocs-Vergleich für .NET ist sowohl mit .NET Framework als auch mit .NET Core kompatibel.
### Kann ich das Erscheinungsbild von Änderungen in den verglichenen Dokumenten anpassen?
Absolut, GroupDocs-Vergleich für .NET bietet umfangreiche Optionen zum Anpassen des Erscheinungsbilds von Änderungen, einschließlich Farbe, Stil und mehr.
### Unterstützt GroupDocs Compare für .NET den Vergleich mehrseitiger Dokumente?
Ja, GroupDocs-Vergleich für .NET unterstützt den Vergleich mehrseitiger Dokumente mit Präzision und Genauigkeit.
### Gibt es eine Testversion für GroupDocs-Vergleich für .NET?
 Ja, Sie können eine kostenlose Testversion des GroupDocs-Vergleichs für .NET unter der bereitgestellten Website in Anspruch nehmen[Verknüpfung](https://releases.groupdocs.com/).