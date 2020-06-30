[목차로 돌아가기](ActivityVocabularyContents.md)

## 5. 구현 비고 (Implementation Notes)

### 5.1 청중 타게팅 (Audience Targeting)

Conceptually, every Object has both a Primary and Secondary audience. The Primary audience consists of those entities directly involved or owning the object. The Secondary audience consists of the collection of entities sharing an interest in the object but who might not be directly involved (e.g."followers").

개념적으로, 모든 객체에는 1차 청중과 2차 청중이 있습니다. 1차 청중은 개체와 직접 관련되거나 개체를 소유한 개체로 구성됩니다. 2차 청중은 개체에 관심을 공유하지만 직접 참여하지 않을수 있는 개체 (예: "팔로워")의 집합으로 구성됩니다.

For instance, suppose a social network of three individuals: Bob, Joe and Jane. Bob and Joe are each friends with Jane but are not friends with one another. Bob has chosen to "follow" activities for which Jane is directly involved. Jane shares a file with Joe.

예를 들어, Bob, Joe와 Jane으로 구성된 소셜 네트워크가 있다고 가정해봅시다. Bob과 Joe는 각각 Jane의 친구지만 그들끼리는 서로 친구가 아닙니다. Bob은 Jane이 직접적으로 참여한 액티비티들을 "팔로우" 하기로 선택했습니다. Jane은 Joe와 파일을 공유합니다.

In this example, Jane and Joe are each directly involved in the file sharing activity and together make up the Primary Audience for that event. Bob, having an interest in activities involving Jane, is the Secondary Audience. Knowing this, a system that produces or consumes the activity can intelligently notify each person of the event.

이 예시에서 Jane과 Joe는 각각 파일 공유 액티비티에 직접 참여하며, 두명 다 그 이벤트에 대한 1차 청중으로 구성됩니다. Jane과 관련된 액티비티에 관심이 있는 Bob은 2차 청중입니다. 이를 이용하여 액티비티를 생산하거나 소비하는 시스템은 각 사람에게 이벤트를 효율적으로 알릴수 있습니다.

While there are means (based on the action type, actor, object and target of the activity) to infer the primary audience for many types of activities, heuristics do not work in every case and do not provide a means of identifying the secondary audience. The [to](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-to), [cc](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-cc), [bto](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-bto) and [bcc](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-bcc) properties *MAY* be used within an Object to explicitly identify the Primary and Secondary audiences.

많은 유형의 액티비티에 대해 1차 청중들을 추론할 수 있는 수단(액티비티의 액션 타입, 액터, 객체와 대상)이 있지만, 휴리스틱은 언제나 작동하지 않기에 2차 청중을 판별하는 수단을 제공하지 않습니다. [to](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-to), [cc](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-cc), [bto](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-bto) 와 [bcc](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-bcc) 속성은 1차 및 2차 청중을 명시적으로 식별하기 위해 객체 내에서 사용 *할 수도* 있습니다.

The prototypical use case for an Object containing these properties is the publication and redistribution of objects through an intermediary. That is, an event source generates the object and publishes it to the intermediary which determines a subset of items to display to specific individual users or groups. Such a determination can be made, in part, by identifying the Primary and Secondary Audiences for each object.

이러한 속성을 포함하는 객체의 원형적인 사용 사례는 중개인을 통한 객체의 게시와 재배포입니다. 즉, 이벤트 소스는 객체를 생성하여 이를 중개자에게 공개하고, 중개자는 특정 개별 사용자나 그룹에 표시할 항목의 하위 집합을 결정합니다. 이러한 결정은 부분적으로 각 객체에 대한 1차 및 2차 청중의 식별에 의해 이루어질수 있습니다.

When the event source generates the object and specifies values for the `to` and `cc` fields, the intermediary *SHOULD* redistribute that object with the values of those fields intact, allowing any processor to see who the object has been targeted to. This is precisely the same model used by the `to` and `cc` fields in email systems.

이벤트 소스가 객체를 생성하고 `to`와 `cc`필드에 대한 값을 지정하면, 중개자는 해당 필드 값을 그대로 유지한채 해당 객체를 재배포하여 모든 프로세서가 대상 객체를 확인할 수 있도록 해야 하는것을 *권장합니다*. 이는 이메일 시스템에서 `to`와 `cc`가 사용하는것과 정확히 같은 모델입니다.

There are situations, however, in which disclosing the identity of specific members of the audience may be inappropriate. For instance, a user may not wish to let other users know that they are interested in various topics, individuals or types of events. To support this option, an implementation generating an object *MAY* use the `bto` and `bcc` properties to list entities to whom the object should be privately targeted. When an intermediary receives an object containing these properties, it *MUST* remove those values prior to redistributing the object. The intent is that systems *MUST* consider entities listed within the `bto` and `bcc` properties as part of the Primary and Secondary audience but *MUST NOT* disclose that fact to any other party.

