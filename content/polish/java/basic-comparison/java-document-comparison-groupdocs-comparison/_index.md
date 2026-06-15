---
categories:
- Java Development
date: '2026-06-15'
description: Dowiedz się, jak porównać pdf java przy użyciu GroupDocs.Comparison.
  Ten krok po kroku poradnik obejmuje najlepsze praktyki porównywania dokumentów,
  przykłady kodu, wskazówki dotyczące wydajności oraz rozwiązywanie problemów.
keywords:
- compare pdf java
- java compare two documents
- compare documents without saving
- document comparison java
- groupdocs comparison java
lastmod: '2026-06-15'
linktitle: Przewodnik po porównywaniu dokumentów w Javie
schemas:
- author: GroupDocs
  dateModified: '2026-06-15'
  description: Learn how to compare pdf java using GroupDocs.Comparison. This step‑by‑step
    tutorial covers document comparison best practices, code examples, performance
    tips, and troubleshooting.
  headline: compare pdf java – Compare PDF Files in Java Programmatically
  type: TechArticle
- description: Learn how to compare pdf java using GroupDocs.Comparison. This step‑by‑step
    tutorial covers document comparison best practices, code examples, performance
    tips, and troubleshooting.
  name: compare pdf java – Compare PDF Files in Java Programmatically
  steps:
  - name: '**Free Trial** – ideal for learning and small‑scale demos.'
    text: '**Free Trial** – ideal for learning and small‑scale demos.'
  - name: '**Temporary License** – request a 30‑day key for extended evaluation.'
    text: '**Temporary License** – request a 30‑day key for extended evaluation.'
  - name: '**Full License** – required for production, unlimited file size, and priority
      support.'
    text: '**Full License** – required for production, unlimited file size, and priority
      support.'
  type: HowTo
- questions:
  - answer: Java 8 is the minimum supported version; Java 11+ is recommended for improved
      garbage collection and module support.
    question: What's the minimum Java version required for GroupDocs.Comparison?
  - answer: GroupDocs.Comparison compares a single pair at a time. For multi‑document
      versioning, iterate over the document list and compare each consecutive pair,
      storing the resulting `ChangeInfo[]` for later aggregation.
    question: Can I compare more than two documents simultaneously?
  - answer: '- Disable coordinate calculation unless you need exact locations. - Prefer
      the stream‑based API to avoid loading the entire file into RAM. - Split processing
      into page‑ranges if you only need changes in specific sections. - Monitor JVM
      heap usage and tune `-Xmx` accordingly.'
    question: How should I handle very large documents (100 MB+)?
  - answer: Yes. After obtaining `ChangeInfo[]`, you can generate a new PDF using
      GroupDocs.Watermark or any PDF library, drawing rectangles at the coordinates
      returned. This produces a “red‑line” version that end users can review in any
      PDF viewer.
    question: Is there a way to visually highlight changes in the output?
  - answer: Pass the password to the `Comparer` constructor or set it on the `LoadOptions`
      object before invoking `compare`. The library will decrypt the document in memory,
      so the password never touches the filesystem.
    question: How do I handle password‑protected documents?
  type: FAQPage
tags:
- java
- document-comparison
- groupdocs
- file-comparison
- version-control
title: compare pdf java – Porównywanie plików PDF w Javie programowo
type: docs
url: /pl/java/basic-comparison/java-document-comparison-groupdocs-comparison/
weight: 1
---

# compare pdf java – Jak porównać pliki PDF w Javie programowo

Jeśli jesteś programistą Javy, który potrzebuje **compare pdf java** szybko i dokładnie, trafiłeś we właściwe miejsce. Niezależnie od tego, czy budujesz system zarządzania treścią, dodajesz kontrolę wersji do umów prawnych, czy automatyzujesz QA dla generowanych raportów, ręczne porównania „obok siebie” są podatne na błędy i czasochłonne. GroupDocs.Comparison for Java zapewnia jedyne, niezawodne API, które wykrywa wstawienia, usunięcia, zmiany formatowania, a nawet przeniesione akapity — bez konieczności pisania własnej złożonej logiki diff.

