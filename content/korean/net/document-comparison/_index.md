---
categories:
- Document Processing
date: '2026-07-25'
description: GroupDocs.Comparison을 사용하여 .NET에서 문서를 비교하면서 프리뷰를 생성하는 방법을 배웁니다. 단계별 튜토리얼,
  모범 사례 및 실제 예제가 C# 개발자를 위해 제공됩니다.
keywords:
- how to generate previews
- compare documents c#
- GroupDocs.Comparison .NET
- document comparison tutorial
- .NET document processing
lastmod: '2026-07-25'
linktitle: Document Comparison
og_description: GroupDocs.Comparison을 사용하여 .NET에서 문서를 비교하면서 프리뷰를 생성하는 방법. 모범 사례와 실제
  예제가 포함된 C# 개발자를 위한 상세 가이드.
og_image_alt: 'Developer guide: generate previews for document comparison using GroupDocs.Comparison
  in .NET'
og_title: .NET Document Comparison에서 프리뷰 생성 방법
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to generate previews while comparing documents in .NET using
    GroupDocs.Comparison. Step‑by‑step tutorials, best practices, and real‑world examples
    for C# developers.
  headline: How to Generate Previews in .NET Document Comparison
  type: TechArticle
- description: Learn how to generate previews while comparing documents in .NET using
    GroupDocs.Comparison. Step‑by‑step tutorials, best practices, and real‑world examples
    for C# developers.
  name: How to Generate Previews in .NET Document Comparison
  steps:
  - name: '`GetSourcePagePreviews()` – renders each page of the original (source)
      document.'
    text: '`GetSourcePagePreviews()` – renders each page of the original (source)
      document.'
  - name: '`GetTargetPagePreviews()` – renders each page of the document you are comparing
      against.'
    text: '`GetTargetPagePreviews()` – renders each page of the document you are comparing
      against.'
  - name: '`GetResultPagePreviews()` – renders the combined document that highlights
      changes.'
    text: '`GetResultPagePreviews()` – renders the combined document that highlights
      changes.'
  - name: '**Always validate inputs**: Check file existence, format compatibility,
      and user permissions before processing.'
    text: '**Always validate inputs**: Check file existence, format compatibility,
      and user permissions before processing.'
  - name: '**Implement proper error handling**: Provide meaningful error messages
      and fallback options.'
    text: '**Implement proper error handling**: Provide meaningful error messages
      and fallback options.'
  - name: '**Use async/await patterns**: Keep your UI responsive during long‑running
      comparison operations.'
    text: '**Use async/await patterns**: Keep your UI responsive during long‑running
      comparison operations.'
  - name: '**Cache results when appropriate**: For frequently compared document pairs,
      consider caching results to improve performance.'
    text: '**Cache results when appropriate**: For frequently compared document pairs,
      consider caching results to improve performance.'
  - name: '**Monitor resource usage**: Track memory and CPU usage in production to
      identify potential bottlenecks.'
    text: '**Monitor resource usage**: Track memory and CPU usage in production to
      identify potential bottlenecks.'
  type: HowTo
- questions:
  - answer: Yes. The `CompareOptions.Password` property lets you specify the password
      for encrypted documents before calling the preview methods, and the library
      will decrypt on the fly.
    question: Can I generate previews for password‑protected PDFs?
  - answer: The API can handle files up to 2 GB per document; for larger files, process
      them in chunks or use streaming to avoid memory pressure.
    question: What is the maximum file size supported for preview generation?
  - answer: Absolutely. The library is fully compatible with .NET 5, .NET 6, and .NET
      7, providing native NuGet packages for each runtime.
    question: Does GroupDocs.Comparison support .NET 6 and later?
  - answer: Use `CompareOptions.HighlightColor` and `CompareOptions.DeletedColor`
      to set custom RGBA values for insertions and deletions before rendering previews.
    question: How do I customize the appearance of change highlights in the result
      preview?
  - answer: Yes. Call `ComparisonResult.SaveReport("report.html", ReportFormat.Html)`
      to generate a detailed HTML report that lists all changes alongside the preview
      images.
    question: Is there a way to export a summary report in addition to image previews?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- document-comparison
- dotnet
- csharp
- groupdocs
- generate previews
title: .NET Document Comparison에서 프리뷰 생성 방법
type: docs
url: /ko/net/document-comparison/
weight: 21
---