하지만 특정 청중의 신원을 공개하는 것이 부적절 할수 있는 상황이 있습니다. 예를 들어, 사용자는 다양한 주제, 개인 또는 이벤트 타입에 관심이 있다는 것을 다른 사용자에게 알리고 싶지 않을수도 있습니다. 
이 옵션을 지원하기 위해 객체를 생성하는 구현단계에서는 `bto` 및 `bcc`속성을 사용하여 객체를 비공개 대상으로 해야하는 개체들을 나열 *할 수도* 있습니다. 중개인이 이러한 속성을 포함하는 객체를 수신할 경우, 객체를 재분배하기 전에 *반드시* 해당 값을 제거해야 합니다. 위 절차들의 의도는 시스템이 1차 및 2차 청중의 일부로 `bto`와 `bcc`에 열거된 개체들을 포함하는 것을 *반드시* 고려해야 하지만, 그 사실을 다른 당사자에게 공개하는것은 *절대 하지 말아야* 합니다.

Audience targeting information included within an Object only describes the intent of the object creator. With clear exception given to the appropriate handling of `bto` and `bcc`, this specification leaves it up to implementations to determine how the audience targeting information is used.

객체에 포함된 청중 대상 정보는 객체 작성자의 의도밖에 보여주지 않습니다. `bto`와 `bcc`의 적절한 취급에 대해서는 명확한 예외를 두지만, 이 규격에서는 청중 대상 정보의 이용 방법을 결정하는 것은 구현 방식에 달려 있게 하였습니다.

#### 5.1.1 청중과 컨텍스트 (Audience and Context)

_This section is non-normative._

_이 항목은 비표준입니다._

Activities are rarely isolated events. Often, multiple individual activities will be performed around a similar context or audience. For instance, a collaborators working on a shared project might perform multiple related activities in the process of achieving some goal. Such activities can be logically grouped together using the [context](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-context) property, and scoped to a particular audience using the [audience](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-audience) property.

액티비티는 대부분 격리되지 않은 이벤트입니다. 대부분의 경우, 유사한 컨텍스트나 청중을 중심으로 여러 개별적인 액티비티들이 수행되는 경우가 종종 있습니다. 예를들어 공유 프로젝트에서 작업하는 공동작업자는 일부 목표를 달성하는 과정에서 여러 관련된 액티비티들을 수행할 수 있습니다. 이러한 활동은 [콘텍스트(context)] 속성을 사용하여 논리적으로 그룹화할 수 있으며, [청중(audience)] 속성을 사용하여 특정 청중을 대상으로 범위를 좁힐 수 있습니다.

For instance, the following shows two related activities that share a common `context` and `audience`:

예를 들어, 다음은 공통적인 `context`와 `audience`을 공유하는 두 가지의 관련 액티비티들을 보여줍니다:

>Example 144
>
>```json
>{
> "summary": "Activities in Project XYZ",
>     "summary": "Sally created a note",
>      "summary": "A note",
>      "content": "A note"
>      "name": "Project XYZ"
>      "name": "Project XYZ Working Group"
>     "summary": "John liked Sally's note",
>       "name": "Project XYZ"
>       "name": "Project XYZ Working Group"
>}
>```

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

### 5.2 개체간의 관계 표현 (Representing Relationships Between Entities)

The [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) object is used to represent relationships between individuals. It can be used, for instance, to describe that one person is a friend of another, or that one person is a member of a particular organization. The intent of modeling Relationship in this way is to allow descriptions of activities that operate on the relationships in general, and to allow representation of Collections of relationships.

[관계(Relationship)] 개체는 개인 간의 관계를 나타내는데 사용됩니다. 예를 들어, 한 사람이 다른 사람의 친구라고 하거나, 한 사람이 특정 조직의 일원이라고 표현하는데 사용할 수 있습니다. 이러한 방식으로 관계를 모델링하는 이유는 관계 전반에 작용하는 액티비티들에 대한 설명을 허용하고 관계 컬렉션의 표현을 허용하기 위함입니다.

For instance, many social systems have a notion of a "friends list". These are the collection of individuals that are directly connected within a person's social graph. Suppose we have a user, Sally, with direct relationships to users Joe and Jane. Sally follows Joe's updates while Sally and Jane have a mutual relationship.

예를 들어, 많은 소셜 시스템들은 "친구 목록"이라는 개념을 가지고 있습니다. 이것은 한 개인의 사회적 그래프 안에서 직접 연결된 개인의 모음입니다. Sally라는 사용자가 Joe와 Jane과 직접적인 관계를 맺고 있다고 가정합시다. Sally는 Joe의 업데이트 내용을 따르는 반면 Sally와 Jane은 상호 관계를 맺고 있습니다.

Using the [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) object, we can model these relationships as:

[Relationship] 객체를 이용하여 이러한 관계를 다음과 같이 모델링할 수 있습니다:

>Example 145
>
>```json
>{
>  "summary": "Sally's friends list",
>      "summary": "Sally is influenced by Joe",
>      "summary": "Sally is a friend of Jane",
>}
>```

>Example 145
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

The [relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) property specifies the kind of relationship that exists between the two individuals identified by the [subject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-subject) and [object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) properties. Used together, these three properties form what is commonly known as a " [reified statement](http://patterns.dataincubator.org/book/reified-statement.html)" where [subject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-subject) identifies the subject, [relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) identifies the predicate, and [object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) identifies the object.

