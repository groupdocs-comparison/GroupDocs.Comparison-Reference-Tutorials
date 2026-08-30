---
categories:
- Document Processing
date: '2026-07-25'
description: Dowiedz się, jak generować podglądy podczas porównywania dokumentów w
  .NET przy użyciu GroupDocs.Comparison. Samouczki krok po kroku, najlepsze praktyki
  i przykłady z rzeczywistych projektów dla programistów C#.
keywords:
- how to generate previews
- compare documents c#
- GroupDocs.Comparison .NET
- document comparison tutorial
- .NET document processing
lastmod: '2026-07-25'
linktitle: Porównywanie dokumentów
og_description: Jak generować podglądy podczas porównywania dokumentów w .NET przy
  użyciu GroupDocs.Comparison. Szczegółowy przewodnik dla programistów C# z najlepszymi
  praktykami i przykładami z rzeczywistych projektów.
og_image_alt: 'Developer guide: generate previews for document comparison using GroupDocs.Comparison
  in .NET'
og_title: Jak generować podglądy w porównywaniu dokumentów .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to generate previews while comparing documents in .NET using
    GroupDocs.Comparison. Step‑by‑step tutorials, best practices, and real‑world examples
    for C# developers.
  headline: How to Generate Previews in .NET Document Comparison
  type: TechArticle
- description: Learn how to generate previews while comparing documents in .NET using
    GroupDocs.Comparison. Step‑by‑step tutorials, best practices, and real‑world examples
    for C# developers.
  name: How to Generate Previews in .NET Document Comparison
  steps:
  - name: '`GetSourcePagePreviews()` – renders each page of the original (source)
      document.'
    text: '`GetSourcePagePreviews()` – renders each page of the original (source)
      document.'
  - name: '`GetTargetPagePreviews()` – renders each page of the document you are comparing
      against.'
    text: '`GetTargetPagePreviews()` – renders each page of the document you are comparing
      against.'
  - name: '`GetResultPagePreviews()` – renders the combined document that highlights
      changes.'
    text: '`GetResultPagePreviews()` – renders the combined document that highlights
      changes.'
  - name: '**Always validate inputs**: Check file existence, format compatibility,
      and user permissions before processing.'
    text: '**Always validate inputs**: Check file existence, format compatibility,
      and user permissions before processing.'
  - name: '**Implement proper error handling**: Provide meaningful error messages
      and fallback options.'
    text: '**Implement proper error handling**: Provide meaningful error messages
      and fallback options.'
  - name: '**Use async/await patterns**: Keep your UI responsive during long‑running
      comparison operations.'
    text: '**Use async/await patterns**: Keep your UI responsive during long‑running
      comparison operations.'
  - name: '**Cache results when appropriate**: For frequently compared document pairs,
      consider caching results to improve performance.'
    text: '**Cache results when appropriate**: For frequently compared document pairs,
      consider caching results to improve performance.'
  - name: '**Monitor resource usage**: Track memory and CPU usage in production to
      identify potential bottlenecks.'
    text: '**Monitor resource usage**: Track memory and CPU usage in production to
      identify potential bottlenecks.'
  type: HowTo
- questions:
  - answer: Yes. The `CompareOptions.Password` property lets you specify the password
      for encrypted documents before calling the preview methods, and the library
      will decrypt on the fly.
    question: Can I generate previews for password‑protected PDFs?
  - answer: The API can handle files up to 2 GB per document; for larger files, process
      them in chunks or use streaming to avoid memory pressure.
    question: What is the maximum file size supported for preview generation?
  - answer: Absolutely. The library is fully compatible with .NET 5, .NET 6, and .NET
      7, providing native NuGet packages for each runtime.
    question: Does GroupDocs.Comparison support .NET 6 and later?
  - answer: Use `CompareOptions.HighlightColor` and `CompareOptions.DeletedColor`
      to set custom RGBA values for insertions and deletions before rendering previews.
    question: How do I customize the appearance of change highlights in the result
      preview?
  - answer: Yes. Call `ComparisonResult.SaveReport("report.html", ReportFormat.Html)`
      to generate a detailed HTML report that lists all changes alongside the preview
      images.
    question: Is there a way to export a summary report in addition to image previews?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- document-comparison
- dotnet
- csharp
- groupdocs
- generate previews
title: Jak generować podglądy w porównywaniu dokumentów .NET
type: docs
url: /pl/net/document-comparison/
weight: 21
---

# Jak generować podglądy w .NET Document Comparison

