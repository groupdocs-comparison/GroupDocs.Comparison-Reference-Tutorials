---
"date": "2025-05-05"
"description": "Naučte se, jak s přesností automatizovat porovnávání dokumentů pomocí nástroje GroupDocs.Comparison pro Javu. Snadno si upravte styly, upravte citlivost a ignorujte záhlaví a zápatí."
"title": "Porovnání hlavních dokumentů v Javě pomocí GroupDocs.Comparison API"
"url": "/cs/java/basic-comparison/mastering-document-comparison-java-groupdocs/"
"weight": 1
type: docs
---
# Zvládnutí porovnávání dokumentů v Javě pomocí GroupDocs.Comparison API

## Zavedení

Už vás nebaví ručně porovnávat dokumenty? Ať už jde o identifikaci změn v záhlaví, zápatí nebo obsahu, porovnávání dokumentů může být náročný úkol. Knihovna GroupDocs.Comparison pro Javu tento proces automatizuje a vylepšuje s přesností a snadností.

Tento komplexní tutoriál vás provede využitím GroupDocs.Comparison v Javě k přizpůsobení stylů porovnávání dokumentů, úpravě nastavení citlivosti, ignorování porovnávání záhlaví/zápatí, nastavení výstupní velikosti papíru a dalším činnostem. Po přečtení tohoto průvodce budete schopni efektivně zefektivnit svůj pracovní postup.

**Co se naučíte:**
- Při porovnávání dokumentů ignorujte záhlaví a zápatí.
- Přizpůsobte změny pomocí úprav stylu.
- Pro podrobnou analýzu upravte citlivost porovnání.
- Nastavení výstupních velikostí papíru v aplikacích Java.
- Implementujte tyto funkce v reálných scénářích.

Než se pustíte do praktických aspektů, ujistěte se, že máte potřebné předpoklady.

## Předpoklady

Chcete-li začít s GroupDocs.Comparison pro Javu, ujistěte se, že máte následující:
1. **Vývojová sada pro Javu (JDK):** Ujistěte se, že máte na počítači nainstalovanou sadu JDK. Měla by stačit jakákoli verze vyšší než 8.
2. **Znalec:** V tomto tutoriálu se předpokládá, že ke správě závislostí projektu používáte Maven.
3. **Knihovna GroupDocs.Comparison:**
   - Přidejte do svého `pom.xml`:

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
4. **Licence:** Získejte bezplatnou zkušební verzi, dočasnou licenci nebo si zakupte plnou verzi od GroupDocs.

S tímto nastavením jste připraveni začít implementovat funkce porovnávání dokumentů ve vašich aplikacích Java.

## Nastavení GroupDocs.Comparison pro Javu

Ujistěte se, že je naše prostředí správně nakonfigurováno:

### Instalace přes Maven

Přidejte výše uvedený fragment XML do souboru vašeho projektu `pom.xml`Tento krok zajišťuje, že Maven rozpozná potřebný repozitář a závislosti. 

