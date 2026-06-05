---
categories:
- Document Comparison
date: '2026-06-05'
description: Узнайте, как сохранять метаданные с помощью GroupDocs Comparison для
  .NET, пошаговое руководство по сохранению свойств целевого документа во время сравнения.
keywords:
- how to preserve metadata
- keep custom properties
- metadata preservation .NET
lastmod: '2026-06-05'
linktitle: Руководство по сохранению метаданных
schemas:
- author: GroupDocs
  dateModified: '2026-06-05'
  description: Learn how to preserve metadata with GroupDocs Comparison for .NET,
    step‑by‑step guide to keep target document properties during comparison.
  headline: How to Preserve Metadata with GroupDocs Comparison – .NET Tutorial
  type: TechArticle
- description: Learn how to preserve metadata with GroupDocs Comparison for .NET,
    step‑by‑step guide to keep target document properties during comparison.
  name: How to Preserve Metadata with GroupDocs Comparison – .NET Tutorial
  steps:
  - name: Initialize Your Comparer Object
    text: 'The `Comparer` class is the core component that performs document comparison
      and controls output options. Load the source (original) file and create a `Comparer`
      instance: **Why use `using` statements?** They automatically dispose of resources,
      preventing memory leaks when processing large documents'
  - name: Add the Target Document
    text: 'The `Add` method registers the target document whose changes will be compared
      against the source. Specify the updated file you want to compare: **Common mistake**:
      Confusing source and target. Think of it this way—source is your “original,”
      target is your “updated version.”'
  - name: Set the Metadata Type (The Magic Happens Here)
    text: '`CloneMetadataType` property determines which document''s metadata is copied
      to the result. Tell the comparer to keep the target’s metadata: **What’s happening?**
      `CloneMetadataType = MetadataType.Target` tells GroupDocs.Comparison: “Hey,
      I want to keep the target document’s metadata in my final resu'
  type: HowTo
- questions:
  - answer: When you add several target files, GroupDocs.Comparison uses the metadata
      from the **first** target document added. Add the document whose metadata you
      want to keep first in the chain.
    question: Can I preserve metadata from multiple target documents when comparing?
  - answer: Only the metadata that exists in the target will be copied to the output.
      Missing fields are simply omitted; the comparison still succeeds.
    question: What happens if the target document lacks some metadata fields?
  - answer: 'Use a `LoadOptions` object with the password, then pass it to the `Comparer`
      constructor:'
    question: How do I handle password‑protected documents?
  - answer: The current API preserves **all** metadata from the chosen source (Target
      or Source). For granular control you’d need to extract the properties after
      comparison and re‑apply them manually.
    question: Is there a way to preserve only selected metadata properties?
  - answer: Most common business formats—DOCX, PDF, PPTX, XLSX, and many others—support
      metadata preservation. See the official docs for the full list.
    question: Which document formats support metadata preservation?
  type: FAQPage
tags:
- GroupDocs.Comparison
- metadata-preservation
- dotnet-tutorial
- document-management
title: Как сохранить метаданные с помощью GroupDocs Comparison – .NET Tutorial
type: docs
url: /ru/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# Как сохранить метаданные с GroupDocs Comparison – .NET учебник

## Введение

Когда вы сравниваете два документа и теряете важные метаданные в процессе? Вы не одиноки. Когда нужно **сохранить метаданные целевого документа** при сравнении в приложении .NET, задача может показаться сложной — но это не так. Этот учебник показывает **как сохранить метаданные**, чтобы полученный файл сохранял точные данные об авторе, дате создания и пользовательских свойствах.

## Быстрые ответы
- **Что означает “preserve target metadata”?** Он сохраняет метаданные (автор, дата создания, пользовательские свойства и т.д.) из документа, который вы указываете как целевой, при генерации результата сравнения.  
- **Какая версия GroupDocs.Comparison требуется?** Версия 25.4.0 или новее.  
- **Можно ли использовать это с .NET Core?** Да — .NET Core 2.0+ или .NET Framework 4.6.1+.  
- **Нужна ли лицензия для продакшн?** Для продакшн требуется коммерческая лицензия; бесплатная пробная версия подходит для обучения.  
- **Будет ли функция работать с PDF и DOCX?** Да — все основные форматы Office и PDF поддерживают сохранение метаданных.

