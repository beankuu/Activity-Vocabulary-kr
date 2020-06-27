[목차로 돌아가기](ActivityVocabularyContents.md)

## 2. 핵심 타입 (Core Types)

~~The Activity Vocabulary Core Types provide the basis for the rest of the vocabulary.~~

액티비티-어휘 핵심 타입은 나머지 어휘들의 기반이 됩니다.

~~Base URI: `https://www.w3.org/ns/activitystreams#`.~~

기반 URI: `https://www.w3.org/ns/activitystreams#`.

~~The Activity Streams 2.0 Core Types include:~~

Activity Streams 2.0 핵심 타입은 다음과 같습니다:

- [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object)
- [Link](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-link)
- [Activity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity)
- [IntransitiveActivity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-intransitiveactivity)
- [Collection](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-collection)
- [OrderedCollection](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-orderedcollection)
- [CollectionPage](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-collectionpage)
- [OrderedCollectionPage](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-orderedcollectionpage)

**[Class] Object**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Object`
Notes: | Describes an object of any kind. The Object type serves as the base type for most of the other kinds of objects defined in the Activity Vocabulary, including other Core types such as Activity, IntransitiveActivity, Collection and OrderedCollection.
Disjoint With: | Link
Properties: | attachment \| attributedTo \| audience \| content \| context \| name \| endTime \| generator \| icon \| image \| inReplyTo \| location \| preview \| published \| replies \| startTime \| summary \| tag \| updated \| url \| to \| bto \| cc \| bcc \| mediaType \| duration

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Object`
비고: | 모든 객체의 종류를 설명하는데 쓰입니다. 객체(Object) 타입은 Activity, IntransitiveActivity, Collection 그리고 OrderedCollection과 같은 다른 핵심 타입들을 포함하여 액티비티-어휘에 정의된 대부분의 객체에 대한 기본 타입으로 사용됩니다.
서로소인 속성: | Link
속성: | attachment \| attributedTo \| audience \| content \| context \| name \| endTime \| generator \| icon \| image \| inReplyTo \| location \| preview \| published \| replies \| startTime \| summary \| tag \| updated \| url \| to \| bto \| cc \| bcc \| mediaType \| duration

>~~Example 1~~
>
>~~"name": "A Simple, non-specific object"~~

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

