---
title: .NET용 GroupDocs 비교에서 변경 사항 승인 및 거부
linktitle: .NET용 GroupDocs 비교에서 변경 사항 승인 및 거부
second_title: GroupDocs.비교 .NET API
description: .NET용 GroupDocs 비교를 사용하여 문서의 변경 사항을 수락하고 거부하는 방법을 알아보세요. 문서 작업 흐름을 손쉽게 간소화하세요.
weight: 10
url: /ko/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---

# .NET용 GroupDocs 비교에서 변경 사항 승인 및 거부

## 소개
문서 관리 및 협업 영역에서는 파일의 정확성과 무결성을 보장하는 것이 무엇보다 중요합니다. .NET용 GroupDocs 비교는 개발자가 문서 내의 변경 사항을 쉽게 승인하고 거부할 수 있도록 지원하여 작업 흐름을 간소화하고 생산성을 향상시키는 강력한 솔루션으로 등장합니다. 이 자습서에서는 .NET용 GroupDocs 비교를 사용하여 변경 사항을 승인하고 거부하는 과정을 안내하고 명확성과 구현 용이성을 위해 각 단계를 세분화합니다.
## 전제조건
튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
### 환경설정
1. .NET SDK 설치: 아직 설치하지 않은 경우 .NET 웹사이트에서 운영 체제에 적합한 .NET SDK를 다운로드하여 설치하세요.
2.  .NET용 GroupDocs 비교 설치: 제공된 웹 사이트에서 최신 버전의 .NET용 GroupDocs 비교를 구합니다.[다운로드 링크](https://releases.groupdocs.com/comparison/net/) 설치 지침을 따르십시오.
3. C# 프로그래밍에 대한 지식: 이 자습서에서는 C# 프로그래밍 언어와 해당 구문에 대한 기본적인 이해가 있다고 가정합니다.

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 프로젝트로 가져옵니다. 이러한 네임스페이스는 문서 비교 및 조작에 필요한 기능에 대한 액세스를 제공합니다.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## 1단계: 출력 디렉터리 및 파일 이름 지정
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 반드시 교체하세요`"Your Document Directory"` 원하는 출력 디렉터리의 경로를 사용하세요.
## 2단계: 비교기 초기화 및 문서 비교
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
이 코드는 소스 문서로 Comparer 개체를 초기화하고 비교할 대상 문서를 추가합니다. 그런 다음 비교 프로세스를 실행합니다.
## 3단계: 변경 사항 검색 및 조작
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
비교에서 변경 사항을 검색하고 필요에 따라 조작합니다. 이 예에서는 변경 사항이 먼저 거부된 다음 승인됩니다. 결과 문서는 그에 따라 저장됩니다.

## 결론
결론적으로, .NET용 GroupDocs 비교는 문서 내의 변경 사항을 승인하고 거부하기 위한 완벽한 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 개발자는 이 기능을 애플리케이션에 효율적으로 통합하여 문서 정확성을 보장하고 협업을 강화할 수 있습니다.
## FAQ
### .NET용 GroupDocs 비교는 다양한 형식의 문서를 비교할 수 있습니까?
예, .NET용 GroupDocs 비교는 DOCX, PDF, PPTX 등과 같은 다양한 형식의 문서 간 비교를 지원합니다.
### .NET용 GroupDocs 비교는 .NET Core와 호환됩니까?
예, .NET용 GroupDocs 비교는 .NET Framework 및 .NET Core 모두와 호환됩니다.
### 비교된 문서의 변경 사항 모양을 사용자 정의할 수 있나요?
물론, .NET용 GroupDocs 비교는 색상, 스타일 등을 포함한 변경 사항의 모양을 사용자 정의하기 위한 광범위한 옵션을 제공합니다.
### .NET용 GroupDocs 비교는 여러 페이지 문서 비교를 지원합니까?
예, .NET용 GroupDocs 비교는 여러 페이지로 구성된 문서를 정밀하고 정확하게 비교할 수 있도록 지원합니다.
### .NET용 GroupDocs 비교에 사용할 수 있는 평가판이 있습니까?
 예, 제공된 GroupDocs Comparison for .NET의 무료 평가판을 이용할 수 있습니다.[링크](https://releases.groupdocs.com/).