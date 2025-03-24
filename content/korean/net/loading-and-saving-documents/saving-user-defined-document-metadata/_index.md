---
title: .NET용 GroupDocs 비교에서 사용자 정의 문서 메타데이터 저장
linktitle: .NET용 GroupDocs 비교에서 사용자 정의 문서 메타데이터 저장
second_title: GroupDocs.비교 .NET API
description: .NET용 GroupDocs 비교를 사용하여 사용자 정의 문서 메타데이터를 저장하는 방법을 알아보세요. 단계별 지침을 통해 메타데이터를 쉽게 비교하고 조작할 수 있습니다.
weight: 16
url: /ko/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## 소개
이 자습서에서는 .NET용 GroupDocs 비교를 사용하여 사용자 정의 문서 메타데이터를 저장하는 방법을 살펴보겠습니다. 메타데이터는 문서를 효율적으로 구성하고 관리하는 데 중요합니다. GroupDocs 비교를 사용하면 특정 요구 사항에 맞게 메타데이터를 쉽게 비교하고 조작할 수 있습니다.
## 전제조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET용 GroupDocs 비교: 다음에서 .NET용 GroupDocs 비교를 다운로드하고 설치하세요.[여기](https://releases.groupdocs.com/comparison/net/).
2. 개발 환경: 시스템에 Visual Studio와 같은 적합한 개발 환경이 설치되어 있는지 확인하십시오.
3. 소스 및 대상 문서: 메타데이터를 비교하고 조작하려는 소스 및 대상 문서를 준비합니다.

## 네임스페이스 가져오기
먼저, .NET용 GroupDocs 비교에서 제공하는 기능에 액세스하려면 필요한 네임스페이스를 가져옵니다.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 1단계: 출력 디렉터리 및 파일 이름 정의
비교된 문서를 저장할 디렉터리를 정의하고 출력 파일 이름을 지정합니다.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## 2단계: 비교기 초기화 및 문서 추가
 초기화`Comparer` 원본 문서와 개체를 비교하고 비교를 위해 대상 문서를 추가합니다.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## 3단계: 메타데이터 옵션 지정
 비교 문서에 저장할 메타데이터 옵션을 지정합니다. 이 예에서는 다음을 설정합니다.`CloneMetadataType` 에게`MetadataType.FileAuthor` 다음에 대한 세부정보를 제공합니다.`FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## 4단계: 문서 비교 및 메타데이터 저장
지정된 메타데이터 옵션을 사용하여 문서를 비교하고 비교된 문서를 저장합니다.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## 5단계: 성공 메시지 표시
문서가 성공적으로 비교되었음을 나타내는 성공 메시지와 출력 위치를 표시합니다.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## 결론
이 자습서에서는 .NET용 GroupDocs 비교를 사용하여 사용자 정의 문서 메타데이터를 저장하는 방법을 배웠습니다. 이러한 단계를 수행하면 요구 사항에 따라 메타데이터를 보존하고 조작하면서 문서를 효율적으로 비교할 수 있습니다.
## FAQ
### .NET용 GroupDocs 비교는 다양한 문서 형식을 처리할 수 있습니까?
예, GroupDocs 비교는 DOCX, PDF, PPTX, XLSX 등을 포함한 광범위한 문서 형식을 지원합니다.
### .NET용 GroupDocs 비교에 사용할 수 있는 무료 평가판이 있습니까?
 예, 무료 평가판에 액세스할 수 있습니다[여기](https://releases.groupdocs.com/).
### 필요에 따라 메타데이터 옵션을 사용자 정의할 수 있나요?
물론, GroupDocs 비교는 문서 비교 중에 메타데이터 처리를 사용자 정의할 수 있는 유연한 옵션을 제공합니다.
### GroupDocs 비교는 기술 지원을 제공합니까?
예, GroupDocs 비교 포럼에서 기술 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/comparison/12).
### .NET용 GroupDocs 비교 라이센스는 어디서 구입할 수 있나요?
 GroupDocs 웹사이트에서 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy).