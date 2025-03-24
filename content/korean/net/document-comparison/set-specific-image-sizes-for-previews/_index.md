---
title: 미리보기를 위한 특정 이미지 크기 설정
linktitle: 미리보기를 위한 특정 이미지 크기 설정
second_title: GroupDocs.비교 .NET API
description: .NET용 GroupDocs.Comparison을 사용하면 문서 비교 기능을 .NET 응용 프로그램에 손쉽게 통합할 수 있습니다.
weight: 14
url: /ko/net/document-comparison/set-specific-image-sizes-for-previews/
---

# 미리보기를 위한 특정 이미지 크기 설정

## 소개
소프트웨어 개발 영역에서는 정보의 무결성과 일관성을 보장하기 위해 효율적이고 정확한 문서 비교가 중요합니다. .NET용 GroupDocs.Comparison은 문서 비교 기능을 .NET 응용 프로그램에 원활하게 통합하려는 개발자에게 강력한 솔루션을 제공합니다.
## 전제조건
.NET용 GroupDocs.Comparison을 사용하여 문서 비교 구현을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
### 1. .NET용 GroupDocs.Comparison 설치
 시작하려면 개발 환경에 .NET용 GroupDocs.Comparison을 설치해야 합니다. 필요한 파일은 다음에서 다운로드할 수 있습니다.[다운로드 링크](https://releases.groupdocs.com/comparison/net/).
### 2. 개발 환경 설정
Visual Studio 또는 선호하는 .NET 개발 IDE를 포함하여 적합한 개발 환경이 구성되어 있는지 확인하세요.
### 3. .NET Framework에 대한 지식
.NET용 GroupDocs.Comparison을 효과적으로 활용하려면 .NET 프레임워크와 C# 프로그래밍 언어에 대한 기본적인 이해가 필수적입니다.

## 네임스페이스 가져오기
문서 비교 기능을 구현하기 전에 필요한 클래스와 메서드에 액세스하려면 필요한 네임스페이스를 가져와야 합니다.
```csharp
using System;
using System.IO;
```
## 1단계: 출력 디렉터리 및 파일 이름 설정
먼저 비교 문서가 저장될 출력 디렉터리와 파일 이름을 정의합니다.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```
## 2단계: 비교기 초기화
 인스턴스화`Comparer` 소스 문서 경로를 매개변수로 전달하여 객체를 생성합니다.
```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
```
## 3단계: 대상 문서 추가
원본 문서와 비교하려는 대상 문서를 추가합니다.
```csharp
comparer.Add("TARGET.pptx");
```
## 4단계: 비교 수행
 호출`Compare` 문서 비교를 수행하고 결과를 저장하는 방법입니다.
```csharp
comparer.Compare(File.Create(outputFileName));
```
## 5단계: 문서 미리보기 생성
육안 검사를 위해 비교된 문서의 미리보기를 생성합니다.
```csharp
Document document = new Document(File.OpenRead(outputFileName));
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2 };
previewOptions.Height = 1000;
previewOptions.Width = 1000;
document.GeneratePreview(previewOptions);
```
## 6단계: 출력 표시
생성된 문서 미리보기 경로와 함께 성공 메시지를 표시합니다.
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

## 결론
.NET용 GroupDocs.Comparison을 사용하면 문서 비교 기능을 .NET 응용 프로그램에 통합하는 것이 단순화됩니다. 설명된 단계를 따르면 개발자는 이 강력한 도구를 원활하게 통합하여 문서 관리 프로세스의 정확성과 일관성을 보장할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Comparison은 모든 문서 형식과 호환됩니까?
.NET용 GroupDocs.Comparison은 DOCX, PDF, PPTX, XLSX 등을 포함한 광범위한 문서 형식을 지원합니다.
### 내 요구 사항에 따라 비교 옵션을 사용자 정의할 수 있습니까?
예, .NET용 GroupDocs.Comparison은 특정 요구 사항에 따라 비교 프로세스를 사용자 정의할 수 있는 광범위한 옵션을 제공합니다.
### .NET용 GroupDocs.Comparison은 문서 버전 관리를 지원합니까?
.NET용 GroupDocs.Comparison은 주로 문서 비교에 중점을 두고 있지만 포괄적인 문서 관리 솔루션을 위해 버전 제어 시스템과 통합될 수 있습니다.
### .NET용 GroupDocs.Comparison에 대한 무료 평가판이 있습니까?
 예, 다음 사이트에서 .NET용 GroupDocs.Comparison 무료 평가판을 이용할 수 있습니다.[웹사이트](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Comparison에 대한 추가 지원은 어디서 찾을 수 있나요?
 전용을 탐색할 수 있습니다.[지원 포럼](https://forum.groupdocs.com/c/comparison/12) 도움을 구하고, 경험을 공유하고, 커뮤니티와 연결하기 위한 .NET용 GroupDocs.Comparison입니다.