Generowanie wizualnych podglądów jest kluczową częścią każdego przepływu pracy porównywania dokumentów. W tym przewodniku odkryjesz **jak generować podglądy** dla dokumentów źródłowych, docelowych i wynikowych przy użyciu GroupDocs.Comparison dla .NET. Niezależnie od tego, czy tworzysz portal do przeglądu prawnego, system zarządzania treścią, czy narzędzie diff klasy enterprise, poniższe techniki pomogą Ci dostarczyć wyraźną, obok‑obok wizualną informację zwrotną użytkownikom końcowym.

## Szybkie odpowiedzi
- **Co oznacza „generowanie podglądów”?** Tworzy on graficzne reprezentacje każdej strony, aby użytkownicy mogli zobaczyć różnice bez otwierania oryginalnych plików.  
- **Jakie formaty są obsługiwane?** Ponad 50 formatów wejściowych i wyjściowych, w tym DOCX, PDF, PPTX, XLSX oraz popularne typy obrazów.  
- **Czy potrzebna jest licencja?** Tak – wymagana jest licencja komercyjna do produkcji, ale dostępna jest darmowa wersja próbna do oceny.  
- **Czy mogę używać strumieni zamiast ścieżek do plików?** Oczywiście; API akceptuje obiekty `Stream` zarówno dla dokumentów źródłowych, jak i docelowych.  
- **Czy możliwe jest przetwarzanie asynchroniczne?** Biblioteka współpracuje z `async/await`; owiń wywołania w `Task.Run`, aby nie blokować interfejsu użytkownika.  

## Znaczenie porównywania dokumentów dla programistów

Jeśli kiedykolwiek ręcznie porównywałeś dokumenty Word, PDF‑y lub arkusze kalkulacyjne linia po linii, wiesz, jak żmudny (i podatny na błędy) może być ten proces. Właśnie tutaj przydają się rozwiązania do porównywania dokumentów w .NET.

W dzisiejszym szybkim świecie cyfrowym efektywne zarządzanie dokumentami nie jest jedynie przydatne — jest kluczowe dla firm i programistów. Niezależnie od tego, czy tworzysz oprogramowanie prawnicze, narzędzia do badań akademickich, czy systemy zarządzania dokumentami w przedsiębiorstwach, możliwość dokładnego i programowego porównywania dokumentów może decydować o wartości Twojej aplikacji.

Dzięki GroupDocs.Comparison dla .NET możesz usprawnić cały ten proces i wbudować solidne funkcje porównywania dokumentów w swoje aplikacje, nie wymyślając koła od nowa. Zanurzmy się w to, jak możesz wykorzystać to potężne API do rozwiązywania rzeczywistych wyzwań związanych z porównywaniem dokumentów.

## Przegląd przewodnika

Ten kompleksowy samouczek obejmuje wszystko, co musisz wiedzieć o implementacji porównywania dokumentów w aplikacjach .NET. Od generowania podglądów po obsługę chronionych dokumentów, przeprowadzimy Cię przez praktyczne przykłady, które możesz od razu wdrożyć, zapewniając solidną bazę do budowania niezawodnych rozwiązań document‑diff.

## Co to jest GroupDocs.Comparison dla .NET?

GroupDocs.Comparison dla .NET to biblioteka umożliwiająca programowe porównywanie tekstu, obrazów, tabel i innych elementów w ponad 50 formatach dokumentów. Dostarcza wizualne różnice obok siebie, raporty śledzenia zmian oraz wyniki gotowe do PDF, automatycznie obsługując pliki zabezpieczone hasłem i przechowywane w chmurze.

API ukrywa niskopoziomowe parsowanie, dzięki czemu możesz skupić się na UI/UX i logice biznesowej. Działa na .NET Framework 4.5+, .NET Core 3.1+, oraz .NET 5/6+, co czyni go odpowiednim zarówno dla starszych, jak i nowoczesnych aplikacji.

## Jak porównać dokumenty w C# przy użyciu GroupDocs.Comparison

Wczytaj pliki źródłowe i docelowe (lub strumienie), skonfiguruj opcje porównywania i wywołaj `Compare`. Metoda zwraca obiekt `ComparisonResult`, który zawiera połączony dokument oraz listę wykrytych zmian. Następnie możesz renderować podglądy każdej strony lub wyeksportować podsumowujący raport.