### Získání licence
- **Bezplatná zkušební verze:** Stáhněte si zkušební verzi z [Soubory ke stažení GroupDocs](https://releases.groupdocs.com/comparison/java/).
- **Dočasná licence:** Požádejte o dočasnou licenci prostřednictvím [Podpora GroupDocs](https://purchase.groupdocs.com/temporary-license/) vyhodnotit všechny funkce.
- **Nákup:** Pro dlouhodobé používání si zakupte licenci prostřednictvím [Nákup GroupDocs](https://purchase.groupdocs.com/buy).

Po získání a nastavení licenčního souboru dle dokumentace GroupDocs inicializujte GroupDocs.Comparison takto:

```java
// Základní příklad inicializace
com.groupdocs.comparison.License license = new com.groupdocs.comparison.License();
license.setLicense("path/to/your/license/file.lic");
```

## Průvodce implementací

### Funkce 1: Ignorovat porovnání záhlaví/zápatí

**Přehled:** Záhlaví a zápatí často obsahují informace, jako jsou čísla stránek nebo názvy dokumentů, které nemusí být relevantní pro porovnání změn obsahu.

#### Možnosti nastavení

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import java.io.FileOutputStream;

public class IgnoreHeaderFooterExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/IgnoreHeaderFooter_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_with_footer.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target_with_footer.docx");

            // Nastavení možností porovnání tak, aby se záhlaví a zápatí ignorovala
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setHeaderFootersComparison(false)
                    .build();

            final Path resultPath = comparer.compare(resultStream, new SaveOptions(), compareOptions);
        }
    }
}
```

#### Vysvětlení
- **`CompareOptions.Builder().setHeaderFootersComparison(false)`**Toto nastavení instruuje knihovnu, aby přeskočila porovnávání záhlaví a zápatí.
- **`try-with-resources`:** Zajišťuje, aby všechny proudy byly po použití řádně uzavřeny.

### Funkce 2: Nastavení výstupní velikosti papíru

**Přehled:** Úprava výstupní velikosti papíru je klíčová pro vytváření dokumentů vhodných pro tisk. Zde je návod, jak ji upravit během porovnávání dokumentů.

#### Kroky implementace

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.enums.PaperSize;

public class SetOutputPaperSizeExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/SetOutputPaperSize_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // Nastavte velikost papíru na A6
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setPaperSize(PaperSize.A6)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Vysvětlení
- **`CompareOptions.Builder().setPaperSize(PaperSize.A6)`**: Nastaví výstupní velikost papíru na A6.

### Funkce 3: Úprava citlivosti porovnání

**Přehled:** Jemné doladění citlivosti porovnání pomáhá identifikovat i drobné změny. Zde je návod, jak ji upravit:

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;

public class AdjustComparisonSensitivityExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/AdjustComparisonSensitivity_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // Nastavte citlivost na 100
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setSensitivityOfComparison(100)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Vysvětlení
- **`CompareOptions.Builder().setSensitivityOfComparison(100)`**: Upravuje úroveň citlivosti pro detekci změn.

### Funkce 4: Přizpůsobení stylů změn (pomocí streamů)

**Přehled:** Rozlišování mezi vloženým, odstraněným a změněným textem usnadňuje porovnávání. Zde je návod, jak přizpůsobit styly pomocí streamů:

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.save.SaveOptions;
import com.groupdocs.comparison.options.style.StyleSettings;

import java.awt.Color;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;

public class CustomizeChangesStylesStreamExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/CustomizeChangesStylesStream_result.docx";

        try (InputStream sourceFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source_word.docx");
             InputStream targetFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");
             OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer(sourceFile)) {

            comparer.add(targetFile);

            // Přizpůsobení stylů změn
            StyleSettings insertedStyle = new StyleSettings();
            insertedStyle.setHighlightColor(Color.GREEN); // Zelená pro vkládání
            StyleSettings deletedStyle = new StyleSettings();
            deletedStyle.setHighlightColor(Color.RED); // Červená pro smazané položky
            StyleSettings changedStyle = new StyleSettings();
            changedStyle.setHighlightColor(Color.BLUE); // Modrá pro změny

            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setInsertedItemStyle(insertedStyle)
                    .setDeletedItemStyle(deletedStyle)
                    .setChangedItemStyle(changedStyle)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Vysvětlení
- **Nastavení vlastního stylu**Použití `StyleSettings` definovat barvy zvýraznění pro vložení (zelená), odstranění (červená) a změny (modrá).
- **`CompareOptions.Builder()`:** Použijte tyto styly během procesu porovnávání.

## Závěr

Využitím nástroje GroupDocs.Comparison pro Javu můžete s přesností automatizovat porovnávání dokumentů. Tento tutoriál se zabýval tím, jak ignorovat záhlaví/zápatí, nastavovat výstupní velikosti papíru, upravovat citlivost a přizpůsobovat styly změn. Implementace těchto funkcí zefektivní váš pracovní postup a vylepší analýzu dokumentů v aplikacích Java.

## Často kladené otázky

### 1. Mohu při porovnávání v GroupDocs pro Javu ignorovat záhlaví a zápatí?  

Ano, použijte `setHeaderFootersComparison(false)` v `CompareOptions` vyloučit záhlaví a zápatí z porovnání.

### 2. Jak nastavím výstupní velikost papíru v Javě pomocí GroupDocs?  

Použít `setPaperSize(PaperSize.A6)` nebo jiné velikosti v `CompareOptions` pro přizpůsobení velikosti papíru finálního dokumentu.

### 3. Je možné jemně doladit citlivost srovnání?  

Ano, použijte `setSensitivityOfComparison()` v `CompareOptions` pro úpravu citlivosti a odpovídající detekci menších nebo větších změn.

### 4. Mohu během porovnávání upravovat styl vloženého, smazaného a změněného textu?  

Rozhodně si můžete upravit styly pomocí `StyleSettings` pro různé typy změn a aplikovat je v `CompareOptions`.

### 5. Jaké jsou předpoklady pro zahájení práce s GroupDocs Comparison v Javě?  

Nainstalujte JDK, spravujte závislosti pomocí Mavenu, získejte licenci a přidejte do svého projektu knihovnu GroupDocs.Comparison.