W tym przewodniku przejdziemy krok po kroku przez wszystkie niezbędne czynności: konfigurację biblioteki, uruchamianie porównań na plikach, strumieniach lub w chmurze, wyodrębnianie współrzędnych zmian oraz obsługę scenariuszy dużych dokumentów. Otrzymasz także praktyczne wskazówki dotyczące optymalizacji wydajności, typowych pułapek i przykładów zastosowań w rzeczywistych projektach, abyś mógł szybciej dostarczyć solidne rozwiązanie.

## Szybkie odpowiedzi
- **Jaką bibliotekę użyć do porównywania plików PDF w Javie?** GroupDocs.Comparison for Java.  
- **Czy potrzebna jest licencja?** Darmowa wersja próbna wystarczy do nauki; pełna licencja jest wymagana w środowisku produkcyjnym.  
- **Jakiej wersji Javy wymaga?** Minimum Java 8, zalecane Java 11+.  
- **Czy mogę porównywać dokumenty bez zapisywania ich na dysku?** Tak – użyj przeciążeń opartych na `InputStream`, aby wszystko pozostało w pamięci.  
- **Jak uzyskać współrzędne zmian?** Wywołaj `setCalculateCoordinates(true)` na obiekcie `CompareOptions` przed wywołaniem `compare`.

## Jak porównać pliki PDF w Javie (compare pdf java)?

Wczytaj dwa pliki PDF przy pomocy instancji `Comparer`, skonfiguruj `CompareOptions` według potrzeb i wywołaj `compare`. Metoda zwraca tablicę `ChangeInfo[]`, która precyzyjnie informuje, co się zmieniło, gdzie i w jaki sposób. Cały przepływ można zapisać w mniej niż dziesięciu linijkach Javy, a biblioteka zajmuje się wszystkimi specyficznymi dla formatu szczegółami.

## Co oznacza „compare pdf files java”?

Wyrażenie **compare pdf files java** odnosi się do programistycznego procesu analizowania dwóch dokumentów PDF (lub obsługiwanych formatów) w aplikacji Java w celu wygenerowania szczegółowego diffu. Diff zawiera wstawiony, usunięty i zmodyfikowany tekst, obrazy, tabele oraz przeniesione sekcje, udostępniane jako ustrukturyzowana lista, którą można renderować, logować lub przekazywać do kolejnych usług.

## Dlaczego warto używać GroupDocs.Comparison for Java?

GroupDocs.Comparison obsługuje ponad 60 formatów wejściowych i wyjściowych, w tym PDF, DOCX, XLSX, PPTX, HTML i obrazy, zachowując przy tym układ dokumentu. Potrafi przetwarzać pliki wielostronicowe bez ładowania całego dokumentu do pamięci, dostarczając wyniki w czasie krótszym niż sekunda dla typowych 50‑stronicowych PDF‑ów. Wbudowane opcje pozwalają ignorować zmiany stylu, wykrywać przeniesioną treść i obliczać współrzędne stron dla każdej zmiany.

## Jak programowo porównać pliki PDF w Javie

Poniżej znajduje się kompletny przepływ, który zastosujesz w swoim projekcie. Każdy krok jest opisany przed odpowiednim fragmentem kodu, abyś zawsze wiedział, dlaczego dany kod jest potrzebny.

### Wymagania wstępne i co będzie potrzebne

- **Java Development Kit (JDK)** – wersja 8 lub wyższa (Java 11+ zapewnia lepsze zarządzanie pamięcią i wsparcie modułów).  
- **IDE** – IntelliJ IDEA, Eclipse lub dowolny edytor obsługujący Maven.  
- **Maven** – do zarządzania zależnościami; w tutorialu używany jest standardowy `pom.xml`.  
- **Przykładowe dokumenty** – dwa pliki PDF (lub inne obsługiwane formaty) z niewielkimi różnicami do testów.

### Konfiguracja GroupDocs.Comparison for Java

#### Konfiguracja Maven
Najpierw dodaj repozytorium GroupDocs i zależność do swojego `pom.xml`. Zachowaj blok dokładnie tak, jak pokazano:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/comparison/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-comparison</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**Wskazówka:** Zawsze sprawdzaj, czy masz najnowszą stabilną wersję na stronie pobierania GroupDocs. Nowe wydania często dodają obsługę kolejnych formatów i usprawnienia wydajności.

#### Typowe problemy z konfiguracją i rozwiązania
- **„Repository not found”** – upewnij się, że element `<repositories>` znajduje się **przed** `<dependencies>`.  
- **„ClassNotFoundException”** – wykonaj odświeżenie Maven (np. *Maven → Reload project* w IntelliJ), aby pobrać JAR‑y do classpath.