[관계](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) 속성은 [주체](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-subject)와 [객체](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) 속성으로 식별된 두 개인 사이에 존재하는 관계의 종류를 지정합니다. 이 세 가지 속성은 함께 사용되며, [주체](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-subject)가 대상을 식별하고, [관계](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship)가 술어를 식별하며, 사물이 대상을 식별하는 "[수정된 문장](http://patterns.dataincubator.org/book/reified-statement.html)"이라고 흔히 알려진 것을 형성합니다.

While use of reified statements can be problematic and confusing in certain situations, their use within the Activity Streams vocabulary to describe relationships provides a straightforward mechanism of describing changes to an individual's social graph. For instance, to indicate that Sally has created a new relationship to user Matt, an implementer can use the [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) object together with the [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create) activity:

수정된 문장의 사용은 특정 상황에서 문제가 있을수도 있고 혼란스러울수도 있지만, 관계를 기술하기 위한 Activity Streams 어휘 내에서 그들의 사용은 개인의 사회적 그래프에 변화를 기술하는 간단한 메커니즘을 제공합니다. 예를 들어, Sally가 사용자 Matt와 새로운 [관계](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship)를 만들었음을 나타내기 위해, 실행자는 [생성](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create) 액티비티과 함께 Relationship 객체를 사용할 수 있습니다.

>Example 146
>
>```json
>{
>  "summary": "Sally became a friend of Matt",
>}
>```

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

Additionally, modeling the relationship in this way allows implementers to articulate additional properties of the relationship itself. For instance, the date and time at which the relationship began or ended.

또한 이러한 방식으로 관계를 모델링하면 구현자는 관계 자체의 추가 특성을 명확하게 표현할 수 있습니다. 예를 들어, 관계가 시작되거나 종료된 날짜와 시간 이 이러한 경우에 해당합니다.

Implementations may reuse existing vocabularies that have been developed for the purpose of describing relationships, or create their own guided by requirements of their particular implementation. Existing vocabularies include the " [Friend of a Friend](http://xmlns.com/foaf/spec/)" and " [Relationship](http://vocab.org/relationship/)" vocabularies.

구현은 관계를 기술할 목적으로 개발된 기존 어휘를 재사용하거나, 특정 구현의 요구사항에 따라 자체적인 어휘를 생성할 수 있습니다. 기존 어휘로는 " [친구의 친구](http://xmlns.com/foaf/spec/)"와 " [관계](http://vocab.org/relationship/)" 어휘가 있습니다.

#### 5.2.1 "친구 요청" 모델링 (Modeling "friend requests")

_This section is non-normative._

_이 항목은 비표준입니다._

One common use case for many social platforms is the establishment of symmetrical "friend" relationships, in which one user initially extends a request to another user to establish a new connection. Once the connection is made, both users automatically begin receiving notifications about activities performed by the other, and the established relationship becomes visible in either user's "friends list".

많은 소셜 플랫폼의 일반적인 사용 사례는 대칭적인 "친구" 관계의 확립으로, 한 사용자가 처음에 다른 사용자에게 새로운 연결을 설정하도록 요청을 확장하는 것입니다. 일단 연결이 되면, 두 사용자 모두 자동으로 상대방의 활동에 대한 알림을 받기 시작하고, 확립된 관계는 두 사용자의 "친구 목록" 모두에서 볼 수 있게 됩니다.

The initial "friend request" can be modeled by composing the [Offer](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer) and [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) object types as in the following example:

초기 "친구 요청"은 다음 예시와 같이 [제안](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer) 및 [관계](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) 객체 타입을 구성하여 모델링할 수 있습니다:

>Example 147
>
>```json
>{
>  "summary": "Sally requested to be a friend of John",
>    "summary": "Sally and John's friendship",
>}
>```

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

Assuming the "friend request" is accepted, the remaining steps in this common application scenario can be represented as a set of distinct activities:

"친구 요청"이 받아들여진다고 가정할 경우, 이 공통 적용 시나리오의 나머지 단계는 일련의 구별되는 활동으로 나타낼 수 있습니다.

>Example 148
>
>```json
>{
>  "summary": "Sally and John's relationship history",
>      "summary": "John accepted Sally's friend request",
>      "summary": "John followed Sally",
>      "summary": "Sally followed John",
>      "summary": "John added Sally to his friends list",
>        "summary": "John's Connections"
>      "summary": "Sally added John to her friends list",
>        "summary": "Sally's Connections"
>}
>```

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

As illustrated in this example, accepting the "friend request" results in four additional activities including: John following Sally, Sally following John, John adding the relationship with Sally to his collection of Connections, and Sally adding the relationship with John to her collection of Connections.

이 예시처럼, "친구 요청"을 수락하면 Sally를 따르는 John, John을 따르는 Sally, 그의 커넥션 컬렉션에 Sally와의 관계를 추가하는 John, 그리고 John과의 관계를 그녀의 커넥션 컬렉션에 추가하는 네 가지 추가 액티비티가 발생합니다.

In this example,

이 예시에서는,