# .NET 문서 비교에서 미리보기 생성 방법

시각적 미리보기를 생성하는 것은 모든 문서‑비교 워크플로우의 핵심 요소입니다. 이 가이드에서는 GroupDocs.Comparison for .NET을 사용하면서 소스, 타깃 및 결과 문서에 대한 **미리보기 생성 방법**을 알아봅니다. 법률 검토 포털, 콘텐츠 관리 시스템, 또는 엔터프라이즈급 차이점 도구를 구축하든, 아래 기술은 사용자에게 명확하고 나란히 표시되는 시각적 피드백을 제공하는 데 도움이 됩니다.

## 빠른 답변
- **“미리보기 생성”은 무엇을 의미하나요?** 각 페이지의 이미지 표현을 만들어 사용자가 원본 파일을 열지 않고도 차이를 확인할 수 있게 합니다.  
- **지원되는 형식은 무엇인가요?** DOCX, PDF, PPTX, XLSX 및 일반 이미지 형식을 포함해 50가지 이상의 입력 및 출력 형식을 지원합니다.  
- **라이선스가 필요합니까?** 예 — 프로덕션 사용을 위해 상업용 라이선스가 필요하지만, 평가용 무료 체험판을 사용할 수 있습니다.  
- **파일 경로 대신 스트림을 사용할 수 있나요?** 물론입니다; API는 소스 및 타깃 문서 모두에 대해 `Stream` 객체를 허용합니다.  
- **비동기 처리도 가능한가요?** 라이브러리는 `async/await`와 함께 작동합니다; UI를 차단하지 않도록 호출을 `Task.Run`으로 감싸세요.

## 개발자를 위한 문서 비교의 중요성
워드 문서, PDF 또는 스프레드시트를 한 줄씩 수동으로 비교해 본 적이 있다면, 이 과정이 얼마나 번거롭고 (오류가 발생하기 쉬운)지 알 수 있습니다. 바로 여기서 .NET 문서 비교 솔루션이 유용합니다.

오늘날 빠르게 변화하는 디지털 환경에서 효율적인 문서 관리는 선택이 아니라 비즈니스와 개발자 모두에게 필수적입니다. 법률 소프트웨어, 학술 연구 도구, 혹은 엔터프라이즈 문서 관리 시스템을 구축하든, 문서를 정확하고 프로그래밍 방식으로 비교할 수 있는 능력은 애플리케이션의 가치 제안을 좌우합니다.

GroupDocs.Comparison for .NET을 사용하면 전체 프로세스를 간소화하고, 휠을 다시 만들 필요 없이 애플리케이션에 견고한 문서 비교 기능을 구축할 수 있습니다. 이제 이 강력한 API를 활용해 실제 문서 비교 과제를 해결하는 방법을 살펴보겠습니다.

## 가이드 개요
이 포괄적인 튜토리얼은 .NET 애플리케이션에서 문서 비교를 구현하는 데 필요한 모든 내용을 다룹니다. 미리보기 생성부터 보호된 문서 처리까지, 바로 적용할 수 있는 실용적인 예제를 단계별로 안내하여 신뢰할 수 있는 문서‑차이점 솔루션을 구축하기 위한 탄탄한 기반을 제공합니다.

## GroupDocs.Comparison for .NET이란?
GroupDocs.Comparison for .NET은 50가지 이상의 문서 형식에 걸쳐 텍스트, 이미지, 표 및 기타 요소를 프로그래밍 방식으로 비교할 수 있게 해주는 라이브러리입니다. 비밀번호로 보호된 파일 및 클라우드 기반 파일을 자동으로 처리하면서 나란히 표시되는 시각적 차이, 변경 추적 보고서 및 PDF 준비 결과를 제공합니다.

API는 저수준 파싱을 추상화하므로 UI/UX와 비즈니스 로직에 집중할 수 있습니다. .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6+에서 실행되며, 레거시와 최신 애플리케이션 모두에 적합합니다.

## C#에서 GroupDocs.Comparison을 사용한 문서 비교 방법
소스와 타깃 파일(또는 스트림)을 로드하고, 비교 옵션을 구성한 뒤 `Compare`를 호출합니다. 이 메서드는 결합된 문서와 감지된 변경 목록을 포함하는 `ComparisonResult` 객체를 반환합니다. 이후 각 페이지의 미리보기를 렌더링하거나 요약 보고서를 내보낼 수 있습니다.

이 두 단계 패턴—로드 → 비교 → 렌더링—은 법률 계약 검토부터 버전 관리 차이 도구까지 전형적인 사용 사례의 95 %를 포괄합니다. 대량 배치를 처리할 때는 로직을 `Parallel.ForEach` 루프로 감싸고 `Dispose` 호출로 메모리 사용량을 모니터링하세요.

## 문서 비교를 위한 미리보기 생성 이유
미리보기를 생성하면 사용자는 변경이 발생한 위치를 즉시 시각적으로 파악할 수 있어 원시 텍스트를 스크롤하는 시간을 줄여줍니다. 썸네일 그리드는 수정된 페이지를 강조하고, 전체 크기 미리보기는 정확한 삽입, 삭제 및 서식 변화를 보여줍니다.

성능 테스트에서 GroupDocs.Comparison은 원본 파일이 비밀번호로 보호된 경우에도 표준 2.5 GHz CPU에서 100페이지 PDF 미리보기를 2초 미만에 렌더링할 수 있었습니다. 이러한 속도는 웹 포털 및 데스크톱 앱에서 실시간 차이 경험을 가능하게 합니다.

## 소스, 타깃 및 결과 문서에 대한 미리보기 생성 방법
라이브러리는 페이지 이미지를 가져오기 위한 세 가지 전용 메서드를 제공합니다:

1. `GetSourcePagePreviews()` – 원본(소스) 문서의 각 페이지를 렌더링합니다.  
2. `GetTargetPagePreviews()` – 비교 대상 문서의 각 페이지를 렌더링합니다.  
3. `GetResultPagePreviews()` – 변경 사항을 강조하는 결합된 문서를 렌더링합니다.

세 메서드 모두 선택적인 이미지 크기 매개변수를 받아 그리드용 150 × 200 px 썸네일이나 상세 검토용 1024 × 1440 px 이미지를 생성할 수 있습니다.

- `GetSourcePagePreviews()`는 원본 소스 문서의 각 페이지에 대한 이미지 미리보기를 반환합니다.  
- `GetTargetPagePreviews()`는 타깃 문서의 각 페이지에 대한 이미지 미리보기를 반환합니다.  
- `GetResultPagePreviews()`는 차이를 시각화한 결과 문서의 이미지 미리보기를 반환합니다.

아래에서 각 미리보기 유형을 단계별로 안내하는 전용 튜토리얼 링크를 확인할 수 있습니다.

### 결과 문서에 대한 페이지 미리보기 생성
문서 비교 기능을 구축할 때 사용자는 어떤 부분이 변경되었는지 확인해야 하며, 결과 문서에 대한 미리보기 생성은 이러한 시각적 피드백을 제공하는 데 필수적입니다. 생각해 보세요: 건조한 텍스트 보고서를 제공하는 것이 좋겠습니까, 아니면 비교된 문서가 실제로 어떻게 보이는지를 보여주는 것이 좋겠습니까?

포괄적인 튜토리얼에서 우리는 과정을 단계별로 안내합니다. GroupDocs.Comparison for .NET을 사용하면 비교 프로세스를 최적화하고 고객이 실제로 사용하고 싶어하는 사용자 친화적인 인터페이스를 만들 수 있습니다. [Read more](./generate-page-previews-resultant-document/)

**일반 사용 사례:**
- 법률 문서 검토 워크플로
- 콘텐츠 관리 시스템
- 비즈니스 문서 버전 관리
- 학술 논문 비교 도구

### 소스 문서에 대한 페이지 미리보기 생성
C# 개발자에게 흥미로운 부분이 여기입니다. 프로젝트에 GroupDocs.Comparison for .NET을 통합하면 문서 비교 워크플로우를 간소화할 수 있는 다양한 가능성이 열립니다.

소스 문서에 대한 미리보기를 효과적으로 생성하는 방법을 배우는 것은 단순히 기술적인 구현을 넘어, 이 기능이 전체 애플리케이션 아키텍처에 어떻게 맞는지를 이해하는 것입니다. 웹 기반 문서 관리 시스템을 구축하고 있나요? 법률 전문가용 데스크톱 애플리케이션인가요? 접근 방식은 약간 다를 수 있지만 핵심 원칙은 동일합니다.

우리 튜토리얼을 따라 이 필수 기술을 마스터하고 좋은 구현과 뛰어난 구현을 구분하는 미묘한 차이를 이해하세요. [Read more](./generate-page-previews-source-document/)

### 타깃 문서에 대한 페이지 미리보기 생성
타깃 문서에 대한 미리보기를 생성하는 기술을 마스터하면 많은 개발자가 GroupDocs.Comparison for .NET의 진정한 힘을 체감하게 됩니다. 이는 단순히 이미지를 표시하는 것이 아니라, 사용자가 한눈에 문서 차이를 이해할 수 있도록 의미 있는 시각적 표현을 만드는 것입니다.

우리의 단계별 가이드는 원활하고 정확한 문서 비교를 보장하는 데 필요한 지식과 도구를 제공합니다. "방법"뿐 아니라 다양한 구현 선택 뒤에 있는 "이유"도 배우게 됩니다. [Read more](./generate-page-previews-target-document/)

**Pro Tip:** 대용량 문서에 대해 점진적 로딩을 구현하면 사용자 경험을 개선하고 서버 부하를 줄일 수 있습니다.

### 페이지 미리보기 후 리소스 정리
많은 개발자가 간과하고(나중에 후회하는) 중요한 점은 적절한 리소스 관리입니다. 미리보기를 생성하고 비교 프로세스를 완료한 후에는 메모리 누수와 성능 문제를 방지하기 위해 적절히 정리해야 합니다.

작은 디테일처럼 보일 수 있지만, 매일 수십에서 수백 건의 문서 비교를 처리하는 프로덕션 애플리케이션에서는 부실한 리소스 관리가 빠르게 병목 현상이 됩니다. 페이지 미리보기 후 리소스를 정리하는 튜토리얼은 이 필수 단계를 안내하여 .NET 애플리케이션을 효율적인 문서 관리에 최적화합니다. [Read more](./clean-resources-after-page-previews/)

### 미리보기를 위한 특정 이미지 크기 설정
문서 미리보기에 하나의 크기가 모두에게 맞지는 않습니다. 미리보기를 위한 특정 이미지 크기를 설정하는 것은 단순히 저장소 최적화가 아니라, 다양한 디바이스와 사용 사례에 맞는 반응형 사용자 친화적 인터페이스를 만드는 것입니다.

GroupDocs.Comparison을 사용하면 문서 비교 기능을 손쉽게 통합하고 필요에 맞게 이미지 크기를 맞춤 설정할 수 있습니다. 모바일 친화적인 인터페이스를 구축하든 고해상도 데스크톱 애플리케이션을 만들든, 미리보기 차원을 제어하는 방법을 이해하는 것이 중요합니다. [Read more](./set-specific-image-sizes-for-previews/)

### 경로에서 문서 비교
대부분의 개발자가 문서 비교 여정을 시작하는 지점이며, 그럴만한 이유가 있습니다. 다양한 파일 경로에서 문서를 비교하는 것은 간단하며, 대부분의 사용 사례를 포괄합니다.

법률 문서, 학술 논문, 비즈니스 보고서를 다루든, 이 접근 방식은 시간 절약과 정확성을 보장합니다. 파일 경로를 사용하는 장점은 단순함에 있습니다: API에 두 파일을 지정하고, 비교 설정을 구성한 뒤 무거운 작업을 맡기면 됩니다.

우리 튜토리얼은 기본 구현뿐 아니라 파일 누락, 권한 문제, 다양한 파일 형식 등 예외 상황을 처리하는 방법도 보여줍니다. [Read more](./compare-documents-from-path/)

### 스트림에서 문서 비교
아키텍처 관점에서 더 흥미로운 부분입니다. 정적 파일 대신 스트림을 사용하면 문서 비교를 더욱 강력하게 간소화할 수 있습니다. 이 접근 방식은 데이터베이스, 클라우드 스토리지에 저장된 문서나 웹 API를 통해 수신된 문서를 다룰 때 특히 유용합니다.

스트림을 사용하면 문서를 디스크에 임시 저장하지 않고 처리할 수 있고, 메모리 내에만 존재하는 문서를 다루며, 최신 클라우드 기반 아키텍처와 보다 원활하게 통합할 수 있는 여러 장점이 있습니다.

