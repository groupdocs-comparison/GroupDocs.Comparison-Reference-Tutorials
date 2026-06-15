---
categories:
- Document Comparison
date: '2026-06-15'
description: Узнайте, как извлечь метаданные из результатов сравнения .NET с помощью
  GroupDocs.Comparison. Пошаговое руководство с примерами кода и практическими советами.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: Извлечение информации о документе из результатов сравнения
schemas:
- author: GroupDocs
  dateModified: '2026-06-15'
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  headline: How to Extract Metadata from .NET Comparison Results – Complete Guide
  type: TechArticle
- description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  name: How to Extract Metadata from .NET Comparison Results – Complete Guide
  steps:
  - name: Initialize Comparer with Source Document
    text: '`Comparer` is the core class in GroupDocs.Comparison that loads the source
      document and orchestrates comparison operations. Using a `using` block guarantees
      that all unmanaged resources are released automatically. > **Pro Tip:** You
      can pass any `Stream` (file, memory, cloud) to the `Comparer` const'
  - name: Add Target Document for Comparison
    text: The `Add()` method accepts additional streams or file paths, enabling one‑to‑many
      comparisons. > **Important:** The order of added documents influences the way
      changes are highlighted in the final report.
  - name: Retrieve Document Info from Result Document
    text: '`IDocumentInfo` provides a unified view of document metadata such as file
      type, page count, and size across all supported formats. > **Understanding the
      Data:** The returned object works the same for DOCX, PDF, XLSX, and PPTX, so
      you can write format‑agnostic code.'
  - name: Display Document Info
    text: 'Once you have the `IDocumentInfo` instance, you can log, store, or present
      its properties. The three most commonly used properties are: - **FileType**
      – e.g., `DOCX`, `PDF`, `XLSX`. - **PageCount** – total pages or slides. - **Size**
      – file size in bytes (useful for storage calculations).'
  type: HowTo
- questions:
  - answer: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT,
      and many others, providing consistent metadata extraction across them.
    question: Is GroupDocs.Comparison for .NET compatible with various document formats?
  - answer: Absolutely. Settings such as sensitivity, change types, and output format
      are independent of the `GetDocumentInfo()` call.
    question: Can I customize comparison settings without affecting metadata extraction?
  - answer: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/).
      The trial includes full metadata extraction capabilities.
    question: Is there a trial version I can use for evaluation?
  - answer: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12)
      for community help and official support from the GroupDocs team.
    question: Where can I get support for implementation questions?
  - answer: GroupDocs offers developer, site, and OEM licenses. Purchase options are
      listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).
    question: What licensing options are available for production deployments?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- groupdocs-comparison
- document-metadata
- dotnet-api
- document-properties
title: Как извлечь метаданные из результатов сравнения .NET – Полное руководство
type: docs
url: /ru/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# Как извлечь метаданные из результатов сравнения .NET – Полное руководство

Когда вы работаете со сравнением документов в приложениях .NET, вы можете задаться вопросом **как извлечь метаданные** из результатов сравнения. Метаданные, такие как тип файла, количество страниц и размер документа, могут быть критически важными для аудита, оптимизации производительности или просто для отображения полезной информации конечным пользователям. Это руководство покажет, как эффективно получать эти данные с помощью GroupDocs.Comparison для .NET.

## Быстрые ответы
- **Какой основной класс для сравнения?** `Comparer` загружает исходный документ и запускает движок сравнения.  
- **Какой метод возвращает метаданные?** `GetDocumentInfo()` у целевого документа возвращает объект `IDocumentInfo`.  
- **Могу ли я получить размер документа в .NET?** Да — свойство `Size` у `IDocumentInfo` возвращает размер в байтах.  
- **Нужна ли лицензия для извлечения метаданных?** Для использования в продакшн требуется действующая лицензия GroupDocs.Comparison; бесплатная пробная версия поддерживает все функции работы с метаданными.  
- **Совместим ли API с .NET 6?** Абсолютно — GroupDocs.Comparison поддерживает .NET Framework 4.6.1+, .NET Core 2.0+, и .NET 5/6+.

Метод `GetDocumentInfo()` возвращает объект `IDocumentInfo`, содержащий метаданные документа.