1\. The optional [result](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-result) property is used within the `Accept` activity to identify the additional activities that occurred as a result of the accept.

2\. The optional [context](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-context) property is used to relate the various activities back to a common reference point, which in this example is the relationship being established. The `context` allows an implementation to efficiently group related activities together for display or analytic purposes.

1. 선택적 결과 속성은 `Accept` 액티비티 내에서 수락의 결과로 발생한 추가 액티비티을 식별하기 위해 사용됩니다.

2. 선택적 컨텍스트 속성은 다양한 액티비티을 공통의 기준점과 다시 연관시키기 위해 사용되는데, 이 예에서는 설정되고 있는 관계가 그것입니다. 이러한 맥락에서 `context`는 표시 또는 분석 목적을 위해 관련 액티비티을 효율적으로 그룹화할 수 있습니다.

### 5.3 장소 표현 (Representing Places)

_This section is non-normative._

_이 항목은 비표준입니다._

The [Place](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-place) object is used to represent both physical and logical locations. While numerous existing vocabularies exist for describing locations in a variety of ways, inconsistencies and incompatibilities between those vocabularies make it difficult to achieve appropriate interoperability between implementations. The `Place` object is included within the Activity vocabulary to provide a minimal, interoperable starting point for describing locations consistently across Activity Streams 2.0 implementations.

[장소](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-place) 객체는 물리적 위치와 논리적 위치 모두를 나타내기 위해 사용됩니다. 위치를 다양한 방식으로 설명하기 위해 수많은 기존의 어휘가 존재하지만, 이러한 어휘들 간의 불일치와 비호환성은 구현간 적절한 상호운용성을 달성하는 것을 어렵게 합니다. `Place` 객체는 Activity Streams 2.0 구현에 걸쳐 일관적으로 위치를 설명하기 위한 최소의 상호운용 가능한 출발점을 제공하기 위해 Activity 어휘에 포함되어 있습니다.

The `Place` object is intentionally flexible. It can, for instance, be used to identify a location simply by name:

`Place` 객체는 의도적으로 유연합니다. 예를 들어, 단순히 이름만으로 위치를 식별하는데 사용될수 있습니다:

>Example 149
>
>```json
>{
>  "name": "San Francisco, CA"
>}
>```