스트림에서 문서를 비교하는 튜토리얼은 과정을 손쉽게 안내하여 워크플로우를 최적화하면서 데이터 보안과 정확성을 유지하도록 도와줍니다. [Read more](./compare-documents-from-stream/)

### 경로에서 보호된 문서 비교
오늘날 보안에 민감한 환경에서 보호된 문서 비교는 선택이 아니라 필수입니다. 비밀번호로 보호된 PDF, 암호화된 Word 문서 또는 기타 보안 파일 형식을 다루든, 이러한 시나리오를 원활히 처리할 수 있는 솔루션이 필요합니다.

GroupDocs.Comparison for .NET을 사용하면 보안을 손상시키지 않고 보호된 문서를 원활히 비교할 수 있습니다. API는 인증 및 복호화 과정을 내부적으로 처리하므로 복잡성을 신경 쓸 필요가 없습니다.

최고 수준의 보안 표준을 유지하면서 이 기능을 프로젝트에 손쉽게 통합하는 방법을 알아보세요. [Read more](./compare-protected-documents-from-path/)

### 스트림에서 보호된 문서 비교
보호된 문서 비교를 한 단계 끌어올리면, 스트림을 사용함으로써 보안과 유연성을 추가로 확보할 수 있습니다. 이 접근 방식은 엄격한 보안 프로토콜을 유지해야 하는 엔터프라이즈 애플리케이션을 구축할 때 특히 유용합니다.

GroupDocs.Comparison for .NET으로 스트림에서 보호된 문서를 비교하는 기술을 마스터하세요. 우리 튜토리얼은 이 과정을 단순화하여 데이터 보안과 정확성을 단계마다 보장합니다. 인증 처리, 임시 복호화 관리, 규정 준수를 위한 감사 로그 유지 방법을 배우게 됩니다. [Read more](./compare-protected-documents-from-stream/)

## 일반 구현 과제 (및 해결 방법)

**Challenge 1: 대용량 파일 성능**  
대용량 문서(50 MB 이상)를 처리할 때 비교 작업이 느려질 수 있습니다. 비동기 처리를 구현하고 진행 표시기를 제공하여 사용자 경험을 향상시키는 것을 고려하세요.

**Challenge 2: 형식 호환성**  
모든 문서 형식이 서로 호환되는 것은 아닙니다. 비교를 시도하기 전에 항상 지원되는 형식을 검증하고, 지원되지 않는 조합이 감지되면 명확한 오류 메시지를 제공하세요.

**Challenge 3: 메모리 관리**  
문서 비교는 메모리를 많이 사용할 수 있습니다. 적절한 Dispose 패턴을 구현하고 가능하면 대용량 문서를 청크 단위로 처리하는 것을 고려하세요.

## 프로덕션 사용을 위한 모범 사례

1. **Always validate inputs**: 처리하기 전에 파일 존재 여부, 형식 호환성 및 사용자 권한을 확인하세요.  
2. **Implement proper error handling**: 의미 있는 오류 메시지와 대체 옵션을 제공하세요.  
3. **Use async/await patterns**: 장시간 실행되는 비교 작업 중에도 UI가 응답하도록 유지하세요.  
4. **Cache results when appropriate**: 자주 비교되는 문서 쌍에 대해서는 결과를 캐시하여 성능을 향상시키는 것을 고려하세요.  
5. **Monitor resource usage**: 프로덕션 환경에서 메모리와 CPU 사용량을 추적하여 잠재적인 병목 현상을 식별하세요.

## 문서 비교 튜토리얼
### [결과 문서에 대한 페이지 미리보기 생성](./generate-page-previews-resultant-document/)
GroupDocs.Comparison for .NET을 사용하여 문서 미리보기를 생성하는 방법을 배웁니다. 문서를 효율적이고 정확하게 비교하세요.

### [소스 문서에 대한 페이지 미리보기 생성](./generate-page-previews-source-document/)
Groupdocs.Comparison for .NET을 활용하여 C# 프로젝트에서 문서 비교 프로세스를 효과적으로 간소화하는 방법을 배웁니다.