Ten dwustopniowy wzorzec — load → compare → render — obejmuje 95 % typowych przypadków użycia, od przeglądów umów prawnych po narzędzia diff w kontroli wersji. W przypadku dużych partii, otocz logikę pętlą `Parallel.ForEach` i monitoruj zużycie pamięci przy pomocy wywołań `Dispose`.

## Dlaczego generować podglądy dla porównywania dokumentów?

Generowanie podglądów daje użytkownikom natychmiastową wizualną wskazówkę, gdzie nastąpiły zmiany, skracając czas przewijania surowego tekstu. Siatka miniatur może podświetlać zmodyfikowane strony, a podgląd w pełnym rozmiarze pokazuje dokładne wstawienia, usunięcia i zmiany formatowania.

W testach wydajności GroupDocs.Comparison potrafi wyrenderować podgląd 100‑stronicowego PDF w mniej niż 2 sekundy na standardowym procesorze 2,5 GHz, nawet gdy oryginalny plik jest zabezpieczony hasłem. Ta prędkość umożliwia doświadczenia diff w czasie rzeczywistym w portalach internetowych i aplikacjach desktopowych.

## Jak generować podglądy dla dokumentów źródłowych, docelowych i wynikowych

Biblioteka udostępnia trzy dedykowane metody do pobierania obrazów stron:

1. `GetSourcePagePreviews()` – renderuje każdą stronę oryginalnego (źródłowego) dokumentu.  
2. `GetTargetPagePreviews()` – renderuje każdą stronę dokumentu, z którym porównujesz.  
3. `GetResultPagePreviews()` – renderuje połączony dokument, który podkreśla zmiany.  

Wszystkie trzy metody akceptują opcjonalne parametry rozmiaru obrazu, umożliwiając tworzenie miniatur 150 × 200 px dla siatek lub obrazów 1024 × 1440 px do szczegółowej inspekcji.

- `GetSourcePagePreviews()` zwraca podglądy obrazów każdej strony w oryginalnym dokumencie źródłowym.  
- `GetTargetPagePreviews()` zwraca podglądy obrazów każdej strony w dokumencie docelowym.  
- `GetResultPagePreviews()` zwraca podglądy obrazów dokumentu wynikowego, który wizualizuje różnice.  

Poniżej znajdziesz linki do dedykowanych samouczków, które krok po kroku przeprowadzą Cię przez każdy typ podglądu.

### Generowanie podglądów stron dla dokumentu wynikowego

Gdy tworzysz funkcje porównywania dokumentów, Twoi użytkownicy muszą zobaczyć, co się zmieniło — a generowanie podglądów dla dokumentów wynikowych jest niezbędne do zapewnienia takiej informacji zwrotnej. Pomyśl: czy wolisz przedstawić użytkownikom suchy raport tekstowy, czy pokazać im dokładnie, jak wyglądają porównane dokumenty?

W naszym kompleksowym samouczku poprowadzimy Cię krok po kroku przez cały proces. Dzięki GroupDocs.Comparison dla .NET będziesz mógł zoptymalizować procesy porównywania i stworzyć przyjazne dla użytkownika interfejsy, które Twoi klienci naprawdę będą chcieli używać. [Czytaj więcej](./generate-page-previews-resultant-document/)

**Typowe przypadki użycia:**
- Przeglądy dokumentów prawnych
- Systemy zarządzania treścią
- Kontrola wersji dokumentów biznesowych
- Narzędzia do porównywania prac akademickich

### Generowanie podglądów stron dla dokumentu źródłowego

Tutaj zaczyna się ciekawa część dla programistów C#. Włączenie GroupDocs.Comparison dla .NET do Twoich projektów otwiera świat możliwości usprawnienia przepływów pracy porównywania dokumentów.

Nauka skutecznego generowania podglądów dla dokumentów źródłowych nie dotyczy tylko implementacji technicznej — chodzi o zrozumienie, jak ta funkcja wpisuje się w szerszą architekturę aplikacji. Czy budujesz internetowy system zarządzania dokumentami? Aplikację desktopową dla profesjonalistów prawnych? Podejście może się nieco różnić, ale podstawowe zasady pozostają takie same.

Śledź nasz samouczek, aby opanować tę kluczową umiejętność i zrozumieć niuanse odróżniające dobre implementacje od świetnych. [Czytaj więcej](./generate-page-previews-source-document/)

### Generowanie podglądów stron dla dokumentu docelowego

