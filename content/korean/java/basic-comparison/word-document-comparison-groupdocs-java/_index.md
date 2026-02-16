---
categories:
- Java Development
date: '2026-02-16'
description: GroupDocs Comparison Java를 사용하여 Java에서 Word 문서를 비교하는 방법을 배워보세요. 코드 예제,
  문제 해결 팁 및 모범 사례가 포함된 단계별 튜토리얼.
keywords: java word document comparison, groupdocs java tutorial, compare word documents
  programmatically java, java document diff tool, automate document comparison java
lastmod: '2026-02-16'
linktitle: Java Word Document Comparison Guide
tags:
- document-comparison
- groupdocs
- word-documents
- java-libraries
title: groupdocs 비교 Java – Java 워드 문서 비교 가이드
type: docs
url: /ko/java/basic-comparison/word-document-comparison-groupdocs-java/
weight: 1
---

# groupdocs comparison java – Java 워드 문서 비교

워드 문서 두 개를 수동으로 비교하면서 사소한 변경까지 찾느라 몇 시간을 보낸 적이 있나요? 당신만 그런 것이 아닙니다. 계약 수정 관리, 콘텐츠 업데이트 추적, 협업 편집 워크플로우 처리 등, 문서를 수동으로 비교하는 것은 시간도 많이 걸리고 오류가 발생하기 쉽습니다.

**groupdocs comparison java**를 사용하면 이 지루한 과정을 몇 초 안에 자동화할 수 있습니다. 라이브러리는 차이점을 정확히 찾아 삽입, 삭제 및 서식 변경을 강조 표시하고, 이해관계자와 공유할 수 있는 전문 보고서를 생성합니다.

이 포괄적인 가이드에서는 Java 애플리케이션에서 문서 비교를 구현하는 방법을 기본 설정부터 고급 시나리오까지 정확히 알아볼 수 있습니다—수동 검토를 신뢰할 수 있는 반복 가능한 자동화로 대체할 수 있습니다.

## Quick Answers
- **Java에서 Word 차이를 처리하는 라이브러리는?** groupdocs comparison java
- **DOCX 파일을 비교할 수 있나요?** 예, `java compare docx files` 기능을 사용하세요
- **프로덕션에 라이선스가 필요합니까?** 전체 GroupDocs.Comparison 라이선스가 필요합니다
- **비교 속도는 어느 정도인가요?** 일반적인 작은 문서는 < 1 초 안에 완료되며, 큰 문서는 몇 초가 걸릴 수 있습니다
- **Maven 및 Gradle과 호환되나요?** 물론이며, 두 빌드 도구 모두 지원됩니다

## groupdocs comparison java란?
groupdocs comparison java는 두 개 이상의 문서를 분석하고 텍스트 및 구조적 변화를 감지하여 강조 표시된 결과 문서를 생성하는 Java SDK입니다. Word, PDF, Excel, PowerPoint 등 다양한 형식을 지원하며, 비기술적인 검토자도 이해할 수 있는 명확한 시각적 차이를 제공합니다.

## 왜 groupdocs comparison java를 사용하나요?
- **Speed:** 자동으로 수동으로 몇 분 또는 몇 시간이 걸리는 작업을 수행합니다.
- **Accuracy:** 가장 작은 문자 변경까지도 감지합니다.
- **Scalability:** 수십 개의 문서를 배치 처리할 수 있습니다.
- **Flexibility:** DOCX, PDF 및 50개 이상의 다른 형식을 지원합니다.

## 사전 요구 사항 및 필요 항목

구현에 들어가기 전에 개발 환경이 준비되었는지 확인합시다. 걱정하지 마세요 – 설정은 간단하며 각 단계를 안내해 드리겠습니다.

**필수 요구 사항:**
- **Java Development Kit (JDK):** 버전 8 이상 (성능 향상을 위해 JDK 11+ 권장)
- **Maven 또는 Gradle:** 의존성 관리용 (예제에서는 Maven 사용)
- **기본 Java 지식:** 클래스, 객체 및 파일 처리에 대한 이해
- **GroupDocs.Comparison 라이브러리:** 버전 25.2 (최신 안정 버전)

**권장 설정:**
- IntelliJ IDEA 또는 Eclipse와 같은 IDE – 더 나은 개발 경험 제공
- 큰 문서를 처리하기 위해 최소 2 GB RAM 확보
- 테스트용 샘플 워드 문서 (테스트 파일 생성 방법을 보여드림)

**빠른 환경 확인:**
터미널에서 `java -version`을 실행하세요. 버전 8 이상이 표시되면 준비된 것입니다!

이제 기본 사항을 다했으니 GroupDocs.Comparison을 프로젝트에 통합해 봅시다.

## Java용 GroupDocs.Comparison 설정

GroupDocs.Comparison을 프로젝트에 추가하는 것은 생각보다 쉽습니다. 라이브러리는 Maven을 통해 제공되므로 수동으로 JAR를 다운로드하거나 클래스패스를 설정할 필요가 없습니다.

### Maven 통합 간단히

`pom.xml` 파일에 다음 구성을 추가하세요:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/comparison/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-comparison</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**이 구성이 작동하는 이유:**
- 저장소 URL이 GroupDocs 공식 Maven 저장소를 직접 가리킵니다
- 버전 25.2는 최신 안정 릴리스이며 최근 버그 수정이 모두 포함됩니다
- 이 의존성은 필요한 모든 하위 의존성을 자동으로 가져옵니다

### Gradle 사용자

Gradle을 선호한다면, 다음과 같은 동등한 구성을 사용하세요:

```gradle
repositories {
    maven { url 'https://releases.groupdocs.com/comparison/java/' }
}
dependencies {
    implementation 'com.groupdocs:groupdocs-comparison:25.2'
}
```

### 라이선스 옵션 (프로덕션 사용 시 중요)

GroupDocs.Comparison은 유연한 라이선스 옵션을 제공합니다:

- **Free Trial:** 평가에 적합 – 약간의 제한이 있는 전체 기능 제공
- **Temporary License:** 장기간 테스트나 PoC 개발에 이상적
- **Full License:** 프로덕션 애플리케이션에 필요 – 모든 제한이 해제됩니다

**프로 팁:** API에 익숙해지기 위해 무료 체험부터 시작하세요. 기능은 전체 버전과 동일하므로 개발 작업이 낭비되지 않습니다.

의존성이 해결되고 프로젝트가 정상적으로 빌드되면 문서 비교 기능을 구현할 준비가 된 것입니다.

## 단계별 구현 가이드

이제 흥미로운 단계인 실제 문서 비교가 시작됩니다! 각 단계마다 자세히 설명하면서 "방법"뿐 아니라 각 결정의 "이유"도 이해하도록 안내하겠습니다.

### 단계 1: Comparer 객체 초기화

모든 문서 비교는 `Comparer` 객체를 생성하는 것부터 시작합니다. 실제 비교를 시작하기 전에 작업 공간을 설정하는 것으로 생각하면 됩니다.

```java
import com.groupdocs.comparison.Comparer;

public class CompareDocuments {
    public static void main(String[] args) throws Exception {
        // Initialize the Comparer with a source document
        try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source.docx")) {
            // The rest of our code will go here
        }
    }
}
```

**여기서 일어나는 일:**
- 리소스 정리를 보장하기 위해 try‑with‑resources 블록을 사용하고 있습니다
- 소스 문서는 "기준" 역할을 하며 모든 변경 사항이 이에 대해 측정됩니다
- `"YOUR_DOCUMENT_DIRECTORY"`를 실제 문서 경로로 교체하세요

**흔한 실수:** 파일 경로가 정확한지 확인하세요! 확실하지 않다면 절대 경로를 사용하거나, 애플리케이션 작업 디렉터리 기준으로 상대 경로가 올바른지 검증하세요.

### 단계 2: 비교 대상 문서 추가

다음으로, 소스와 비교할 문서(들)를 지정합니다. 여기서 마법이 시작됩니다!

```java
// Add a target document for comparison
comparer.add("YOUR_DOCUMENT_DIRECTORY/target1.docx");
```

**이 단계가 중요한 이유:**
- 대상 문서는 식별하려는 변경 사항을 포함합니다
- 필요에 따라 여러 대상 문서를 추가할 수 있습니다(여러 버전 비교에 유용)
- 라이브러리는 소스와 모든 대상 문서 간의 차이를 분석합니다

**고급 사용법:** 여러 문서와 비교해야 하나요? 문제 없습니다:

```java
comparer.add("YOUR_DOCUMENT_DIRECTORY/target1.docx");
comparer.add("YOUR_DOCUMENT_DIRECTORY/target2.docx");
// Add as many as needed
```

### 단계 3: 비교 실행 및 결과 생성

여기서 모든 무거운 작업이 수행됩니다. 라이브러리는 두 문서를 분석하고 포괄적인 비교 보고서를 생성합니다.

```java
// Compare documents and output the result
final Path resultPath = comparer.compare("YOUR_OUTPUT_DIRECTORY/compare_result.docx");
```

**얻는 결과:**
- 모든 차이가 강조 표시된 새로운 워드 문서
- 삭제된 텍스트는 명확히 표시(보통 취소선)
- 추가된 텍스트는 강조 표시(보통 다른 색상)
- 수정된 섹션이 명확히 표시

생성된 비교 문서는 단순한 diff가 아니라 이해관계자와 공유하거나 문서에 포함하거나 감사 용도로 사용할 수 있는 전문 수준의 보고서입니다.

### 전체 작업 예제

복사하여 실행할 수 있는 전체 구현 예제는 다음과 같습니다:

```java
import com.groupdocs.comparison.Comparer;
import java.nio.file.Path;

public class DocumentComparisonDemo {
    public static void main(String[] args) {
        try {
            // Set up your document paths
            String sourceDoc = "path/to/your/source.docx";
            String targetDoc = "path/to/your/target.docx";
            String outputDoc = "path/to/your/output/comparison_result.docx";
            
            // Perform the comparison
            try (Comparer comparer = new Comparer(sourceDoc)) {
                comparer.add(targetDoc);
                Path resultPath = comparer.compare(outputDoc);
                
                System.out.println("Comparison completed successfully!");
                System.out.println("Result saved to: " + resultPath.toString());
            }
            
        } catch (Exception e) {
            System.err.println("Error during comparison: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

### 일반적인 문제 해결

**문제:** `FileNotFoundException`  
**해결책:** 파일 경로를 다시 확인하고 문서가 존재하는지 확인하세요. 비교 전에 `File.exists()`로 검증하십시오.

**문제:** 대형 문서에서 `OutOfMemoryError` 발생  
**해결책:** 실행 구성에 `-Xmx2g` 이상으로 JVM 힙 크기를 늘리세요.

**문제:** 예상치 못한 비교 결과  
**해결책:** 두 문서가 유효한 워드 파일이며 손상되지 않았는지 확인하세요. 먼저 Microsoft Word에서 열어보세요.

이제 기본 비교가 작동하므로, 실제 애플리케이션에서 이 기능이 빛을 발하는 영역을 살펴보겠습니다.

## 실제 적용 사례 및 사용 사례

문서 비교는 단순히 있으면 좋은 기능이 아니라 많은 비즈니스 시나리오에서 게임 체인저입니다. 이 기능이 수작업 시간을 몇 시간 절약할 수 있는 실용적인 적용 사례를 보여드리겠습니다.

### 1. 계약 관리 및 법률 검토

**도전 과제:** 법무법인 및 기업은 계약 수정 간의 변화를 추적하여 중요한 내용이 누락되거나 실수로 수정되지 않도록 해야 합니다.

**GroupDocs가 돕는 방법:**
- 계약 버전 간 모든 변경 사항을 자동으로 강조 표시
- 고객 검토용 전문 보고서 생성
- 법률 검토 시간을 70‑80% 단축
- 변경 감지 시 인간 오류 제거

**구현 팁:** 새 초안이 업로드될 때 자동으로 여러 계약 버전을 비교하는 배치 처리 시스템을 구축하세요.

### 2. 콘텐츠 관리 및 출판 워크플로우

**시나리오:** 출판 팀은 콘텐츠 업데이트를 출판 전에 검토하여 품질과 일관성을 보장해야 합니다.

**이점:**
- 편집 검토 프로세스 간소화
- 협업 프로젝트에서 기여자 변경 사항 추적
- 콘텐츠 품질 기준 유지
- 출판 전 검사를 자동화

### 3. 비기술 팀을 위한 버전 관리

**문제:** 모든 사람이 Git을 사용하거나 기술적인 버전 관리를 이해하는 것은 아니지만, 문서 변경을 추적해야 합니다.

**해결책:**
- 시각적이고 이해하기 쉬운 변경 추적 제공
- 비기술 이해관계자가 수정 사항을 검토하도록 지원
- 규정 준수를 위한 감사 추적 생성
- 승인 워크플로우 간소화

### 4. 문서 품질 보증

**사용 사례:** 사용자 매뉴얼, API 문서 또는 규정 문서를 유지 관리하는 기술 작가 팀.

**제공 가치:**
- 문서 업데이트 전반에 걸쳐 정확성 보장
- 기술 용어의 일관성 유지
- 검토 주기 가속화
- 문서 오류 감소

### 통합 가능성

다음과 같은 시스템에 문서 비교를 통합하는 것을 고려하세요:
- **Document Management Systems:** 새 파일이 업로드될 때 자동으로 버전을 비교
- **Workflow Automation:** 승인 프로세스의 일부로 비교 보고서를 트리거
- **Notification Systems:** 중요한 변경이 감지되면 이해관계자에게 알림
- **Compliance Monitoring:** 규제 보고를 위한 변경 추적

프로그래밍 방식의 문서 비교는 비즈니스 프로세스를 개선할 수 있는 무한한 가능성을 제공합니다.

## 성능 최적화 및 모범 사례

프로덕션 환경에서 문서 비교를 다룰 때 성능은 매우 중요합니다. 아래는 높은 부하에서도 구현이 원활히 동작하도록 보장하는 검증된 전략입니다.

### 대형 문서 메모리 관리

**도전:** 50페이지 이상 대형 워드 문서는 비교 중에 상당한 메모리를 소비할 수 있습니다.

**해결책:**
- **JVM 튜닝:** `-Xmx4g` 이상으로 충분한 힙 메모리 할당
- **스트리밍 처리:** 매우 큰 문서는 섹션으로 나누는 것을 고려
- **가비지 컬렉션:** 메모리 관리를 개선하기 위해 G1 가비지 컬렉터 사용

**메모리 절약 비교 코드 예시:**

```java
// Configure JVM options for better performance
// -Xmx4g -XX:+UseG1GC -XX:MaxGCPauseMillis=200

try (Comparer comparer = new Comparer(sourceDocument)) {
    comparer.add(targetDocument);
    
    // Process comparison with explicit memory management
    System.gc(); // Suggest garbage collection before intensive operation
    Path result = comparer.compare(outputDocument);
    
    // Clear references to help garbage collection
    comparer = null;
    System.gc();
}
```

### 배치 처리 전략

여러 문서 쌍을 비교할 때:

**Sequential Processing** (간단하지만 느림):

```java
for (DocumentPair pair : documentPairs) {
    try (Comparer comparer = new Comparer(pair.getSource())) {
        comparer.add(pair.getTarget());
        comparer.compare(pair.getOutputPath());
    }
}
```

**Parallel Processing** (빠르지만 메모리 집약적):

```java
documentPairs.parallelStream().forEach(pair -> {
    try (Comparer comparer = new Comparer(pair.getSource())) {
        comparer.add(pair.getTarget());
        comparer.compare(pair.getOutputPath());
    } catch (Exception e) {
        // Handle exceptions appropriately
        logger.error("Comparison failed for: " + pair.getSource(), e);
    }
});
```

### 성능 모니터링 팁

**추적할 주요 지표:**
- 문서 크기당 비교 시간
- 메모리 사용 패턴
- 성공/실패 비율
- 큐 처리 시간(비동기 처리 사용 시)

**구현 예시:**

```java
long startTime = System.currentTimeMillis();
long startMemory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();

try (Comparer comparer = new Comparer(sourceDoc)) {
    comparer.add(targetDoc);
    Path result = comparer.compare(outputDoc);
    
    long endTime = System.currentTimeMillis();
    long endMemory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();
    
    System.out.println("Comparison completed in: " + (endTime - startTime) + "ms");
    System.out.println("Memory used: " + (endMemory - startMemory) / 1024 / 1024 + "MB");
}
```

### 라이브러리 업데이트 및 유지 관리

**업데이트 유지:** GroupDocs는 성능 향상 및 버그 수정을 포함한 업데이트를 정기적으로 릴리스합니다. 최소 분기별로 의존성을 업데이트하세요:

```xml
<!-- Check for updates regularly -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-comparison</artifactId>
    <version>25.2</version> <!-- Keep this current -->
</dependency>
```

이러한 관행을 따르면 사용량이 증가해도 문서 비교 시스템이 빠르고 안정적으로 유지됩니다.

## 고급 구성 및 커스터마이징

기본 비교 기능은 바로 사용할 수 있지만, GroupDocs.Comparison은 강력한 커스터마이징 옵션을 제공하여 요구 사항에 맞게 동작을 조정할 수 있습니다.

### 비교 설정 커스터마이징

**왜 커스터마이징하나요?** 사용 사례에 따라 접근 방식이 달라집니다. 법률 문서는 일반 콘텐츠 검토보다 더 높은 민감도가 필요합니다.

**예시 – 고감도 비교:**

```java
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.style.DetalisationLevel;

CompareOptions compareOptions = new CompareOptions();
compareOptions.setDetalisationLevel(DetalisationLevel.High);
compareOptions.setShowDeletedContent(true);
compareOptions.setShowInsertedContent(true);

try (Comparer comparer = new Comparer("source.docx")) {
    comparer.add("target.docx");
    comparer.compare("detailed_result.docx", compareOptions);
}
```

### 출력 형식 옵션

결과 문서에서 차이가 표시되는 방식을 제어하세요:
- **색상 체계:** 강조 색상 맞춤 설정
- **변경 표시:** 삽입 및 삭제 표시 방식 선택
- **요약 보고서:** 변경에 대한 통계 요약 포함

### 오류 처리 모범 사례

**견고한 오류 처리 예시:**

```java
public class DocumentComparisonService {
    
    public ComparisonResult compareDocuments(String source, String target, String output) {
        try {
            validateInputs(source, target);
            
            try (Comparer comparer = new Comparer(source)) {
                comparer.add(target);
                Path resultPath = comparer.compare(output);
                
                return new ComparisonResult(true, resultPath.toString(), "Success");
            }
            
        } catch (FileNotFoundException e) {
            return new ComparisonResult(false, null, "Document not found: " + e.getMessage());
        } catch (Exception e) {
            return new ComparisonResult(false, null, "Comparison failed: " + e.getMessage());
        }
    }
    
    private void validateInputs(String source, String target) throws IllegalArgumentException {
        if (!new File(source).exists()) {
            throw new IllegalArgumentException("Source document does not exist: " + source);
        }
        if (!new File(target).exists()) {
            throw new IllegalArgumentException("Target document does not exist: " + target);
        }
    }
}
```

이 접근 방식은 애플리케이션이 오류를 우아하게 처리하고 사용자에게 의미 있는 피드백을 제공하도록 보장합니다.

## 자주 묻는 질문

### 두 개 이상의 문서를 동시에 비교할 수 있나요?

물론입니다! GroupDocs.Comparison은 단일 소스에 대해 여러 대상 문서를 지원합니다. `comparer.add()`를 여러 번 호출하면 됩니다:

```java
try (Comparer comparer = new Comparer("source.docx")) {
    comparer.add("version1.docx");
    comparer.add("version2.docx");
    comparer.add("version3.docx");
    comparer.compare("multi_comparison_result.docx");
}
```

이는 여러 문서 버전 간 변경 사항을 추적하거나 팀 구성원별 기여를 비교할 때 특히 유용합니다.

### Word 문서 외에 GroupDocs.Comparison이 지원하는 파일 형식은 무엇인가요?

GroupDocs.Comparison은 다음을 포함한 50개 이상의 파일 형식을 지원합니다:
- **문서:** DOCX, DOC, PDF, RTF, TXT
- **스프레드시트:** XLSX, XLS, CSV
- **프레젠테이션:** PPTX, PPT
- **이미지:** PNG, JPEG, BMP, TIFF
- **웹:** HTML, MHT
- **이메일:** EML, MSG

API는 모든 형식에서 일관되므로 기술을 쉽게 전이할 수 있습니다.

### 암호로 보호된 문서는 어떻게 처리하나요?

GroupDocs.Comparison은 초기화 시 비밀번호를 지정하여 암호로 보호된 문서를 처리할 수 있습니다:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your_password");

try (Comparer comparer = new Comparer("protected_source.docx", loadOptions)) {
    // Add target document (also protected)
    LoadOptions targetOptions = new LoadOptions();
    targetOptions.setPassword("target_password");
    comparer.add("protected_target.docx", targetOptions);
    
    comparer.compare("comparison_result.docx");
}
```

### 대형 문서에서 성능 영향은 어떨까요?

성능은 문서 크기와 복잡도에 따라 달라집니다:
- **소형 문서** (< 10 페이지): 1초 미만 비교
- **중형 문서** (10‑50 페이지): 일반적으로 2‑10 초
- **대형 문서** (50 페이지 이상): 30 초 이상 및 추가 메모리 필요

**최적화 팁:**
- 대형 문서용으로 충분한 JVM 힙 메모리 할당(4 GB 이상)
- 빠른 I/O를 위해 SSD 스토리지 사용
- 매우 큰 파일은 문서 분할을 고려

### Spring Boot 등 다른 Java 프레임워크와 통합할 수 있나요?

물론 가능합니다! GroupDocs.Comparison은 모든 Java 프레임워크와 원활히 통합됩니다. 다음은 Spring Boot 서비스 예시입니다:

```java
@Service
public class DocumentComparisonService {
    
    @Autowired
    private DocumentRepository documentRepository;
    
    public String compareDocuments(Long sourceId, Long targetId) {
        Document source = documentRepository.findById(sourceId).orElseThrow();
        Document target = documentRepository.findById(targetId).orElseThrow();
        
        try (Comparer comparer = new Comparer(source.getFilePath())) {
            comparer.add(target.getFilePath());
            String outputPath = generateOutputPath(sourceId, targetId);
            comparer.compare(outputPath);
            return outputPath;
        } catch (Exception e) {
            throw new DocumentComparisonException("Failed to compare documents", e);
        }
    }
}
```

### 비교 결과의 외관을 어떻게 커스터마이징하나요?

GroupDocs는 광범위한 스타일 옵션을 제공합니다:

```java
CompareOptions options = new CompareOptions();
options.setInsertedItemStyle(new StyleSettings());
options.getInsertedItemStyle().setFontColor(Color.BLUE);
options.getInsertedItemStyle().setHighlightColor(Color.LIGHT_GRAY);

options.setDeletedItemStyle(new StyleSettings());
options.getDeletedItemStyle().setFontColor(Color.RED);
options.getDeletedItemStyle().setStrikethrough(true);

comparer.compare("styled_result.docx", options);
```

이를 통해 조직의 문서 표준에 맞추거나 테마가 적용된 비교 보고서를 만들 수 있습니다.

## 추가 자료

- **문서:** [GroupDocs.Comparison for Java Docs](https://docs.groupdocs.com/comparison/java/)
- **API 레퍼런스:** [Complete API Reference](https://reference.groupdocs.com/comparison/java/)
- **최신 버전 다운로드:** [GroupDocs Releases](https://releases.groupdocs.com/comparison/java/)
- **라이선스 구매:** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)
- **무료 체험:** [Download Free Trial](https://releases.groupdocs.com/comparison/java/)
- **임시 라이선스:** [Get Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **커뮤니티 지원:** [GroupDocs Forum](https://forum.groupdocs.com/c/comparison)

---

**마지막 업데이트:** 2026-02-16  
**테스트 환경:** GroupDocs.Comparison 25.2 for Java  
**작성자:** GroupDocs

---