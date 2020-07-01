[README로 돌아가기](README.md)

# [액티비티 어휘(Activity Vocabulary)](https://www.w3.org/TR/activitystreams-vocabulary/)

2017년 5월 23일 <abbr title="World Wide Web Consortium">W3C</abbr>권고안

**현재 버전**
- https://www.w3.org/TR/2017/REC-activitystreams-vocabulary-20170523/

**최신 게시 버전**
- https://www.w3.org/TR/activitystreams-vocabulary/

**최신 편집자 초안**
- http://w3c.github.io/activitystreams/vocabulary/

**테스트 모음**
- https://github.com/w3c/activitystreams/tree/master/test

**구현 보고서**
- https://github.com/w3c/activitystreams/tree/master/implementation-reports

**이전 버전**
- https://www.w3.org/TR/2017/PR-activitystreams-vocabulary-20170413/

**편집자:**
- [James M Snell](http://jasnell.me/), IBM
- [Evan Prodromou](https://fuzzy.ai/about), Fuzzy.ai

**저장소**
- [Github](https://github.com/w3c/activitystreams)
- [이슈들](https://github.com/w3c/activitystreams/issues)
- [커밋들](https://github.com/w3c/activitystreams/commits/master)

**테스트**
- [검증기](https://as2.rocks/)

이 게시물 이후 보고된 오류나 이슈에 대해서는 [**정오표**](https://github.com/w3c/activitystreams/blob/master/ERRATA.md) 를 확인해 주시길 바랍니다.

이 표준은 영어 버전만이 유일한 표준 버전입니다. 비-표준적인 번역본들도 제공될 수도 있습니다.

[Copyright](https://www.w3.org/Consortium/Legal/ipr-notice#Copyright) © 2017 [<abbr title="World Wide Web Consortium">W3C</abbr>](https://www.w3.org/)® (<abbr title="매사추세츠 공과대학교">[MIT](https://www.csail.mit.edu/)</abbr>, <abbr title="European Research Consortium for Informatics and Mathematics">[ERCIM](https://www.ercim.eu/)</abbr>, [Keio](https://www.keio.ac.jp/), [Beihang](http://ev.buaa.edu.cn/)). <abbr title="World Wide Web Consortium">W3C</abbr> [법적 책임](https://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [상표](https://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks)와 [문서 허용 라이센스](https://www.w3.org/Consortium/Legal/2015/copyright-software-and-document) 규칙이 적용됩니다.

-----

## 요약 (Abstract)

이 문서에서는 액티비티 어휘(Activity vocabulary)에 대해 설명합니다. ActivityStreams 2.0 형식의 컨텍스트에서 사용되도록 고안되었으며, 액티비티 구조와 특정 액티비티 타입에 대해 기반이 되는 어휘들을 제공합니다.

### 글쓴이의 말 (Author's Note)

__이 항목은 비표준입니다.__

이 초안은 Martin Atkins, Will Norris, Chris Messina, Monica Wilkinson, Rob Dolin 및 James Snell이 공동 작성한 JSON Activity Streams 1.0 문서의 영향을 많이 받았습니다. 저는 그들의 중대한 기여에 대해 매우 감사하며 그들의 노고를 잊지 않을겁니다. Activity Streams 1.0 원문의 일부는 이 문서에서 그대로 사용됩니다.

## 이 문서의 상태 (Status of This Document)

_이 문단에서는 현 문서의 발행 당시의 상태에 대하여 기술합니다. 다른 문서가 이 문서를 대체 할 수 있습니다. 현재 <abbr title="World Wide Web Consortium">W3C</abbr> 출판물 목록 및 이 기술보고서의 최신 개정판은 https://www.w3.org/TR/ 에 있는 [<abbr title="World Wide Web Consortium">W3C</abbr> 기술보고서 색인](https://www.w3.org/TR/)에서 찾아볼 수 있습니다._

이 문서는 [소셜 웹 워킹 그룹(Social Web Working Group)](https://www.w3.org/Social/WG)에 의하여 작성된 권고안입니다. 이 문서에 관한 의견은 언제나 환영합니다. 의견이 있을시 public-socialweb@w3.org ([구독](public-socialweb-request@w3.org), [기록들](https://lists.w3.org/Archives/Public/public-socialweb/))로 보내주시길 바랍니다.

작업 그룹의 [구현 레포트](https://github.com/w3c/activitystreams/tree/master/implementation-reports)를 확인해 주시길 바랍니다.

이 문서는 <abbr title="World Wide Web Consortium">W3C</abbr> 회원, 소프트웨어 개발자 및 기타 W3C 그룹과 이해 관계자들에게 검토되었으며, 위원장이 <abbr title="World Wide Web Consortium">W3C</abbr> 권고안으로 발표하였습니다. 이 문서는 안정적이며, 참고자료로 사용되거나 다른 문서에서 인용될수 있습니다. <abbr title="World Wide Web Consortium">W3C</abbr>가 권고안을 만드는 것은 표준사양에 대하여 주의를 환기시키고, 보다 넓은 범위에서 그 사용을 촉진시키기 위함입니다. 이는 웹의 기능성과 보편성을 향상시킬 수 있습니다.

이 문서는 [2004년 02월 05일 <abbr title="World Wide Web Consortium">W3C</abbr> 특허 정책](https://www.w3.org/Consortium/Patent-Policy/)에 따라 운영되는 그룹이 작성하였습니다. <abbr title="World Wide Web Consortium">W3C</abbr>는 그룹의 성과물에 관한 [모든 공개 특허 공개 목록](https://www.w3.org/2004/01/pp-impl/72531/status)을 관리합니다. 이곳에서는 특허 공개에 대한 지시사항도 포함됩니다. [필수 주장(들)](https://www.w3.org/Consortium/Patent-Policy-20040205/#def-essential)을 포함한다고 생각되는 특허에 대하여 실제 지식을 보유한 개인은 [<abbr title="World Wide Web Consortium">W3C</abbr> 특허 정책의 섹션 6](https://www.w3.org/Consortium/Patent-Policy-20040205/#sec-Disclosure)에 의하여 정보를 공개하여야 합니다.

이 문서는 [2017년 3월 1일 <abbr title="World Wide Web Consortium">W3C</abbr> 프로세스 문서](https://www.w3.org/2017/Process-20170301/)를 적용받습니다.

## 목차 (Table of Contents)

1\. [서문 (Introduction)](#1-서문-introduction)

- 1.1 [관례 (Conventions)](#11-관례-conventions)

2\. [핵심 타입 (Core Types)](#2-핵심-타입-core-types)

3\. [확장 타입 (Extended Types)](#3-확장-타입-extended-types)

- 3.1 [액티비티 타입 (Activity Types)](#31-액티비티-타입-activity-types)
- 3.2 [액터 타입 (Actor Types)](#32-액터-타입-actor-types)
- 3.3 [객체와 링크 타입 (Object and Link Types)](#33-객체와-링크-타입-object-and-link-types)

4\. [속성 (Properties)](#4-속성-properties)

5\. [구현 비고 (Implementation Notes)](#5-구현-비고-implementation-notes)

- 5.1 [청중 타게팅 (Audience Targeting)](#51-청중-타게팅-audience-targeting)
- 5.2 [개체간의 관계 표현(Representing Relationships Between Entities)](#52-개체간의-관계-표현-representing-relationships-between-entities)
- 5.3 [장소 표현 (Representing Places)](#53-장소-표현-representing-places)
- 5.4 [질문 표현 (Representing Questions)](#54-질문-표현-representing-questions)
- 5.5 [역 액티비티와 "실행 취소" (Inverse Activities and "Undo")](#55-역-액티비티와-실행-취소-inverse-activities-and-undo)
- 5.6 [멘션, 태그 및 다른 일반적인 소셜 마이크로신택스들 (Mentions, Tags and Other Common Social Microsyntaxes)](#56-멘션-태그-및-다른-일반적인-소셜-마이크로신택스들-mentions-tags-and-other-common-social-microsyntaxes)
- 5.7 [출발지 및 목표 (Origin and Target)](#57-출발지-및-목표-origin-and-target)
- 5.8 [액티비티 타입의 사용 사례 (Activity Type Motivating Use Cases)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

A\. [비 표준 온톨로지 정의 (Non-normative Ontology Definition)](#a-비-표준-온톨로지-정의-non-normative-ontology-definition)

B\. [변경 기록 (Changelog)](#b-변경-기록-changelog)

C\. [참고 문헌 (References)](#c-참고-문헌-references)

- C.1 [규정 참고 문헌 (Normative references)](#c1-규정-참고-문헌-normative-references)
- C.2 [정보 참고 문헌 (Informative references)](#c2-정보-참고-문헌-informative-references)

## 1. [서문 (Introduction)](#목차-table-of-contents)

[Activity Streams 2.0 핵심 구문](https://www.w3.org/TR/activitystreams-core/)에서는 Activity Streams에 대한 JSON 구문을 정의합니다. 이 문서에서는 해당 어휘의 속성들을 정의합니다.

Activity Streams 2.0 어휘는 과거, 현재 그리고 미래의 액티비티들을 설명하는데 쓰이는 추상 타입들과 속성들의 집합을 정의합니다. 어휘는 두 부분으로 정의됩니다:

1. 액티비티의 일반화된 구조를 설명하는데 쓰이는 핵심 속성들의 집합; 그리고
2. 많은 소셜 웹 어플리케이션 시스템에 자주 사용되는 특정한 유형의 액티비티들과 아티팩트들을 다루는 확장된 특성 집합.

모든 Activity Streams 2.0 구현체들이 확장된 속성들에 대한 지원을 구현할 것으로 예상하지는 않지만, 모든 구현체는 [Activity Streams 2.0 핵심 구문](https://www.w3.org/TR/activitystreams-core/)에 따라 *반드시* 확장된 속성을 직렬화(serializing) 및 역 직렬화를 할 수 있어야 합니다.

이 문서에 있는 "*반드시 (MUST)*", "*절대 하지 말아야 (MUST NOT)*", "*요구한다 (REQUIRED)*", "*할 것이다 (SHALL)*", "*해서는 안될 것이다 (SHALL NOT)*", "*해야 한다 (SHOULD)*", "*해서는 안된다 (SHOULD NOT)*", "*권장한다 (RECOMMENDED)*", "*할 수도 있다 (MAY)*", 그리고 "*선택적으로 (OPTIONAL)*" 의 키워드들의 해석은  [[RFC2119](#rfc2119)] 를 따릅니다.

### 1.1 [관례 (Conventions)](#1-서문-introduction)

따로 명시되지 않는 한, `xsd:dateTime`으로 정의된 모든 속성은 *반드시* Activity Streams 2.0 핵심의 [문단 2.3](https://www.w3.org/TR/activitystreams-core/#dates)에 정의된 규칙을 따라야 합니다.

이 문서에 포함된 예시는 이 사양에서 정의한 표준 JSON 직렬화를 사용합니다.

## 2. [핵심 타입 (Core Types)](#목차-table-of-contents)

액티비티-어휘 핵심 타입들은 나머지 어휘들의 기반이 됩니다.

기반 URI: `https://www.w3.org/ns/activitystreams#`.

Activity Streams 2.0 핵심 타입은 다음과 같습니다:

- [Object](#class-object)
- [Link](#class-link)
- [Activity](#class-activity)
- [IntransitiveActivity](#class-intransitiveactivity)
- [Collection](#class-collection)
- [OrderedCollection](#class-orderedcollection)
- [CollectionPage](#class-collectionpage)
- [OrderedCollectionPage](#class-orderedcollectionpage)

#### [Class] [Object](#2-핵심-타입-core-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Object`
비고: | 모든 객체의 종류를 설명하는데 쓰입니다. 객체(Object) 타입은 [Activity](#class-activity), [IntransitiveActivity](#class-intransitiveactivity), [Collection](#class-collection) 그리고 [OrderedCollection](#class-orderedcollection)과 같은 다른 핵심 타입들을 포함하여 액티비티-어휘에 정의된 대부분의 객체에 대한 기본 타입으로 사용됩니다.
서로소: | [Link](#class-link)
속성: | [attachment](#class-attachment) \| [attributedTo](#class-attributedto) \| [audience](#class-audience) \| [content](#class-content) \| [context](#class-context) \| [name](#class-name) \| [endTime](#class-endtime) \| [generator](#class-generator) \| [icon](#class-icon) \| [image](#class-image) \| [inReplyTo](#class-inreplyto) \| [location](#class-location) \| [preview](#class-preview) \| [published](#class-published) \| [replies](#class-replies) \| [startTime](#class-starttime) \| [summary](#class-summary) \| [tag](#class-tag) \| [updated](#class-updated) \| [url](#class-url) \| [to](#class-to) \| [bto](#class-bto) \| [cc](#class-cc) \| [bcc](#class-bcc) \| [mediaType](#class-mediatype) \| [duration](#class-duration)

>예시 1
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Object",
>  "id": "http://www.test.example/object/1",
>  "name": "간단하고, 특정되지 않은 객체"
>}
>```

#### [Class] [Link](#2-핵심-타입-core-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Link`
비고: | 링크(Link)는 URL로 식별되는 리소스에 대한 간접적이고 정규화된 참조입니다. 링크들이 기반하는 모델은 [ [RFC5988](#rfc5988)]에 정의되어 있습니다. 액티비티-어휘에 의해 정의된 많은 속성들은 [Object](#class-object)의 인스턴스나 [Link](#class-link)의 값을 사용하는것을 허용합니다. [Link](#class-link)가 사용될 경우 (담겨 있는 객체의) 대상을 [href](#class-href)로 식별된 리소스에 연결하는 [검증된 관계](http://patterns.dataincubator.org/book/qualified-relation.html)를 만들어냅니다. [Link](#class-link)의 속성은 리소스의 속성과 달리 참조의 속성입니다.
서로소인 속성: | [Object](#class-object)
속성: | [href](#class-href) \| [rel](#class-rel) \| [mediaType](#class-mediatype) \| [name](#class-name) \| [hreflang](#class-hreflang) \| [height](#class-height) \| [width](#class-width) \| [preview](#class-preview)

>예시 2
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "hreflang": "en",
>  "mediaType": "text/html",
>  "name": "링크(link) 예시"
>}
>```

#### [Class] [Activity](#2-핵심-타입-core-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Activity`
비고: | 액티비티는 발생중인, 현재 진행중인, 또는 이미 발생한 일부 행동(action)을 설명하는데 사용되는 [Object](#class-object)의 하위 타입입니다. `Activity` 타입 자신은 모든 타입의 액티비티들에 대한 추상 기반 타입으로 사용됩니다. 중요 사항으로 `Activity` 타입은 그 자체에 가해지는 행동에 대해서는 아무런 의미도 포함하고 있지 않습니다.
상속함: | [Object](#class-object)
속성: | [actor](#class-actor) \| [object](#class-object) \| [target](#class-target) \| [result](#class-result) \| [origin](#class-origin) \| [instrument](#class-instrument) </br> [Object](#class-object)로부터 모든 속성을 물려받습니다.

>예시 3
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Activity",
>  "summary": "Sally가 노트에 무슨 짓을 했어요",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Note",
>    "name": "노트"
>  }
>}
>```

#### [Class] [IntransitiveActivity](#2-핵심-타입-core-types)

설멍| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#IntransitiveActivity`
비고: | `IntransitiveActivity`의 인스턴스들은 비-과도적 행동들(intransitive actions)을 나타내는 `Activity`의 하위 타입입니다. 따라서 [object](#class-object) 속성은 이러한 액티비티들에게 적합하지 않습니다.
상속함: | [Activity](#class-activity)
속성: | `object`를 제외한 모든 [Activity](#class-activity)의 속성들을 물려받습니다.

>예시 4
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Travel",
>  "summary": "Sally는 일하러 갔습니다",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "target": {
>    "type": "Place",
>    "name": "일하는곳"
>  }
>}
>```

#### [Class] [Collection](#2-핵심-타입-core-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Collection`
비고: | `Collection`은 정렬된 또는 정렬되지 않은 [`Object`](#class-object) 이거나 [`Link`](#class-link) 인스턴트들의 집합을 나타내는 [Object](#class-object)의 하위 타입입니다. </br> `Collection` 타입에 대한 자세한 설명은 [Activity Streams 2.0 핵심](https://www.w3.org/TR/activitystreams-core/#collection) 사양을 참고하시길 바랍니다.
상속함: | [Object](#class-object)
속성: | [totalItems](#class-totalitems) \| [current](#class-current) \| [first](#class-first) \| [last](#class-last) \| [items](#class-items) </br> [Object](#class-object)로부터 모든 속성을 물려받습니다.

>예시 5
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 메모들",
>  "type": "Collection",
>  "totalItems": 2,
>  "items": [
>    {
>      "type": "Note",
>      "name": "간단한 메모"
>    },
>    {
>      "type": "Note",
>      "name": "다른 간단한 메모"
>    }
>  ]
>}
>```

#### [Class] [OrderedCollection](#2-핵심-타입-core-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollection`
비고: | 논리적 컬렉션(collection)의 멤버가 항상 엄격하게 정렬(ordered)된 것으로 간주되는 [Collection](#class-collection)의 하위 타입입니다.
상속함: | [Collection](#class-collection)
속성: | [Collection](#class-collection)으로부터 모든 속성을 물려받습니다.

>예시 6
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 메모들",
>  "type": "OrderedCollection",
>  "totalItems": 2,
>  "orderedItems": [
>    {
>      "type": "Note",
>      "name": "간단한 메모"
>    },
>    {
>      "type": "Note",
>      "name": "다른 간단한 메모"
>    }
>  ]
>}
>```

#### [Class] [CollectionPage](#2-핵심-타입-core-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#CollectionPage`
비고: | `Collection`이 보유하고 있는 항목들의 고유한 하위 집합들을 나타내는데 사용됩니다. `CollectionPage` 객체에 대한 자세한 설명은 [Activity Streams 2.0 핵심](https://www.w3.org/TR/activitystreams-core/#dfn-collectionpage) 문서를 참고하시길 바랍니다.
상속함: | [Collection](#class-collection)
속성: | [partOf](#class-partof) \| [next](#class-next) \| [prev](#class-prev) </br> [Collection](#class-collection)으로부터 모든 속성을 물려받습니다.

>예시 7
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 메모들 1페이지",
>  "type": "CollectionPage",
>  "id": "http://example.org/foo?page=1",
>  "partOf": "http://example.org/foo",
>  "items": [
>    {
>      "type": "Note",
>      "name": "간단한 메모"
>    },
>    {
>      "type": "Note",
>      "name": "다른 간단한 메모"
>    }
>  ]
>}
>```

#### [Class] [OrderedCollectionPage](#2-핵심-타입-core-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollectionPage`
비고: | `OrderedCollection`이 보유하고 있는 항목들의 정렬된 하위 집합들을 나타내는데 사용됩니다. `OrderedCollectionPage` 객체에 대한 자세한 설명은 [Activity Streams 2.0 핵심](https://www.w3.org/TR/activitystreams-core/#dfn-orderedcollectionpage) 문서를 참고하시길 바랍니다.
상속함: | [OrderedCollection](#class-orderedcollection) \| [CollectionPage](#class-collectionpage)
속성: | [startIndex](#class-startindex) </br> [OrderedCollection](#class-orderedcollection)과 [CollectionPage](#class-collectionpage)로부터 모든 속성을 물려받습니다.

>예시 8
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 메모들 1페이지",
>  "type": "OrderedCollectionPage",
>  "id": "http://example.org/foo?page=1",
>  "partOf": "http://example.org/foo",
>  "orderedItems": [
>    {
>      "type": "Note",
>      "name": "간단한 메모"
>    },
>    {
>      "type": "Note",
>      "name": "다른 간단한 메모"
>    }
>  ]
>}
>```

## 3. [확장 타입 (Extended Types)](#목차-table-of-contents)

기반 URI: `https://www.w3.org/ns/activitystreams#`.

Activity Streams 2.0 확장 타입에는 많은 소셜 웹 어플리케이션에게 공통적인 액티비티와 Object의 하위 타입들이 포함됩니다. 이들은 다음과 같이 세가지 유형으로 나뉩니다:

- [액티비티 타입](#31-액티비티-타입-activity-types)
- [액터 타입](#32-액터-타입-actor-types)
- [객체 타입](#33-객체와-링크-타입-object-and-link-types)

특정한 확장 어휘 타입에 대한 지원은 다양할것으로 예상되며, 구현시에는 해당 응용프로그램의 특정 컨텍스트와 요구사항에 적합한 확장유형들과 속성들만 선택하면 됩니다. 하지만 상호 운용성(interoperability) 문제를 피하기 위해서는 구현시 이 문서에 정의된 확장 어휘와 중복되거나 중복되는 확장 타입 또는 속성을 *절대* 사용하지 말아야 합니다.

### 3.1 [액티비티 타입 (Activity Types)](#목차-table-of-contents)

모든 액티비티 타입은 기본 [Activity](#class-activity) 타입의 속성을 상속합니다. 일부 특정한 액티비티 타입들은 더욱더 일반화된 액티비티 타입의 하위타입 이거나 특수화된 경우입니다 (예를 들어, [Invite](#class-invite) 액티비티 타입은 [Offer](#class-offer) 액티비티 타입이 특수화된 경우입니다).

액티비티 타입은 다음과 같은 타입들을 포함합니다:

- [Accept](#class-accept)
- [Add](#class-add)
- [Announce](#class-announce)
- [Arrive](#class-arrive)
- [Block](#class-block)
- [Create](#class-create)
- [Delete](#class-delete)
- [Dislike](#class-dislike)
- [Flag](#class-flag)
- [Follow](#class-follow)
- [Ignore](#class-ignore)
- [Invite](#class-invite)
- [Join](#class-join)
- [Leave](#class-leave)
- [Like](#class-like)
- [Listen](#class-listen)
- [Move](#class-move)
- [Offer](#class-offer)
- [Question](#class-question)
- [Reject](#class-reject)
- [Read](#class-read)
- [Remove](#class-remove)
- [TentativeReject](#class-tentativereject)
- [TentativeAccept](#class-tentativeaccept)
- [Travel](#class-travel)
- [Undo](#class-undo)
- [Update](#class-update)
- [View](#class-view)


#### [Class] [Accept](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Accept`
비고: | `actor`가 `object`를 수락(accept)함을 나타냅니다. `target` 속성은 특정 상황에서 `object`가 받아들여진 컨텍스트를 나타내기 위해 사용될 수 있습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 9
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 파티 초대를 수락했습니다",
>  "type": "Accept",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Invite",
>    "actor": "http://john.example.org",
>    "object": {
>      "type": "Event",
>      "name": "Jim을 위한 송별회"
>    }
>  }
>}
>```

>예시 10
>
>```json
>{
>    "@context": "https://www.w3.org/ns/activitystreams",
>    "summary": "Sally가 Joe를 클럽으로 받아들였습니다",
>    "type": "Accept",
>    "actor": {
>      "type": "Person",
>      "name": "Sally"
>    },
>    "object": {
>      "type": "Person",
>      "name": "Joe"
>    },
>    "target": {
>      "type": "Group",
>      "name": "그 클럽"
>    }
>}
>```

#### [Class] [TentativeAccept](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeAccept`
비고: | 수락(acceptance)이 잠정적임을 나타내는, Accept의 특화된 경우입니다.
상속함: | [Accept](#class-accept)
속성: | [Accept](#class-accept)로부터 모든 속성을 상속받습니다.

>예시 11
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 파티 초대를 잠정적으로 수락하였습니다.",
>  "type": "TentativeAccept",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Invite",
>    "actor": "http://john.example.org",
>    "object": {
>      "type": "Event",
>      "name": "Jim을 위한 송별회"
>    }
>  }
>}
>```

#### [Class] [Add](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Add`
비고: | `actor`가 `object`를 `target`에 추가하였음을 나타냅니다. `target` 속성이 명시적으로 지정되어 있지 않으면, 대상(target)은 컨텍스트에 의해 암시적으로 결정되어야 합니다. `origin`은 `object`가 시작된 컨텍스트를 식별하는데 사용할 수도 있습니다.`
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 12
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 객체를 추가하였습니다",
>  "type": "Add",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/abc"
>}
>```

>예시 13
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 고양이 사진 모음집에 그녀의 고양이 사진을 추가하였습니다",
>  "type": "Add",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Image",
>    "name": "내 고양이의 사진",
>    "url": "http://example.org/img/cat.png"
>  },
>  "origin": {
>    "type": "Collection",
>    "name": "카메라 롤"
>  },
>  "target": {
>    "type": "Collection",
>    "name": "내 고양이 사진들"
>  }
>}
>```


#### [Class] [Arrive](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Arrive`
비고: | `actor`가 `location`에 도착했음(arrived)을 나타내는 [IntransitiveActivity](#class-intransitiveactivity)입니다. `origin`은 `actor`가 시작된 컨텍스트를 식별하는데 사용할 수도 있습니다. 이 클래스의 경우, `target`은 일반적으로 정의된 의미가 없습니다.
상속함: | [IntransitiveActivity](#class-intransitiveactivity)
속성: | [IntransitiveActivity](#class-intransitiveactivity) 모든 속성을 상속받습니다.

>예시 14
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 직장에 도착했습니다",
>  "type": "Arrive",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "location": {
>    "type": "Place",
>    "name": "직장"
>  },
>  "origin": {
>    "type": "Place",
>    "name": "집"
>  }
>}
>```

#### [Class] [Create](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Create`
비고: | `actor`가 `object`를 생성했음(created)을 나타냅니다
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 15
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 노트를 생성했습니다",
>  "type": "Create",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Note",
>    "name": "간단한 노트",
>    "content": "이것은 간단한 노트입니다"
>  }
>}
>```

#### [Class] [Delete](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Delete`
비고: | `actor`가 `object`를 삭제했음(deleted)을 나타냅니다. 특별히 지정된 경우, `origin`은 `object`가 삭제된 컨텍스트를 나타냅니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 16
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 노트를 삭제했습니다",
>  "type": "Delete",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1",
>  "origin": {
>    "type": "Collection",
>    "name": "Sally의 노트들"
>  }
>}
>```

#### [Class] [Follow](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Follow`
비고: | `actor`가 `object`를 "따르고(following)" 있음을 나타냅니다. Following은 일반적으로 소셜 시스템 내에서 액터가 주어진 객체에 의해 또는 주어진 객체가 수행하는 모든 액티비티에 관심이 있다 라는 의미로 정의됩니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 17
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John을 팔로우 했습니다",
>  "type": "Follow",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Person",
>    "name": "John"
>  }
>}
>```

#### [Class] [Ignore](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Ignore`
비고: | `actor`가 `object`를 무시하고(ignoring) 있음을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 18
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 노트를 무시했습니다",
>  "type": "Ignore",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1"
>}
>```


#### [Class] [Join](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Join`
비고: | `actor`가 `object`에 합류(join)했음을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 19
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 그룹에 참가했습니다",
>  "type": "Join",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Group",
>    "name": "간단한 그룹"
>  }
>}
>```

#### [Class] [Leave](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Leave`
비고: | `actor`가 `object`를 떠났음(left)을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 20
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 직장을 떠났습니다",
>  "type": "Leave",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Place",
>    "name": "직장"
>  }
>}
>```

>예시 21
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 그룹을 떠났습니다",
>  "type": "Leave",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Group",
>    "name": "간단한 그룹"
>  }
>}
>```

#### [Class] [Like](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Like`
비고: | `actor`가 `object`를 좋아(likes)하거나, 추천(recommends)하거나 또는 지지(endorses)함을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 22
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 노트를 좋아합니다",
>  "type": "Like",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1"
>}
>```

#### [Class] [Offer](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Offer`
비고: | `actor`가 `object`를 제공(offering)하고 있음을 나타냅니다. 특별히 지정된 경우, `origin`은 `object`가 제공하는 개체(entity)를 나타냅니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 23
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 Leweis에게 50% 할인을 제시했습니다",
>  "type": "Offer",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "http://www.types.example/ProductOffer",
>    "name": "50% 할인!"
>  },
>  "target": {
>    "type": "Person",
>    "name": "Lewis"
>  }
>}
>```


#### [Class] [Invite](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Invite`
비고: | `actor`가 `object`에 대한 초대(invitation)를 `target`으로 확장하는, [Offer](#class-offer)의 특화된 경우입니다.
상속함: | [Offer](#class-offer)
속성: | [Offer](#class-offer)로부터 모든 속성을 상속받습니다.

>예시 24
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John과 Lisa를 파티에 초대했습니다",
>  "type": "Invite",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Event",
>    "name": "파티"
>  },
>  "target": [
>    {
>      "type": "Person",
>      "name": "John"
>    },
>    {
>      "type": "Person",
>      "name": "Lisa"
>    }
>  ]
>}
>```

#### [Class] [Reject](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Reject`
비고: | `actor`가 `object`를 거부(rejecting)함을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 25
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 파티 초대를 거부했습니다",
>  "type": "Reject",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Invite",
>    "actor": "http://john.example.org",
>    "object": {
>      "type": "Event",
>      "name": "Jim을 위한 송별회"
>    }
>  }
>}
>```

#### [Class] [TentativeReject](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeReject`
비고: | 거부함(rejection)이 잠정적(tentative)임을 나타내는, [Reject](#class-reject)의 특화된 경우입니다.
상속함: | [Reject](#class-reject)
속성: | [Reject](#class-reject)로부터 모든 속성을 상속받습니다.

>예시 26
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 잠정적으로 파티 초대를 거부했습니다",
>  "type": "TentativeReject",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Invite",
>    "actor": "http://john.example.org",
>    "object": {
>      "type": "Event",
>      "name": "Jim을 위한 송별회"
>    }
>  }
>}
>```

#### [Class] [Remove](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Remove`
비고: | `actor`가 `object`를 제거(removing)하고 있음을 나타냅니다. 특별히 지정된 경우, `origin`은 `object`가 제거되는 컨텍스트를 나타냅니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 27
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 노트 폴더에서 노트를 제거했습니다",
>  "type": "Remove",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1",
>  "target": {
>    "type": "Collection",
>    "name": "노트 폴더"
>  }
>}
>```

>예시 28
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "게시판 관리자는 샐리를 그룹에서 제거했습니다",
>  "type": "Remove",
>  "actor": {
>    "type": "http://example.org/Role",
>    "name": "게시판 관리자"
>  },
>  "object": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "origin": {
>    "type": "Group",
>    "name": "간단한 그룹"
>  }
>}
>```

#### [Class] [Undo](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Undo`
비고: | `actor`가 `object`를 실행취소(undoing)하고 있음을 나타냅니다. 대부분의 경우, `object`는 이전에 수행된 일부 작업을 설명하는 [Activity](#class-activity)입니다 (예를 들어, 어떤 사람이 특정 기사를 "좋아했을수도(liked)" 있지만, 어떠한 이유에서인지 차후에 그 행동을 실행취소 할 수도 있습니다). </br> 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 29
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John에게 보낸 제안을 철회하였습니다",
>  "type": "Undo",
>  "actor": "http://sally.example.org",
>  "object": {
>    "type": "Offer",
>    "actor": "http://sally.example.org",
>    "object": "http://example.org/posts/1",
>    "target": "http://john.example.org"
>  }
>}
>```

#### [Class] [Update](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Update`
비고: | `actor`가 `object`를 업데이트(updated) 했음을 나타냅니다. 그러나 이 어휘에서는 `object`에 대한 수정 방법들을 설명하기 위한 메커니즘을 정의하지 않습니다. </br> 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 30
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 그녀의 노트를 업데이트했습니다",
>  "type": "Update",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1"
>}
>```

#### [Class] [View](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#View`
비고: | `actor`가 객체를 보았음(viewed)을 나타냅니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 31
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 기사(article)를 읽었습니다",
>  "type": "View",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Article",
>    "name": "당신이 Activity Streams에 대해 알아야 할 것들"
>  }
>}
>```

#### [Class] [Listen](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Listen`
비고: | `actor`가 `object`를 청취했음(listened)을 나타냅니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 32
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 음악을 들었습니다",
>  "type": "Listen",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/music.mp3"
>}
>```

#### [Class] [Read](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Read`
비고: | `actor`가 `object`를 읽었음(read)을 나타냅니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 33
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 블로그 게시물을 읽었습니다",
>  "type": "Read",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/posts/1"
>}
>```

#### [Class] [Move](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Move`
비고: | `actor`가 `object`를 `origin`에서 `target`으로 옮겼음(moved)을 나타냅니다. `origin`이나 `target`이 지정되지 않았을 경우, 이들의 값은 컨텍스트에 따라 결정될 수 있습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 34
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 리스트 A에서 리스트 B로 게시물을 옮겼습니다.",
>  "type": "Move",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/posts/1",
>  "target": {
>    "type": "Collection",
>    "name": "리스트 B"
>  },
>  "origin": {
>    "type": "Collection",
>    "name": "리스트 A"
>  }
>}
>```

#### [Class] [Travel](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Travel`
비고: | `actor`가 `object`를 `origin`에서 `target`으로 이동중(traveling)임을 나타냅니다. `Travel`은 `actor`가 직접적인 객체(direct object)를 지정하는 `IntransitiveObject` 입니다. `origin`이나 `target`이 지정되지 않았을 경우, 이들의 값은 컨텍스트에 따라 결정될 수 있습니다.
상속함: | [IntransitiveActivity](#class-intransitiveactivity)
속성: | [IntransitiveActivity](#class-intransitiveactivity)로부터 모든 속성을 상속받습니다.

>예시 35
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 직장에서 집으로 갔습니다.",
>  "type": "Travel",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "target": {
>    "type": "Place",
>    "name": "집"
>  },
>  "origin": {
>    "type": "Place",
>    "name": "직장"
>  }
>}
>```

#### [Class] [Announce](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Announce`
비고: | `actor`가 `target`의 주의를 `object`에 두고 있음을 나타냅니다. </br> 이 클래스의 경우, `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 36
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 직장에 도착했다고 발표(announced)했습니다",
>  "type": "Announce",
>  "actor": {
>    "type": "Person",
>    "id": "http://sally.example.org",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Arrive",
>    "actor": "http://sally.example.org",
>    "location": {
>      "type": "Place",
>      "name": "직장"
>    }
>  }
>}
>```

#### [Class] [Block](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Block`
비고: | `actor`가 `object`를 차단중(blocking)임을 나타냅니다. 차단(Blocking)은 더 강력한 형태의 [Ignore](#class-ignore)입니다. 이 클래스의 일반적인 용도는, 소셜 시스템에서 한 사용자가 다른 사용자의 액티비티나 콘텐츠를 차단할 수 있는 방법을 지원하는 것입니다. `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | [Ignore](#class-ignore)
속성: | [Ignore](#class-ignore)로부터 모든 속성을 상속받습니다.

>예시 37
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 Joe를 차단했습니다",
>  "type": "Block",
>  "actor": "http://sally.example.org",
>  "object": "http://joe.example.org"
>}
>```

#### [Class] [Flag](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Flag`
비고: | `actor`가 `object`를 "신고(flagging)" 하고 있음을 나타냅니다. 신고는 일반적으로 여러 소셜 플랫폼에서 콘텐츠를 여러가지 이유로 부적절하다고 보고하는 것 으로 정의됩니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 38
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 부적절한 노트를 신고했습니다",
>  "type": "Flag",
>  "actor": "http://sally.example.org",
>  "object": {
>    "type": "Note",
>    "content": "An inappropriate note"
>  }
>}
>```

#### [Class] [Dislike](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Dislike`
비고: | `actor`가 `object`를 싫어함(dislikes)을 나타냅니다.
상속함: | [Activity](#class-activity)
속성: | [Activity](#class-activity)로부터 모든 속성을 상속받습니다.

>예시 39
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 게시물을 싫어했습니다",
>  "type": "Dislike",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1"
>}
>```

#### [Class] [Question](#31-액티비티-타입-activity-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Question`
비고: | 묻는 질문(question)을 나타냅니다. Question 객체들은 [IntransitiveActivity](#class-intransitiveactivity)의 확장입니다. 즉 Question 객체는 Activity지만 직접적인 객체(direct object)는 질문 그 자체이므로 [object](#class-object) 속성을 포함하지 않습니다. </br> [anyOf](#class-anyof) 또는 [oneOf](#class-oneof) 속성중 하나를 사용하여 가능한 답변을 표현 *할 수도* 있지만, Question 객체에는 두 객체 모두 보유하는것을 *절대로 하지 말아야* 합니다.
상속함: | [IntransitiveActivity](#class-intransitiveactivity)
속성: | [oneOf](#class-oneof) \| [anyOf](#class-anyof) \| [closed](#class-closed) </br> [IntransitiveActivity](#class-intransitiveactivity)로부터 모든 속성을 상속받습니다.

>예시 40
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "어느게 정답일까요?",
>  "oneOf": [
>    {
>      "type": "Note",
>      "name": "선택지 A"
>    },
>    {
>      "type": "Note",
>      "name": "선택지 B"
>    }
>  ]
>}
>```

>예시 41
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "어느게 정답일까요?",
>  "closed": "2016-05-10T00:00:00Z"
>}
>```

### 3.2 [액터 타입 (Actor Types)](#목차-table-of-contents)

액터 타입은 액티비티를 수행할 수 있는 [Object](#class-object) 타입입니다.

핵심 액터 타입은 다음과 같은 타입들을 포함합니다:

- [Application](#class-application)
- [Group](#class-group)
- [Organization](#class-organization)
- [Person](#class-person)
- [Service](#class-service)

#### [Class] [Application](#32-액터-타입-actor-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Application`
비고: | 소프트웨어 어플리케이션(application)을 표현합니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 42
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Application",
>  "name": "예시제조기 3000"
>}
>```

#### [Class] [Group](#32-액터-타입-actor-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Group`
비고: | 액터들의 공식 또는 비공식 집단을 나타냅니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 43
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Group",
>  "name": "Austin의 큰수염"
>}
>```

#### [Class] [Organization](#32-액터-타입-actor-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Organization`
비고: | 조직(organization)을 나타냅니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 44
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Organization",
>  "name": "예시 (주)"
>}
>```

#### [Class] [Person](#32-액터-타입-actor-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Person`
비고: | 독립적인 사람(person)을 나타냅니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 45
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Person",
>  "name": "Sally Smith"
>}
>```

#### [Class] [Service](#32-액터-타입-actor-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Service`
비고: | 모든 종류의 서비스(service)를 나타냅니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 46
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Service",
>  "name": "최상의 웹 서비스"
>}
>```

### 3.3 [객체와 링크 타입 (Object and Link Types)](#목차-table-of-contents)

모든 객체 타입들은 기본 [Object](#class-object) 타입을 상속합니다. 링크 타입들은 기본 [Link](#class-link) 타입을 상속합니다. 일부 특정한 객체 타입들은 일반화된 객체 타입의 하위 타입이나 특수화된 경우입니다. (예를 들어, [Like](#class-like) 유형은 [Activity](#class-activity) 유형보다 구체적인 경우입니다).

객체 타입은 다음과 같은 타입들을 포함합니다:

- [Article](#class-article)
- [Audio](#class-audio)
- [Document](#class-document)
- [Event](#class-event)
- [Image](#class-image)
- [Note](#class-note)
- [Page](#class-page)
- [Place](#class-place)
- [Profile](#class-profile)
- [Relationship](#class-relationship)
- [Tombstone](#class-tombstone)
- [Video](#class-video)

링크 타입은 다음과 같은 타입들을 포함합니다:

- [Mention](#class-mention)

#### [Class] [Relationship](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Relationship`
비고: | 두 개개인 사이의 관계(relationship)을 나타냅니다. [subject](#class-subject) 및 [object](#class-object) 속성은 연결된 개인을 식별하는데 사용됩니다. </br> 추가적인 정보는 [5.2 개체 간의 관계 표현](#52-개체간의-관계-표현-representing-relationships-between-entities) 을 참고하시길 바랍니다.
상속함: | [Object](#class-object)
속성: | [subject](#class-subject) \| [object](#class-object) \| [relationship](#class-relationship) </br> [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 47
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John의 지인입니다",
>  "type": "Relationship",
>  "subject": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "relationship": "http://purl.org/vocab/relationship/acquaintanceOf",
>  "object": {
>    "type": "Person",
>    "name": "John"
>  }
>}
>```

#### [Class] [Article](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Article`
비고: | 모든 종류의 다중-문단으로 쓰여진 작업을 나타냅니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 48
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Article",
>  "name": "정말 대단한 하루였어",
>  "content": "<div>... 나한테 일어난 일을 넌 절대 못믿을거야 ...</div>",
>  "attributedTo": "http://sally.example.org"
>}
>```

#### [Class] [Document](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Document`
비고: | 모든 종류의 문서(document)를 나타냅니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 49
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Document",
>  "name": "4분기 판매 동향",
>  "url": "http://example.org/4q-sales-forecast.pdf"
>}
>```

#### [Class] [Audio](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Audio`
비고: | 모든 종류의 청각(audio) 문서를 나타냅니다.
상속함: | [Document](#class-document)
속성: | [Document](#class-document)로부터 모든 속성을 상속받습니다.

>예시 50
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Audio",
>  "name": "유명한 기술자와의 인터뷰",
>  "url": {
>    "type": "Link",
>    "href": "http://example.org/podcast.mp3",
>    "mediaType": "audio/mp3"
>  }
>}
>```

#### [Class] [Image](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Image`
비고: | 모든 종류의 시각(image) 문서를 나타냅니다.
상속함: | [Document](#class-document)
속성: | [Document](#class-document)로부터 모든 속성을 상속받습니다.

>예시 51
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Image",
>  "name": "수레위로 뛰어든 고양이",
>  "url": [
>    {
>      "type": "Link",
>      "href": "http://example.org/image.jpeg",
>      "mediaType": "image/jpeg"
>    },
>    {
>      "type": "Link",
>      "href": "http://example.org/image.png",
>      "mediaType": "image/png"
>    }
>  ]
>}
>```

#### [Class] [Video](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Video`
비고: | 모든 종류의 영상(video) 문서를 나타냅니다.
상속함: | [Document](#class-document)
속성: | [Document](#class-document)로부터 모든 속성을 상속받습니다.

>예시 52
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Video",
>  "name": "공놀이 하는 강아지",
>  "url": "http://example.org/video.mkv",
>  "duration": "PT2H"
>}
>```

#### [Class] [Note](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Note`
비고: | 일반적으로 한 문단 이하로 짧게 쓰여진 작업을 나타냅니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 53
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Note",
>  "name": "경고문",
>  "content": "오늘은 비가 내릴것 같네요. 우산을 챙기세요!"
>}
>```

#### [Class] [Page](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Page`
비고: | 웹 페이지(Page)를 나타냅니다.
상속함: | [Document](#class-document)
속성: | [Document](#class-document)로부터 모든 속성을 상속받습니다.

>예시 54
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Page",
>  "name": "Omaha 기상 보고서",
>  "url": "http://example.org/weather-in-omaha.html"
>}
>```

#### [Class] [Event](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Event`
비고: | 모든 종류의 이벤트(event)를 나타냅니다.
상속함: | [Object](#class-object)
속성: | [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 55
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Event",
>  "name": "Jim을 위한 송별회",
>  "startTime": "2014-12-31T23:00:00-08:00",
>  "endTime": "2015-01-01T06:00:00-08:00"
>}
>```

#### [Class] [Place](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Place`
비고: | 논리적 또는 물리적 위치를 나타냅니다. 추가적인 정보는 [5.3 장소 표시](#53-장소-표현-representing-places) 를 참고하시길 바랍니다.
상속함: | [Object](#class-object)
속성: | [accuracy](#class-accuracy) \| [altitude](#class-altitude) \| [latitude](#class-latitude) \| [longitude](#class-longitude) \| [radius](#class-radius) \| [units](#class-units) </br> [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 56
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "직장"
>}
>```

>예시 57
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Fresno 지역",
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "radius": 15,
>  "units": "miles"
>}
>```

#### [Class] [Mention](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Mention`
비고: | @mention을 나타내는 특수한 [Link](#class-link)입니다.
상속함: | [Link](#class-link)
속성: | [Link](#class-link)로부터 모든 속성을 상속받습니다.

>Example 58
>
>```json
>{
>  "summary": "Mention of Joe by Carrie in her note",
>}
>```

>예시 58
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Carrie의 노트에 있는 Joe에 대한 언급(mention)",
>  "type": "Mention",
>  "href": "http://example.org/joe",
>  "name": "Joe"
>}
>```

#### [Class] [Profile](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Profile`
비고: | 프로필(Profile)은 일반적으로 [액터 타입](#32-액터-타입-actor-types) 객체를 설명하는데 사용되는, 다른 객체를 설명하는 컨텐츠 객체입니다. [describes](#class-describes) 속성은 프로필에서 설명하는 객체를 참조하는데 사용됩니다.
상속함: | [Object](#class-object)
속성: | [describes](#class-describes) </br> [Object](#class-object)로부터 모든 속성을 상속받습니다.

>Example 59
>
>```json
>{
>  "summary": "Sally's Profile",
>}
>```

>예시 59
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Profile",
>  "summary": "Sally의 프로필",
>  "describes": {
>    "type": "Person",
>    "name": "Sally Smith"
>  }
>}
>```

#### [Class] [Tombstone](#33-객체와-링크-타입-object-and-link-types)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Tombstone`
비고: | 묘지(Tombstone)는 삭제된 컨텐츠 객체를 나타냅니다. [Collection](#class-collection)에서 이 위치에 객체가 있었지만, 지금은 삭제된 것을 나타내기 위해 사용할 수 있습니다.
상속함: | [Object](#class-object)
속성: | [formerType](#class-formertype) \| [deleted](#class-deleted) </br> [Object](#class-object)로부터 모든 속성을 상속받습니다.

>예시 60
>
>```json
>{
>  "type": "OrderedCollection",
>  "totalItems": 3,
>  "name": "휴가 사진들 2016",
>  "orderedItems": [
>    {
>      "type": "Image",
>      "id": "http://image.example/1"
>    },
>    {
>      "type": "Tombstone",
>      "formerType": "Image",
>      "id": "http://image.example/2",
>      "deleted": "2016-03-17T00:00:00Z"
>    },
>    {
>      "type": "Image",
>      "id": "http://image.example/3"
>    }
>  ]
>}
>```

## 4. [속성 (Properties)](#목차-table-of-contents)

기반 URI: `https://www.w3.org/ns/activitystreams#`.

일반적인 속성들은 다음과 같습니다:

 [actor](#class-actor) \|
 [attachment](#class-attachment) \|
 [attributedTo](#class-attributedto) \|
 [audience](#class-audience) \|
 [bcc](#class-bcc) \|
 [bto](#class-bto) \|
 [cc](#class-cc) \|
 [context](#class-context) \|
 [current](#class-current) \|
 [first](#class-first) \|
 [generator](#class-generator) \|
 [icon](#class-icon) \|
 [id](#class-id) \|
 [image](#class-image) \|
 [inReplyTo](#class-inreplyto) \|
 [instrument](#class-instrument) \|
 [last](#class-last) \|
 [location](#class-location) \|
 [items](#class-items) \|
 [oneOf](#class-oneof) \|
 [anyOf](#class-anyof) \|
 [closed](#class-closed) \|
 [origin](#class-origin) \|
 [next](#class-next) \|
 [object](#class-object) \|
 [prev](#class-prev) \|
 [preview](#class-preview) \|
 [result](#class-result) \|
 [replies](#class-replies) \|
 [tag](#class-tag) \|
 [target](#class-target) \|
 [to](#class-to) \|
 [type](#class-type) \|
 [url](#class-url) \|
 [accuracy](#class-accuracy) \|
 [altitude](#class-altitude) \|
 [content](#class-content) \|
 [name](#class-name) \|
 [duration](#class-duration) \|
 [height](#class-height) \|
 [href](#class-href) \|
 [hreflang](#class-hreflang) \|
 [partOf](#class-partof) \|
 [latitude](#class-latitude) \|
 [longitude](#class-longitude) \|
 [mediaType](#class-mediatype) \|
 [endTime](#class-endtime) \|
 [published](#class-published) \|
 [startTime](#class-starttime) \|
 [radius](#class-radius) \|
 [rel](#class-rel) \|
 [startIndex](#class-startindex) \|
 [summary](#class-summary) \|
 [totalItems](#class-totalitems) \|
 [units](#class-units) \|
 [updated](#class-updated) \|
 [width](#class-width) \|
 [subject](#class-subject) \|
 [relationship](#class-relationship) \|
 [describes](#class-describes) \|
 [formerType](#class-formertype) \|
 [deleted](#class-deleted)

"도메인(Domain)"은 속성 용어가 적용되는 객체의 타입을 나타냅니다. "범위(Range)"는 속성 용어가 가질수 있는 값의 타입을 나타냅니다. 특정 속성은 다른 용어의 "하위속성(Subproperty)"으로 표시됩니다. 즉, 해당 용어는 참조된 용어의 특수화된 경우입니다. 예를 들어 [actor](#class-actor)는 [attributedTo](#class-attributedto)의 하위 속성입니다. "기능적(Functional)"으로 표시되어 있는 속성은 하나의 값만 가질수도 있습니다. "기능적(Functional)"으로 표시되지 않은 항목은 여러개의 값을 가질 수 있습니다.

#### [Class] [id](#4-속성-properties)

설명| |
--|--
URI: | `@id`
비고: | [Object](#class-object)나 [Link](#class-link)에 대한 전역 고유 식별자를 제공합니다.
도메인: | [Object](#class-object) \| [Link](#class-link)
범위: | `anyURI`
기능적: | True

>예시 61
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "Foo",
>  "id": "http://example.org/foo"
>}
>```

#### [Class] [type](#4-속성-properties)

설명| |
--|--
URI: | `@type`
비고: | [Object](#class-object)나 [Link](#class-link) 타입을 식별합니다. 다중 값을 지정 할 수도 있습니다.
도메인: | [Object](#class-object) \| [Link](#class-link)
범위: | `anyURI`

>예시 62
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A foo",
>  "type": "http://example.org/Foo"
>}
>```

#### [Class] [actor](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#actor`
비고: | 액티비티를 수행했거나 수행할 것으로 예상되는 하나 이상의 개체들을 표현합니다. 단일 액티비티에는 여러 `actor`가 있을 수 있습니다. `actor`는 간접 [Link](#class-link)를 사용하여 지정 *할 수도* 있습니다.
도메인: | [Activity](#class-activity)
범위: | [Object](#class-object) \| [Link](#class-link)
하위속성: | [attributedTo](#class-attributedto)

>예시 63
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 Foo 객체를 제공했습니다",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/foo"
>}
>```

>예시 64
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 Foo 객체를 제공했습니다",
>  "type": "Offer",
>  "actor": {
>    "type": "Person",
>    "id": "http://sally.example.org",
>    "summary": "Sally"
>  },
>  "object": "http://example.org/foo"
>}
>```

>예시 65
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally와 Joe는 Foo 객체를 제공했습니다",
>  "type": "Offer",
>  "actor": [
>    "http://joe.example.org",
>    {
>      "type": "Person",
>      "id": "http://sally.example.org",
>      "name": "Sally"
>    }
>  ],
>  "object": "http://example.org/foo"
>}
>```

#### [Class] [attachment](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#attachment`
비고: | 특별한 처리가 필요할수도 있는 개체에 첨부(attached)되었거나 관련된 리소스를 식별합니다. 이메일의 첨부파일과 의미적으로 유사한 모델을 제공하는것 이 목적입니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 66
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Note",
>  "name": "제 고양이를 보신적이 있나요?",
>  "attachment": [
>    {
>      "type": "Image",
>      "content": "이렇게 생겼어요.",
>      "url": "http://example.org/cat.jpeg"
>    }
>  ]
>}
>```

#### [Class] [attributedTo](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#attributedTo`
비고: | 이 객체가 속하는(attributed) 하나 이상의 개체들을 식별합니다. 속하는 개체들은 액터(Actor)가 아닐 수도 있습니다. 예를 들어, 어떤 객체는 '다른 액티비티가 완료되는것' 에 속할 수도 있습니다.
도메인: | [Link](#class-link) \| [Object](#class-object)
범위: | [Link](#class-link) \| [Object](#class-object)

>예시 67
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Image",
>  "name": "낮잠을 자고 있는 내 고양이",
>  "url": "http://example.org/cat.jpeg",
>  "attributedTo": [
>    {
>      "type": "Person",
>      "name": "Sally"
>    }
>  ]
>}
>```

>예시 68
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Image",
>  "name": "낮잠을 자고 있는 내 고양이",
>  "url": "http://example.org/cat.jpeg",
>  "attributedTo": [
>    "http://joe.example.org",
>    {
>      "type": "Person",
>      "name": "Sally"
>    }
>  ]
>}
>```

#### [Class] [audience](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#audience`
비고: | 해당 객체와 관련있는 것으로 간주되는, 총 개체수를 나타내는 하나 이상의 개체들을 식별합니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 69
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "휴무일 발표",
>  "type": "Note",
>  "content": "목요일은 회사 전체 휴무일입니다. 휴일을 즐기세요!",
>  "audience": {
>    "type": "http://example.org/Organization",
>    "name": "(유) ExampleCo"
>  }
>}
>```

#### [Class] [bcc](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#bcc`
비고: | 이 객체(Object)의 2차적 비공개 청자에 속하는 하나 이상의 Objects를 식별합니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 70
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John에게 게시물을 제공했습니다",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org",
>  "bcc": [ "http://joe.example.org" ]
>}
>```

#### [Class] [bto](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#bto`
비고: | 이 객체(Object)의 주요 비공개 청자의 일부인 Object를 식별합니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 71
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John에게 게시물을 제공했습니다",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org",
>  "bto": [ "http://joe.example.org" ]
>}
>```

#### [Class] [cc](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#cc`
비고: | 이 객체(Object)의 2차적 공개 청자의 일부인 Object를 식별합니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 72
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John에게 게시물을 제공했습니다",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org",
>  "cc": [ "http://joe.example.org" ]
>}
>```

#### [Class] [context](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#context`
비고: | 개체가 존재하거나 액티비티가 실행된 된 컨텍스트(context)를 식별합니다. </br> "컨텍스트"라는 개념은 의도적으로 모호하게 사용되었습니다. 의도되었던 기능은 공통적인 컨텍스트 또는 목적을 공유하는 객체와 액티비티를 그룹화하는 수단으로 사용하려는 것입니다. 예시로는 일반적인 프로젝트 또는 이벤트와 관련된 모든 액티비티들 입니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 73
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "컨텍스트 1 안의 액티비티들",
>  "type": "Collection",
>  "items": [
>    {
>      "type": "Offer",
>      "actor": "http://sally.example.org",
>      "object": "http://example.org/posts/1",
>      "target": "http://john.example.org",
>      "context": "http://example.org/contexts/1"
>    },
>    {
>      "type": "Like",
>      "actor": "http://joe.example.org",
>      "object": "http://example.org/posts/2",
>      "context": "http://example.org/contexts/1"
>    }
>  ]
>}
>```

#### [Class] [current](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#current`
비고: | 페이징 된 컬렉션에서 가장 최근에 업데이트된 구성원의 항목이 포함된 페이지를 나타냅니다.
도메인: | [Collection](#class-collection)
범위: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
기능적: | True

>예시 74
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 블로그 포스트들",
>  "type": "Collection",
>  "totalItems": 3,
>  "current": "http://example.org/collection",
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

>예시 75
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 블로그 포스트들",
>  "type": "Collection",
>  "totalItems": 3,
>  "current": {
>    "type": "Link",
>    "summary": "가장 최근의 항목들",
>    "href": "http://example.org/collection"
>  },
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

#### [Class] [first](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#first`
비고: | 페이징 된 컬렉션에서 컬렉션의 가장 앞에있는 페이지를 나타냅니다.
도메인: | [Collection](#class-collection)
범위: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
기능적: | True

>예시 76
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 블로그 포스트들",
>  "type": "Collection",
>  "totalItems": 3,
>  "first": "http://example.org/collection?page=0"
>}
>```

>예시 77
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 블로그 포스트들",
>  "type": "Collection",
>  "totalItems": 3,
>  "first": {
>    "type": "Link",
>    "summary": "첫 페이지",
>    "href": "http://example.org/collection?page=0"
>  }
>}
>```

#### [Class] [generator](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#generator`
비고: | 객체를 생성한(generated) 개체(예: 어플리케이션)을 식별합니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 78
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "content": "여기 있는게 전부에요.",
>  "generator": {
>    "type": "Application",
>    "name": "예시제조기 3000"
>  }
>}
>```

#### [Class] [icon](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#icon`
비고: | 이 객체의 아이콘(icon)을 나타내는 개체를 나타냅니다. 이미지의 가로-세로 비율은 1(수평) 대 1(수직)이여야 하며 작은 크기로 보여주는것에 적합하여야 합니다.
도메인: | [Object](#class-object)
범위: | [Image](#class-image) \| [Link](#class-link)

>예시 79
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "content": "여기 있는게 전부에요.",
>  "icon": {
>    "type": "Image",
>    "name": "노트 아이콘",
>    "url": "http://example.org/note.png",
>    "width": 16,
>    "height": 16
>  }
>}
>```

>예시 80
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "content": "간단한 노트",
>  "icon": [
>    {
>      "type": "Image",
>      "summary": "노트 (16x16)",
>      "url": "http://example.org/note1.png",
>      "width": 16,
>      "height": 16
>    },
>    {
>      "type": "Image",
>      "summary": "노트 (32x32)",
>      "url": "http://example.org/note2.png",
>      "width": 32,
>      "height": 32
>    }
>  ]
>}
>```

#### [Class] [image](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#image`
비고: | 이 객체의 이미지(image)를 기술하는 개체를 나타냅니다. icon속성과 달리 종횡비나 디스클레이에 대한 크기 제한은 없습니다.
도메인: | [Object](#class-object)
범위: | [Image](#class-image) \| [Link](#class-link)

>예시 81
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "간단한 노트",
>  "type": "Note",
>  "content": "여기 있는게 전부에요.",
>  "image": {
>    "type": "Image",
>    "name": "고양이",
>    "url": "http://example.org/cat.png"
>  }
>}
>```

>예시 82
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "간단한 노트",
>  "type": "Note",
>  "content": "여기 있는게 전부에요.",
>  "image": [
>    {
>      "type": "Image",
>      "name": "고양이 1",
>      "url": "http://example.org/cat1.png"
>    },
>    {
>      "type": "Image",
>      "name": "고양이 2",
>      "url": "http://example.org/cat2.png"
>    }
>  ]
>}
>```

#### [Class] [inReplyTo](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#inReplyTo`
비고: | 이 객체를 응답으로 간주하는 하나 이상의 개체를 나타냅니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 83
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "content": "여기 있는게 전부에요.",
>  "inReplyTo": {
>    "summary": "이전 노트",
>    "type": "Note",
>    "content": "거기에 더 있나요?"
>  }
>}
>```

>예시 84
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "content": "여기 있는게 전부에요.",
>  "inReplyTo": "http://example.org/posts/1"
>}
>```

#### [Class] [instrument](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#instrument`
비고: | [Activity](#class-activity)가 완료시 사용된 (또는 사용되는) 하나 이상의 객체들을 식별합니다.
도메인: | [Activity](#class-activity)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 85
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 '최상의 음악 서비스'에서 음악을 들었습니다",
>  "type": "Listen",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/foo.mp3",
>  "instrument": {
>    "type": "Service",
>    "name": "최상의 음악 서비스"
>  }
>}
>```

#### [Class] [last](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#last`
비고: | 페이징 된 [Collection](#class-collection)에서 컬렉션의 뒷방향으로 가장 멀리있는 페이지를 나타냅니다.
도메인: | [Collection](#class-collection)
범위: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
기능적: | True

>예시 86
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "컬렉션",
>  "type": "Collection",
>  "totalItems": 3,
>  "last": "http://example.org/collection?page=1"
>}
>```

>예시 87
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "컬렉션",
>  "type": "Collection",
>  "totalItems": 5,
>  "last": {
>    "type": "Link",
>    "summary": "마지막 페이지",
>    "href": "http://example.org/collection?page=1"
>  }
>}
>```

#### [Class] [location](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#location`
비고: | 주어진 객체와 관련된 하나 이상의 물리적 또는 논리적인 위치(locations)를 나타냅니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 88
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Person",
>  "name": "Sally",
>  "location": {
>    "name": "아라비아 해를 넘어서, 소코트라 섬 자연 보호구역의 동쪽",
>    "type": "Place",
>    "longitude": 12.34,
>    "latitude": 56.78,
>    "altitude": 90,
>    "units": "m"
>  }
>}
>```

#### [Class] [items](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#items`
비고: | 컬렉션에 포함된 항목(items)을 식별합니다. 항목은 정렬되었거나 정렬되지 않았을 수도 있습니다.
도메인: | [Collection](#class-collection)
범위: | [Object](#class-object) \| [Link](#class-link) \| [ [Object](#class-object) \| [Link](#class-link) ]의 정렬된 리스트

>예시 89
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 노트",
>  "type": "Collection",
>  "totalItems": 2,
>  "items": [
>    {
>      "type": "Note",
>      "name": "송별회 알림"
>    },
>    {
>      "type": "Note",
>      "name": "회의 2016-11-17"
>    }
>  ]
>}
>```

>예시 90
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 노트",
>  "type": "OrderedCollection",
>  "totalItems": 2,
>  "orderedItems": [
>    {
>      "type": "Note",
>      "name": "회의 2016-11-17"
>    },
>    {
>      "type": "Note",
>      "name": "송별회 알림"
>    }
>  ]
>}
>```

#### [Class] [oneOf](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#oneOf`
비고: | 질문(Question)에 대한 독점적인 선택지를 식별합니다. `oneOf`를 사용하는 Question에 대해서는 하나의 답변만 할수 있음을 의미합니다. Question에 여러개의 답변이 있을수 있음을 나타내려면 [anyOf](#class-anyof)를 사용하시길 바랍니다.
도메인: | [Question](#class-question)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 91
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "무엇이 정답일까요?",
>  "oneOf": [
>    {
>      "type": "Note",
>      "name": "선택지 A"
>    },
>    {
>      "type": "Note",
>      "name": "선택지 B"
>    }
>  ]
>}
>```

#### [Class] [anyOf](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#anyOf`
비고: | 질문(Question)에 대한 포괄적인 선택지를 식별합니다. `anyOf`를 사용하는 Question에 대해서는 여러개의 답변이 있을수 있음을 나타냅니다. Question에 대해 답변이 단 하나만 존재할수 있음을 나타내려면 [oneOf](#class-oneof)를 사용하시길 바랍니다.
도메인: | [Question](#class-question)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 92
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "무엇이 정답일까요?",
>  "anyOf": [
>    {
>      "type": "Note",
>      "name": "선택지 A"
>    },
>    {
>      "type": "Note",
>      "name": "선택지 B"
>    }
>  ]
>}
>```

#### [Class] [closed](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#closed`
비고: | 질문이 마감(closed)되었으며, 더 이상 답변을 받지 않음을 나타냅니다.
도메인: | [Question](#class-question)
범위: | [Object](#class-object) \| [Link](#class-link) \| `xsd:dateTime` \| `xsd:boolean`

>예시 93
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "무엇이 정답일까요?",
>  "closed": "2016-05-10T00:00:00Z"
>}
>```

#### [Class] [origin](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#origin`
비고: | 액티비티가 지시하는 액티비티의 간접적인 객체를 표현합니다. 원산지(origin)의 정확한 의미는 영어 전치사 "from"의 목적 입니다. 예를 들어, "John이 품목을 리스트A 에서 리스트B로 옮겼습니다" 액티비티에서 액티비티의 원산지는 "리스트A" 입니다.
도메인: | [Activity](#class-activity)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 94
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 리스트 A에서 리스트 B로 게시물을 옮겼습니다.",
>  "type": "Move",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": {
>    "type": "Collection",
>    "name": "리스트 B"
>  },
>  "origin": {
>    "type": "Collection",
>    "name": "리스트 A"
>  }
>}
>```

#### [Class] [next](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#next`
비고: | 페이징 된 [Collection](#class-collection)에서 항목들의 다음(next) 페이지를 나타냅니다.
도메인: | [CollectionPage](#class-collectionpage)
범위: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
기능적: | True

>예시 95
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 블로그 포스트 2 페이지",
>  "type": "CollectionPage",
>  "next": "http://example.org/collection?page=2",
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

>예시 96
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 블로그 포스트 2 페이지",
>  "type": "CollectionPage",
>  "next": {
>    "type": "Link",
>    "name": "다음 페이지",
>    "href": "http://example.org/collection?page=2"
>  },
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

#### [Class] [object](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#object`
비고: | [Activity](#class-activity) 내에서 사용될 경우, 액티비티의 직접적인 대상인 객체(object)를 설명합니다. 예를 들어 "John이 자신의 위시리스트에 영화를 추가했습니다" 액티비티에서 액티비티의 객체는 추가된 영화입니다. </br> [Relationship](#class-relationship) 내에서 사용될 경우 [subject](#class-subject)와 관련된 개체를 설명합니다.
도메인: | [Activity](#class-activity) \| [Relationship](#class-relationship)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 97
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally가 게시물을 좋아했습니다",
>  "type": "Like",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1"
>}
>```

>예시 98
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Like",
>  "actor": "http://sally.example.org",
>  "object": {
>    "type": "Note",
>    "content": "간단한 노트"
>  }
>}
>```

>예시 99
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally가 게시물을 좋아했습니다",
>  "type": "Like",
>  "actor": "http://sally.example.org",
>  "object": [
>    "http://example.org/posts/1",
>    {
>      "type": "Note",
>      "summary": "간단한 노트",
>      "content": "저건 나무야."
>    }
>  ]
>}
>```

#### [Class] [prev](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#prev`
비고: | 페이징 된 [Collection](#class-collection)에서 항목들의 이전(previous) 페이지를 식별합니다.
도메인: | [CollectionPage](#class-collectionpage)
범위: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
기능적: | True

>예시 100
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 블로그 게시물 1 페이지",
>  "type": "CollectionPage",
>  "prev": "http://example.org/collection?page=1",
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

>예시 101
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 블로그 게시물 1 페이지",
>  "type": "CollectionPage",
>  "prev": {
>    "type": "Link",
>    "name": "이전 페이지",
>    "href": "http://example.org/collection?page=1"
>  },
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

#### [Class] [preview](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#preview`
비고: | 이 객체의 미리보기(preview)를 제공하는 개체를 식별합니다.
도메인: | [Link](#class-link) \| [Object](#class-object)
범위: | [Link](#class-link) \| [Object](#class-object)

>예시 102
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Video",
>  "name": "멋진 새 영화",
>  "duration": "PT2H30M",
>  "preview": {
>    "type": "Video",
>    "name": "예고편",
>    "duration": "PT1M",
>    "url": {
>      "href": "http://example.org/trailer.mkv",
>      "mediaType": "video/mkv"
>    }
>  }
>}
>```

#### [Class] [result](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#result`
비고: | 액티비티의 결과(result)를 표현합니다. 예를 들어, 특정 작업으로 인해 새 리소스가 생성되면 result 속성을 사용하여 해당 새 리소스를 표현할 수 있습니다.
도메인: | [Activity](#class-activity)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 103
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 비행기가 정시에 도착했는지 확인했습니다",
>  "type": ["Activity", "http://www.verbs.example/Check"],
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/flights/1",
>  "result": {
>    "type": "http://www.types.example/flightstatus",
>    "name": "정시 도착"
>  }
>}
>```

#### [Class] [replies](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#replies`
비고: | 이 객체에 대한 응답으로 간주되는 객체가 포함된 [Collection](#class-collection)을 식별합니다.
도메인: | [Object](#class-object)
범위: | [Collection](#class-collection)
기능적: | True

>예시 104
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "id": "http://www.test.example/notes/1",
>  "content": "전 괜찮아요.",
>  "replies": {
>    "type": "Collection",
>    "totalItems": 1,
>    "items": [
>      {
>        "summary": "노트에 대한 답장",
>        "type": "Note",
>        "content": "정말 다행이네요.",
>        "inReplyTo": "http://www.test.example/notes/1"
>      }
>    ]
>  }
>}
>```

#### [Class] [tag](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#tag`
비고: | 개체와 관련된 하나 이상의 "태그들(tags)"입니다. 태그는 모든 종류의 Object일수 있습니다. `attachment`과 `tag`의 주요 차이점은 전자는 포함에 의한 연관을 의미하고, 후자는 참조에 의해 연관됨을 의미합니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 105
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Image",
>  "summary": "Sally의 사진",
>  "url": "http://example.org/sally.jpg",
>  "tag": [
>    {
>      "type": "Person",
>      "id": "http://sally.example.org",
>      "name": "Sally"
>    }
>  ]
>}
>```

#### [Class] [target](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#target`
비고: | 액티비티의 간접 객체 또는 대상(target)을 설명합니다. target의 정확한 의미는 표현하고 있는 작업 유형에 따라 크게 달라지지만, 종종 영어 전치사 "to"의 대상이 됩니다. 예를 들어, "John이 자신의 위시리스트에 영화를 추가했습니다" 액티비티에서 이 액티비티의 target은 John의 위시리스트 입니다. 액티비티에는 둘 이상의 target이 있을수도 있습니다.
도메인: | [Activity](#class-activity)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 106
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John에게 게시물을 제공했습니다",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org"
>}
>```

>예시 107
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John에게 그 게시물을 제공했습니다",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": {
>    "type": "Person",
>    "name": "John"
>  }
>}
>```

#### [Class] [to](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#to`
비고: | 객체의 공개 주요 대상의 일부로 간주되는 개체를 식별합니다.
도메인: | [Object](#class-object)
범위: | [Object](#class-object) \| [Link](#class-link)

>예시 108
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John에게 그 게시물을 제공했습니다",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org",
>  "to": [ "http://joe.example.org" ]
>}
>```

#### [Class] [url](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#url`
비고: | 객체 표현에 대한 하나 이상의 링크를 식별합니다.
도메인: | [Object](#class-object)
범위: | `xsd:anyURI` \| [Link](#class-link)

>예시 109
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Document",
>  "name": "4분기 판매 동향",
>  "url": "http://example.org/4q-sales-forecast.pdf"
>}
>```

>예시 110
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Document",
>  "name": "4분기 판매 동향",
>  "url": {
>    "type": "Link",
>    "href": "http://example.org/4q-sales-forecast.pdf"
>  }
>}
>```

>예시 111
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Document",
>  "name": "4분기 판매 동향",
>  "url": [
>    {
>      "type": "Link",
>      "href": "http://example.org/4q-sales-forecast.pdf",
>      "mediaType": "application/pdf"
>    },
>    {
>      "type": "Link",
>      "href": "http://example.org/4q-sales-forecast.html",
>      "mediaType": "text/html"
>    }
>  ]
>}
>```

#### [Class] [accuracy](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#accuracy`
비고: | [Place](#class-place) 객체에서 위치 좌표의 정확도(accuracy)를 나타냅니다. 백분율 속성으로 표현됩니다. 예: "94.0"은 "94.0% 정확도"를 의미합니다.
도메인: | [Place](#class-place)
범위: | `xsd:float` [>= 0.0f, <= 100.0f]
기능적: | True

>예시 112
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "류구루촌, 핑두시, 칭다오시, 산둥성, 중국",
>  "type": "Place",
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "accuracy": 94.5
>}
>```

#### [Class] [altitude](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#altitude`
비고: | 장소의 고도(altitude)를 나타냅니다. 측정 단위(units)는 [units](#class-units) 속성을 사용하여 표시됩니다. [units](#class-units)가 지정되지 않은 경우, 기본값은 미터를 나타내는 "`m`"으로 가정됩니다.
도메인: | [Object](#class-object)
범위: | `xsd:float`
기능적: | True

>예시 113
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Fresno 지역",
>  "altitude": 15.0,
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "units": "miles"
>}
>```

#### [Class] [content](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#content`
비고: | JSON 문자열로 인코딩된 객체(Object)의 컨텐츠(content) 또는 텍스트 표현입니다. 기본적으로 `content`의 값은 HTML입니다. [mediaType](#class-mediatype) 속성을 객체에서 사용하여 다른 내용 유형을 나타낼 수 있습니다. </br> 컨텐츠는 여러 언어 태그값을 사용하여 표현될 수 있습니다.
도메인: | [Object](#class-object)
범위: | `xsd:string` \| `rdf:langString`

>예시 114
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "content": "<em>간단한</em> 노트"
>}
>```

>예시 115
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "contentMap": {
>    "en": "A <em>simple</em> note",
>    "es": "Una nota <em>sencilla</em>",
>    "zh-Hans": "一段<em>简单的</em>笔记"
>  }
>}
>```

>예시 116
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "mediaType": "text/markdown",
>  "content": "## 간단한 노트\n간단한 마크다운 `노트`"
>}
>```

#### [Class] [name](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#name`
비고: | 간단하고 사람이 읽을수 있는 객체의 일반 텍스트 이름(name)입니다. HTML 마크업을 포함하는 것을 *절대 하지 말아야* 합니다. name은 여러 언어 태그 값을 사용하여 표현 *할 수도* 있습니다.
도메인: | [Object](#class-object) \| [Link](#class-link)
범위: | `xsd:string` \| `rdf:langString`

>예시 117
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Note",
>  "name": "간단한 노트"
>}
>```

>예시 118
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Note",
>  "nameMap": {
>    "en": "A simple note",
>    "es": "Una nota sencilla",
>    "zh-Hans": "一段简单的笔记"
>  }
>}
>```

#### [Class] [duration](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#duration`
비고: | 객체가 오디오 또는 비디오, 회의등과 같은 시간 제한 리소스를 설명할떄 [duration](#class-duration) 속성은 객체의 대략적인 지속(duration) 시간을 나타냅니다. 값은 [ [xmlschema11-2](#xmlschema11-2)], 섹션 3.3.6에 정의된 `xsd:duration`으로 표현되어야 합니다 (예: 5초 주기는 "`PT5S`"로 표기).
도메인: | [Object](#class-object)
범위: | `xsd:duration`
기능적: | True

>예시 119
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Video",
>  "name": "새들이 날라다님",
>  "url": "http://example.org/video.mkv",
>  "duration": "PT2H"
>}
>```

#### [Class] [height](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#height`
비고: | [Link](#class-link)에서 링크된 리소스의 장치 독립적 픽셀의 렌더링 높이(height)에 대한 힌트를 지정합니다.
도메인: | [Link](#class-link)
범위: | `xsd:nonNegativeInteger`
기능적: | True

>예시 120
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/image.png",
>  "height": 100,
>  "width": 100
>}
>```

#### [Class] [href](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#href`
비고: | [Link](#class-link)가 가리키는 대상 자원입니다.
도메인: | [Link](#class-link)
범위: | `xsd:anyURI`
기능적: | True

>예시 121
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "mediaType": "text/html",
>  "name": "이전"
>}
>```

#### [Class] [hreflang](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#hreflang`
비고: | 대상 자원이 사용하는 언어에 대한 힌트입니다. 값은 *반드시* [[BCP47](#BCP47)] 언어 태그여야 합니다.
도메인: | [Link](#class-link)
범위: | [[BCP47](#BCP47)] 언어 태그
기능적: | True

>예시 122
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "hreflang": "en",
>  "mediaType": "text/html",
>  "name": "이전"
>}
>```

#### [Class] [partOf](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#partOf`
비고: | [CollectionPage](#class-collectionpage) 객체 항목이 속하는 [Collection](#class-collection)을 식별합니다.
도메인: | [CollectionPage](#class-collectionpage)
범위: | [Link](#class-link) \| [Collection](#class-collection)
기능적: | True

>예시 123
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 노트 1 페이지",
>  "type": "CollectionPage",
>  "id": "http://example.org/collection?page=1",
>  "partOf": "http://example.org/collection",
>  "items": [
>    {
>      "type": "Note",
>      "name": "시도해볼 피자 토핑"
>    },
>    {
>      "type": "Note",
>      "name": "캘리포니아에 대한 생각"
>    }
>  ]
>}
>```

#### [Class] [latitude](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#latitude`
비고: | 장소의 위도(latitude)를 표시합니다.
도메인: | [Place](#class-place)
범위: | `xsd:float`
기능적: | True

>예시 124
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Fresno 지역",
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "radius": 15,
>  "units": "miles"
>}
>```

#### [Class] [longitude](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#longitude`
비고: | 장소의 경도(longitude)를 표시합니다.
도메인: | [Place](#class-place)
범위: | `xsd:float`
기능적: | True

>예시 125
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Fresno 지역",
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "radius": 15,
>  "units": "miles"
>}
>```

#### [Class] [mediaType](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#mediaType`
비고: | [Link](#class-link)에서 사용될 떄 참조된 리소스의 MIME 미디어 타입(media type)을 식별합니다. </br> [Object](#class-object)에서 사용될 때 [content](#class-content) 속성 값의 MIME 미디어 유형을 식별합니다. 지정하지 않으면 [content](#class-content) 속성은 `text/html` 컨텐츠를 포함한다고 가정합니다.
도메인: | [Link](#class-link) \| [Object](#class-object)
범위: | MIME 미디어 타입
기능적: | True

>예시 126
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "hreflang": "en",
>  "mediaType": "text/html",
>  "name": "다음"
>}
>```

#### [Class] [endTime](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#endTime`
비고: | 객체의 실제 또는 예상 종료 시간을 설명하는 날짜 및 시간입니다. 예를 들어, [Activity](#class-activity) 객체와 함께 사용되는 경우 [endTime](#class-endtime) 속성은 액티비티가 종료되거나 종료 될것으로 예상되는 순간을 지정합니다.
도메인: | [Object](#class-object)
범위: | `xsd:dateTime`
기능적: | True

>예시 127
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Event",
>  "name": "Jim을 위한 송별회",
>  "startTime": "2014-12-31T23:00:00-08:00",
>  "endTime": "2015-01-01T06:00:00-08:00"
>}
>```

#### [Class] [published](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#published`
비고: | 개체가 게시된(published) 날짜와 시간입니다.
도메인: | [Object](#class-object)
범위: | `xsd:dateTime`
기능적: | True

>예시 128
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "간단한 노트",
>  "type": "Note",
>  "content": "물고기가 헤엄친다.",
>  "published": "2014-12-12T12:12:12Z"
>}
>```

#### [Class] [startTime](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#startTime`
비고: | 객체의 실제 또는 예상 시작 시간(starting time)을 설명하는 날짜 및 시간입니다. 예를 들어, [Activity](#class-activity) 객체와 함께 사용되는 경우 [startTime](#class-starttime) 속성은 액티비티가 시작되거나 예정된 순간을 지정합니다.
도메인: | [Object](#class-object)
범위: | `xsd:dateTime`
기능적: | True

>예시 129
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Event",
>  "name": "Jim을 위한 송별회",
>  "startTime": "2014-12-31T23:00:00-08:00",
>  "endTime": "2015-01-01T06:00:00-08:00"
>}
>```

#### [Class] [radius](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#radius`
비고: | 장소에 대해 주어진 위도와 경도의 반경(radius)입니다. 단위(units)는 [units](#class-units) 속성으로 표시됩니다. [units](#class-units)가 지정되지 않은 경우 기본값은 "meters"를 나타내는 "`m`"으로 가정됩니다.
도메인: | [Place](#class-place)
범위: | `xsd:float` [>= 0.0f]
기능적: | True

>예시 130
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Fresno 지역",
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "radius": 15,
>  "units": "miles"
>}
>```

#### [Class] [rel](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#rel`
비고: | Link와 관련된 링크 관계(relation). [HTML5](#HTML5)와 [RFC5988](#RFC5988) "링크 관계" 정의를 *반드시* 둘 다 준수해야합니다. </br> [HTML5](#HTML5)에서 "space" U+0020, "tab" (U+0009), "LF" (U+000A), "FF" (U+000C), "CR" (U+000D) 또는 "," (U+002C) 문자를 포함하고 있지 않은 문자열은 유효한 링크 관계로 사용할 수 있습니다.
도메인: | [Link](#class-link)
범위: | [RFC5988](#RFC5988) 또는 [HTML5](#HTML5) Link 관계

>예시 131
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "hreflang": "en",
>  "mediaType": "text/html",
>  "name": "미리보기",
>  "rel": ["canonical", "preview"]
>}
>```

#### [Class] [startIndex](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#startIndex`
비고: | 엄격하게 정렬된 컬렉션의 논리적 뷰 내에서 상대 위치를 식별하는, 음이 아닌 정수의 값입니다.
도메인: | [OrderedCollectionPage](#class-orderedcollectionpage)
범위: | `xsd:nonNegativeInteger`
기능적: | True

>예시 132
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Page 1 of Sally's notes",
>  "type": "OrderedCollectionPage",
>  "startIndex": 0,
>  "orderedItems": [
>    {
>      "type": "Note",
>      "name": "물의 밀도"
>    },
>    {
>      "type": "Note",
>      "name": "공기 매트리스 아이디어"
>    }
>  ]
>}
>```

#### [Class] [summary](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#summary`
비고: | HTML로 인코딩 된 객체의 자연어 요약(summary)입니다. 여러 언어 태그 요약이 제공 *될 수도* 있습니다.
도메인: | [Object](#class-object)
범위: | `xsd:string` \| `rdf:langString`

>예시 133
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "사탕수수 가공",
>  "type": "Note",
>  "summary": "간단한 <em>노트</em>"
>}
>```

>예시 134
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "사탕수수 가공",
>  "type": "Note",
>  "summaryMap": {
>    "en": "A simple <em>note</em>",
>    "es": "Una <em>nota</em> sencilla",
>    "zh-Hans": "一段<em>简单的</em>笔记"
>  }
>}
>```

#### [Class] [totalItems](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#totalItems`
비고: | 컬렉션의 논리적 뷰에 포함된 총 개체수를 지정하는, 음이 아닌 정수입니다. 이 숫자는 [Collection](#class-collection) 개체 인스턴스 내에서 직렬화된 실제 항목수를 반영하지 않을 수 있습니다.
도메인: | [Collection](#class-collection)
범위: | `xsd:nonNegativeInteger`
기능적: | True

>예시 135
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 노트",
>  "type": "Collection",
>  "totalItems": 2,
>  "items": [
>    {
>      "type": "Note",
>      "name": "어떤 계단을 사용해야 하지?"
>    },
>    {
>      "type": "Note",
>      "name": "기억해둬야 할것들"
>    }
>  ]
>}
>```

#### [Class] [units](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#units`
비고: | [Place](#class-place) 객체의 [radius](#class-radius) 및 [altitude](#class-altitude) 속성에 대한 측정 단위(units)를 지정합니다. 지정하지 않으면 기본값으로는 "미터"를 나타내는 "m"으로 간주됩니다.
도메인: | [Place](#class-place)
범위: | "`cm`" \| " `feet`" \| " `inches`" \| " `km`" \| " `m`" \| " `miles`" \| `xsd:anyURI`
기능적: | True

>예시 136
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Fresno 지역",
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "radius": 15,
>  "units": "miles"
>}
>```

#### [Class] [updated](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#updated`
비고: | 객체가 업데이트된(updated) 날짜 및 시간입니다.
도메인: | [Object](#class-object)
범위: | `xsd:dateTime`
기능적: | True

>예시 137
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "크랜베리 소스 아이디어",
>  "type": "Note",
>  "content": "캔과 동일한 모양을 갖추지 않도록 위로 밀어 올리기.",
>  "updated": "2014-12-12T12:12:12Z"
>}
>```

#### [Class] [width](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#width`
비고: | [Link](#class-link)에서 링크된 리소스의 장치 독립적인 픽셀의 렌더링 너비(width)에 대한 힌트를 지정합니다.
도메인: | [Link](#class-link)
범위: | `xsd:nonNegativeInteger`
기능적: | True

>예시 138
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/image.png",
>  "height": 100,
>  "width": 100
>}
>```

#### [Class] [subject](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#subject`
비고: | [Relationship](#class-relationship) 객체에서 `subject` 속성은 연결된 개개인중 한명을 식별합니다. 예를 들어, "John은 Sally와 관련이 있습니다"라는 관계 객체의 경우, `subject`는 John을 나타냅니다.
도메인: | [Relationship](#class-relationship)
범위: | [Link](#class-link) \| [Object](#class-object)
기능적: | True

>예시 139
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John의 지인입니다.",
>  "type": "Relationship",
>  "subject": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "relationship": "http://purl.org/vocab/relationship/acquaintanceOf",
>  "object": {
>    "type": "Person",
>    "name": "John"
>  }
>}
>```

#### [Class] [relationship](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#relationship`
비고: | [Relationship](#class-relationship) 객체에서 `relationship` 속성은 [subject](#class-subject)와 [object](#class-object) 사이에 존재하는 관계의 종류를 식별합니다.
도메인: | [Relationship](#class-relationship)
범위: | Object

>예시 140
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 John의 지인입니다.",
>  "type": "Relationship",
>  "subject": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "relationship": "http://purl.org/vocab/relationship/acquaintanceOf",
>  "object": {
>    "type": "Person",
>    "name": "John"
>  }
>}
>```

#### [Class] [describes](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#describes`
비고: | [Profile](#class-profile) 객체에서 `describes` 속성은 Profile이 설명(describes)하는 객체를 식별합니다.
도메인: | [Profile](#class-profile)
범위: | [Object](#class-object)
기능적: | True

>예시 141
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 프로필",
>  "type": "Profile",
>  "describes": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "url": "http://sally.example.org"
>}
>```

#### [Class] [formerType](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#formerType`
비고: | [Tombstone](#class-tombstone) 객체에서 `formerType` 속성은 삭제된 객체의 타입을 식별합니다.
도메인: | [Tombstone](#class-tombstone)
범위: | [Object](#class-object)
기능적: | False

>예시 142
>
>```json
>{
>"@context": "https://www.w3.org/ns/activitystreams",
>"summary": "이 이미지는 삭제되었습니다",
>"type": "Tombstone",
>"formerType": "Image",
>"url": "http://example.org/image/2"
>}
>```

#### [Class] [deleted](#4-속성-properties)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#deleted`
비고: | [Tombstone](#class-tombstone) 객체에서 `deleted` 속성은 객체가 삭제(deleted)된 타임스탬프를 나타냅니다.
도메인: | [Tombstone](#class-tombstone)
범위: | `xsd:dateTime`
기능적: | True

>예시 143
>
>```json
>{
>"@context": "https://www.w3.org/ns/activitystreams",
>"summary": "이 이미지는 삭제되었습니다",
>"type": "Tombstone",
>"deleted": "2016-05-03T00:00:00Z"
>}
>```

## 5. [구현 비고 (Implementation Notes)](#목차-table-of-contents)

### 5.1 [청중 타게팅 (Audience Targeting)](#목차-table-of-contents)

개념적으로, 모든 객체에는 1차 청중과 2차 청중이 있습니다. 1차 청중은 개체와 직접 관련되거나 개체를 소유한 개체로 구성됩니다. 2차 청중은 개체에 관심을 공유하지만 직접 참여하지 않을수 있는 개체 (예: "팔로워")의 집합으로 구성됩니다.

예를 들어, Bob, Joe와 Jane으로 구성된 소셜 네트워크가 있다고 가정해봅시다. Bob과 Joe는 각각 Jane의 친구지만 그들끼리는 서로 친구가 아닙니다. Bob은 Jane이 직접적으로 참여한 액티비티들을 "팔로우" 하기로 선택했습니다. Jane은 Joe와 파일을 공유합니다.

이 예시에서 Jane과 Joe는 각각 파일 공유 액티비티에 직접 참여하며, 두명 다 그 이벤트에 대한 1차 청중으로 구성됩니다. Jane과 관련된 액티비티에 관심이 있는 Bob은 2차 청중입니다. 이를 이용하여 액티비티를 생산하거나 소비하는 시스템은 각 사람에게 이벤트를 효율적으로 알릴수 있습니다.

많은 유형의 액티비티에 대해 1차 청중들을 추론할 수 있는 수단(액티비티의 액션 타입, 액터, 객체와 대상)이 있지만, 휴리스틱은 언제나 작동하지 않기에 2차 청중을 판별하는 수단을 제공하지 않습니다. [to](#class-to), [cc](#class-cc), [bto](#class-bto) 와 [bcc](#class-bcc) 속성은 1차 및 2차 청중을 명시적으로 식별하기 위해 객체 내에서 사용 *할 수도* 있습니다.

이러한 속성을 포함하는 객체의 원형적인 사용 사례는 중개인을 통한 객체의 게시와 재배포입니다. 즉, 이벤트 소스는 객체를 생성하여 이를 중개자에게 공개하고, 중개자는 특정 개별 사용자나 그룹에 표시할 항목의 하위 집합을 결정합니다. 이러한 결정은 부분적으로 각 객체에 대한 1차 및 2차 청중의 식별에 의해 이루어질수 있습니다.

이벤트 소스가 객체를 생성하고 `to`와 `cc`필드에 대한 값을 지정하면, 중개자는 해당 필드 값을 그대로 유지한채 해당 객체를 재배포하여 모든 프로세서가 대상 객체를 확인할 수 있도록 해야 하는것을 *권장합니다*. 이는 이메일 시스템에서 `to`와 `cc`가 사용하는것과 정확히 같은 모델입니다.

하지만 특정 청중의 신원을 공개하는 것이 부적절 할수 있는 상황이 있습니다. 예를 들어, 사용자는 다양한 주제, 개인 또는 이벤트 타입에 관심이 있다는 것을 다른 사용자에게 알리고 싶지 않을수도 있습니다. 
이 옵션을 지원하기 위해 객체를 생성하는 구현단계에서는 `bto` 및 `bcc`속성을 사용하여 객체를 비공개 대상으로 해야하는 개체들을 나열 *할 수도* 있습니다. 중개인이 이러한 속성을 포함하는 객체를 수신할 경우, 객체를 재분배하기 전에 *반드시* 해당 값을 제거해야 합니다. 위 절차들의 의도는 시스템이 1차 및 2차 청중의 일부로 `bto`와 `bcc`에 열거된 개체들을 포함하는 것을 *반드시* 고려해야 하지만, 그 사실을 다른 당사자에게 공개하는것은 *절대 하지 말아야* 합니다.

객체에 포함된 청중 대상 정보는 객체 작성자의 의도밖에 보여주지 않습니다. `bto`와 `bcc`의 적절한 취급에 대해서는 명확한 예외를 두지만, 이 규격에서는 청중 대상 정보의 이용 방법을 결정하는 것은 구현 방식에 달려 있게 하였습니다.

#### 5.1.1 [청중과 컨텍스트 (Audience and Context)](#51-청중-타게팅-audience-targeting)

_이 항목은 비표준입니다._

액티비티는 대부분 격리되지 않은 이벤트입니다. 대부분의 경우, 유사한 컨텍스트나 청중을 중심으로 여러 개별적인 액티비티들이 수행되는 경우가 종종 있습니다. 예를들어 공유 프로젝트에서 작업하는 공동작업자는 일부 목표를 달성하는 과정에서 여러 관련된 액티비티들을 수행할 수 있습니다. 이러한 활동은 [context](#class-context) 속성을 사용하여 논리적으로 그룹화할 수 있으며, [audience](#class-audience) 속성을 사용하여 특정 청중을 대상으로 범위를 좁힐 수 있습니다.

예를 들어, 다음은 공통적인 `context`와 `audience`을 공유하는 두 가지의 관련 액티비티들을 보여줍니다:

>예시 144
>
>```json
>{
> "@context": "https://www.w3.org/ns/activitystreams",
> "summary": "프로젝트 XYZ의 액티비티들",
> "type": "Collection",
> "items": [
>   {
>     "summary": "Sally는 노트를 생성했습니다",
>     "type": "Create",
>     "id": "http://activities.example.com/1",
>     "actor": "http://sally.example.org",
>     "object": {
>      "summary": "노트",
>       "type": "Note",
>       "id": "http://notes.example.com/1",
>       "content": "노트"
>     },
>     "context": {
>       "type": "http://example.org/Project",
>       "name": "프로젝트 XYZ"
>     },
>     "audience": {
>       "type": "Group",
>       "name": "프로젝트 XYZ 워킹 그룹"
>     },
>     "to": "http://john.example.org"
>   },
>   {
>     "summary": "John은 Sally의 노트를 좋아했습니다",
>     "type": "Like",
>     "id": "http://activities.example.com/1",
>     "actor": "http://john.example.org",
>     "object": "http://notes.example.com/1",
>     "context": {
>       "type": "http://example.org/Project",
>       "name": "프로젝트 XYZ"
>     },
>     "audience": {
>       "type": "Group",
>       "name": "프로젝트 XYZ 워킹 그룹"
>     },
>     "to": "http://sally.example.org"
>   }
> ]
>}
>```

### 5.2 [개체간의 관계 표현 (Representing Relationships Between Entities)](#목차-table-of-contents)

[Relationship](#class-relationship) 개체는 개인 간의 관계를 나타내는데 사용됩니다. 예를 들어, 한 사람이 다른 사람의 친구라고 하거나, 한 사람이 특정 조직의 일원이라고 표현하는데 사용할 수 있습니다. 이러한 방식으로 관계를 모델링하는 이유는 관계 전반에 작용하는 액티비티들에 대한 설명을 허용하고 관계 컬렉션의 표현을 허용하기 위함입니다.

예를 들어, 많은 소셜 시스템들은 "친구 목록"이라는 개념을 가지고 있습니다. 이것은 한 개인의 사회적 그래프 안에서 직접 연결된 개인의 모음입니다. Sally라는 사용자가 Joe와 Jane과 직접적인 관계를 맺고 있다고 가정합시다. Sally는 Joe의 업데이트 내용을 따르는 반면 Sally와 Jane은 상호 관계를 맺고 있습니다.

[Relationship](#class-relationship) 객체를 이용하여 이러한 관계를 다음과 같이 모델링할 수 있습니다:

>예시 145
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally의 친구들 리스트",
>  "type": "Collection",
>  "items": [
>    {
>      "summary": "Sally는 Joe에게 영향을 받습니다",
>      "type": "Relationship",
>      "subject": {
>        "type": "Person",
>        "name": "Sally"
>      },
>      "relationship": "http://purl.org/vocab/relationship/influencedBy",
>      "object": {
>        "type": "Person",
>        "name": "Joe"
>      }
>    },
>    {
>      "summary": "Sally는 Jane의 친구입니다",
>      "type": "Relationship",
>      "subject": {
>        "type": "Person",
>        "name": "Sally"
>      },
>      "relationship": "http://purl.org/vocab/relationship/friendOf",
>      "object": {
>        "type": "Person",
>        "name": "Jane"
>      }
>    }
>  ]
>}
>```

[relationship](#class-relationship) 속성은 [subject](#class-subject)와 [object](#class-object) 속성으로 식별된 두 개인 사이에 존재하는 관계의 종류를 지정합니다. 이 세 가지 속성은 함께 사용되며, [subject](#class-subject)가 대상을 식별하고, [relationship](#class-relationship)가 술어를 식별하며, [object](#class-object)가 대상을 식별하는 "[구체화한 문장](http://patterns.dataincubator.org/book/reified-statement.html)"이라고 흔히 알려진 것을 형성합니다.

수정된 문장의 사용은 특정 상황에서 문제가 있을수도 있고 혼란스러울수도 있지만, 관계를 기술하기 위한 Activity Streams 어휘 내에서 그들의 사용은 개인의 사회적 그래프에 변화를 기술하는 간단한 메커니즘을 제공합니다. 예를 들어, Sally가 사용자 Matt와 새로운 [Relationship](#class-relationship)를 만들었음을 나타내기 위해, 실행자는 [Create](#class-create) 액티비티과 함께 Relationship 객체를 사용할 수 있습니다.

>예시 146
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally는 Matt의 친구가 되었습니다",
>  "type": "Create",
>  "actor": "http://sally.example.org",
>  "object": {
>    "type": "Relationship",
>    "subject": "http://sally.example.org",
>    "relationship": "http://purl.org/vocab/relationship/friendOf",
>    "object": "http://matt.example.org",
>    "startTime": "2015-04-21T12:34:56"
>  }
>}
>```

또한 이러한 방식으로 관계를 모델링하면 구현자는 관계 자체의 추가 특성을 명확하게 표현할 수 있습니다. 예를 들어, 관계가 시작되거나 종료된 날짜와 시간 이 이러한 경우에 해당합니다.

구현은 관계를 기술할 목적으로 개발된 기존 어휘를 재사용하거나, 특정 구현의 요구사항에 따라 자체적인 어휘를 생성할 수 있습니다. 기존 어휘로는 " [친구의 친구](http://xmlns.com/foaf/spec/)"와 " [관계](http://vocab.org/relationship/)" 어휘가 있습니다.

#### 5.2.1 ["친구 요청" 모델링 (Modeling "friend requests")](#52-개체간의-관계-표현-representing-relationships-between-entities)

_이 항목은 비표준입니다._

많은 소셜 플랫폼의 일반적인 사용 사례는 대칭적인 "친구" 관계의 확립으로, 한 사용자가 처음에 다른 사용자에게 새로운 연결을 설정하도록 요청을 확장하는 것입니다. 일단 연결이 되면, 두 사용자 모두 자동으로 상대방의 활동에 대한 알림을 받기 시작하고, 확립된 관계는 두 사용자의 "친구 목록" 모두에서 볼 수 있게 됩니다.

초기 "친구 요청"은 다음 예시와 같이 [Offer](#class-offer) 및 [Relationship](#class-relationship) 객체 타입을 구성하여 모델링할 수 있습니다:

>예시 147
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "id": "http://example.org/connection-requests/123",
>  "summary": "Sally는 John에게 친구요청을 보냈습니다",
>  "type": "Offer",
>  "actor": "acct:sally@example.org",
>  "object": {
>    "summary": "Sally와 John사이의 우정",
>    "id": "http://example.org/connections/123",
>    "type": "Relationship",
>    "subject": "acct:sally@example.org",
>    "relationship": "http://purl.org/vocab/relationship/friendOf",
>    "object": "acct:john@example.org"
>  },
>  "target": "acct:john@example.org"
>}
>```

"친구 요청"이 받아들여진다고 가정할 경우, 이 공통 적용 시나리오의 나머지 단계는 일련의 구별되는 활동으로 나타낼 수 있습니다.

>예시 148
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally와 John간의 관계 기록",
>  "type": "Collection",
>  "items": [
>    {
>      "summary": "John은 Sally의 친구 요청을 수락했습니다",
>      "id": "http://example.org/activities/122",
>      "type": "Accept",
>      "actor": "acct:john@example.org",
>      "object": "http://example.org/connection-requests/123",
>      "inReplyTo": "http://example.org/connection-requests/123",
>      "context": "http://example.org/connections/123",
>      "result": [
>        "http://example.org/activities/123",
>        "http://example.org/activities/124",
>        "http://example.org/activities/125",
>        "http://example.org/activities/126"
>      ]
>    },
>    {
>      "summary": "John은 Sally를 팔로잉 했습니다",
>      "id": "http://example.org/activities/123",
>      "type": "Follow",
>      "actor": "acct:john@example.org",
>      "object": "acct:sally@example.org",
>      "context": "http://example.org/connections/123"
>    },
>    {
>      "summary": "Sally는 John을 팔로잉했습니다",
>      "id": "http://example.org/activities/124",
>      "type": "Follow",
>      "actor": "acct:sally@example.org",
>      "object": "acct:john@example.org",
>      "context": "http://example.org/connections/123"
>    },
>    {
>      "summary": "John은 Sally를 친구 목록에 추가했습니다",
>      "id": "http://example.org/activities/125",
>      "type": "Add",
>      "actor": "acct:john@example.org",
>      "object": "http://example.org/connections/123",
>      "target": {
>        "type": "Collection",
>        "summary": "John의 연착처"
>      },
>      "context": "http://example.org/connections/123"
>    },
>    {
>      "summary": "Sally는 John을 친구 목록에 추가했습니다",
>      "id": "http://example.org/activities/126",
>      "type": "Add",
>      "actor": "acct:sally@example.org",
>      "object": "http://example.org/connections/123",
>      "target": {
>        "type": "Collection",
>        "summary": "Sally의 연락처"
>      },
>      "context": "http://example.org/connections/123"
>    }
>  ]
>}
>```

이 예시처럼, "친구 요청"을 수락하면 Sally를 따르는 John, John을 따르는 Sally, 그의 커넥션 컬렉션에 Sally와의 관계를 추가하는 John, 그리고 John과의 관계를 그녀의 커넥션 컬렉션에 추가하는 네 가지 추가 액티비티가 발생합니다.

이 예시에서는,

1. 선택적 [result](#class-result) 속성은 `Accept` 액티비티 내에서 수락의 결과로 발생한 추가 액티비티을 식별하기 위해 사용됩니다.

2. 선택적 [context](#class-context) 속성은 다양한 액티비티을 공통의 기준점과 다시 연관시키기 위해 사용되는데, 이 예에서는 설정되고 있는 관계가 그것입니다. 이러한 맥락에서 `context`는 표시 또는 분석 목적을 위해 관련 액티비티을 효율적으로 그룹화할 수 있습니다.

### 5.3 [장소 표현 (Representing Places)](#목차-table-of-contents)

_이 항목은 비표준입니다._

[Place](#class-place) 객체는 물리적 위치와 논리적 위치 모두를 나타내기 위해 사용됩니다. 위치를 다양한 방식으로 설명하기 위해 수많은 기존의 어휘가 존재하지만, 이러한 어휘들 간의 불일치와 비호환성은 구현간 적절한 상호운용성을 달성하는 것을 어렵게 합니다. `Place` 객체는 Activity Streams 2.0 구현에 걸쳐 일관적으로 위치를 설명하기 위한 최소의 상호운용 가능한 출발점을 제공하기 위해 Activity 어휘에 포함되어 있습니다.

`Place` 객체는 의도적으로 유연합니다. 예를 들어, 단순히 이름만으로 위치를 식별하는데 사용될수 있습니다:

>예시 149
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "샌프란시스코, 캘리포니아"
>}
>```

또는 [longitude](#class-longitude) 및 [latitude](#class-latitude) 기준으로는:

>예시 150
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "샌프란시스코, 캘리포니아",
>  "longitude": "122.4167",
>  "latitude": "37.7833"
>}
>```

또한 `Place` 객체는 [radius](#class-radius) 속성, 위치 [altitude](#class-altitude) 및 [accuracy](#class-accuracy)를 사용하여 주어진 지점 주변의 영역을 설명할 수 있습니다.

출판사는 이러한 특정 속성을 사용할 필요가 없고 위치를 설명하는 다른 메커니즘을 사용 *할 수도* 있지만, [Place](#class-place) 객체를 지원하는 구현을 만들 경우에는 *반드시* 이러한 속성 사용을 지원해야 합니다.

### 5.4 [질문 표현 (Representing Questions)](#목차-table-of-contents)

_이 항목은 비표준입니다._

[Question](#class-question) 객체는 다양한 유형의 질문을 표현하는 데 사용할 수 있습니다.

예를 들어, 크라우드소싱 된 질문과 정답 웹사이트에 게시된 것과 유사한 간단한 개방형 질문이 있습니다:

>예시 151
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "로봇에 관한 질문",
>  "id": "http://help.example.org/question/1",
>  "type": "Question",
>  "content": "고양이에게 먹이를 줄 로봇을 만들고 싶어요. 아두이노를 쓸까요 라즈베리 >파이를 쓸까요?"
>}
>```

다중 선택 질문 또는 "투표"도 [oneOf](#class-oneof) 또는 [anyOf](#class-anyof) 속성을 사용하여 지원됩니다:

>예시 152
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "id": "http://polls.example.org/question/1",
>  "name": "로봇에 관한 질문",
>  "type": "Question",
>   "content": "고양이에게 먹이를 줄 로봇을 만들고 싶어요. 어떤 플랫폼이 가장 좋나요?",
>   "oneOf": [
>     {"name": "아두이노"},
>     {"name": "라즈베리 파이"}
>   ]
> }
>```

질문에 대한 응답은 질문을 참조하는 [inReplyto](#class-inreplyto) 속성이 포함된 [Objects](#class-object)로 표현됩니다.

>예시 153
>
>```json
>{
> "@context": "https://www.w3.org/ns/activitystreams",
> "attributedTo": "http://sally.example.org",
> "inReplyTo": "http://polls.example.org/question/1",
> "name": "아두이노"
>}
>```

[Question](#class-question) 객체는 또한 [Activity](#class-activity)의 인스턴스이기 때문에 [result](#class-result) 속성을 사용하여 질문의 결과나 결과를 (적절하게) 표시할 수 있습니다:

>예시 154
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "로봇에 관한 질문",
>  "id": "http://polls.example.org/question/1",
>  "type": "Question",
>   "content": "고양이에게 먹이를 줄 로봇을 만들고 싶어요. 어떤 플랫폼이 가장 좋나요?",
>   "oneOf": [
>     {"name": "아두이노"},
>     {"name": "라즈베리 파이"}
>   ],
>   "replies": {
>     "type": "Collection",
>     "totalItems": 3,
>     "items": [
>       {
>         "attributedTo": "http://sally.example.org",
>         "inReplyTo": "http://polls.example.org/question/1",
>         "name": "아두이노"
>       },
>       {
>         "attributedTo": "http://joe.example.org",
>         "inReplyTo": "http://polls.example.org/question/1",
>         "name": "아두이노"
>       },
>       {
>         "attributedTo": "http://john.example.org",
>         "inReplyTo": "http://polls.example.org/question/1",
>         "name": "라즈베리 파이"
>       }
>     ]
>   },
>   "result": {
>     "type": "Note",
>     "content": "사용자들은 &quot;아두이노&quot;를 33% 더 선호하는것으로 집계됩니다."
>   }
> }
> ```

### 5.5 [역 액티비티와 "실행 취소" (Inverse Activities and "Undo")](#목차-table-of-contents)

_이 항목은 비표준입니다._

몇가지 핵심 [액티비티 타입](#31-액티비티-타입-activity-types)은 서로에 대한 자연 반전으로 정의됩니다. 여기에는 다음 타입들이 포함됩니다:

- [Accept](#class-accept) 와 [Reject](#class-reject),
- [Arrive](#class-arrive) 와 [Leave](#class-leave),
- [Join](#class-join) 과 [Leave](#class-leave),
- [Create](#class-create) 와 [Delete](#class-delete),
- [Like](#class-like) 와 [Dislike](#class-dislike)

이러한 유형의 액티비티들은 의미상 구별되며 다른 유형의 액티비티에는 직접적인 관계가 없습니다. 즉, 액터가 한 시점에 노트를 "좋아요"라고 했다가 나중에 "싫어요"라고 하면, "싫어요" 액티비티는 이전의 액티비티를 "실행취소"하거나 "좋아요"를 부정하여 처리하지 않습니다.

다음에 대한 적절한 해석은 Sally가 처음에는 좋아하다가 나중에는 John의 쪽지를 싫어했다는 것입나다:

>예시 155
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "John의 노트 기록",
>  "type": "Collection",
>  "items": [
>    {
>      "summary": "Sally는 John의 노트를 좋아했습니다",
>      "type": "Like",
>      "actor": "http://sally.example.org",
>      "id": "http://activities.example.com/1",
>      "published": "2015-11-12T12:34:56Z",
>      "object": {
>        "summary": "John의 노트",
>        "type": "Note",
>        "id": "http://notes.example.com/1",
>        "attributedTo": "http://john.example.org",
>        "content": "내 노트"
>      }
>    },
>    {
>      "summary": "Sally는 John의 노트를 싫어헀습니다",
>      "type": "Dislike",
>      "actor": "http://sally.example.org",
>      "id": "http://activities.example.com/2",
>      "published": "2015-12-11T21:43:56Z",
>      "object": {
>        "summary": "John의 노트",
>        "type": "Note",
>        "id": "http://notes.example.com/1",
>        "attributedTo": "http://john.example.org",
>        "content": "내 노트"
>      }
>    }
>  ]
> }
>```

[Undo](#class-undo) 액티비티 타입은 이전 활동을 실행 취소하거나 취소할 수 있는 특정 기능을 제공하도록 정의됩니다. 그렇다면, 다음에 대한 적절한 해석은 Sally가 어느 순간 John의 노트를 좋아했지만 나중에 그런 식으로 명백하게 수정했다는 것입니다.

>예시 156
>
>```json
>{
> "@context": "https://www.w3.org/ns/activitystreams",
> "summary": "John의 노트 기록",
> "type": "Collection",
> "items": [
>   {
>     "summary": "Sally는 john의 노트를 좋아했습니다",
>     "type": "Like",
>     "id": "http://activities.example.com/1",
>     "actor": "http://sally.example.org",
>     "published": "2015-11-12T12:34:56Z",
>     "object": {
>       "summary": "John의 노트",
>       "type": "Note",
>       "id": "http://notes.example.com/1",
>       "attributedTo": "http://john.example.org",
>       "content": "내 노트"
>     }
>   },
>   {
>     "summary": "Sally는 더이상 john의 노트를 좋아하지 않습니다",
>     "type": "Undo",
>     "id": "http://activities.example.com/2",
>     "actor": "http://sally.example.org",
>     "published": "2015-12-11T21:43:56Z",
>     "object": "http://activities.example.com/1"
>   }
> ]
>}
>```

전자의 예에 대한 최종 결과는 Sally가 John의 노트에 대한 자신의 의견을 바꾸었고 지금은 그것을 싫어한다고 지적한 반면, 후자의 예에서는 현재 그것을 좋아하지도 싫어하지도 않습니다.

### 5.6 [멘션, 태그 및 다른 일반적인 소셜 마이크로신택스들 (Mentions, Tags and Other Common Social Microsyntaxes)](#목차-table-of-contents)

_이 항목은 비표준입니다._

많은 소셜 소프트웨어 시스템은 사용자가 객체 내에서 알림, 링크 또는 분류에 대한 특별한 주소 지정을 정의할 수 있는 특수 텍스트 기반의 마이크로싱택을 사용합니다. 예를 들어, 객체의 내용 내에 "`@username`"과 같은 텍스트를 포함하면 객체가 특정 사용자를 위한 특별한 "멘션" 또는 "인박스" 스트림으로 라우팅되는 경우가 많습니다. 마찬가지로, 오브젝트의 내용 내에 "`#topic`"과 같은 텍스트를 포함하면 오브젝트가 "`topic`" 주제와 관련된 것으로 표시되는 경우가 많습니다. 이러한 메커니즘을 일반적으로 "멘션"과 "해시태그"라고 부릅니다.

이러한 마이크로싱택스는 Activity Stream [Object](#class-object)의 [content](#class-content), [name](#class-name) 및 [summary](#class-summary) 속성의 값 내에서 사용 *할 수도* 있지만, 적절한 통지 라우팅, 분류 또는 객체 간 연결을 결정하기 위해 그러한 속성 값을 구문 분석할 필요가 *있어서는 안됩니다*. 대신에 출판사는 이러한 목적을 위해 특별히 제공된 어휘 용어를 적절하게 *사용해야 합니다*.

예를 들어, 저자가 "@sally"라는 이름의 다른 사용자에게 "#감사드립니다"라는 해시태그와 함께 "@sally"라는 감사 메모를 보내고 싶다고 가정해 봅시다. 이 메시지가 노트의 내용 내에 나타나는 일반적인 방법은 다음과 같습니다.

<div align="center"><em>
그림 1 해시 태그가 포함된 간단한 참고 사항:
</em></div>

"@sally님의 많은 노고에 감사드립니다! #감사드립니다"

일반적인 소셜 소프트웨어 구현은 일반적으로 "@sally"가 "@sally"의 소셜 프로필 페이지에 대한 하이퍼링크로 대체되고 "#감사드립니다"가 동일한 주제를 "태그"한 다른 노트 목록에 대한 하이퍼링크로 대체되는 것과 같은 콘텐츠를 렌더링할 수 있습니다. 또한 대부분의 구현은 Sally에게 자신을 언급하는 노트가 작성되었음을 알리는 특별 통지를 보낼 것입니다.

다음은 동등한 Activity Streams [Note](#class-note) 객체를 보여줍니다:

>예시 157
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "감사의 말",
>  "type": "Note",
>  "content": "<a href='http://sally.example.org'>@sally</a>
>      님의 노고에 감사드립니다!
>      <a href='http://example.org/tags/givingthanks'>#감사드립니다</a>",
>  "to": {
>    "name": "Sally",
>    "type": "Person",
>    "id": "http://sally.example.org"
>  },
>  "tag": {
>    "id": "http://example.org/tags/감사드립니다",
>    "name": "#감사드립니다"
>  }
>}
>```

`to` 속성은 사용자 "@sally"가 노트의 [주요 청중](#51-청중-타게팅-audience-targeting)의 일부로 간주되므로 통지를 받아야 함을 나타냅니다. `tag` 속성은 노트를 "`http://example.org/tags/givingthanks`"에 대한 참조와 연결됩니다. `content`에는 여전히 "`@sally`"와 "`#감사드립니다`" 마이크로신택스가 포함되지만, 적절한 연결을 위해 이를 구문 분석하는데 소비적인 구현이 필요하지 않다는 점에 유의하시길 바랍니다.

게시자가 관련 통지 없이 언급을 표시하려는 경우, 게시자는 [Mention](#class-mention) 객체 타입을 [tag](#class-tag) 속성의 값으로 사용할 수 있습니다.

>예시 158
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "감사의 말",
>  "type": "Note",
>  "content": "@sally님의 노고에 감사드립니다! #감사드립니다",
>  "tag": [
>    {
>      "type": "Mention",
>      "href": "http://example.org/people/sally",
>      "name": "@sally"
>    },
>    {
>      "id": "http://example.org/tags/감사드립니다",
>      "name": "#감사드립니다"
>    }
>  ]
>}
>```

### 5.7 [출발지 및 목표 (Origin and Target)](#목차-table-of-contents)

액티비티의 [origin](#class-origin)와 [target](#class-target) 속성은 각각 조치가 지시되는 대상과 대상을 식별합니다. 예를 들어 영어 문장 "A폴더에서 B폴더로 파일을 옮겼습니다"에서 `origin`은 "Folder A"이고 `target`은 "Folder B"입니다. 이 액티비티은 아래 예에 설명되어 있습니다:

>예시 159
>
>```json
>{
>    "@context": "https://www.w3.org/ns/activitystreams",
>    "summary": "Sally는 판매량 수치를 폴더 A에서 폴더 B로 옮겼습니다",
>    "type": "Move",
>    "actor": "http://sally.example.org",
>    "object": {
>      "type": "Document",
>      "name": "판매량 수치"
>    },
>    "origin": {
>      "type": "Collection",
>      "name": "폴더 A"
>    },
>    "target": {
>      "type": "Collection",
>      "name": "폴더 B"
>    }
>  }
>```

`origin` 속성은 액티비티 `object`의 출발지, 출처 또는 입증의 관점에서 영어 전치사 "출처"가 적용 가능한 것으로 간주될 수 있는 모든 타입의 액티비티에 적용됩니다.

`target` 특성은 액티비티 `object`의 간접 대상 또는 목적지를 식별한다는 의미에서 영어 전치사 "to"가 적용 가능하다고 간주할수 있는 모든 타입의 액티비티에 적용할 수 있습니다.

### 5.8 [액티비티 타입의 사용 사례 (Activity Type Motivating Use Cases)](#목차-table-of-contents)

_이 항목은 비표준입니다._

이 어휘에서 정의한 [액티비티 타입](#31-액티비티-타입-activity-types)은 아래에 기술된 공통적으로 구현된 사회적 사용 사례를 다루기 위해 주로 선택되었습니다.

#### 5.8.1 [컨텐츠 관리 (Content Management)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

콘텐츠 관리 활용 사례는 주로 콘텐츠의 생성, 수정 또는 삭제와 관련된 액티비티을 다룹니다. 예를 들어 "John이 새 노트를 만들어습니다", "Sally가 노트를 업데이트 했습니다", "Joe는 사진을 삭제했습니다" 등의 액티비티을 포함합니다.

관련 액티비티:

- [Create](#class-create)
- [Delete](#class-delete)
- [Update](#class-update)

#### 5.8.2 [컬렉션 관리 (Collection Management)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

컬렉션 관리 사용 사례는 주로 컬렉션 내 콘텐츠 관리와 관련된 액티비티를 다룹니다. 컬렉션의 예로는 폴더, 앨범, 친구 목록 등이 있습니다. 예를 들어 "Sally는 폴더 A에 파일을 추가했습니다", "John이 해당 파일을 폴더 A에서 폴더 B로 옮겼습니다" 등의 액티비티를 포함합니다.

관련 액티비티:

- [Add](#class-add)
- [Move](#class-move)
- [Remove](#class-remove)

#### 5.8.3 [리액션 (Reactions)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

리액션 활용 사례는 주로 콘텐츠에 대한 리액션을 다룬다. 여기에는 콘텐츠를 좋아하거나 싫어하거나, 업데이트를 무시하거나, 콘텐츠를 부적절하다고 플래그 지정하거나, 개체를 승인하거나 거부하는 등의 액티비티들이 포함될 수 있습니다.

관련 액티비티:

- [Accept](#class-accept)
- [Block](#class-block)
- [Dislike](#class-dislike)
- [Flag](#class-flag)
- [Ignore](#class-ignore)
- [Like](#class-like)
- [Reject](#class-reject)
- [TentativeAccept](#class-tentativeaccept)
- [TentativeReject](#class-tentativereject)

#### 5.8.4 [이벤트 RSVP (Event RSVP)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

이벤트 RSVP 활용 사례는 주로 이벤트에 대한 초대와 RSVP 타입 응답을 다룹니다.

관련 액티비티:

- [Accept](#class-accept)
- [Ignore](#class-ignore)
- [Invite](#class-invite)
- [Reject](#class-reject)
- [TentativeAccept](#class-tentativeaccept)
- [TentativeReject](#class-tentativereject)

#### 5.8.5 [그룹 관리 (Group Management)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

그룹 관리 활용 사례는 주로 그룹 관리를 다룹니다. 예를 들어, "John이 A그룹에 Sally를 추가했습니다", "Sally는 A그룹에 참가했습니다", "Joe는 그룹을 떠났습니다" 등과 같은 활동을 포함할수 있습니다.

관련 액티비티:

- [Add](#class-add)
- [Join](#class-join)
- [Leave](#class-leave)
- [Remove](#class-remove)

#### 5.8.6 [컨텐츠 경험 (Content Experience)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

콘텐츠 경험 활용 사례는 주로 콘텐츠 듣기, 읽기 또는 보기와 관련된 활동을 기술하는 것을 다룹니다. 예를 들어, "Sally는 게시물을 읽었습니다" "Joe는 노래를 들었습니다" 같은 예시들이 있습니다.

관련 액티비티:

- [Listen](#class-listen)
- [Read](#class-read)
- [View](#class-view)

#### 5.8.7 [지구-사회적 행사 (Geo-Social Events)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

지구-사회적 이벤트 활용 사례는 주로 지오태깅(geo-tagging) 타입 액티비티와 관련된 활동들을 다룹니다. 예를 들어, "조이는 출근했습니다", "Sally는 퇴근했습니다", "John이 집에서 직장까지 가는 중입니다"과 같은 액티비티들을 포함할 수 있습니다.

관련 액티비티:

- [Arrive](#class-arrive)
- [Leave](#class-leave)
- [Travel](#class-travel)

#### 5.8.8 [알림 (Notification)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

알림 사용 사례는 주로 특정 객체 또는 알림에 대한 주의를 환기하는 것을 다룹니다.

관련 액티비티:

- [Announce](ActivityVocabularyChapter3.md#class-announce)

#### 5.8.9 [질문 (Questions)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

질문 활용 사례는 주로 모든 타입의 대표 질문을 다룹니다. 자세한 내용은 [5.4 질문 표현하기](#54-질문-표현-representing-questions)를 참조하시길 바랍니다.

관련 액티비티:

- [Question](#class-question)

#### 5.8.10 [관계 관리 (Relationship Management)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

관계 관리 활용 사례는 주로 대인관계 및 사회적 관계의 관리와 관련된 대표 액티비티(예: 친구 요청, 소셜 네트워크 관리 등)을 다룬다. 자세한 내용은 [5.2 기업 간의 관계 표현](#52-개체간의-관계-표현-representing-relationships-between-entities)을 참조하시길 바랍니다.

관련 액티비티:

- [Accept](#class-accept)
- [Add](#class-add)
- [Block](#class-block)
- [Create](#class-create)
- [Delete](#class-delete)
- [Follow](#class-follow)
- [Ignore](#class-ignore)
- [Invite](#class-invite)
- [Reject](#class-reject)

#### 5.8.11 [액티비티 부정 (Negating Activity)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

부정 액티비티 사용 사례는 주로 이전에 완료된 액티비티을 수정하는 기능을 다룹니다. 자세한 내용은 [5.5 역방향 액티비티 및 "실행 취소"](#55-역-액티비티와-실행-취소-inverse-activities-and-undo)를 참조하시기 바랍니다.

관련 액티비티:

- [Undo](#class-undo)

#### 5.8.12 [제공 (Offers)](#58-액티비티-타입의-사용-사례-activity-type-motivating-use-cases)

제안 사용 사례는 한 개체를 다른 개체에 제공하는 것과 관련된 액티비티을 다룹니다. 예를 들어, "A 회사가 Sally에게 제품 Z 구매에 대한 할인을 제공하고 있다", "Sally가 A 폴더에 파일을 추가하려고 한다" 등의 액티비티가 포함될 수 있습니다.

관련 액티비티:

- [Offer](#class-offer)

## A. [비 표준 온톨로지 정의 (Non-normative Ontology Definition)](#목차-table-of-contents)

_이 항목은 비표준입니다._

Activity Streams 2.0을 처리하기 위해 RDF 메커니즘을 사용해 구현하시려는 분들께, 편의를 위하여 제공되는 Activity Streams 2.0 어휘의 비-표준적인 turtle의 정의는 [이곳](https://www.w3.org/ns/activitystreams-owl) 그리고/또는 [네임스페이스](https://www.w3.org/ns/activitystreams)에 정의되어 있습니다. 그러나 이 문서에서는 Activity Streams 2.0에 대한 표준적인 정의를 제공하는 것을 알아두시길 바랍니다.

## B. [변경 기록 (Changelog)](#목차-table-of-contents)

_이 항목은 비표준입니다._

다음은 이전 후보 문서인 [2016-12-15](https://www.w3.org/TR/2016/CR-activitystreams-vocabulary-20161215/#changelog) 작성 이후 변경된 중요사항입니다.

- 구현 부족으로 인하여 4개의 표준 [relationship](#class-relationship)값들이 제거되었습니다. 대신 [관계(Relationship)](http://vocab.org/relationship/) 어휘를 사용하도록 예시를 변경하였습니다.
- 프로세스(process) 부분을, 특히 종료 기준(exit criteria) 및 위험요소를 지적한 부분이 제거되었습니다.
- [deleted](#class-deleted) 부분의 오타를 수정하였습니다.
- [closed](#class-closed) 속성 항목에 `datetime`과 `boolean`을 추가하였습니다.
- [first](#class-first) 및 [current](#class-current) 속성의 도메인을 [Collection](#class-collection)으로 설정하였습니다.

## C. [참고 문헌 (References)](#목차-table-of-contents)

### C.1 [규정 참고 문헌 (Normative references)](#목차-table-of-contents)

#### [BCP47]

- Tags for Identifying Languages. A. Phillips; M. Davis. IETF. September 2009. IETF Best Current Practice. URL: https://tools.ietf.org/html/bcp47 

#### [RFC2119]

- Key words for use in RFCs to Indicate Requirement Levels. S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119 

#### [RFC5988]

- Web Linking. M. Nottingham. IETF. October 2010. Proposed Standard. URL: https://tools.ietf.org/html/rfc5988 

#### [xmlschema11-2]

- W3C XML Schema Definition Language (XSD) 1.1 Part 2: Datatypes. David Peterson; Sandy Gao; Ashok Malhotra; Michael Sperberg-McQueen; Henry Thompson; Paul V. Biron et al. W3C. 5 April 2012. W3C Recommendation. URL: https://www.w3.org/TR/xmlschema11-2/ 

### C.2 [정보 참고 문헌 (Informative references)](#목차-table-of-contents)

#### [HTML5]

- HTML5. Ian Hickson; Robin Berjon; Steve Faulkner; Travis Leithead; Erika Doyle Navara; Theresa O'Connor; Silvia Pfeiffer. W3C. 28 October 2014. W3C Recommendation. URL: https://www.w3.org/TR/html5/
