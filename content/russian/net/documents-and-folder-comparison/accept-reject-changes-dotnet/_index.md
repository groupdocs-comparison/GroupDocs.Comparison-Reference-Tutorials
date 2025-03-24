---
title: Принять и отклонить изменения в сравнении GroupDocs для .NET
linktitle: Принять и отклонить изменения в сравнении GroupDocs для .NET
second_title: GroupDocs.Comparison .NET API
description: Узнайте, как принимать и отклонять изменения в документах с помощью GroupDocs Comparison for .NET. Оптимизируйте рабочие процессы с документами без особых усилий.
weight: 10
url: /ru/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---
## Введение
В сфере управления документами и совместной работы обеспечение точности и целостности файлов имеет первостепенное значение. GroupDocs Comparison для .NET представляет собой надежное решение, позволяющее разработчикам легко принимать и отклонять изменения в документах, тем самым оптимизируя рабочие процессы и повышая производительность. Это руководство проведет вас через процесс принятия и отклонения изменений с помощью GroupDocs Comparison для .NET, разбив каждый шаг для ясности и простоты реализации.
## Предварительные условия
Прежде чем приступить к изучению руководства, убедитесь, что у вас есть следующие предварительные условия:
### Настройка среды
1. Установите .NET SDK. Если вы еще этого не сделали, загрузите и установите .NET SDK, подходящий для вашей операционной системы, с веб-сайта .NET.
2.  Установите GroupDocs Comparison для .NET. Получите последнюю версию GroupDocs Comparison для .NET из предоставленного файла.[ссылка для скачивания](https://releases.groupdocs.com/comparison/net/) и следуйте инструкциям по установке.
3. Знакомство с программированием на C#. В этом руководстве предполагается базовое понимание языка программирования C# и его синтаксиса.

## Импортировать пространства имен
Для начала импортируйте необходимые пространства имен в свой проект. Эти пространства имен обеспечат доступ к функциям, необходимым для сравнения документов и манипулирования ими.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Шаг 1. Укажите выходной каталог и имена файлов
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 Обязательно замените`"Your Document Directory"` с путем к желаемому выходному каталогу.
## Шаг 2. Инициализируйте средство сравнения и сравните документы
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Этот код инициализирует объект Comparer с исходным документом и добавляет целевой документ для сравнения. Затем он выполняет процесс сравнения.
## Шаг 3. Извлечение изменений и управление ими
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Извлеките изменения из сравнения и манипулируйте ими по мере необходимости. В этом примере изменения сначала отклоняются, а затем принимаются. Полученные документы соответствующим образом сохраняются.

## Заключение
В заключение, GroupDocs Comparison для .NET предлагает простое решение для принятия и отклонения изменений в документах. Следуя шагам, описанным в этом руководстве, разработчики могут эффективно интегрировать эту функцию в свои приложения, обеспечивая точность документов и улучшая совместную работу.
## Часто задаваемые вопросы
### Может ли GroupDocs Comparison для .NET сравнивать документы разных форматов?
Да, GroupDocs Comparison для .NET поддерживает сравнение документов различных форматов, таких как DOCX, PDF, PPTX и других.
### Совместимо ли сравнение GroupDocs для .NET с .NET Core?
Да, сравнение GroupDocs для .NET совместимо как с .NET Framework, так и с .NET Core.
### Можно ли настроить внешний вид изменений в сравниваемых документах?
Конечно, GroupDocs Comparison для .NET предоставляет широкие возможности для настройки внешнего вида изменений, включая цвет, стиль и многое другое.
### Поддерживает ли GroupDocs Comparison для .NET сравнение многостраничных документов?
Да, GroupDocs Comparison для .NET поддерживает точное и достоверное сравнение многостраничных документов.
### Доступна ли пробная версия для сравнения GroupDocs для .NET?
 Да, вы можете воспользоваться бесплатной пробной версией GroupDocs Comparison для .NET из предоставленного[связь](https://releases.groupdocs.com/).