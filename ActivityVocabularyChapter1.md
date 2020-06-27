[목차로 돌아가기](ActivityVocabularyContents.md)

## 1. 서문 (Introduction)

~~[The Activity Streams 2.0 Core Syntax](https://www.w3.org/TR/activitystreams-core/) defines the JSON syntax for Activity Streams. This document defines the vocabulary properties.~~

[Activity Streams 2.0 핵심 구문](https://www.w3.org/TR/activitystreams-core/)에서는 Activity Streams에 대한 JSON 구문을 정의합니다. 이 문서에서는 해당 어휘의 속성들을 정의합니다.

~~The Activity Streams 2.0 Vocabulary defines a set of abstract types and properties that describe past, present and future Activities. The vocabulary is defined in two parts:~~

Activity Streams 2.0 어휘는 과거, 현재 그리고 미래의 액티비티들을 설명하는데 쓰이는 추상 타입들과 속성들의 집합을 정의합니다. 어휘는 두 부분으로 정의되는데:

~~1. A Core set of properties describing the generalized structure of an Activity; and~~

~~2. An Extended set of properties that cover specific types of Activities and Artifacts common to many social Web application systems.~~

1. 액티비티의 일반화 된 구조를 설명하는데 쓰이는 핵심 속성의 집합; 그리고
2. 많은 소셜 웹 어플리케이션 시스템에 자주 사용되는 특정한 유형의 액티비티들과 아티팩트들을 다루는 확장된 특성 집합.

~~While not all Activity Streams 2.0 implementations are expected to implement support for the Extended properties, all implementations *MUST* at least be capable of serializing and deserializing the Extended properties in accordance with the [Activity Streams 2.0 Core Syntax](https://www.w3.org/TR/activitystreams-core/).~~

모든 Activity Streams 2.0 구현체들이 확장된 속성에 대한 지원을 구현할 것으로 예상하지는 않지만, 모든 구현체는 [Activity Streams 2.0 핵심 구문](https://www.w3.org/TR/activitystreams-core/)에 따라 *반드시* 확장된 속성을 직렬화(serializing) 및 역 직렬화를 할 수 있어야 합니다.

~~The key words "*MUST*", "*MUST NOT*", "*REQUIRED*", "*SHALL*", "*SHALL NOT*", " *SHOULD*", "*SHOULD NOT*", "*RECOMMENDED*", "*MAY*", and "*OPTIONAL*" in this document are to be interpreted as described in [[RFC2119](https://www.w3.org/TR/activitystreams-vocabulary/#bib-RFC2119)].~~

이 문서에 있는 "*반드시 (MUST)*", "*절대 하지 말아야 (MUST NOT)*", "*요구한다 (REQUIRED)*", "*할 것이다 (SHALL)*", "*해서는 안될 것이다 (SHALL NOT)*", "*해야 한다 (SHOULD)*", "*해서는 안된다 (SHOULD NOT)*", "*권장한다 (RECOMMENDED)*", "*할 수도 있다 (MAY)*", 그리고 "*선택적으로 (OPTIONAL)*" 의 키워드들의 해석은  [[RFC2119](https://www.w3.org/TR/activitypub/#bib-RFC2119)] 를 따릅니다.

[//Comment]: # "REQUIRED, SHALL, SHALL NOT, RECOMMENDED, OPTIONAL은 문서 어디에서도 사용되지 않는 것을 확인하였습니다."

### 1.1 관례 (Conventions)

~~Unless otherwise specified, all properties defined as `xsd:dateTime` values *MUST* conform to the rules defined in Activity Streams 2.0 Core, [Section 2.3](https://www.w3.org/TR/activitystreams-core/#dates).~~

달리 명시되지 않는 한, `xsd:dateTime`으로 정의된 모든 속성은 *반드시* Activity Streams 2.0 핵심의 [문단 2.3](https://www.w3.org/TR/activitystreams-core/#dates)에 정의된 규칙을 따라야 합니다.

~~The examples included in this document use the normative JSON serialization defined by this specification.~~

이 문서에 포함된 예제는 이 사양에서 정의한 표준 JSON 직렬화를 사용합니다.