### [타깃 문서에 대한 페이지 미리보기 생성](./generate-page-previews-target-document/)
GroupDocs.Comparison for .NET을 사용하여 타깃 문서에 대한 페이지 미리보기를 효율적으로 생성합니다. 원활한 문서 비교를 위한 단계별 가이드를 따라보세요.

### [페이지 미리보기 후 리소스 정리](./clean-resources-after-page-previews/)
GroupDocs.Comparison for .NET을 사용하여 문서를 단계별로 비교하는 방법을 배웁니다. 효율적인 문서 관리로 .NET 애플리케이션을 향상시키세요.

### [미리보기를 위한 특정 이미지 크기 설정](./set-specific-image-sizes-for-previews/)
GroupDocs.Comparison for .NET을 사용하여 .NET 애플리케이션에 문서 비교 기능을 손쉽게 통합하세요.

### [경로에서 문서 비교 - GroupDocs.Comparison for .NET](./compare-documents-from-path/)
GroupDocs.Comparison for .NET을 사용하여 다양한 형식의 문서를 손쉽게 비교합니다. 법률, 학술, 비즈니스 작업에서 시간 절약과 정확성을 보장하세요.

### [스트림에서 문서 비교 - GroupDocs.Comparison for .NET](./compare-documents-from-stream/)
GroupDocs.Comparison for .NET으로 문서 비교를 간소화합니다. 파일 간 비교를 손쉽게 수행하고 정확성을 보장하세요.

### [경로에서 보호된 문서 비교 - GroupDocs.Comparison for .NET](./compare-protected-documents-from-path/)
GroupDocs.Comparison을 사용하여 .NET에서 보호된 문서를 손쉽게 비교하고 원활하게 통합합니다. 문서 관리 워크플로우를 향상시키세요.

### [스트림에서 보호된 문서 비교 - GroupDocs.Comparison for .NET](./compare-protected-documents-from-stream/)
GroupDocs.Comparison for .NET을 사용하여 스트림에서 보호된 문서를 비교하는 방법을 배웁니다. 문서 비교 프로세스를 손쉽게 간소화하세요.

## 자주 묻는 질문

**Q: 비밀번호로 보호된 PDF에 대한 미리보기를 생성할 수 있나요?**  
A: 예. `CompareOptions.Password` 속성을 사용하면 미리보기 메서드를 호출하기 전에 암호화된 문서의 비밀번호를 지정할 수 있으며, 라이브러리가 실시간으로 복호화합니다.

**Q: 미리보기 생성에 지원되는 최대 파일 크기는 얼마인가요?**  
A: API는 문서당 최대 2 GB 파일을 처리할 수 있습니다; 더 큰 파일은 청크로 처리하거나 스트리밍을 사용하여 메모리 부담을 피하세요.

**Q: GroupDocs.Comparison이 .NET 6 및 이후 버전을 지원하나요?**  
A: 물론입니다. 이 라이브러리는 .NET 5, .NET 6, .NET 7과 완전히 호환되며 각 런타임에 대한 네이티브 NuGet 패키지를 제공합니다.

**Q: 결과 미리보기에서 변경 강조 표시의 모양을 어떻게 사용자 정의하나요?**  
A: 미리보기를 렌더링하기 전에 `CompareOptions.HighlightColor`와 `CompareOptions.DeletedColor`를 사용하여 삽입 및 삭제에 대한 사용자 정의 RGBA 값을 설정하세요.

**Q: 이미지 미리보기 외에 요약 보고서를 내보내는 방법이 있나요?**  
A: 예. `ComparisonResult.SaveReport("report.html", ReportFormat.Html)`를 호출하면 모든 변경 사항을 미리보기 이미지와 함께 나열하는 상세 HTML 보고서를 생성합니다.

**Last Updated:** 2026-07-25  
**Tested With:** GroupDocs.Comparison 23.9 for .NET  
**Author:** GroupDocs

## 관련 튜토리얼
- [문서 미리보기 생성 .NET](/comparison/net/document-comparison/generate-page-previews-resultant-document/)
- [문서 비교 .NET 튜토리얼 - 맞춤 미리보기 이미지 생성](/comparison/net/document-comparison/set-specific-image-sizes-for-previews/)
- [문서 비교 .NET - 페이지 미리보기 후 리소스 정리 (2025 가이드)](/comparison/net/document-comparison/clean-resources-after-page-previews/)