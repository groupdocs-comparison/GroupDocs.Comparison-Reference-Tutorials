---
title: 계량 라이센스 설정 - .NET용 GroupDocs 비교
linktitle: 계량 라이센스 설정 - .NET용 GroupDocs 비교
second_title: GroupDocs.비교 .NET API
description: 효율적인 문서 비교 작업 흐름을 위해 .NET용 GroupDocs 비교를 .NET 프로젝트에 완벽하게 통합하세요.
type: docs
weight: 12
url: /ko/net/quick-start/set-metered-license/
---
## 소개
.NET 개발 영역에서는 문서 비교를 위한 강력한 도구를 갖추는 것이 필수적입니다. .NET용 GroupDocs 비교는 프로그래밍 방식으로 다양한 문서 형식을 비교할 수 있는 강력한 솔루션입니다. 텍스트 문서에서 스프레드시트 및 프리젠테이션에 이르기까지 이 라이브러리를 통해 개발자는 파일 간의 차이점을 효율적으로 식별할 수 있습니다.
## 전제조건
.NET용 GroupDocs 비교 활용에 대한 복잡한 내용을 살펴보기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. .NET 개발 지식: .NET용 GroupDocs 비교를 효과적으로 활용하려면 C# 프로그래밍 및 .NET 환경에 대한 지식이 필수적입니다.
2.  GroupDocs 비교 라이브러리 설치: 다음에서 .NET용 GroupDocs 비교 라이브러리를 다운로드하여 설치합니다.[다운로드 링크](https://releases.groupdocs.com/comparison/net/).
3. 계량형 라이선스: GroupDocs에서 계량형 라이선스를 획득하여 라이브러리의 잠재력을 최대한 활용하세요. 임시면허를 취득하실 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).
4. 통합 개발 환경(IDE): 원활한 개발 환경을 위해 Visual Studio와 같은 IDE를 설치하세요.

## 네임스페이스 가져오기
.NET용 GroupDocs 비교 사용을 시작하려면 필요한 네임스페이스를 프로젝트로 가져옵니다. 다음과 같이하세요:

```csharp
using System;
```
이러한 네임스페이스는 문서 비교 기능에 필요한 필수 클래스 및 메서드에 대한 액세스를 제공합니다.
## 계량 라이센스 설정
.NET용 GroupDocs 비교의 모든 기능을 활용하기 전에 계량 라이센스를 설정하는 것이 중요합니다. 이를 달성하기 위한 단계별 가이드는 다음과 같습니다.
## 1단계: 공개 및 개인 키 획득
먼저, 계량 라이센스를 구매한 후 GroupDocs에서 제공하는 공개 및 개인 키를 획득합니다.
## 2단계: 계량 라이센스 설정
이제 획득한 공개 키와 개인 키를 사용하여 아래와 같이 계량형 라이선스를 설정합니다.
```csharp
string publicKey = "*****";
string privateKey = "*****";
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```
 바꾸다`"*****"`GroupDocs에서 제공하는 실제 공개 및 개인 키를 사용합니다. 이 코드는 제공된 키를 사용하여 계량 라이센스를 초기화하여 .NET용 GroupDocs 비교의 전체 기능에 액세스할 수 있도록 합니다.

## 결론
결론적으로, .NET용 GroupDocs 비교는 .NET 응용 프로그램 내 문서 비교를 위한 포괄적인 솔루션을 제공합니다. 네임스페이스 가져오기 및 계량 라이선스 설정을 위한 간략한 단계를 따르면 개발자는 이 강력한 라이브러리를 프로젝트에 원활하게 통합하여 효율적인 문서 비교 작업 흐름을 촉진할 수 있습니다.
## FAQ
### 라이센스 없이 .NET용 GroupDocs 비교를 사용할 수 있습니까?
아니요. 라이브러리의 전체 기능을 활용하려면 유효한 라이센스가 필요합니다. 그러나 테스트 목적으로 임시 라이센스를 얻을 수 있습니다.
### .NET용 GroupDocs 비교는 어떤 문서 형식을 지원합니까?
.NET용 GroupDocs 비교는 DOCX, XLSX, PPTX, PDF 등을 포함한 광범위한 문서 형식을 지원합니다.
### .NET용 GroupDocs 비교는 .NET Core와 호환됩니까?
예, .NET용 GroupDocs 비교는 .NET Framework 및 .NET Core 환경 모두와 호환됩니다.
### 비교 설정을 사용자 정의할 수 있나요?
예, 개발자는 비교 유형, 스타일 설정, 비교 범위 등 문서 비교의 다양한 측면을 유연하게 사용자 정의할 수 있습니다.
### 문제가 발생하면 어디서 도움을 받을 수 있나요?
 GroupDocs 비교 커뮤니티 포럼에서 도움을 구할 수 있습니다.[여기](https://forum.groupdocs.com/c/comparison/12).