#### Wyjaśnienie opcji licencjonowania
1. **Free Trial** – idealny do nauki i małych demonstracji.  
2. **Temporary License** – klucz na 30 dni do rozszerzonej oceny.  
3. **Full License** – wymagana w produkcji, nieograniczony rozmiar plików i priorytetowe wsparcie.

#### Podstawowa struktura projektu
```
your-project/
├── src/main/java/
│   └── com/yourcompany/comparison/
│       └── DocumentComparison.java
├── src/test/resources/
│   ├── source.docx
│   └── target.docx
└── pom.xml
```

### Implementacja podstawowa: przewodnik krok po kroku

#### Zrozumienie klasy Comparer
Klasa `Comparer` jest centralnym punktem wejścia dla wszystkich operacji porównywania w GroupDocs.Comparison.

```java
import com.groupdocs.comparison.Comparer;

try (Comparer comparer = new Comparer("sourceFilePath")) {
    comparer.add("targetFilePath");
    // Your comparison logic goes here
}
```

**Dlaczego używać try‑with‑resources?** Ponieważ `Comparer` implementuje `AutoCloseable`, ten wzorzec zapewnia automatyczne zwolnienie zasobów natywnych (bufory pamięci, pliki tymczasowe), co zapobiega wyciekom pamięci przy przetwarzaniu dużych PDF‑ów.

#### Funkcja 1: Pobieranie współrzędnych zmian
Ta funkcja zwraca dokładne współrzędne X/Y na poziomie strony dla każdej wykrytej zmiany, umożliwiając budowę wizualnych podglądów diffu.

##### Kiedy używać
- Tworzenie internetowego przeglądarki dokumentów, która podświetla edycje.  
- Generowanie dzienników audytu wskazujących lokalizację każdej modyfikacji.  
- Integracja z przeglądarkami PDF obsługującymi nakładki adnotacji.

##### Szczegóły implementacji
```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.result.ChangeInfo;

String sourceFilePath = "path/to/source.docx";
String targetFilePath = "path/to/target.docx";

try (Comparer comparer = new Comparer(sourceFilePath)) {
    // Add the target document for comparison.
    comparer.add(targetFilePath);
```

`CompareOptions` konfiguruje zachowanie porównania, m.in. włączenie obliczania współrzędnych.

Włączenie obliczania współrzędnych:

```java
import com.groupdocs.comparison.options.CompareOptions;

final Path resultPath = comparer.compare(
        new CompareOptions.Builder()
                .setCalculateCoordinates(true)
                .build());
```

Wyodrębnianie i przetwarzanie informacji o zmianach:

```java
ChangeInfo[] changes = comparer.getChanges();
for (ChangeInfo change : changes) {
    System.out.printf("Change Type: %s, X: %f, Y: %f, Text: %s%n",
            change.getType(), change.getBox().getX(), change.getBox().getY(), change.getText());
}
```

**Uwaga dotycząca wydajności:** Włączenie współrzędnych zwiększa obciążenie o około 15‑20 %; wyłącz je przy masowych zadaniach diff, gdy dane o położeniu nie są potrzebne.

#### Funkcja 2: Pobieranie zmian z ścieżek plików
Jeśli potrzebujesz jedynie listy zmian, ta metoda zwraca lekki `ChangeInfo[]` bez współrzędnych.

`ChangeInfo` reprezentuje pojedynczą wykrytą zmianę, w tym jej typ i lokalizację.

##### Idealne zastosowanie
- Generowanie podsumowań zmian w formie tekstowej.  
- Uruchamianie nocnych zadań wsadowych, które porównują tysiące par dokumentów.  
- Szybkie sprawdzanie, czy dwie wersje są identyczne.

##### Implementacja
```java
try (Comparer comparer = new Comparer(sourceFilePath)) {
    comparer.add(targetFilePath);
```

Uruchom porównanie bez dodatkowych opcji:

```java
final Path resultPath = comparer.compare();
ChangeInfo[] changes = comparer.getChanges();
System.out.println("\nCount of changes: " + changes.length);
}
```

**Najlepsza praktyka:** Zawsze sprawdzaj `changes.length`. Pusta tablica oznacza, że dokumenty są identyczne, co pozwala pominąć dalsze przetwarzanie.

#### Funkcja 3: Praca ze strumieniami
Strumienie umożliwiają porównywanie plików znajdujących się w pamięci, na udostępnionym dysku sieciowym lub w chmurze, bez zapisywania ich na dysku lokalnym.

##### Typowe przypadki użycia
- Przyjmowanie plików w kontrolerze Spring Boot i porównywanie ich w locie.  
- Pobieranie PDF‑ów z AWS S3, Azure Blob lub Google Cloud Storage bezpośrednio do `ByteArrayInputStream`.  
- Porównywanie dokumentów przechowywanych w kolumnie BLOB bazy danych.

##### Implementacja strumieniowa
```java
import java.io.FileInputStream;
import java.io.InputStream;

try (InputStream sourceStream = new FileInputStream(sourceFilePath);
     InputStream targetStream = new FileInputStream(targetFilePath);
     Comparer comparer = new Comparer(sourceStream)) {
    comparer.add(targetStream);
```

Kontynuuj tym samym wywołaniem porównania:

```java
final Path resultPath = comparer.compare();
ChangeInfo[] changes = comparer.getChanges();
System.out.println("\nCount of changes: " + Arrays.toString(changes).length);
}
```

**Wskazówka pamięciowa:** Blok try‑with‑resources zapewnia automatyczne zamknięcie strumieni, co jest kluczowe przy obsłudze wielu dużych PDF‑ów w usługach wielowątkowych.

#### Funkcja 4: Wyodrębnianie docelowego tekstu
Czasami potrzebny jest dokładny fragment tekstu, który został dodany lub usunięty, np. do powiadomień e‑mail lub wpisów w logu zmian.

##### Praktyczne zastosowania
- Wysyłanie wiadomości e‑mail zawierającej wstawiony akapit.  
- Wypełnianie siatki UI, która pokazuje „stary vs. nowy” tekst obok siebie.  
- Audyt dokumentów regulacyjnych pod kątem zmian konkretnych fraz.

##### Implementacja
```java
try (Comparer comparer = new Comparer(sourceFilePath)) {
    comparer.add(targetFilePath);
    
    final Path resultPath = comparer.compare();
    ChangeInfo[] changes = comparer.getChanges();

    for (ChangeInfo change : changes) {
        String text = change.getText();
        System.out.println(text);
    }
}
```

**Wskazówka filtrowania:** Użyj `ChangeInfo.getChangeType()`, aby skupić się wyłącznie na wstawieniach (`INSERT`) lub usunięciach (`DELETE`).

### Typowe pułapki i jak ich unikać

#### 1. Problemy ze ścieżkami plików
**Problem:** „File not found”, mimo że plik istnieje.  
**Rozwiązanie:** Używaj ścieżek bezwzględnych podczas rozwoju lub sprawdzaj katalog roboczy IDE. W Windows escapuj backslash (`\\`) lub używaj ukośników (`/`).

```java
// Good
String path = "C:/Users/yourname/documents/test.docx";
// Or
String path = "C:\\Users\\yourname\\documents\\test.docx";
```

#### 2. Wycieki pamięci przy dużych plikach
**Problem:** `OutOfMemoryError` przy porównywaniu PDF‑ów o 200 stronach.  
**Rozwiązanie:** Zawsze otaczaj `Comparer` blokiem try‑with‑resources i preferuj przeciążenia oparte na strumieniach, które ładować będą tylko niezbędne strony.

#### 3. Nieobsługiwane formaty plików
**Problem:** Wyjątki dla niektórych starszych formatów.  
**Rozwiązanie:** Sprawdź oficjalną listę **supported‑formats** (GroupDocs obsługuje **60+** formatów). Jeśli format nie figuruje, przekonwertuj go najpierw do PDF lub DOCX przed porównaniem.

#### 4. Problemy z wydajnością
**Problem:** Porównania trwają dłużej niż oczekiwano.  
**Rozwiązanie:**  
- Wyłącz obliczanie współrzędnych, jeśli nie jest potrzebne.  
- Używaj `CompareOptions.setDetectMovedBlocks(true)` tylko wtedy, gdy rzeczywiście potrzebujesz wykrywania przeniesionych bloków.  
- Równolegle uruchamiaj niezależne zadania porównawcze przy pomocy puli wątków.