>예시 149
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "샌프란시스코, 캘리포니아"
>}
>```

Or, by [longitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-longitude) and [latitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-latitude):

또는 경도 및 위도 기준으로는:

>Example 150
>
>```json
>{
>  "name": "San Francisco, CA",
>}
>```

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

The `Place` object can also describe an area around a given point using the [radius](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-radius) property, the [altitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-altitude) of the location, and a degree of [accuracy](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accuracy).

또한 `Place` 객체는 [반지름](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-radius) 속성, 위치 [고도](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-altitude) 및 [정확도](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accuracy)를 사용하여 주어진 지점 주변의 영역을 설명할 수 있습니다.

While publishers are not required to use these specific properties and *MAY* make use of other mechanisms for describing locations, consuming implementations that support the [Place](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-place) object *MUST* support the use of these properties.

출판사는 이러한 특정 속성을 사용할 필요가 없고 위치를 설명하는 다른 메커니즘을 사용 *할 수도* 있지만, 장소 [객체](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-place) 지원하는 구현을 만들 경우에는 *반드시* 이러한 속성 사용을 지원해야 합니다.

### 5.4 질문 표현 (Representing Questions)

_This section is non-normative._

_이 항목은 비표준입니다._

The [Question](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question) object can be used to express various types of inquiries.

[질문](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question) 객체는 다양한 유형의 질문을 표현하는 데 사용할 수 있습니다.

For instance, simple open-ended questions similar to those posted to crowd-sourced question and answer websites:

예를 들어, 크라우드소싱된 질문과 정답 웹사이트에 게시된 것과 유사한 간단한 개방형 질문이 있습니다:

>Example 151
>
>```json
>{
>  "name": "A question about robots",
>  "content": "I'd like to build a robot to feed my cat. Should I use Arduino or Raspberry >Pi?"
>}
>```

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

Multiple-choice questions or "polls" are also supported using either the [oneOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-oneof) or [anyOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-anyof) properties:

다중 선택 질문 또는 "투표"도 [oneOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-oneof) 또는 [anyOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-anyof) 속성을 사용하여 지원됩니다:

>Example 152
>
>```json
>{
>  "name": "A question about robots",
>   "content": "I'd like to build a robot to feed my cat. Which platform is best?",
>     {"name": "arduino"},
>     {"name": "raspberry pi"}
> }
>```

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

Responses to questions are expressed as [Objects](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) containing an [inReplyto](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-inreplyto) property referencing the Question.

질문에 대한 응답은 질문을 참조하는 [inReplyto](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-inreplyto) 속성이 포함된 [객체](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object)로 표현됩니다.

>Example 153
>
>```json
>{
> "name": "아두이노"
>}
>```

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

Because [Question](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question) objects are also instances of [Activity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity), the [result](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-result) property can be used to express the results or outcome of the Question (as appropriate):

[질문](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question) 객체는 또한 [액티비티](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity)의 인스턴스이기 때문에 [결과](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-result) 속성을 사용하여 질문의 결과나 결과를 (적절하게) 표시할 수 있습니다:

>Example 154
>
>```json
>{
>  "name": "A question about robots",
>   "content": "I'd like to build a robot to feed my cat. Which platform is best?",
>     {"name": "arduino"},
>     {"name": "raspberry pi"}
>         "name": "arduino"
>         "name": "arduino"
>         "name": "raspberry pi"
>     "content": "Users are favoriting &quot;arduino&quot; by a 33% margin."
> }
> ```

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

### 5.5 역 액티비티와 "실행 취소" (Inverse Activities and "Undo")

_This section is non-normative._

_이 항목은 비표준입니다._

Several of the core [Activity types](https://www.w3.org/TR/activitystreams-vocabulary/#activity-types) are defined as natural inversions of one another. These include:

몇가지 핵심 [액티비티 타입](https://www.w3.org/TR/activitystreams-vocabulary/#activity-types)은 서로에 대한 자연 반전으로 정의됩니다. 여기에는 다음 타입들이 포함됩니다:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept) 와 [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject),
- [Arrive](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-arrive) 와 [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave),
- [Join](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-join) 과 [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave),
- [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create) 와 [Delete](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-delete),
- [Like](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like) 와 [Dislike](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-dislike)

It is important to note that these types of activities are semantically distinct from one another and have no direct relationship on the other. That is, for example, if an actor "likes" a note at one point in time then later "dislikes" it, the "dislike" activity does not "undo" or negate out the prior "like".

이러한 유형의 액티비티들은 의미상 구별되며 다른 유형의 액티비티에는 직접적인 관계가 없습니다. 즉, 액터가 한 시점에 노트를 "좋아요"라고 했다가 나중에 "싫어요"라고 하면, "싫어요" 액티비티는 이전의 액티비티를 "실행취소"하거나 "좋아요"를 부정하여 처리하지 않습니다.

The appropriate interpretation for the following is that Sally first liked, then later disliked John's note:

다음에 대한 적절한 해석은 Sally가 처음에는 좋아하다가 나중에는 John의 쪽지를 싫어했다는 것입나다:

>Example 155
>
>```json
>{
>  "summary": "History of John's note",
>      "summary": "Sally liked John's note",
>        "summary": "John's note",
>        "content": "My note"
>      "summary": "Sally disliked John's note",
>        "summary": "John's note",
>        "content": "My note"
> }
>```

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

The [Undo](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-undo) activity type is defined to provide the specific ability to undo or cancel out a prior activity. The appropriate interpretation for the following, then, is that Sally liked John's note at one point but has explicitly redacted that like later on.

[실행 취소](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-undo) 액티비티 타입은 이전 활동을 실행 취소하거나 취소할 수 있는 특정 기능을 제공하도록 정의됩니다. 그렇다면, 다음에 대한 적절한 해석은 Sally가 어느 순간 John의 노트를 좋아했지만 나중에 그런 식으로 명백하게 수정했다는 것입니다.

>Example 156
>
>```json
>{
> "summary": "History of John's note",
>     "summary": "Sally liked John's note",
>       "summary": "John's note",
>       "content": "My note"
>     "summary": "Sally no longer likes John's note",
>}
>```

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

The end result of the former example is that Sally has indicated that she changed her opinion about John's note and now dislikes it, while in the latter example she currently neither likes or dislikes it.

전자의 예에 대한 최종 결과는 Sally가 John의 노트에 대한 자신의 의견을 바꾸었고 지금은 그것을 싫어한다고 지적한 반면, 후자의 예에서는 현재 그것을 좋아하지도 싫어하지도 않습니다.

### 5.6 멘션, 태그 및 다른 일반적인 소셜 마이크로신택스들 (Mentions, Tags and Other Common Social Microsyntaxes)

_This section is non-normative._

_이 항목은 비표준입니다._

Many social software systems use special text-based microsyntaxes that allow users to define special addressing for notifications, linking, or categorization within objects. For example, including text such as "`@username`" within an object's content will often route the object to a special "mentions" or "inbox" stream for a particular user. Likewise, including text such as " `#topic`" within the object's content will often mark the object as being related to the topic "`topic`". Such mechanisms are commonly referred to as "mentions" and "hashtags", respectively.

많은 소셜 소프트웨어 시스템은 사용자가 객체 내에서 알림, 링크 또는 분류에 대한 특별한 주소 지정을 정의할 수 있는 특수 텍스트 기반의 마이크로싱택을 사용합니다. 예를 들어, 객체의 내용 내에 "`@username`"과 같은 텍스트를 포함하면 객체가 특정 사용자를 위한 특별한 "멘션" 또는 "인박스" 스트림으로 라우팅되는 경우가 많습니다. 마찬가지로, 오브젝트의 내용 내에 "`#topic`"과 같은 텍스트를 포함하면 오브젝트가 "`topic`" 주제와 관련된 것으로 표시되는 경우가 많습니다. 이러한 메커니즘을 일반적으로 "멘션"과 "해시태그"라고 부릅니다.

