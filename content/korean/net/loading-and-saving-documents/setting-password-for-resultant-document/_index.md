---
title: .NET용 GroupDocs 비교에서 결과 문서의 비밀번호 설정
linktitle: .NET용 GroupDocs 비교에서 결과 문서의 비밀번호 설정
second_title: GroupDocs.비교 .NET API
description: .NET용 GroupDocs 비교에서 결과 문서에 대한 암호를 설정하는 방법을 알아보세요. 보안을 강화하고 비교 파일을 보호하세요.
type: docs
weight: 17
url: /ko/net/loading-and-saving-documents/setting-password-for-resultant-document/
---
## 소개
이 자습서에서는 .NET용 GroupDocs 비교를 사용하여 결과 문서에 대한 암호를 설정하는 과정을 안내합니다. 이 기능은 비교 문서에 추가 보안 계층을 추가하여 승인된 개인만 해당 문서에 액세스할 수 있도록 보장합니다.
## 전제조건
계속하기 전에 다음 사항을 확인하세요.
1.  .NET용 GroupDocs 비교: .NET 환경에 GroupDocs 비교 라이브러리가 설치되어 있는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/comparison/net/).
2. 소스 및 대상 문서: 소스 문서 준비(`SOURCE.docx`) 및 대상 문서(`TARGET.docx`) 결과 문서를 비교하고 비밀번호를 설정하려는 경우.

## 네임스페이스 가져오기
먼저 GroupDocs 비교 기능을 사용하려면 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 1단계: 출력 디렉터리 및 파일 이름 정의
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
결과 문서를 저장할 디렉터리를 지정하고 출력 파일의 이름을 정의합니다.
## 2단계: 문서와 비밀번호 설정 비교
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    CompareOptions cOptions = new CompareOptions
    {
        PasswordSaveOption = PasswordSaveOption.User
    };
    SaveOptions sOptions = new SaveOptions()
    {
        Password = "YourPasswordHere"
    };
    comparer.Compare(outputFileName, sOptions, cOptions);
}
```
 여기서는`Comparer` 원본 문서와 개체. 그런 다음 비교할 대상 문서를 추가합니다. 우리는`PasswordSaveOption` 에게`User` 결과 문서에 비밀번호가 적용되도록 지정합니다. 원하는 비밀번호를 입력하세요.`Password` 의 재산`SaveOptions` 물체.
## 3단계: 성공 메시지 표시
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
마지막으로 문서가 성공적으로 비교되었으며 설정된 비밀번호를 가진 결과 문서가 지정된 디렉터리에 저장되었음을 나타내는 성공 메시지가 표시됩니다.

## 결론
.NET용 GroupDocs 비교에서 결과 문서에 대한 암호를 설정하면 비교된 문서에 추가 보안 계층이 추가되어 기밀성과 무결성이 보장됩니다. 이 자습서에 설명된 단계를 따르면 .NET 애플리케이션에서 이 기능을 쉽게 구현할 수 있습니다.
## FAQ
### 다양한 형식의 문서를 비교할 수 있나요?
예, .NET용 GroupDocs 비교는 DOCX, PDF, PPTX, XLSX 등과 같은 다양한 형식의 문서 비교를 지원합니다.
### 평가판을 사용할 수 있나요?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### 문제가 발생하면 어떻게 지원을 받을 수 있나요?
 GroupDocs 비교 커뮤니티 포럼에서 도움을 구할 수 있습니다.[여기](https://forum.groupdocs.com/c/comparison/12).
### .NET용 GroupDocs 비교를 사용하려면 라이센스가 필요합니까?
 예, 다음에서 라이센스를 구입할 수 있습니다.[여기](https://purchase.groupdocs.com/buy) 아니면 임시면허를 취득하세요.[여기](https://purchase.groupdocs.com/temporary-license/).
### .NET용 GroupDocs 비교에 사용할 수 있는 문서가 있습니까?
 예, 문서에 액세스할 수 있습니다[여기](https://reference.groupdocs.com/comparison/net/).