### Wskazówki optymalizacji wydajności

#### Wybór odpowiednich opcji
```java
CompareOptions options = new CompareOptions.Builder()
    .setCalculateCoordinates(false) // Only enable when needed
    .setDetectStyleChanges(false)   // Skip formatting if you only care about content
    .build();
```

#### Zarządzanie pamięcią
- Przetwarzaj dokumenty partiami, zamiast ładować wszystko jednocześnie.  
- Korzystaj z API strumieniowego dla plików większych niż 50 MB.  
- Polegaj na try‑with‑resources, aby zapewnić czyszczenie zasobów.

#### Strategie buforowania
```java
// Pseudo-code for caching concept
String cacheKey = generateCacheKey(sourceFile, targetFile);
if (cache.contains(cacheKey)) {
    return cache.get(cacheKey);
}
```

### Scenariusze rzeczywiste i rozwiązania

#### Scenariusz 1: System zarządzania treścią
```java
public class ArticleVersionComparison {
    public List<ChangeInfo> compareVersions(String oldVersion, String newVersion) {
        try (Comparer comparer = new Comparer(oldVersion)) {
            comparer.add(newVersion);
            final Path result = comparer.compare();
            return Arrays.asList(comparer.getChanges());
        } catch (Exception e) {
            log.error("Failed to compare article versions", e);
            return Collections.emptyList();
        }
    }
}
```

#### Scenariusz 2: Zautomatyzowana kontrola jakości
```java
public boolean validateReportAgainstTemplate(InputStream report, InputStream template) {
    try (Comparer comparer = new Comparer(template)) {
        comparer.add(report);
        comparer.compare();
        ChangeInfo[] changes = comparer.getChanges();
        
        // Only allow certain types of changes
        return Arrays.stream(changes)
                .allMatch(change -> isAllowedChange(change));
    } catch (Exception e) {
        return false;
    }
}
```

#### Scenariusz 3: Przetwarzanie wsadowe dokumentów
```java
public void processBatchComparison(List<DocumentPair> documents) {
    documents.parallelStream().forEach(pair -> {
        try (Comparer comparer = new Comparer(pair.getSource())) {
            comparer.add(pair.getTarget());
            Path result = comparer.compare();
            // Process results...
        } catch (Exception e) {
            log.error("Failed to process document pair: " + pair, e);
        }
    });
}
```

### Zaawansowane funkcje i najlepsze praktyki

#### Praca z różnymi formatami plików
```java
public boolean isFormatSupported(String filePath) {
    String extension = getFileExtension(filePath);
    List<String> supportedFormats = Arrays.asList(
        ".docx", ".pdf", ".txt", ".rtf", ".odt", // Add more as needed
    );
    return supportedFormats.contains(extension.toLowerCase());
}
```

#### Obsługa dużych dokumentów
```java
CompareOptions largeDocOptions = new CompareOptions.Builder()
    .setCalculateCoordinates(false)  // Saves memory
    .setDetectStyleChanges(false)    // Focuses on content only
    .setWordsLimit(1000)             // Limits processing scope
    .build();
```

#### Wzorce obsługi błędów
```java
public ComparisonResult compareDocuments(String source, String target) {
    try (Comparer comparer = new Comparer(source)) {
        comparer.add(target);
        Path result = comparer.compare();
        
        return ComparisonResult.success(comparer.getChanges());
        
    } catch (SecurityException e) {
        log.error("Access denied when comparing documents", e);
        return ComparisonResult.failure("Access denied");
    } catch (IOException e) {
        log.error("IO error during document comparison", e);
        return ComparisonResult.failure("File access error");
    } catch (Exception e) {
        log.error("Unexpected error during comparison", e);
        return ComparisonResult.failure("Comparison failed");
    }
}
```

## Najczęściej zadawane pytania

**P: Jaka jest minimalna wersja Javy wymagana dla GroupDocs.Comparison?**  
O: Java 8 jest minimalnie wspieraną wersją; Java 11+ jest zalecana ze względu na lepsze zarządzanie pamięcią i wsparcie modułów.

**P: Czy mogę porównywać jednocześnie więcej niż dwa dokumenty?**  
O: GroupDocs.Comparison porównuje jedną parę na raz. W przypadku wersjonowania wielu dokumentów, iteruj listę dokumentów i porównuj kolejne pary, zapisując otrzymane `ChangeInfo[]` do późniejszej agregacji.

