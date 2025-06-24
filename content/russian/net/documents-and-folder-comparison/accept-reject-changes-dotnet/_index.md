---
"description": "Узнайте, как принимать и отклонять изменения в документах с помощью GroupDocs Comparison для .NET. Оптимизируйте свои рабочие процессы с документами без усилий."
"linktitle": "Принять и отклонить изменения в сравнении GroupDocs для .NET"
"second_title": "GroupDocs.Сравнение .NET API"
"title": "Принять и отклонить изменения в сравнении GroupDocs для .NET"
"url": "/ru/net/documents-and-folder-comparison/accept-reject-changes-dotnet/"
"weight": 10
---

# Принять и отклонить изменения в сравнении GroupDocs для .NET

## Введение
В сфере управления документами и совместной работы обеспечение точности и целостности файлов имеет первостепенное значение. GroupDocs Comparison для .NET выступает в качестве надежного решения, позволяющего разработчикам без усилий принимать и отклонять изменения в документах, тем самым оптимизируя рабочие процессы и повышая производительность. Это руководство проведет вас через процесс принятия и отклонения изменений с помощью GroupDocs Comparison для .NET, разбив каждый шаг для ясности и простоты реализации.
## Предпосылки
Прежде чем приступить к изучению руководства, убедитесь, что выполнены следующие предварительные условия:
### Настройка среды
1. Установите .NET SDK: если вы еще этого не сделали, загрузите и установите .NET SDK, подходящий для вашей операционной системы, с веб-сайта .NET.
2. Установите GroupDocs Comparison для .NET: получите последнюю версию GroupDocs Comparison для .NET из предоставленного [ссылка для скачивания](https://releases.groupdocs.com/comparison/net/) и следуйте инструкциям по установке.
3. Знакомство с программированием на C#: это руководство предполагает наличие базовых знаний языка программирования C# и его синтаксиса.

## Импорт пространств имен
Для начала импортируйте необходимые пространства имен в свой проект. Эти пространства имен предоставят доступ к функциональным возможностям, необходимым для сравнения и обработки документов.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Шаг 1: Укажите выходной каталог и имена файлов
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
Обязательно замените `"Your Document Directory"` с путем к желаемому выходному каталогу.
## Шаг 2: Инициализация компаратора и сравнение документов
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Этот код инициализирует объект Comparer с исходным документом и добавляет целевой документ для сравнения. Затем он выполняет процесс сравнения.
## Шаг 3: Извлечение и обработка изменений
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Извлеките изменения из сравнения и обработайте их по мере необходимости. В этом примере изменения сначала отклоняются, а затем принимаются. Полученные документы сохраняются соответствующим образом.

## Заключение
В заключение, GroupDocs Comparison for .NET предлагает бесшовное решение для принятия и отклонения изменений в документах. Следуя шагам, описанным в этом руководстве, разработчики могут эффективно интегрировать эту функциональность в свои приложения, обеспечивая точность документов и улучшая сотрудничество.
## Часто задаваемые вопросы
### Может ли GroupDocs Comparison for .NET сравнивать документы разных форматов?
Да, GroupDocs Comparison для .NET поддерживает сравнение документов различных форматов, таких как DOCX, PDF, PPTX и другие.
### Совместимо ли GroupDocs Comparison для .NET с .NET Core?
Да, GroupDocs Comparison для .NET совместим как с .NET Framework, так и с .NET Core.
### Могу ли я настроить внешний вид изменений в сравниваемых документах?
Безусловно, GroupDocs Comparison для .NET предоставляет обширные возможности для настройки внешнего вида изменений, включая цвет, стиль и многое другое.
### Поддерживает ли GroupDocs Comparison for .NET сравнение многостраничных документов?
Да, GroupDocs Comparison для .NET поддерживает точное и аккуратное сравнение многостраничных документов.
### Существует ли пробная версия GroupDocs Comparison для .NET?
Да, вы можете воспользоваться бесплатной пробной версией GroupDocs Comparison для .NET из предоставленного [связь](https://releases.groupdocs.com/).