While such microsyntaxes *MAY* be used within the values of the [content](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-content), [name](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-name), and [summary](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-summary) properties on an Activity Streams [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object), implementations *SHOULD NOT* be required to parse the values of those properties in order to determine the appropriate routing of notifications, categorization or linking between objects. Instead, publishers *SHOULD* make appropriate use of the vocabulary terms provided specifically for these purposes.

이러한 마이크로싱택스는 Activity Stream [객체](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object)의 [컨텐츠](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-content), [이름](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-name) 및 [요약](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-summary) 속성의 값 내에서 사용 *할 수도* 있지만, 적절한 통지 라우팅, 분류 또는 객체 간 연결을 결정하기 위해 그러한 속성 값을 구문 분석할 필요가 *있어서는 안됩니다*. 대신에 출판사는 이러한 목적을 위해 특별히 제공된 어휘 용어를 적절하게 *사용해야 합니다*.

For example, suppose that an author wishes to send a note of thanks to another user named "@sally" with a hashtag of "#givingthanks". A typical way this message would appear within the content of a note is shown below:

예를 들어, 저자가 "@sally"라는 이름의 다른 사용자에게 "#감사드립니다"라는 해시태그와 함께 "@sally"라는 감사 메모를 보내고 싶다고 가정해 봅시다. 이 메시지가 노트의 내용 내에 나타나는 일반적인 방법은 다음과 같습니다.

[//Comment]: # "일단 한국어 태그는 mastodon에서 작동하는것을 확인하였고, tag에 대한 언어 제약이 없었던것으로 판단되어 #givingthanks를 #감사드립니다 로 번역하였습니다."

<div align="center"><em>
Figure 1 A simple note with a mention an a hashtag:
</em></div>

<div align="center"><em>
그림 1 해시 태그가 포함된 간단한 참고 사항:
</em></div>

"Thank you @sally for all your hard work! #givingthanks"

"@sally님의 많은 노고에 감사드립니다! #감사드립니다"

[//Comment]: # "일단 국립국어원에서는 '노고'보다는 다른 단어로 대체하는게 좋다는데..."

A typical social software implementation would typically render such a content such that "`@sally`" is replaced with a hyperlink to "@sally"'s social profile page and "`#givingthanks`" is replaced with a hyperlink to a listing of other notes that have been "tagged" with the same topic. Most implementations would also send a special notification to sally letting her know that a note mentioning her has been created.

일반적인 소셜 소프트웨어 구현은 일반적으로 "@sally"가 "@sally"의 소셜 프로필 페이지에 대한 하이퍼링크로 대체되고 "#감사드립니다"가 동일한 주제를 "태그"한 다른 노트 목록에 대한 하이퍼링크로 대체되는 것과 같은 콘텐츠를 렌더링할 수 있습니다. 또한 대부분의 구현은 Sally에게 자신을 언급하는 노트가 작성되었음을 알리는 특별 통지를 보낼 것입니다.

The following illustrates an equivalent Activity Streams [Note](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-note) object:

다음은 동등한 Activity Streams [노트](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-note) 객체를 보여줍니다:

>Example 157
>
>```json
>{
>  "name": "A thank-you note",
>  "content": "Thank you <a href='http://sally.example.org'>@sally</a>
>      for all your hard work!
>      <a href='http://example.org/tags/givingthanks'>#givingthanks</a>",
>    "id": "http://example.org/tags/givingthanks",
>    "name": "#givingthanks"
>}
>```

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

The `to` property indicates that the user "@sally" is to be considered part of the [primary audience](https://www.w3.org/TR/activitystreams-vocabulary/#audienceTargeting) of the note and should therefore receive notification. The `tag` property associates the Note with a reference to " `http://example.org/tags/givingthanks`". Note that the `content` still includes the "`@sally`" and " `#givingthanks`" microsyntaxes but that consuming implementations are not required to parse those in order to make the appropriate associations.

`to` 속성은 사용자 "@sally"가 노트의 [주요 청중](https://www.w3.org/TR/activitystreams-vocabulary/#audienceTargeting)의 일부로 간주되므로 통지를 받아야 함을 나타냅니다. `tag` 속성은 노트를 "`http://example.org/tags/givingthanks`"에 대한 참조와 연결됩니다. `content`에는 여전히 "`@sally`"와 "`#감사드립니다`" 마이크로신택스가 포함되지만, 적절한 연결을 위해 이를 구문 분석하는데 소비적인 구현이 필요하지 않다는 점에 유의하시길 바랍니다.

In the case a publisher wishes to indicate a mention without an associated notification, the publisher can use the [Mention](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-mention) object type as a value of the [tag](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tag) property.

게시자가 관련 통지 없이 언급을 표시하려는 경우, 게시자는 [멘션](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-mention) 객체 타입을 [태그](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tag) 속성의 값으로 사용할 수 있습니다.

>Example 158
>
>```json
>{
>  "name": "A thank-you note",
>  "content": "Thank you @sally for all your hard work! #givingthanks",
>      "id": "http://example.org/tags/givingthanks",
>      "name": "#givingthanks"
>}
>```

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

### 5.7 출발지 및 목표 (Origin and Target)

The [origin](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-origin) and [target](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-target) properties of an Activity respectively identify the entities from which and to which the action is directed. For instance, in the English statement, "Sally moved the file from Folder A to Folder B", the `origin` is "Folder A" and the `target` is "Folder B". This activity is illustrated in the example below:

액티비티의 [출발지](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-origin)와 [목표](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-target) 속성은 각각 조치가 지시되는 대상과 대상을 식별합니다. 예를 들어 영어 문장 "A폴더에서 B폴더로 파일을 옮겼습니다"에서 `origin`은 "Folder A"이고 `target`은 "Folder B"입니다. 이 액티비티은 아래 예에 설명되어 있습니다:

>Example 159
>
>```json
>{
>    "summary": "Sally moved the sales figures from Folder A to Folder B",
>      "name": "sales figures"
>      "name": "Folder A"
>      "name": "Folder B"
>  }
>```

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

The `origin` property is applicable to any type of activity for which the English preposition "from" can be considered applicable in the sense of identifying the origin, source or provenance of the activity's `object`.

`origin` 속성은 액티비티 `object`의 출발지, 출처 또는 입증의 관점에서 영어 전치사 "출처"가 적용 가능한 것으로 간주될 수 있는 모든 타입의 액티비티에 적용됩니다.

The `target` property is applicable to any type of activity for which the English preposition "to" can be considered applicable in the sense of identifying the indirect object or destination of the activity's `object`.

`target` 특성은 액티비티 `object`의 간접 대상 또는 목적지를 식별한다는 의미에서 영어 전치사 "to"가 적용 가능하다고 간주할수 있는 모든 타입의 액티비티에 적용할 수 있습니다.

### 5.8 액티비티 타입의 사용 사례 (Activity Type Motivating Use Cases)

_This section is non-normative._

_이 항목은 비표준입니다._

The [Activity types](https://www.w3.org/TR/activitystreams-vocabulary/#activity-types) defined in this vocabulary have been primarily selected to address the commonly implemented social use cases described below.

이 어휘에서 정의한 액티비티 타입은 아래에 기술된 공통적으로 구현된 사회적 사용 사례를 다루기 위해 주로 선택되었습니다.

#### 5.8.1 컨텐츠 관리 (Content Management)

The Content Management use case primarily deals with activities that involve the creation, modification or deletion of content. This includes, for instance, activities such as "John created a new note", "Sally updated an article", and "Joe deleted the photo".

콘텐츠 관리 활용 사례는 주로 콘텐츠의 생성, 수정 또는 삭제와 관련된 액티비티을 다룹니다. 예를 들어 "John이 새 노트를 만들어습니다", "Sally가 노트를 업데이트 했습니다", "Joe는 사진을 삭제했습니다" 등의 액티비티을 포함합니다.

Relevant Activities:

관련 액티비티:

- [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create)
- [Delete](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-delete)
- [Update](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-update)

#### 5.8.2 컬렉션 관리 (Collection Management)

The Collection Management use case primarily deals with activities involving the management of content within collections. Examples of collections include things like folders, albums, friend lists, etc. This includes, for instance, activities such as "Sally added a file to Folder A", "John moved the file from Folder A to Folder B", etc.

컬렉션 관리 사용 사례는 주로 컬렉션 내 콘텐츠 관리와 관련된 액티비티를 다룹니다. 컬렉션의 예로는 폴더, 앨범, 친구 목록 등이 있습니다. 예를 들어 "Sally는 폴더 A에 파일을 추가했습니다", "John이 해당 파일을 폴더 A에서 폴더 B로 옮겼습니다" 등의 액티비티를 포함합니다.

Relevant Activities:

관련 액티비티:

- [Add](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-add)
- [Move](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-move)
- [Remove](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-remove)

#### 5.8.3 리액션 (Reactions)

The Reactions use case primarily deals with reactions to content. This can include activities such as liking or disliking content, ignoring updates, flagging content as being inappropriate, accepting or rejecting objects, etc.

리액션 활용 사례는 주로 콘텐츠에 대한 리액션을 다룬다. 여기에는 콘텐츠를 좋아하거나 싫어하거나, 업데이트를 무시하거나, 콘텐츠를 부적절하다고 플래그 지정하거나, 개체를 승인하거나 거부하는 등의 액티비티들이 포함될 수 있습니다.

Relevant Activities:

관련 액티비티:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept)
- [Block](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-block)
- [Dislike](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-dislike)
- [Flag](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-flag)
- [Ignore](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-ignore)
- [Like](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like)
- [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject)
- [TentativeAccept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativeaccept)
- [TentativeReject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativereject)

#### 5.8.4 이벤트 RSVP (Event RSVP)

The Event RSVP use case primarily deals with invitations to events and RSVP type responses.

이벤트 RSVP 활용 사례는 주로 이벤트에 대한 초대와 RSVP 타입 응답을 다룹니다.

Relevant Activities:

관련 액티비티:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept)
- [Ignore](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-ignore)
- [Invite](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-invite)
- [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject)
- [TentativeAccept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativeaccept)
- [TentativeReject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativereject)

#### 5.8.5 그룹 관리 (Group Management)

The Group Management use case primarily deals with management of groups. It can include, for instance, activities such as "John added Sally to Group A", "Sally joined Group A", "Joe left Group A", etc.

그룹 관리 활용 사례는 주로 그룹 관리를 다룹니다. 예를 들어, "John이 A그룹에 Sally를 추가했습니다", "Sally는 A그룹에 참가했습니다", "Joe는 그룹을 떠났습니다" 등과 같은 활동을 포함할수 있습니다.

Relevant Activities:

관련 액티비티:

- [Add](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-add)
- [Join](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-join)
- [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave)
- [Remove](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-remove)

#### 5.8.6 컨텐츠 경험 (Content Experience)

The Content Experience use case primarily deals with describing activities involving listening to, reading, or viewing content. For instance, "Sally read the article", "Joe listened to the song".

콘텐츠 경험 활용 사례는 주로 콘텐츠 듣기, 읽기 또는 보기와 관련된 활동을 기술하는 것을 다룹니다. 예를 들어, "Sally는 게시물을 읽었습니다" "Joe는 노래를 들었습니다" 같은 예시들이 있습니다.

Relevant Activities:

관련 액티비티:

- [Listen](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-listen)
- [Read](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-read)
- [View](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-view)

#### 5.8.7 지구-사회적 행사 (Geo-Social Events)

The Geo-Social Events use case primarily deals with activities involving geo-tagging type activities. For instance, it can include activities such as "Joe arrived at work", "Sally left work", and "John is travel from home to work".

지구-사회적 이벤트 활용 사례는 주로 지오태깅(geo-tagging) 타입 액티비티와 관련된 활동들을 다룹니다. 예를 들어, "조이는 출근했습니다", "Sally는 퇴근했습니다", "John이 집에서 직장까지 가는 중입니다"과 같은 액티비티들을 포함할 수 있습니다.

Relevant Activities:

관련 액티비티:

- [Arrive](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-arrive)
- [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave)
- [Travel](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-travel)

#### 5.8.8 알림 (Notification)

The Notification use case primarily deals with calling attention to particular objects or notifications.

알림 사용 사례는 주로 특정 객체 또는 알림에 대한 주의를 환기하는 것을 다룹니다.

Relevant Activities:

관련 액티비티:

- [Announce](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-announce)

#### 5.8.9 질문 (Questions)

the Questions use case primarily deals with representing inquiries of any type. See [5.4 Representing Questions](https://www.w3.org/TR/activitystreams-vocabulary/#questions) for more information.

질문 활용 사례는 주로 모든 타입의 대표 질문을 다룹니다. 자세한 내용은 [5.4 질문 표현하기](https://www.w3.org/TR/activitystreams-vocabulary/#questions)를 참조하시길 바랍니다.

Relevant Activities:

관련 액티비티:

- [Question](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question)

#### 5.8.10 관계 관리 (Relationship Management)

The Relationship Management use case primarily deals with representing activities involving the management of interpersonal and social relationships (e.g. friend requests, management of social network, etc). See [5.2 Representing Relationships Between Entities](https://www.w3.org/TR/activitystreams-vocabulary/#connections) for more information.

관계 관리 활용 사례는 주로 대인관계 및 사회적 관계의 관리와 관련된 대표 액티비티(예: 친구 요청, 소셜 네트워크 관리 등)을 다룬다. 자세한 내용은 [5.2 기업 간의 관계 표현](https://www.w3.org/TR/activitystreams-vocabulary/#connections)을 참조하시길 바랍니다.

Relevant Activities:

관련 액티비티:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept)
- [Add](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-add)
- [Block](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-block)
- [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create)
- [Delete](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-delete)
- [Follow](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-follow)
- [Ignore](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-ignore)
- [Invite](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-invite)
- [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject)

#### 5.8.11 액티비티 부정 (Negating Activity)

The Negating Activity use case primarily deals with the ability to redact previously completed activities. See [5.5 Inverse Activities and "Undo"](https://www.w3.org/TR/activitystreams-vocabulary/#inverse) for more information.

부정 액티비티 사용 사례는 주로 이전에 완료된 액티비티을 수정하는 기능을 다룹니다. 자세한 내용은 [5.5 역방향 액티비티 및 "실행 취소"](https://www.w3.org/TR/activitystreams-vocabulary/#inverse)를 참조하시기 바랍니다.

Relevant Activities:

관련 액티비티:

- [Undo](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-undo)

#### 5.8.12 제공 (Offers)

The Offers use case deals with activities involving offering one object to another. It can include, for instance, activities such as "Company A is offering a discount on purchase of Product Z to Sally", "Sally is offering to add a File to Folder A", etc.

제안 사용 사례는 한 개체를 다른 개체에 제공하는 것과 관련된 액티비티을 다룹니다. 예를 들어, "A 회사가 Sally에게 제품 Z 구매에 대한 할인을 제공하고 있다", "Sally가 A 폴더에 파일을 추가하려고 한다" 등의 액티비티가 포함될 수 있습니다.

Relevant Activities:

관련 액티비티:

- [Offer](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer)