**[Class] Link**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Link`
Notes: | A Link is an indirect, qualified reference to a resource identified by a URL. The fundamental model for links is established by [ [RFC5988](https://www.w3.org/TR/activitystreams-vocabulary/#bib-RFC5988)]. Many of the properties defined by the Activity Vocabulary allow values that are either instances of Object or Link. When a Link is used, it establishes a qualified relation connecting the subject (the containing object) to the resource identified by the href. Properties of the Link are properties of the reference as opposed to properties of the resource.
Disjoint With: | Object
Properties: | href \| rel \| mediaType \| name \| hreflang \| height \| width \| preview

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Link`
비고: | 링크(Link)는 URL로 식별되는 리소스에 대한 간접적이고 정규화된 참조입니다. 링크들이 기반하는 모델은 [ [RFC5988](https://www.w3.org/TR/activitystreams-vocabulary/#bib-RFC5988)]에 정의되어 있습니다. 액티비티-어휘에 의해 정의된 많은 속성들은 객체의 인스턴스나 링크의 값을 사용하는것을 허용합니다. 링크가 사용될 경우 (담겨 있는 객체의) 대상을 href로 식별된 리소스에 연결하는 규정된 관계를 만들어냅니다. 링크의 속성은 리소스의 속성과 달리 참조의 속성입니다.
서로소인 속성: | Object
속성: | href \| rel \| mediaType \| name \| hreflang \| height \| width \| preview

>~~Example 2~~
>
>~~"name": "An example link"~~

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

**[Class] Activity**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Activity`
Notes: | An Activity is a subtype of Object that describes some form of action that may happen, is currently happening, or has already happened. The `Activity` type itself serves as an abstract base type for all types of activities. It is important to note that the `Activity` type itself does not carry any specific semantics about the kind of action being taken.
Extends: | Object
Properties: | actor \| object \| target \| result \| origin \| instrument </br> Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Activity`
비고: | 액티비티는 발생중인, 현재 진행중인, 또는 이미 발생한 일부 행동(action)을 설명하는데 사용되는 Object의 하위 타입입니다. `Activity` 타입 자신은 모든 타입의 액티비티들에 대한 추상 기반 타입으로 사용됩니다. 중요 사항으로 `Activity` 타입은 그 자체에 가해지는 행동에 대해서는 아무런 의미도 포함하고 있지 않습니다.
다음으로부터 상속: | Object
속성: | actor \| object \| target \| result \| origin \| instrument </br> Object로부터 모든 속성을 물려받습니다.

>~~Example 3~~
>
>  ~~"summary": "Sally did something to a note",~~
>
>    ~~"name": "A Note"~~

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

**[Class] IntransitiveActivity**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#IntransitiveActivity`
Notes: | Instances of `IntransitiveActivity` are a subtype of `Activity` representing intransitive actions. The object property is therefore inappropriate for these activities.
Extends: | Activity
Properties: | Inherits all properties from Activity except `object`.

설멍| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#IntransitiveActivity`
비고: | `IntransitiveActivity`의 인스턴스들은 전이 행동들(intransitive actions)을 나타내는 `Activity`의 하위 타입입니다. 따라서 객체(object) 속성은 이러한 액티비티들에게 적합하지 않습니다.
다음으로부터 상속: | Activity
속성: | `object`를 제외한 모든 Activity의 속성들을 물려받습니다.

>~~Example 4~~
>
>~~"summary": "Sally went to work",~~
>
>    ~~"name": "Work"~~

>예시 4
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Travel",
>  "summary": "Sally는 일하러 갔어요",
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

**[Class] Collection**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Collection`
Notes: | A `Collection` is a subtype of Object that represents ordered or unordered sets of `Object` or `Link` instances. </br> Refer to the Activity Streams 2.0 Core specification for a complete description of the `Collection` type.
Extends: | Object
Properties: | totalItems \| current \| first \| last \| items </br> Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Collection`
비고: | `Collection`은 정렬된 또는 정렬되지 않은 `Object` 이거나 `Link` 인스턴트들의 집합을 나타내는 Object의 하위 타입입니다. </br> `Collection` 타입에 대한 자세한 설명은 Activity Streams 2.0 핵심 사양을 참고하시길 바랍니다.
다음으로부터 상속: | Object
속성: | totalItems \| current \| first \| last \| items </br> Object로부터 모든 속성을 물려받습니다.


[//Comment]: # "Activity-vocabulary 원문에서는 `Object or Link`로 or도 <code></code> 안에 포함되어 있었습니다."

>~~Example 5~~
>
>  ~~"summary": "Sally's notes",~~
>
>      ~~"name": "A Simple Note"~~
>
>      ~~"name": "Another Simple Note"~~

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

**[Class] OrderedCollection**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollection`
Notes: | A subtype of Collection in which members of the logical collection are assumed to always be strictly ordered.
Extends: | Collection
Properties: | Inherits all properties from Collection.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollection`
비고: | 논리적 컬렉션의 멤버가 항상 엄격하게 정렬된 것으로 간주되는 Collection의 하위 타입입니다.
다음으로부터 상속: | Collection
속성: | Collection으로부터 모든 속성을 물려받습니다.

>~~Example 6~~
>
>  ~~"summary": "Sally's notes",~~
>
>      ~~"name": "A Simple Note"~~
>
>      ~~"name": "Another Simple Note"~~

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

**[Class] CollectionPage**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#CollectionPage`
Notes: | Used to represent distinct subsets of items from a `Collection`. Refer to the Activity Streams 2.0 Core for a complete description of the `CollectionPage` object.
Extends: | Collection
Properties: | partOf \| next \| prev </br> Inherits all properties from Collection.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#CollectionPage`
비고: | `Collection`이 보유하고 있는 항목들의 고유한 하위 집합들을 나타내는데 사용됩니다. `CollectionPage` 객체에 대한 자세한 설명은 Activity Streams 2.0 핵심 문서를 참조하시길 바랍니다.
다음으로부터 상속: | Collection
속성: | partOf \| next \| prev </br> Collection으로부터 모든 속성을 물려받습니다.

>~~Example 7~~
>
>  ~~"summary": "Page 1 of Sally's notes",~~
>
>      ~~"name": "A Simple Note"~~
>
>      ~~"name": "Another Simple Note"~~

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

**[Class] OrderedCollectionPage** 

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollectionPage`
Notes: | Used to represent ordered subsets of items from an `OrderedCollection`. Refer to the Activity Streams 2.0 Core for a complete description of the `OrderedCollectionPage` object.
Extends: | OrderedCollection \| CollectionPage
Properties: | startIndex </br> Inherits all properties from OrderedCollection and CollectionPage.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollectionPage`
비고: | `OrderedCollection`이 보유하고 있는 항목들의 정렬된 하위 집합들을 나타내는데 사용됩니다. `OrderedCollectionPage` 객체에 대한 자세한 설명은 Activity Streams 2.0 핵심 문서를 참조하시길 바랍니다.
다음으로부터 상속: | OrderedCollection \| CollectionPage
속성: | startIndex </br> OrderedCollection과 CollectionPage으로부터 모든 속성을 물려받습니다.

>~~Example 8~~
>
>  ~~"summary": "Page 1 of Sally's notes",~~
>
>      ~~"name": "A Simple Note"~~
>
>      ~~"name": "Another Simple Note"~~


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