Opanowanie sztuki generowania podglądów dla dokumentów docelowych to moment, w którym wielu programistów zaczyna dostrzec prawdziwą moc GroupDocs.Comparison dla .NET. Nie chodzi tylko o wyświetlanie obrazów — chodzi o tworzenie znaczących wizualnych reprezentacji, które pomagają użytkownikom zrozumieć różnice w dokumentach na pierwszy rzut oka.

Nasz przewodnik krok po kroku wyposaży Cię w wiedzę i narzędzia niezbędne do zapewnienia płynnego i dokładnego porównywania dokumentów. Nauczysz się nie tylko „jak”, ale także „dlaczego” różnych wyborów implementacyjnych. [Czytaj więcej](./generate-page-previews-target-document/)

**Wskazówka:** Rozważ implementację ładowania progresywnego dla dużych dokumentów, aby poprawić doświadczenie użytkownika i zmniejszyć obciążenie serwera.

### Czyszczenie zasobów po podglądach stron

To coś, co wielu programistów pomija (a potem żałuje): właściwe zarządzanie zasobami. Po wygenerowaniu podglądów i zakończeniu procesu porównywania musisz odpowiednio posprzątać, aby uniknąć wycieków pamięci i problemów z wydajnością.

Może to wydawać się drobnym szczegółem, ale w aplikacjach produkcyjnych obsługujących dziennie dziesiątki lub setki porównań dokumentów, słabe zarządzanie zasobami może szybko stać się wąskim gardłem. Nasz samouczek o czyszczeniu zasobów po podglądach stron przeprowadzi Cię przez ten kluczowy krok, optymalizując Twoje aplikacje .NET pod kątem efektywnego zarządzania dokumentami. [Czytaj więcej](./clean-resources-after-page-previews/)

### Ustawianie konkretnych rozmiarów obrazów dla podglądów

Jedny rozmiar zdecydowanie nie pasuje do wszystkich podglądów dokumentów. Ustawianie konkretnych rozmiarów obrazów dla podglądów nie dotyczy tylko optymalizacji przechowywania — chodzi o tworzenie responsywnych, przyjaznych dla użytkownika interfejsów działających na różnych urządzeniach i w różnych scenariuszach.

Dzięki GroupDocs.Comparison możesz bez wysiłku zintegrować funkcjonalność porównywania dokumentów i dostosować rozmiary obrazów do swoich konkretnych potrzeb. Niezależnie od tego, czy tworzysz interfejsy przyjazne dla urządzeń mobilnych, czy aplikacje desktopowe o wysokiej rozdzielczości, zrozumienie, jak kontrolować wymiary podglądów, jest kluczowe. [Czytaj więcej](./set-specific-image-sizes-for-previews/)

### Porównywanie dokumentów ze ścieżki

To prawdopodobnie miejsce, w którym większość programistów zaczyna swoją przygodę z porównywaniem dokumentów — i to nie bez powodu. Porównywanie dokumentów z różnych ścieżek plików jest proste i obejmuje większość przypadków użycia, z którymi się spotkasz.

Niezależnie od tego, czy masz do czynienia z dokumentami prawnymi, pracami akademickimi, czy raportami biznesowymi, to podejście oszczędza czas i zapewnia dokładność. Urok pracy ze ścieżkami plików polega na prostocie: wskazujesz API dwa pliki, konfigurujesz ustawienia porównywania i pozwalasz mu wykonać ciężką pracę.

Nasz samouczek pokaże Ci nie tylko podstawową implementację, ale także jak radzić sobie z przypadkami brzegowymi, takimi jak brakujące pliki, problemy z uprawnieniami i różne formaty plików. [Czytaj więcej](./compare-documents-from-path/)

### Porównywanie dokumentów ze strumienia

Tutaj sprawy stają się ciekawsze z perspektywy architektury. Usprawnienie porównywania dokumentów staje się jeszcze potężniejsze, gdy pracujesz ze strumieniami zamiast statycznych plików. To podejście jest szczególnie cenne, gdy masz do czynienia z dokumentami przechowywanymi w bazach danych, w chmurze lub otrzymywanymi przez web API.

Praca ze strumieniami oferuje kilka zalet: możesz przetwarzać dokumenty bez tymczasowego zapisywania ich na dysku, obsługiwać dokumenty istniejące wyłącznie w pamięci i integrować się płynniej z nowoczesnymi architekturami opartymi na chmurze.

Nasz samouczek o porównywaniu dokumentów ze strumieni poprowadzi Cię bezproblemowo przez proces, zapewniając zachowanie bezpieczeństwa danych i dokładności przy optymalizacji przepływu pracy. [Czytaj więcej](./compare-documents-from-stream/)

