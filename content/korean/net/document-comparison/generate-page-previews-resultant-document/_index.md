---
title: 결과 문서에 대한 페이지 미리보기 생성
linktitle: 결과 문서에 대한 페이지 미리보기 생성
second_title: GroupDocs.비교 .NET API
description: .NET용 GroupDocs.Comparison을 사용하여 문서 미리보기를 생성하는 방법을 알아보세요. 문서를 효율적이고 정확하게 비교하세요.
weight: 10
url: /ko/net/document-comparison/generate-page-previews-resultant-document/
---

# 결과 문서에 대한 페이지 미리보기 생성

## 소개
소프트웨어 개발 세계에서는 문서를 효율적이고 정확하게 비교하는 것이 가장 중요합니다. 팀 구성원 간의 협업이 포함된 프로젝트에서 작업하든 법률 문서를 처리하든 관계없이 버전을 효과적으로 비교할 수 있으면 시간을 절약하고 정확성을 보장할 수 있습니다. .NET용 GroupDocs.Comparison은 .NET 개발자를 위한 문서 비교 프로세스를 간소화하도록 설계된 강력한 도구입니다. 이 자습서에서는 .NET용 GroupDocs.Comparison을 사용하여 결과 문서에 대한 페이지 미리 보기를 생성하는 방법을 자세히 살펴보겠습니다. 프로세스를 포괄적으로 이해할 수 있도록 각 단계를 자세히 살펴보겠습니다.
## 전제조건
시작하기 전에 갖춰야 할 몇 가지 전제 조건이 있습니다.
1.  .NET용 GroupDocs.Comparison: .NET용 GroupDocs.Comparison을 설치했는지 확인하십시오. 그렇지 않은 경우 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/comparison/net/).
2. .NET의 기본 이해: .NET 프레임워크 및 C# 프로그래밍 언어에 익숙하면 이 자습서를 따라가는 데 도움이 됩니다.
3. 문서 파일: 비교하려는 소스 및 대상 문서 파일이 필요합니다. 준비가 되어 있는지 확인하세요.
4. 개발 환경: Visual Studio 또는 .NET 개발을 위해 선호하는 기타 IDE를 사용하여 개발 환경을 설정합니다.

## 네임스페이스 가져오기
먼저, .NET용 GroupDocs.Comparison 기능을 활용하려면 필요한 네임스페이스를 가져와야 합니다.
## 1단계: 네임스페이스 가져오기
```csharp
using System;
using System.IO;
```
이제 제공된 예제를 여러 단계로 나누어 각 부분을 철저하게 이해해 보겠습니다.
### 1단계: 출력 디렉터리 및 파일 이름 설정
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
이 단계에서는 결과 문서가 저장될 출력 디렉터리를 정의하고 결과 파일의 이름을 지정합니다.
## 2단계: 비교기 초기화 및 문서 추가
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
 여기서는`Comparer` 소스 문서의 경로를 제공하여 객체를 생성합니다. 그런 다음 원본 문서와 비교하려는 대상 문서를 추가합니다.
## 3단계: 문서 비교 및 출력 생성
```csharp
    comparer.Compare(File.Create(outputFileName));
```
이 단계에서는 원본 문서와 대상 문서를 비교하고 비교 결과를 바탕으로 결과 문서를 생성합니다. 출력 파일은 지정된 위치에 생성됩니다.
## 4단계: 페이지 미리보기 생성
```csharp
    Document document = new Document(File.OpenRead(outputFileName));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    document.GeneratePreview(previewOptions);
}
```
이 마지막 단계에서는 결과 문서에 대한 페이지 미리보기를 생성합니다. 미리보기 형식(이 경우 PNG)과 미리보기를 생성할 페이지 번호를 지정합니다.

## 결론
.NET용 GroupDocs.Comparison은 문서를 비교하고 페이지 미리 보기를 생성하는 편리하고 효율적인 방법을 제공합니다. 이 자습서에 설명된 단계를 따르면 문서 비교 기능을 .NET 애플리케이션에 원활하게 통합하여 생산성과 정확성을 높일 수 있습니다.
## FAQ
### .NET용 GroupDocs.Comparison을 사용하여 다양한 형식의 문서를 비교할 수 있습니까?
예, .NET용 GroupDocs.Comparison은 DOCX, PDF, PPTX 등과 같은 다양한 형식의 문서 비교를 지원합니다.
### .NET용 GroupDocs.Comparison에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Comparison의 비교 옵션을 사용자 정의할 수 있습니까?
물론 .NET용 GroupDocs.Comparison은 요구 사항에 따라 비교 프로세스를 사용자 정의할 수 있는 다양한 옵션을 제공합니다.
### .NET용 GroupDocs.Comparison은 클라우드 통합을 지원합니까?
예, .NET용 GroupDocs.Comparison은 클라우드 플랫폼과의 원활한 통합을 위한 클라우드 API를 제공합니다.
### .NET용 GroupDocs.Comparison에 대한 지원은 어디서 받을 수 있나요?
 GroupDocs 커뮤니티 포럼에서 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/comparison/12).