## Что такое сохранение метаданных?

Сохранение метаданных означает удержание описательной информации исходного документа — такой как автор, заголовок, номер ревизии и пользовательские свойства — без изменений после операции обработки. В GroupDocs.Comparison вы можете решить, сохраняются ли метаданные исходного или целевого документа в окончательном результате сравнения.

## Почему сохранение метаданных важно

Сохранение метаданных важно, поскольку многие отрасли рассматривают их как юридическое доказательство или критически важную бизнес‑информацию. **Почему?** Потому что метаданные фиксируют право собственности, теги соответствия, историю версий и аудиторские следы, на которые организации полагаются при регуляторной отчетности, управлении контрактами и академическом цитировании. Потеря этих данных может аннулировать юридический статус документа или нарушить автоматизированные рабочие процессы.

## Требования

### Необходимые библиотеки и версии
- **GroupDocs.Comparison for .NET**: Версия 25.4.0 или новее (ранние версии имеют ограниченные возможности работы с метаданными).  
- **.NET Framework**: 4.6.1 или выше, либо .NET Core 2.0+.

### Настройка окружения
- Visual Studio (или любой предпочитаемый IDE для C#).  
- Базовые знания C# (ничего слишком сложного, обещаю!).  
- Два образцовых документа для тестирования (Word *.docx* отлично подходит).

### Требуемые знания
Не нужно быть экспертом по GroupDocs, но вы должны быть уверены в следующем:
- Операторы `using` в C# и работа с файлами.  
- Основные концепции обработки документов.  
- Что такое метаданные (автор, заголовок, пользовательские свойства и т.д.).

Готовы? Давайте настроим.

## Настройка GroupDocs.Comparison для .NET

Установка GroupDocs.Comparison проста, но есть несколько подводных камней, о которых стоит помнить.

### Варианты установки

**Консоль менеджера пакетов NuGet** (самый простой способ):
```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

**.NET CLI** (если предпочитаете командную строку):
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

**Совет**: Всегда указывайте версию, чтобы избежать неожиданных несовместимых изменений в проекте.

### Получение лицензии
Здесь многие разработчики сталкиваются с проблемой. GroupDocs.Comparison не бесплатен, но у вас есть варианты:

- **Бесплатная пробная версия** — полная функциональность на 30 дней, идеально для оценки.  
- **Временная лицензия** — продленный период оценки, если нужно больше времени.  
- **Коммерческая лицензия** — для продакшн использования (доступны разные ценовые уровни).

Не беспокойтесь о лицензировании сейчас, если вы просто учитесь — пробная версия включает все функции **preserve target metadata**.

### Базовая проверка настройки

Давайте убедимся, что всё работает, с помощью простого теста:

```csharp
using System.IO;
using GroupDocs.Comparison;

string sourceFilePath = "source.docx";
string targetFilePath = "target.docx";

// Initialize the Comparer object.
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // Add the target document for comparison.
    comparer.Add(targetFilePath);
}
```

Если это компилируется без ошибок, вы готовы к работе. Если нет, проверьте установку пакета и операторы `using`.

## Как сохранить метаданные целевого документа

Чтобы сохранить метаданные целевого документа, необходимо настроить сравниватель так, чтобы он клонировал метаданные из целевого документа перед генерацией результата. Это включает установку свойства `CloneMetadataType` в значение `MetadataType.Target` у экземпляра `Comparer`. Таким образом, все поля метаданных — автор, дата создания, пользовательские свойства — копируются из целевого документа в выходной файл, гарантируя сохранение информации обновлённого документа.

### Понимание потока метаданных

Во время типичного сравнения:

1. **Исходный документ** предоставляет базовое содержание.  
2. **Целевой документ** содержит изменения для сравнения.  
3. **Выходной документ** объединяет оба, но чьи метаданные победят?

По умолчанию GroupDocs.Comparison использует метаданные исходного документа. Чтобы **preserve target metadata**, необходимо явно указать это API.

### Пошаговая реализация

#### Шаг 1: Инициализировать объект Comparer

Класс `Comparer` — основной компонент, который выполняет сравнение документов и управляет параметрами вывода.  
Загрузите исходный (оригинальный) файл и создайте экземпляр `Comparer`:

```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```

**Зачем использовать операторы `using`?** Они автоматически освобождают ресурсы, предотвращая утечки памяти при обработке больших документов. Поверьте, вы будете благодарны себе позже, когда будете работать с Word‑файлами размером 50 МБ.

#### Шаг 2: Добавить целевой документ

Метод `Add` регистрирует целевой документ, изменения которого будут сравниваться с исходным.  
Укажите обновлённый файл, который хотите сравнить:

```csharp
comparer.Add(targetFilePath);
```

**Распространённая ошибка**: путать исходный и целевой документы. Думайте так — source — это ваш “оригинал”, target — ваша “обновлённая версия”.

#### Шаг 3: Установить тип метаданных (здесь происходит магия)

Свойство `CloneMetadataType` определяет, чьи метаданные копируются в результат.  
Скажите сравнивателю сохранить метаданные целевого документа:

```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```

**Что происходит?** `CloneMetadataType = MetadataType.Target` сообщает GroupDocs.Comparison: “Эй, я хочу сохранить метаданные целевого документа в окончательном результате.”

### Полный рабочий пример

Вот всё вместе в исполняемой программе:

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;

class Program
{
    static void Main(string[] args)
    {
        try
        {
            string sourceFile = "original_document.docx";
            string targetFile = "updated_document.docx";
            string outputFile = "comparison_result.docx";
            
            using (Comparer comparer = new Comparer(sourceFile))
            {
                comparer.Add(targetFile);
                
                // Preserve target document metadata
                comparer.Compare(outputFile, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
                
                Console.WriteLine($"Comparison completed! Check {outputFile}");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error during comparison: {ex.Message}");
        }
    }
}
```

### Распространённые подводные камни, которых следует избегать

**Проблемы с путями к файлам** — всегда используйте полные пути или убедитесь, что файлы находятся в рабочем каталоге:

```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```

**Управление памятью** — для больших документов всегда оборачивайте объекты `Comparer` в операторы `using`.

**Совместимость версий** — разные выпуски GroupDocs.Comparison предоставляют разные возможности работы с метаданными — используйте 25.4.0 или новее для наилучших результатов.

## Продвинутые сценарии работы с метаданными

### Когда использовать метаданные **Target** vs. **Source**

| Сценарий | Предпочтительно **Target** метаданные | Предпочтительно **Source** метаданные |
|----------|----------------------------------------|----------------------------------------|
| Требуется обновлённая информация об авторе | ✅ | ❌ |
| Оригинальный документ имеет юридическую приоритетность | ❌ | ✅ |
| Пользовательские свойства добавлены только в новом файле | ✅ | ❌ |
| Нужно сохранить историю “главного” документа | ❌ | ✅ |

### Работа с несколькими целевыми документами

Вы можете сравнивать несколько целевых файлов, при этом сохранять метаданные из первого добавленного целевого документа:

```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    comparer.Add(targetFilePath1);
    comparer.Add(targetFilePath2);
    comparer.Add(targetFilePath3);
    
    // Metadata will come from the first target document
    comparer.Compare(outputFileName, new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target 
    });
}
```

## Практические применения и примеры использования

### Управление юридическими документами
Юридические фирмы часто нуждаются в сравнении версий контрактов, сохраняя определённые метки метаданных:

```csharp
// Preserve client metadata from updated contract
using (Comparer comparer = new Comparer("original_contract.docx"))
{
    comparer.Add("client_revised_contract.docx");
    
    comparer.Compare("final_contract_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Keep client's metadata
    });
}
```

### Академическое и исследовательское сотрудничество
Когда несколько исследователей работают совместно, нужно сохранять самую свежую информацию об авторе:

```csharp
// Keep metadata from the researcher's latest submission
using (Comparer comparer = new Comparer("draft_paper.docx"))
{
    comparer.Add("researcher_updates.docx");
    
    comparer.Compare("paper_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Preserve researcher metadata
    });
}
```

### Корпоративные процессы соответствия
В регулируемых отраслях поддержание метаданных соответствия критически важно:

```csharp
// Preserve compliance tags from updated policy document
using (Comparer comparer = new Comparer("old_policy.docx"))
{
    comparer.Add("compliance_approved_policy.docx");
    
    comparer.Compare("policy_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Keep compliance metadata
    });
}
```

## Устранение распространённых проблем

### Ошибки “File Not Found”

Самая распространённая проблема. Отладьте с явными проверками:

```csharp
string sourceFile = "source.docx";

// Always check if files exist before comparison
if (!File.Exists(sourceFile))
{
    Console.WriteLine($"Source file not found: {Path.GetFullPath(sourceFile)}");
    return;
}

// Same for target files
if (!File.Exists(targetFile))
{
    Console.WriteLine($"Target file not found: {Path.GetFullPath(targetFile)}");
    return;
}
```

### Проблемы с памятью при больших документах

Для документов более 10 МБ рассмотрите следующие оптимизации:

```csharp
// Use explicit disposal for large documents
using (var comparer = new Comparer(sourceFile))
{
    comparer.Add(targetFile);
    
    var saveOptions = new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target 
    };
    
    comparer.Compare(outputFile, saveOptions);
    
    // Explicitly clean up
    GC.Collect();
    GC.WaitForPendingFinalizers();
}
```

### Проблемы с разрешениями и доступом

При работе с защищёнными файлами или сетевыми ресурсами:

```csharp
try
{
    using (var comparer = new Comparer(sourceFile))
    {
        comparer.Add(targetFile);
        comparer.Compare(outputFile, new SaveOptions() 
        { 
            CloneMetadataType = MetadataType.Target 
        });
    }
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine("Access denied. Check file permissions.");
    Console.WriteLine($"Details: {ex.Message}");
}
catch (IOException ex)
{
    Console.WriteLine("File I/O error occurred.");
    Console.WriteLine($"Details: {ex.Message}");
}
```

## Соображения по производительности и лучшие практики

### Управление памятью

GroupDocs.Comparison может быть ресурсоёмким. Используйте операторы `using` для гарантированного освобождения:

```csharp
// Good - automatic resource cleanup
using (var comparer = new Comparer(sourceFile))
{
    // comparison logic here
}

// Bad - potential memory leaks
var comparer = new Comparer(sourceFile);
// ... comparison logic
// comparer.Dispose(); // Easy to forget!
```

**Обрабатывайте документы пакетами** — если вы сравниваете много файлов, обрабатывайте их небольшими группами, чтобы снизить использование памяти.

### Асинхронные операции для лучшей отзывчивости

Для настольных или веб‑приложений оберните сравнение в асинхронный метод:

```csharp
public async Task<bool> CompareDocumentsAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            using (var comparer = new Comparer(source))
            {
                comparer.Add(target);
                comparer.Compare(output, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
                return true;
            }
        }
        catch
        {
            return false;
        }
    });
}
```

### Рекомендации по размеру файлов

- **Маленькие (< 1 МБ)** — обрабатывать напрямую.  
- **Средние (1‑10 МБ)** — показывать прогресс, чтобы UI оставался отзывчивым.  
- **Большие (> 10 МБ)** — всегда использовать асинхронную обработку и рассматривать явный вызов GC, как показано выше.