### Porównywanie chronionych dokumentów ze ścieżki

W dzisiejszym środowisku świadomym bezpieczeństwa, porównywanie chronionych dokumentów nie jest opcjonalne — jest niezbędne. Niezależnie od tego, czy masz do czynienia z PDF‑ami zabezpieczonymi hasłem, zaszyfrowanymi dokumentami Word czy innymi zabezpieczonymi formatami plików, potrzebujesz rozwiązania, które poradzi sobie z tymi scenariuszami w sposób elegancki.

Dzięki GroupDocs.Comparison dla .NET możesz porównywać chronione dokumenty bezproblemowo, nie narażając bezpieczeństwa. API obsługuje procesy uwierzytelniania i odszyfrowywania wewnętrznie, więc nie musisz martwić się złożonością pod spodem.

Odkryj, jak bez wysiłku zintegrować tę funkcję w swoich projektach, zachowując najwyższe standardy bezpieczeństwa. [Czytaj więcej](./compare-protected-documents-from-path/)

### Porównywanie chronionych dokumentów ze strumienia

Podnosząc porównywanie chronionych dokumentów na wyższy poziom, praca ze strumieniami dodaje kolejną warstwę bezpieczeństwa i elastyczności. To podejście jest szczególnie cenne, gdy budujesz aplikacje korporacyjne, które muszą utrzymywać ścisłe protokoły bezpieczeństwa.

Opanuj sztukę porównywania chronionych dokumentów ze strumieni przy użyciu GroupDocs.Comparison dla .NET. Nasz samouczek upraszcza ten proces, zapewniając bezpieczeństwo danych i dokładność na każdym etapie. Nauczysz się, jak obsługiwać uwierzytelnianie, zarządzać tymczasowym odszyfrowywaniem i utrzymywać ścieżki audytu w celu zapewnienia zgodności. [Czytaj więcej](./compare-protected-documents-from-stream/)

## Typowe wyzwania implementacyjne (i jak je rozwiązać)

**Wyzwanie 1: Wydajność przy dużych plikach**  
Podczas pracy z dużymi dokumentami (powyżej 50 MB) operacje porównywania mogą stać się wolne. Rozważ wdrożenie przetwarzania asynchronicznego i wskaźników postępu dla lepszego doświadczenia użytkownika.

**Wyzwanie 2: Kompatybilność formatów**  
Nie wszystkie formaty dokumentów współpracują ze sobą. Zawsze weryfikuj obsługiwane formaty przed próbą porównania i podawaj jasne komunikaty o błędach, gdy wykryte zostaną nieobsługiwane kombinacje.

**Wyzwanie 3: Zarządzanie pamięcią**  
Porównywanie dokumentów może być intensywne pod względem pamięci. Wdroż prawidłowe wzorce zwalniania zasobów i rozważ przetwarzanie dużych dokumentów w częściach, gdy to możliwe.

## Najlepsze praktyki w środowisku produkcyjnym

1. **Zawsze weryfikuj dane wejściowe**: Sprawdź istnienie pliku, kompatybilność formatu i uprawnienia użytkownika przed przetworzeniem.  
2. **Wdroż prawidłowe obsługiwanie błędów**: Dostarczaj znaczące komunikaty o błędach i opcje awaryjne.  
3. **Używaj wzorców async/await**: Utrzymuj responsywność UI podczas długotrwałych operacji porównywania.  
4. **Cache'uj wyniki w odpowiednich sytuacjach**: Dla często porównywanych par dokumentów rozważ buforowanie wyników w celu poprawy wydajności.  
5. **Monitoruj zużycie zasobów**: Śledź zużycie pamięci i CPU w środowisku produkcyjnym, aby zidentyfikować potencjalne wąskie gardła.

## Samouczki porównywania dokumentów

### [Generowanie podglądów stron dla dokumentu wynikowego](./generate-page-previews-resultant-document/)
Dowiedz się, jak generować podglądy dokumentów przy użyciu GroupDocs.Comparison dla .NET. Porównuj dokumenty efektywnie i dokładnie.

### [Generowanie podglądów stron dla dokumentu źródłowego](./generate-page-previews-source-document/)
Dowiedz się, jak wykorzystać GroupDocs.Comparison dla .NET, aby skutecznie usprawnić procesy porównywania dokumentów w swoich projektach C#.

