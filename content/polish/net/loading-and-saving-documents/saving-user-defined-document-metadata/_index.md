---
title: Zapisywanie metadanych dokumentu zdefiniowanego przez użytkownika w porównaniu GroupDocs dla .NET
linktitle: Zapisywanie metadanych dokumentu zdefiniowanego przez użytkownika w porównaniu GroupDocs dla .NET
second_title: GroupDocs.Comparison API .NET
description: Dowiedz się, jak zapisywać metadane dokumentów zdefiniowanych przez użytkownika za pomocą narzędzia GroupDocs Comparison dla platformy .NET. Z łatwością porównuj metadane i manipuluj nimi, korzystając z instrukcji krok po kroku.
weight: 16
url: /pl/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---

# Zapisywanie metadanych dokumentu zdefiniowanego przez użytkownika w porównaniu GroupDocs dla .NET

## Wstęp
W tym samouczku omówimy, jak zapisać metadane dokumentu zdefiniowane przez użytkownika za pomocą narzędzia GroupDocs Comparison dla platformy .NET. Metadane mają kluczowe znaczenie dla efektywnego organizowania dokumentów i zarządzania nimi. Dzięki porównaniu GroupDocs możesz łatwo porównywać metadane i manipulować nimi, aby spełnić Twoje specyficzne wymagania.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1.  Porównanie GroupDocs dla .NET: Pobierz i zainstaluj Porównanie GroupDocs dla .NET z[Tutaj](https://releases.groupdocs.com/comparison/net/).
2. Środowisko programistyczne: Upewnij się, że w systemie zainstalowano odpowiednie środowisko programistyczne, takie jak Visual Studio.
3. Dokumenty źródłowe i docelowe: Przygotuj dokumenty źródłowe i docelowe, dla których chcesz porównywać metadane i manipulować nimi.

## Importuj przestrzenie nazw
Najpierw zaimportuj niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcjonalności udostępnianych przez GroupDocs Comparison for .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Krok 1: Zdefiniuj katalog wyjściowy i nazwę pliku
Zdefiniuj katalog, w którym chcesz zapisać porównywany dokument i podaj nazwę pliku wyjściowego.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Krok 2: Zainicjuj porównywarkę i dodaj dokumenty
 Zainicjuj`Comparer` obiekt z dokumentem źródłowym i dodaj dokument docelowy do porównania.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Krok 3: Określ opcje metadanych
 Określ opcje metadanych do zapisania w porównywanym dokumencie. W tym przykładzie ustawiamy`CloneMetadataType` Do`MetadataType.FileAuthor` i podaj szczegóły dot`FileAuthorMetadata`.
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
## Krok 4: Porównaj dokumenty i zapisz metadane
Porównaj dokumenty z określonymi opcjami metadanych i zapisz porównany dokument.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Krok 5: Wyświetl komunikat o powodzeniu
Wyświetl komunikat o powodzeniu wskazujący, że dokumenty zostały pomyślnie porównane, oraz lokalizację wyjściową.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Wniosek
W tym samouczku dowiedzieliśmy się, jak zapisywać metadane dokumentów zdefiniowanych przez użytkownika przy użyciu narzędzia GroupDocs Comparison dla platformy .NET. Wykonując poniższe kroki, możesz efektywnie porównywać dokumenty, zachowując metadane i manipulować nimi zgodnie ze swoimi wymaganiami.
## Często zadawane pytania
### Czy porównanie GroupDocs dla .NET obsługuje różne formaty dokumentów?
Tak, GroupDocs Comparison obsługuje szeroką gamę formatów dokumentów, w tym DOCX, PDF, PPTX, XLSX i inne.
### Czy dostępna jest bezpłatna wersja próbna oprogramowania GroupDocs Comparison dla platformy .NET?
 Tak, możesz uzyskać dostęp do bezpłatnego okresu próbnego[Tutaj](https://releases.groupdocs.com/).
### Czy mogę dostosować opcje metadanych do swoich potrzeb?
Absolutnie, GroupDocs Comparison zapewnia elastyczne opcje dostosowywania obsługi metadanych podczas porównywania dokumentów.
### Czy porównanie GroupDocs oferuje pomoc techniczną?
Tak, możesz uzyskać pomoc techniczną na forum porównawczym GroupDocs[Tutaj](https://forum.groupdocs.com/c/comparison/12).
### Gdzie mogę kupić licencję na porównanie GroupDocs dla .NET?
 Licencję można kupić w witrynie GroupDocs[Tutaj](https://purchase.groupdocs.com/buy).