```java
try (Comparer comparer = new Comparer(sourceDocument)) {
    comparer.add(targetDocument1);
    comparer.add(targetDocument2);
    comparer.add(targetDocument3);
    // Now compare against all targets
}
```

**P: Jak postępować z bardzo dużymi dokumentami (100 MB+)?**  
O:  
- Wyłącz obliczanie współrzędnych, jeśli nie są potrzebne.  
- Preferuj API oparte na strumieniach, aby uniknąć ładowania całego pliku do RAM.  
- Podziel przetwarzanie na zakresy stron, jeśli potrzebujesz zmian tylko w określonych sekcjach.  
- Monitoruj zużycie heapu JVM i dostosuj parametr `-Xmx`.

**P: Czy istnieje sposób na wizualne podświetlenie zmian w wyniku?**  
O: Tak. Po uzyskaniu `ChangeInfo[]` możesz wygenerować nowy PDF przy użyciu GroupDocs.Watermark lub dowolnej biblioteki PDF, rysując prostokąty w zwróconych współrzędnych. Powstaje wersja „red‑line”, którą użytkownik może przeglądać w dowolnym czytniku PDF.

```java
CompareOptions options = new CompareOptions.Builder()
    .setShowInsertedContent(true)
    .setShowDeletedContent(true)
    .setGenerateOutputDocument(true)
    .build();
```

**P: Jak obsłużyć dokumenty zabezpieczone hasłem?**  
O: Przekaż hasło do konstruktora `Comparer` lub ustaw je w obiekcie `LoadOptions` przed wywołaniem `compare`. Biblioteka odszyfruje dokument w pamięci, więc hasło nigdy nie trafia na system plików.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your-password");

try (Comparer comparer = new Comparer(protectedDocument, loadOptions)) {
    // Comparison logic here
}
```

**P: Czy mogę dostosować sposób wykrywania zmian?**  
O: Oczywiście. `CompareOptions` oferuje flagi takie jak `setIgnoreFormatting(true)`, `setDetectMovedBlocks(true)` oraz `setGranularity(Granularity.WORD)`. Dostosuj je do reguł biznesowych — np. ignoruj zmiany czcionki, a jednocześnie wykrywaj przeniesione akapity.

```java
CompareOptions options = new CompareOptions.Builder()
    .setDetectStyleChanges(false)     // Ignore formatting changes
    .setSensitivityOfComparison(100)  // Adjust sensitivity (0‑100)
    .build();
```

**P: Jaki jest najlepszy sposób integracji z Spring Boot?**  
O: Utwórz bean `@Service`, który wstrzykuje ścieżkę do licencji, a następnie udostępnij endpoint `@RestController` przyjmujący pliki `MultipartFile`. W kontrolerze zamień `MultipartFile` na `InputStream` i wywołaj metodę porównania opartą na strumieniu. Zwróć `ChangeInfo[]` jako JSON do renderowania po stronie front‑endu.

```java
@Service
public class DocumentComparisonService {
    
    public ComparisonResult compare(MultipartFile source, MultipartFile target) {
        // Implementation using the techniques from this guide
    }
}
```

## Dodatkowe zasoby

- [GroupDocs.Comparison Documentation](https://docs.groupdocs.com/comparison/java/)
- [API Reference Guide](https://reference.groupdocs.com/comparison/java/)
- [Community Support Forum](https://forum.groupdocs.com/c/comparison)

---

**Ostatnia aktualizacja:** 2026-06-15  
**Testowane z:** GroupDocs.Comparison 25.2 for Java  
**Autor:** GroupDocs  

---

```java
for (ChangeInfo change : changes) {
    if (change.getType() == ComparisonAction.INSERT) {
        System.out.println("Added: " + change.getText());
    }
}
```

## Powiązane tutoriale

- [compare pdf java – Java Document Comparison Tutorial – Complete Guide to Loading & Comparing Documents](/comparison/java/document-loading/)
- [compare pdf files java - Java Document Comparison Tutorial - Complete GroupDocs Guide](/comparison/java/advanced-comparison/master-java-document-comparisons-groupdocs/)
- [GroupDocs.Comparison Java Licensing Setup Guide - Complete Configuration Tutorial](/comparison/java/licensing-configuration/)