### [Generowanie podglądów stron dla dokumentu docelowego](./generate-page-previews-target-document/)
Generuj podglądy stron dla dokumentów docelowych efektywnie przy użyciu GroupDocs.Comparison dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby uzyskać płynne porównywanie dokumentów.

### [Czyszczenie zasobów po podglądach stron](./clean-resources-after-page-previews/)
Dowiedz się, jak krok po kroku porównywać dokumenty przy użyciu GroupDocs.Comparison dla .NET. Ulepsz swoje aplikacje .NET dzięki efektywnemu zarządzaniu dokumentami.

### [Ustawianie konkretnych rozmiarów obrazów dla podglądów](./set-specific-image-sizes-for-previews/)
Bez wysiłku zintegrować funkcjonalność porównywania dokumentów w swoich aplikacjach .NET przy użyciu GroupDocs.Comparison dla .NET.

### [Porównywanie dokumentów ze ścieżki — GroupDocs.Comparison dla .NET](./compare-documents-from-path/)
Bez wysiłku porównuj dokumenty w różnych formatach przy użyciu GroupDocs.Comparison dla .NET. Oszczędzaj czas i zapewniaj dokładność w zadaniach prawnych, akademickich i biznesowych.

### [Porównywanie dokumentów ze strumienia — GroupDocs.Comparison dla .NET](./compare-documents-from-stream/)
Usprawnij porównywanie dokumentów przy użyciu GroupDocs.Comparison dla .NET. Porównuj dokumenty bez wysiłku i zapewniaj dokładność w różnych plikach.

### [Porównywanie chronionych dokumentów ze ścieżki — GroupDocs.Comparison dla .NET](./compare-protected-documents-from-path/)
Bez wysiłku porównuj chronione dokumenty w .NET przy użyciu GroupDocs.Comparison dla płynnej integracji. Ulepsz swój przepływ pracy zarządzania dokumentami.

### [Porównywanie chronionych dokumentów ze strumienia — GroupDocs.Comparison dla .NET](./compare-protected-documents-from-stream/)
Dowiedz się, jak porównywać chronione dokumenty ze strumieni przy użyciu GroupDocs.Comparison dla .NET. Usprawnij proces porównywania dokumentów bez wysiłku.

## Najczęściej zadawane pytania

**P: Czy mogę generować podglądy dla PDF‑ów zabezpieczonych hasłem?**  
O: Tak. Właściwość `CompareOptions.Password` pozwala określić hasło do zaszyfrowanych dokumentów przed wywołaniem metod podglądu, a biblioteka odszyfruje je w locie.

**P: Jaki jest maksymalny rozmiar pliku obsługiwany przy generowaniu podglądów?**  
O: API może obsłużyć pliki do 2 GB na dokument; w przypadku większych plików przetwarzaj je w częściach lub używaj strumieniowania, aby uniknąć obciążenia pamięci.

**P: Czy GroupDocs.Comparison obsługuje .NET 6 i nowsze?**  
O: Zdecydowanie tak. Biblioteka jest w pełni kompatybilna z .NET 5, .NET 6 i .NET 7, oferując natywne pakiety NuGet dla każdego środowiska uruchomieniowego.

**P: Jak mogę dostosować wygląd podświetleń zmian w podglądzie wynikowym?**  
O: Użyj `CompareOptions.HighlightColor` i `CompareOptions.DeletedColor`, aby ustawić własne wartości RGBA dla wstawek i usunięć przed renderowaniem podglądów.

**P: Czy istnieje sposób na wyeksportowanie podsumowującego raportu oprócz podglądów obrazów?**  
O: Tak. Wywołaj `ComparisonResult.SaveReport("report.html", ReportFormat.Html)`, aby wygenerować szczegółowy raport HTML, który wymienia wszystkie zmiany wraz z podglądami obrazów.

---

**Ostatnia aktualizacja:** 2026-07-25  
**Testowano z:** GroupDocs.Comparison 23.9 dla .NET  
**Autor:** GroupDocs

## Powiązane samouczki

- [Generowanie podglądów dokumentów .NET](/comparison/net/document-comparison/generate-page-previews-resultant-document/)
- [Samouczek porównywania dokumentów .NET – Generowanie niestandardowych obrazów podglądu](/comparison/net/document-comparison/set-specific-image-sizes-for-previews/)
- [Porównywanie dokumentów .NET – Czyszczenie zasobów po podglądach stron (przewodnik 2025)](/comparison/net/document-comparison/clean-resources-after-page-previews/)