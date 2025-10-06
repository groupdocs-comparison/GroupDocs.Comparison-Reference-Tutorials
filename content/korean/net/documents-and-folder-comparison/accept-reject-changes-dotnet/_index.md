---
"description": "GroupDocs Comparison for .NET을 사용하여 문서의 변경 사항을 적용하고 거부하는 방법을 알아보세요. 문서 워크플로를 손쉽게 간소화하세요."
"linktitle": ".NET용 GroupDocs 비교에서 변경 사항 수락 및 거부"
"second_title": "GroupDocs.Comparison .NET API"
"title": ".NET용 GroupDocs 비교에서 변경 사항 수락 및 거부"
"url": "/ko/net/documents-and-folder-comparison/accept-reject-changes-dotnet/"
"weight": 10
type: docs
---
# .NET용 GroupDocs 비교에서 변경 사항 수락 및 거부

## 소개
문서 관리 및 협업 분야에서 파일의 정확성과 무결성을 보장하는 것은 매우 중요합니다. GroupDocs Comparison for .NET은 개발자가 문서 내 변경 사항을 손쉽게 수락하고 거부할 수 있도록 지원하는 강력한 솔루션으로, 워크플로를 간소화하고 생산성을 향상시킵니다. 이 튜토리얼에서는 GroupDocs Comparison for .NET을 사용하여 변경 사항을 수락하고 거부하는 과정을 단계별로 안내하며, 명확성과 구현 편의성을 위해 각 단계를 자세히 설명합니다.
## 필수 조건
튜토리얼을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
### 환경 설정
1. .NET SDK 설치: 아직 설치하지 않았다면 .NET 웹사이트에서 운영 체제에 적합한 .NET SDK를 다운로드하여 설치하세요.
2. .NET용 GroupDocs Comparison 설치: 제공된 .NET용 GroupDocs Comparison의 최신 버전을 가져옵니다. [다운로드 링크](https://releases.groupdocs.com/comparison/net/) 설치 지침을 따르세요.
3. C# 프로그래밍에 대한 익숙함: 이 튜토리얼은 C# 프로그래밍 언어와 그 구문에 대한 기본적인 이해가 있다고 가정합니다.

## 네임스페이스 가져오기
먼저, 필요한 네임스페이스를 프로젝트에 가져오세요. 이 네임스페이스를 통해 문서 비교 및 조작에 필요한 기능에 액세스할 수 있습니다.

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
교체를 확인하세요 `"Your Document Directory"` 원하는 출력 디렉토리 경로를 입력하세요.
## 2단계: 비교자 초기화 및 문서 비교
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
이 코드는 Comparer 객체를 소스 문서로 초기화하고, 비교를 위해 대상 문서를 추가합니다. 그런 다음 비교 프로세스를 실행합니다.
## 3단계: 변경 사항 검색 및 조작
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
비교에서 변경 사항을 검색하여 필요에 따라 조정합니다. 이 예에서는 변경 사항을 먼저 거부한 후 적용합니다. 결과 문서는 그에 따라 저장됩니다.

## 결론
결론적으로, GroupDocs Comparison for .NET은 문서 내 변경 사항을 승인하고 거부하는 완벽한 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 개발자는 이 기능을 애플리케이션에 효율적으로 통합하여 문서 정확성을 보장하고 협업을 향상시킬 수 있습니다.
## 자주 묻는 질문
### GroupDocs Comparison for .NET을 사용하면 서로 다른 형식의 문서를 비교할 수 있나요?
네, GroupDocs Comparison for .NET은 DOCX, PDF, PPTX 등 다양한 형식의 문서 비교를 지원합니다.
### GroupDocs Comparison for .NET은 .NET Core와 호환됩니까?
네, GroupDocs Comparison for .NET은 .NET Framework와 .NET Core 모두와 호환됩니다.
### 비교하는 문서에서 변경 사항이 표시되는 방식을 사용자 정의할 수 있나요?
물론입니다. GroupDocs Comparison for .NET은 색상, 스타일 등 변경 사항의 모양을 사용자 정의하기 위한 광범위한 옵션을 제공합니다.
### .NET용 GroupDocs Comparison은 여러 페이지 문서 비교를 지원합니까?
네, GroupDocs Comparison for .NET은 정밀하고 정확한 다중 페이지 문서 비교를 지원합니다.
### GroupDocs Comparison for .NET의 평가판이 있나요?
예, 제공된 .NET용 GroupDocs Comparison의 무료 평가판을 이용할 수 있습니다. [링크](https://releases.groupdocs.com/).