## Что такое извлечение метаданных при сравнении документов?
Извлечение метаданных — это процесс получения описательной информации, такой как тип файла, количество страниц и размер файла, из документов, участвующих в операции сравнения. GroupDocs.Comparison предоставляет эти данные через единый API, что упрощает их логирование, отображение или использование в условной обработке.

## Зачем извлекать метаданные из результатов сравнения?
Извлечение метаданных позволяет создавать подробные журналы аудита, маршрутизировать файлы в зависимости от их типа и корректировать стратегии обработки больших документов. Зная тип файла, количество страниц и размер, вы можете обеспечивать соблюдение нормативных требований, оценивать время обработки и предоставлять пользователям ясную информацию перед началом сравнения.

## Предварительные требования

1. **GroupDocs.Comparison for .NET** – Установите библиотеку со [official releases page](https://releases.groupdocs.com/comparison/net/).  
   Вы также можете просмотреть все релизы на [GroupDocs releases page](https://releases.groupdocs.com/).  
2. **Development Environment** – Visual Studio, VS Code или любой IDE, поддерживающий .NET 6+.  
3. **Sample Documents** – Два файла (например, `SOURCE.docx` и `TARGET.docx`) для тестирования. API работает более чем с **50 документными форматами**.

## Импорт пространств имён

Следующие директивы `using` дают доступ к ядру движка сравнения, утилитам работы с файлами и интерфейсам метаданных.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

Эти импорты необходимы перед созданием любых объектов GroupDocs.

## Как извлечь метаданные из результатов сравнения?

Класс `Comparer` загружает исходный документ и управляет процессом сравнения.

Чтобы получить метаданные, сначала загрузите исходный документ с помощью экземпляра `Comparer`, затем добавьте целевой(ые) документ(ы). После инициализации движка сравнения вызовите `GetDocumentInfo()` для каждого целевого документа, чтобы получить объект `IDocumentInfo`, содержащий свойства типа файла, количество страниц и размер. Такой подход работает одинаково для всех поддерживаемых форматов.

### Шаг 1: Инициализировать Comparer с исходным документом

`Comparer` — основной класс в GroupDocs.Comparison, который загружает исходный документ и управляет операциями сравнения. Использование блока `using` гарантирует автоматическое освобождение всех неуправляемых ресурсов.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Pro Tip:** Вы можете передать любой `Stream` (файл, память, облако) в конструктор `Comparer`, а не только путь к файлу.

### Шаг 2: Добавить целевой документ для сравнения

Метод `Add()` принимает дополнительные потоки или пути к файлам, позволяя выполнять сравнение один‑ко‑многим.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Important:** Порядок добавленных документов влияет на способ выделения изменений в окончательном отчёте.

### Шаг 3: Получить информацию о документе из результирующего документа

`IDocumentInfo` предоставляет единый вид метаданных документа, таких как тип файла, количество страниц и размер, для всех поддерживаемых форматов.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Understanding the Data:** Возвращаемый объект работает одинаково для DOCX, PDF, XLSX и PPTX, поэтому вы можете писать код, не зависящий от формата.

### Шаг 4: Отобразить информацию о документе

После получения экземпляра `IDocumentInfo` вы можете вести журнал, сохранять или отображать его свойства.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

Три наиболее часто используемых свойства:

- **FileType** – например, `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – общее количество страниц или слайдов.  
- **Size** – размер файла в байтах (полезно для расчётов хранилища).

## Как получить размер документа в .NET?

Свойство `Size` возвращает размер файла в байтах.

Размер документа можно получить напрямую из экземпляра `IDocumentInfo` через его свойство `Size`. Это свойство возвращает точное количество байтов оригинального файла, позволяя конвертировать его в килобайты или мегабайты для отображения или расчётов хранилища. Оно отражает размер исходного файла, а не обработанной версии.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Note:** Значение `Size` отражает оригинальный размер файла, а не размер после внутренней обработки или сжатия.

## Распространённые сценарии использования и практические применения

- **Batch Processing:** Используйте тип файла для маршрутизации DOCX в воркфлоу, специфичный для Word, а PDF — в оптимизированный PDF‑конвейер.  
- **Storage Management:** Автоматически архивируйте документы размером более 10 МБ в холодное хранилище.  
- **User Feedback:** Показывайте количество страниц и размер перед сравнением, чтобы установить реалистичные ожидания по времени обработки.  
- **Quality Assurance:** Проверяйте полноту загруженных файлов, сравнивая ожидаемое и фактическое количество страниц.

## Устранение распространённых проблем

- **File Access Errors:** Проверьте права чтения и используйте абсолютные пути во время разработки.  
- **Memory Pressure with Large Files:** Предпочитайте потоковую передачу (`File.OpenRead`) вместо загрузки всего файла в память.  
- **Null Reference Exceptions:** `FirstOrDefault()` может вернуть `null`, если не был добавлен целевой документ; всегда проверяйте перед вызовом `GetDocumentInfo()`.  

```csharp
var target = comparer.Targets.FirstOrDefault();
if (target != null)
{
    var info = target.GetDocumentInfo();
    // Use info safely
}
else
{
    Console.WriteLine("No target document was added.");
}
```

- **Limited Metadata for Plain Text:** Форматы вроде `.txt` могут не предоставлять значимого `PageCount`. Защищайте код от отсутствующих значений.

## Соображения по производительности

- **Stream Management:** Всегда оборачивайте потоки в конструкции `using`, чтобы своевременно освобождать файловые дескрипторы.  
- **Caching:** Сохраняйте часто запрашиваемые метаданные в кэше, чтобы избежать повторного извлечения.  
- **Batch Operations:** Обрабатывайте документы группами, чтобы снизить накладные расходы и повысить пропускную способность.

## Лучшие практики для продакшн использования

- **Robust Error Handling:** Оборачивайте извлечение метаданных в блоки try‑catch для корректной обработки повреждённых или неподдерживаемых файлов.  
- **Comprehensive Logging:** Записывайте тип документа, размер и количество страниц для каждого сравнения, чтобы облегчить отладку и обеспечить соответствие требованиям аудита.  
- **Security Hygiene:** Не раскрывайте полные пути к файлам или внутренние детали сервера в пользовательских сообщениях.  
- **Resource Disposal:** Своевременно освобождайте экземпляры `Comparer`, особенно в веб‑службах с большим количеством одновременных запросов.

## Расширенные сценарии

### Несколько целевых документов

Если вы сравниваете один источник с несколькими целями, пройдитесь по коллекции `Targets` и извлеките метаданные из каждой.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Условная обработка на основе метаданных

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Сохранение метаданных в базе данных

Сохраняйте `FileType`, `PageCount` и `Size` в реляционной таблице, чтобы обеспечить отчётность и аналитику по тысячам сравнений.

## Часто задаваемые вопросы

**Q: Is GroupDocs.Comparison for .NET compatible with various document formats?**  
A: Да, поддерживает **50+ форматов**, включая DOCX, PDF, PPTX, XLSX, TXT и многие другие, обеспечивая согласованное извлечение метаданных во всех из них.

**Q: Can I customize comparison settings without affecting metadata extraction?**  
A: Абсолютно. Настройки, такие как чувствительность, типы изменений и формат вывода, независимы от вызова `GetDocumentInfo()`.

**Q: Is there a trial version I can use for evaluation?**  
A: Да, скачайте бесплатную пробную версию со [GroupDocs releases page](https://releases.groupdocs.com/). Пробная версия включает полные возможности извлечения метаданных.

**Q: Where can I get support for implementation questions?**  
A: Используйте [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12) для получения помощи от сообщества и официальной поддержки команды GroupDocs.

**Q: What licensing options are available for production deployments?**  
A: GroupDocs предлагает лицензии для разработчиков, сайтов и OEM. Варианты покупки указаны на [GroupDocs purchase page](https://purchase.groupdocs.com/buy).

---

**Последнее обновление:** 2026-06-15  
**Тестировано с:** GroupDocs.Comparison 6.0 for .NET  
**Автор:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Связанные руководства

- [Document Metadata Management .NET - Complete Guide for GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Get Document Properties C# .NET - Extract File Metadata](/comparison/net/basic-usage/get-document-info-from-path/)
- [Preserve Target Metadata with GroupDocs.Comparison – .NET Tutorial](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)