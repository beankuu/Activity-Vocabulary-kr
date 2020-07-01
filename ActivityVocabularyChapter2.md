[목차로 돌아가기](ActivityVocabularyContents.md)

## 2. [핵심 타입 (Core Types)](ActivityVocabularyContents.md)

The Activity Vocabulary Core Types provide the basis for the rest of the vocabulary.

액티비티-어휘 핵심 타입들은 나머지 어휘들의 기반이 됩니다.

Base URI: `https://www.w3.org/ns/activitystreams#`.

기반 URI: `https://www.w3.org/ns/activitystreams#`.

The Activity Streams 2.0 Core Types include:

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

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Object`
Notes: | Describes an object of any kind. The Object type serves as the base type for most of the other kinds of objects defined in the Activity Vocabulary, including other Core types such as [Activity](#class-activity), [IntransitiveActivity](#class-intransitiveactivity), [Collection](#class-collection) and [OrderedCollection](#class-orderedcollection).
Disjoint With: | [Link](#class-link)
Properties: | [attachment](ActivityVocabularyChapter4.md#class-attachment) \| [attributedTo](ActivityVocabularyChapter4.md#class-attributedto) \| [audience](ActivityVocabularyChapter4.md#class-audience) \| [content](ActivityVocabularyChapter4.md#class-content) \| [context](ActivityVocabularyChapter4.md#class-context) \| [name](ActivityVocabularyChapter4.md#class-name) \| [endTime](ActivityVocabularyChapter4.md#class-endtime) \| [generator](ActivityVocabularyChapter4.md#class-generator) \| [icon](ActivityVocabularyChapter4.md#class-icon) \| [image](ActivityVocabularyChapter3.md#class-image) \| [inReplyTo](ActivityVocabularyChapter4.md#class-inreplyto) \| [location](ActivityVocabularyChapter4.md#class-location) \| [preview](ActivityVocabularyChapter4.md#class-preview) \| [published](ActivityVocabularyChapter4.md#class-published) \| [replies](ActivityVocabularyChapter4.md#class-replies) \| [startTime](ActivityVocabularyChapter4.md#class-starttime) \| [summary](ActivityVocabularyChapter4.md#class-summary) \| [tag](ActivityVocabularyChapter4.md#class-tag) \| [updated](ActivityVocabularyChapter4.md#class-updated) \| [url](ActivityVocabularyChapter4.md#class-url) \| [to](ActivityVocabularyChapter4.md#class-to) \| [bto](ActivityVocabularyChapter4.md#class-bto) \| [cc](ActivityVocabularyChapter4.md#class-cc) \| [bcc](ActivityVocabularyChapter4.md#class-bcc) \| [mediaType](ActivityVocabularyChapter4.md#class-mediatype) \| [duration](ActivityVocabularyChapter4.md#class-duration)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Object`
비고: | 모든 객체의 종류를 설명하는데 쓰입니다. 객체(Object) 타입은 [Activity](#class-activity), [IntransitiveActivity](#class-intransitiveactivity), [Collection](#class-collection) 그리고 [OrderedCollection](#class-orderedcollection)과 같은 다른 핵심 타입들을 포함하여 액티비티-어휘에 정의된 대부분의 객체에 대한 기본 타입으로 사용됩니다.
서로소: | [Link](#class-link)
속성: | [attachment](ActivityVocabularyChapter4.md#class-attachment) \| [attributedTo](ActivityVocabularyChapter4.md#class-attributedto) \| [audience](ActivityVocabularyChapter4.md#class-audience) \| [content](ActivityVocabularyChapter4.md#class-content) \| [context](ActivityVocabularyChapter4.md#class-context) \| [name](ActivityVocabularyChapter4.md#class-name) \| [endTime](ActivityVocabularyChapter4.md#class-endtime) \| [generator](ActivityVocabularyChapter4.md#class-generator) \| [icon](ActivityVocabularyChapter4.md#class-icon) \| [image](ActivityVocabularyChapter3.md#class-image) \| [inReplyTo](ActivityVocabularyChapter4.md#class-inreplyto) \| [location](ActivityVocabularyChapter4.md#class-location) \| [preview](ActivityVocabularyChapter4.md#class-preview) \| [published](ActivityVocabularyChapter4.md#class-published) \| [replies](ActivityVocabularyChapter4.md#class-replies) \| [startTime](ActivityVocabularyChapter4.md#class-starttime) \| [summary](ActivityVocabularyChapter4.md#class-summary) \| [tag](ActivityVocabularyChapter4.md#class-tag) \| [updated](ActivityVocabularyChapter4.md#class-updated) \| [url](ActivityVocabularyChapter4.md#class-url) \| [to](ActivityVocabularyChapter4.md#class-to) \| [bto](ActivityVocabularyChapter4.md#class-bto) \| [cc](ActivityVocabularyChapter4.md#class-cc) \| [bcc](ActivityVocabularyChapter4.md#class-bcc) \| [mediaType](ActivityVocabularyChapter4.md#class-mediatype) \| [duration](ActivityVocabularyChapter4.md#class-duration)

>Example 1
>
>```json
>{
>"name": "A Simple, non-specific object"
>}
>```

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

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Link`
Notes: | A Link is an indirect, qualified reference to a resource identified by a URL. The fundamental model for links is established by [ [RFC5988](ActivityVocabularyChapterC.md#rfc5988)]. Many of the properties defined by the Activity Vocabulary allow values that are either instances of [Object](#class-object) or [Link](#class-link). When a [Link](#class-link) is used, it establishes a [qualified relation](http://patterns.dataincubator.org/book/qualified-relation.html) connecting the subject (the containing object) to the resource identified by the [href](#class-href). Properties of the [Link](#class-link) are properties of the reference as opposed to properties of the resource.
Disjoint With: | [Object](#class-object)
Properties: | [href](ActivityVocabularyChapter4.md#class-href) \| [rel](ActivityVocabularyChapter4.md#class-rel) \| [mediaType](ActivityVocabularyChapter4.md#class-mediatype) \| [name](ActivityVocabularyChapter4.md#class-name) \| [hreflang](ActivityVocabularyChapter4.md#class-hreflang) \| [height](ActivityVocabularyChapter4.md#class-height) \| [width](ActivityVocabularyChapter4.md#class-width) \| [preview](ActivityVocabularyChapter4.md#class-preview)

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Link`
비고: | 링크(Link)는 URL로 식별되는 리소스에 대한 간접적이고 정규화된 참조입니다. 링크들이 기반하는 모델은 [ [RFC5988](ActivityVocabularyChapterC.md#rfc5988)]에 정의되어 있습니다. 액티비티-어휘에 의해 정의된 많은 속성들은 [Object](#class-object)의 인스턴스나 [Link](#class-link)의 값을 사용하는것을 허용합니다. [Link](#class-link)가 사용될 경우 (담겨 있는 객체의) 대상을 [href](#class-href)로 식별된 리소스에 연결하는 [검증된 관계](http://patterns.dataincubator.org/book/qualified-relation.html)를 만들어냅니다. [Link](#class-link)의 속성은 리소스의 속성과 달리 참조의 속성입니다.
서로소인 속성: | [Object](#class-object)
속성: | [href](ActivityVocabularyChapter4.md#class-href) \| [rel](ActivityVocabularyChapter4.md#class-rel) \| [mediaType](ActivityVocabularyChapter4.md#class-mediatype) \| [name](ActivityVocabularyChapter4.md#class-name) \| [hreflang](ActivityVocabularyChapter4.md#class-hreflang) \| [height](ActivityVocabularyChapter4.md#class-height) \| [width](ActivityVocabularyChapter4.md#class-width) \| [preview](ActivityVocabularyChapter4.md#class-preview)

>Example 2
>
>```json
>{
>"name": "An example link"
>}
>```

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

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Activity`
Notes: | An Activity is a subtype of [Object](#class-object) that describes some form of action that may happen, is currently happening, or has already happened. The `Activity` type itself serves as an abstract base type for all types of activities. It is important to note that the `Activity` type itself does not carry any specific semantics about the kind of action being taken.
Extends: | [Object](#class-object)
Properties: | [Object](#class-object)
속성: | [actor](ActivityVocabularyChapter4.md#class-actor) \| [object](#class-object) \| [target](ActivityVocabularyChapter4.md#class-target) \| [result](ActivityVocabularyChapter4.md#class-result) \| [origin](ActivityVocabularyChapter4.md#class-origin) \| [instrument](ActivityVocabularyChapter4.md#class-instrument) </br> Inherits all properties from [Object](#class-object).

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Activity`
비고: | 액티비티는 발생중인, 현재 진행중인, 또는 이미 발생한 일부 행동(action)을 설명하는데 사용되는 [Object](#class-object)의 하위 타입입니다. `Activity` 타입 자신은 모든 타입의 액티비티들에 대한 추상 기반 타입으로 사용됩니다. 중요 사항으로 `Activity` 타입은 그 자체에 가해지는 행동에 대해서는 아무런 의미도 포함하고 있지 않습니다.
상속함: | [Object](#class-object)
속성: | [actor](ActivityVocabularyChapter4.md#class-actor) \| [object](#class-object) \| [target](ActivityVocabularyChapter4.md#class-target) \| [result](ActivityVocabularyChapter4.md#class-result) \| [origin](ActivityVocabularyChapter4.md#class-origin) \| [instrument](ActivityVocabularyChapter4.md#class-instrument) </br> [Object](#class-object)로부터 모든 속성을 물려받습니다.

>Example 3
>
>```json
>{
>  "summary": "Sally did something to a note",
>
>    "name": "A Note"
>}
>```

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

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#IntransitiveActivity`
Notes: | Instances of `IntransitiveActivity` are a subtype of `Activity` representing intransitive actions. The [object](#class-object) property is therefore inappropriate for these activities.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity) except `object`.

설멍| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#IntransitiveActivity`
비고: | `IntransitiveActivity`의 인스턴스들은 비-과도적 행동들(intransitive actions)을 나타내는 `Activity`의 하위 타입입니다. 따라서 [object](#class-object) 속성은 이러한 액티비티들에게 적합하지 않습니다.
상속함: | [Activity](#class-activity)
속성: | `object`를 제외한 모든 [Activity](#class-activity)의 속성들을 물려받습니다.

[//Comment]: # "intransitive을 비 과도적(완료된)으로 해석했습니다"

>Example 4
>
>```json
>{
>"summary": "Sally went to work",
>
>    "name": "Work"
>}
>```

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

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Collection`
Notes: | A `Collection` is a subtype of [Object](#class-object) that represents ordered or unordered sets of [`Object`](#class-object) or [`Link`](#class-link) instances. </br> Refer to the [Activity Streams 2.0 Core](https://www.w3.org/TR/activitystreams-core/#collection) specification for a complete description of the `Collection` type.
Extends: | [Object](#class-object)
Properties: | [totalItems](ActivityVocabularyChapter4.md#class-totalitems) \| [current](ActivityVocabularyChapter4.md#class-current) \| [first](ActivityVocabularyChapter4.md#class-first) \| [last](ActivityVocabularyChapter4.md#class-last) \| [items](ActivityVocabularyChapter4.md#class-items) </br> Inherits all properties from [Object](#class-object).

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Collection`
비고: | `Collection`은 정렬된 또는 정렬되지 않은 [`Object`](#class-object) 이거나 [`Link`](#class-link) 인스턴트들의 집합을 나타내는 [Object](#class-object)의 하위 타입입니다. </br> `Collection` 타입에 대한 자세한 설명은 [Activity Streams 2.0 핵심](https://www.w3.org/TR/activitystreams-core/#collection) 사양을 참고하시길 바랍니다.
상속함: | [Object](#class-object)
속성: | [totalItems](ActivityVocabularyChapter4.md#class-totalitems) \| [current](ActivityVocabularyChapter4.md#class-current) \| [first](ActivityVocabularyChapter4.md#class-first) \| [last](ActivityVocabularyChapter4.md#class-last) \| [items](ActivityVocabularyChapter4.md#class-items) </br> [Object](#class-object)로부터 모든 속성을 물려받습니다.

[//Comment]: # "Activity-vocabulary 원문에서는 `Object or Link`로 or도 <code></code> 안에 포함되어 있었습니다."

>Example 5
>
>```json
>{
>  "summary": "Sally's notes",
>
>      "name": "A Simple Note"
>
>      "name": "Another Simple Note"
>}
>```

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

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollection`
Notes: | A subtype of [Collection](#class-collection) in which members of the logical collection are assumed to always be strictly ordered.
Extends: | [Collection](#class-collection)
Properties: | Inherits all properties from [Collection](#class-collection).

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollection`
비고: | 논리적 컬렉션(collection)의 멤버가 항상 엄격하게 정렬(ordered)된 것으로 간주되는 [Collection](#class-collection)의 하위 타입입니다.
상속함: | [Collection](#class-collection)
속성: | [Collection](#class-collection)으로부터 모든 속성을 물려받습니다.

>Example 6
>
>```json
>{
>  "summary": "Sally's notes",
>
>      "name": "A Simple Note"
>
>      "name": "Another Simple Note"
>}
>```

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

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#CollectionPage`
Notes: | Used to represent distinct subsets of items from a `Collection`. Refer to the [Activity Streams 2.0 Core](https://www.w3.org/TR/activitystreams-core/#dfn-collectionpage) for a complete description of the `CollectionPage` object.
Extends: | [Collection](#class-collection)
Properties: | [partOf](ActivityVocabularyChapter4.md#class-partof) \| [next](ActivityVocabularyChapter4.md#class-next) \| [prev](ActivityVocabularyChapter4.md#class-prev) </br> Inherits all properties from [Collection](#class-collection).

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#CollectionPage`
비고: | `Collection`이 보유하고 있는 항목들의 고유한 하위 집합들을 나타내는데 사용됩니다. `CollectionPage` 객체에 대한 자세한 설명은 [Activity Streams 2.0 핵심](https://www.w3.org/TR/activitystreams-core/#dfn-collectionpage) 문서를 참고하시길 바랍니다.
상속함: | [Collection](#class-collection)
속성: | [partOf](ActivityVocabularyChapter4.md#class-partof) \| [next](ActivityVocabularyChapter4.md#class-next) \| [prev](ActivityVocabularyChapter4.md#class-prev) </br> [Collection](#class-collection)으로부터 모든 속성을 물려받습니다.

>Example 7
>
>```json
>{
>  "summary": "Page 1 of Sally's notes",
>
>      "name": "A Simple Note"
>
>      "name": "Another Simple Note"
>}
>```

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

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollectionPage`
Notes: | Used to represent ordered subsets of items from an `OrderedCollection`. Refer to the [Activity Streams 2.0 Core](https://www.w3.org/TR/activitystreams-core/#dfn-orderedcollectionpage) for a complete description of the `OrderedCollectionPage` object.
Extends: | [OrderedCollection](#class-orderedcollection) \| [CollectionPage](#class-collectionpage)
Properties: | [startIndex](ActivityVocabularyChapter4.md#class-startindex) </br> Inherits all properties from [OrderedCollection](#class-orderedcollection) and [CollectionPage](#class-collectionpage).

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollectionPage`
비고: | `OrderedCollection`이 보유하고 있는 항목들의 정렬된 하위 집합들을 나타내는데 사용됩니다. `OrderedCollectionPage` 객체에 대한 자세한 설명은 [Activity Streams 2.0 핵심](https://www.w3.org/TR/activitystreams-core/#dfn-orderedcollectionpage) 문서를 참고하시길 바랍니다.
상속함: | [OrderedCollection](#class-orderedcollection) \| [CollectionPage](#class-collectionpage)
속성: | [startIndex](ActivityVocabularyChapter4.md#class-startindex) </br> [OrderedCollection](#class-orderedcollection)과 [CollectionPage](#class-collectionpage)로부터 모든 속성을 물려받습니다.

>Example 8
>
>```json
>{
>  "summary": "Page 1 of Sally's notes",
>
>      "name": "A Simple Note"
>
>      "name": "Another Simple Note"
>}
>```

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

[맨 위로](#2-핵심-타입-core-types)