## Интеграция с более крупными системами

### Интеграция с ASP.NET Core

Ниже готовый контроллер, который принимает два загруженных файла, запускает сравнение и возвращает результат, **сохраняя метаданные целевого документа**:

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentComparisonController : ControllerBase
{
    [HttpPost("compare-with-target-metadata")]
    public async Task<IActionResult> CompareWithTargetMetadata(
        IFormFile sourceFile, 
        IFormFile targetFile)
    {
        var tempSource = Path.GetTempFileName();
        var tempTarget = Path.GetTempFileName();
        var outputPath = Path.GetTempFileName();
        
        try
        {
            // Save uploaded files temporarily
            await sourceFile.CopyToAsync(new FileStream(tempSource, FileMode.Create));
            await targetFile.CopyToAsync(new FileStream(tempTarget, FileMode.Create));
            
            // Perform comparison with target metadata preservation
            using (var comparer = new Comparer(tempSource))
            {
                comparer.Add(tempTarget);
                comparer.Compare(outputPath, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
            }
            
            // Return comparison result
            var resultBytes = await System.IO.File.ReadAllBytesAsync(outputPath);
            return File(resultBytes, "application/vnd.openxmlformats-officedocument.wordprocessingml.document", 
                       "comparison_result.docx");
        }
        finally
        {
            // Clean up temporary files
            if (System.IO.File.Exists(tempSource)) System.IO.File.Delete(tempSource);
            if (System.IO.File.Exists(tempTarget)) System.IO.File.Delete(tempTarget);
            if (System.IO.File.Exists(outputPath)) System.IO.File.Delete(outputPath);
        }
    }
}
```

## Часто задаваемые вопросы

**В: Можно ли сохранять метаданные из нескольких целевых документов при сравнении?**  
О: При добавлении нескольких целевых файлов GroupDocs.Comparison использует метаданные **первого** добавленного целевого документа. Добавьте документ, метаданные которого нужно сохранить, первым в цепочке.

**В: Что происходит, если у целевого документа отсутствуют некоторые поля метаданных?**  
О: Будут скопированы только те метаданные, которые присутствуют в целевом документе. Отсутствующие поля просто игнорируются; сравнение всё равно завершится успешно.

**В: Как работать с документами, защищёнными паролем?**  
О: Используйте объект `LoadOptions` с паролем, затем передайте его в конструктор `Comparer`:

```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```

**В: Есть ли способ сохранять только выбранные свойства метаданных?**  
О: Текущий API сохраняет **все** метаданные из выбранного источника (Target или Source). Для более точного контроля необходимо извлечь свойства после сравнения и применить их вручную.

**В: Какие форматы документов поддерживают сохранение метаданных?**  
О: Большинство распространённых бизнес‑форматов — DOCX, PDF, PPTX, XLSX и многие другие — поддерживают сохранение метаданных. Смотрите официальную документацию для полного списка.

**В: Где можно получить помощь, если возникнут проблемы?**  
О: Посетите [форум поддержки GroupDocs](https://forum.groupdocs.com/c/comparison) для помощи от сообщества, либо свяжитесь напрямую со службой поддержки GroupDocs, если у вас коммерческая лицензия.

## Дополнительные ресурсы

- **Официальная документация**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **Ссылка на API**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **Скачать последнюю версию**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **Бесплатная пробная версия**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **Варианты покупки**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)

**Последнее обновление:** 2026-06-05  
**Тестировано с:** GroupDocs.Comparison 25.4.0 for .NET  
**Автор:** GroupDocs  

## Связанные учебники

- [Метаданные документа .NET - Сохранить и сохранить пользовательские свойства](/comparison/net/loading-and-saving-documents/saving-user-defined-document-metadata/)
- [Управление метаданными документа .NET - Полное руководство по GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Получить свойства документа C# .NET - Извлечь метаданные файла](/comparison/net/basic-usage/get-document-info-from-path/)