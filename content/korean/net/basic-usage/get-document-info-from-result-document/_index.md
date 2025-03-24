---
title: 결과 문서에서 문서 정보 가져오기 - .NET용 GroupDocs.Comparison
linktitle: 결과 문서에서 문서 정보 가져오기 - .NET용 GroupDocs.Comparison
second_title: GroupDocs.비교 .NET API
description: .NET용 GroupDocs.Comparison을 사용하여 결과 문서에서 문서 정보를 검색하는 방법을 알아보세요. .NET 개발자를 위해 설명된 쉬운 단계입니다.
weight: 12
url: /ko/net/basic-usage/get-document-info-from-result-document/
---
## 소개
.NET 개발 영역에서는 문서 관리 및 비교가 일반적인 요구 사항입니다. .NET용 GroupDocs.Comparison은 이 작업을 위한 강력한 솔루션을 제공하므로 개발자는 문서 비교 기능을 응용 프로그램에 원활하게 통합할 수 있습니다. 이 자습서에서는 .NET용 GroupDocs.Comparison을 활용하여 결과 문서에서 문서 정보를 검색하는 과정을 안내합니다. 
## 전제조건
이 튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. .NET용 GroupDocs.Comparison: .NET용 GroupDocs.Comparison 라이브러리를 설치합니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/comparison/net/).
2. 개발 환경: IDE(예: Visual Studio) 및 필요한 구성을 포함하여 .NET 개발 환경을 설정합니다.
3.  문서 파일: 소스 및 대상 문서 파일을 준비합니다(예:`SOURCE.docx` 그리고`TARGET.docx`) 비교하려고.

## 네임스페이스 가져오기
먼저, GroupDocs.Comparison 기능에 액세스하려면 필요한 네임스페이스를 가져와야 합니다.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

## 1단계: 소스 문서로 비교기 초기화
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```
 이 단계에서는`Comparer` 원본 문서가 포함된 개체(`SOURCE.docx` 이 경우)`using` 적절한 자원 폐기를 보장하기 위한 성명입니다.
## 2단계: 비교할 대상 문서 추가
```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```
여기에 대상 문서(`TARGET.docx`) 비교를 위해 비교자 개체에 연결합니다.
## 3단계: 결과 문서에서 문서 정보 검색
```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```
 이 단계에서는 결과 문서에서 문서 정보를 검색합니다. 다음을 사용하여 대상 문서에 액세스합니다.`FirstOrDefault()` 그런 다음 전화`GetDocumentInfo()`파일 형식, 페이지 수, 문서 크기 등의 정보를 얻으려면
## 4단계: 문서 정보 표시
```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```
여기에서는 파일 형식, 페이지 수, 문서 크기(바이트)를 포함하여 검색된 문서 정보를 표시합니다.

## 결론
.NET용 GroupDocs.Comparison은 .NET 응용 프로그램의 문서 비교 프로세스를 단순화합니다. 이 자습서를 따라 .NET용 GroupDocs.Comparison을 사용하여 결과 문서에서 문서 정보를 검색하는 방법을 배웠습니다. 문서 관리 기능을 향상하려면 이러한 기술을 프로젝트에 통합하십시오.
## FAQ
### .NET용 GroupDocs.Comparison은 다양한 문서 형식과 호환됩니까?
예, .NET용 GroupDocs.Comparison은 DOCX, PDF, PPTX, XLSX 등을 포함한 광범위한 문서 형식을 지원합니다.
### 문서 비교 설정을 사용자 정의할 수 있나요?
물론, .NET용 GroupDocs.Comparison은 특정 요구 사항에 맞게 문서 비교를 위한 광범위한 사용자 정의 옵션을 제공합니다.
### 평가할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Comparison에 대한 지원을 받으려면 어떻게 해야 합니까?
 GroupDocs.Comparison 포럼에서 도움을 구하고 커뮤니티에 참여할 수 있습니다.[여기](https://forum.groupdocs.com/c/comparison/12).
### .NET용 GroupDocs.Comparison의 라이센스 옵션은 무엇입니까?
 라이선스 옵션을 살펴보고 다음에서 라이선스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy).