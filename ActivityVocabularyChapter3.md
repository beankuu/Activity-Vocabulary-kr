[목차로 돌아가기](ActivityVocabularyContents.md)

## 3. 확장 타입 (Extended Types)

Base URI: `https://www.w3.org/ns/activitystreams#`.

기반 URI: `https://www.w3.org/ns/activitystreams#`.

The Activity Streams 2.0 Extended Types include Activity and Object subtypes that are common to many social Web applications. They are divided into three sets:

Activity Streams 2.0 확장 타입에는 많은 소셜 웹 어플리케이션에게 공통적인 액티비티와 Object의 하위 타입들이 포함됩니다. 이들은 다음과 같이 세가지 유형으로 나뉩니다:

- Activity Types
- Actor Types
- Object Types

[//Comment]: # "BLANK"

- [액티비티 타입](https://www.w3.org/TR/activitystreams-vocabulary/#activity-types)
- [액터 타입](https://www.w3.org/TR/activitystreams-vocabulary/#actor-types)
- [객체 타입](https://www.w3.org/TR/activitystreams-vocabulary/#object-types)

Support for specific extended vocabulary types is expected to vary, with implementations only selecting the extended types and properties that make sense within the specific context and requirements of those applications. However, to avoid possible interoperability issues, implementations *MUST* avoid using extension types or properties that unduly overlap with or duplicate the extended vocabulary defined here.

특정한 확장 어휘 타입에 대한 지원은 다양할것으로 예상되며, 구현시에는 해당 응용프로그램의 특정 컨텍스트와 요구사항에 적합한 확장유형들과 속성들만 선택하면 됩니다. 하지만 상호 운용성(interoperability) 문제를 피하기 위해서는 구현시 이 문서에 정의된 확장 어휘와 중복되거나 중복되는 확장 타입 또는 속성을 *절대* 사용하지 말아야 합니다.

### 3.1 액티비티 타입 (Activity Types)

All Activity Types inherit the properties of the base [Activity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity) type. Some specific Activity Types are subtypes or specializations of more generalized Activity Types (for instance, the [Invite](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-invite) Activity Type is a more specific form of the [Offer](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer) Activity Type).

모든 액티비티 타입은 기본 [액티비티(Activity)](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity) 타입의 속성을 상속합니다. 일부 특정한 액티비티 타입들은 더욱더 일반화된 액티비티 타입의 하위타입 이거나 특수화된 경우입니다 (예를 들어, [Invite](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-invite) 액티비티 타입은 [Offer](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer) 액티비티 타입이 특수화된 경우입니다).

The Activity Types include:

액티비티 타입은 다음과 같은 타입들을 포함합니다:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept)
- [Add](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-add)
- [Announce](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-announce)
- [Arrive](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-arrive)
- [Block](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-block)
- [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create)
- [Delete](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-delete)
- [Dislike](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-dislike)
- [Flag](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-flag)
- [Follow](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-follow)
- [Ignore](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-ignore)
- [Invite](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-invite)
- [Join](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-join)
- [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave)
- [Like](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like)
- [Listen](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-listen)
- [Move](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-move)
- [Offer](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer)
- [Question](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question)
- [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject)
- [Read](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-read)
- [Remove](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-remove)
- [TentativeReject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativereject)
- [TentativeAccept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativeaccept)
- [Travel](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-travel)
- [Undo](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-undo)
- [Update](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-update)
- [View](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-view)


#### [Class] Accept

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Accept`
Notes: | Indicates that the `actor` accepts the `object`. The `target` property can be used in certain circumstances to indicate the context into which the `object` has been accepted.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Accept`
비고: | `actor`가 `object`를 수락(accept)함을 나타냅니다. `target` 속성은 특정 상황에서 `object`가 받아들여진 컨텍스트를 나타내기 위해 사용될 수 있습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 9
>
>```json
>{
>  "summary": "Sally accepted an invitation to a party",
>    "name": "Going-Away Party for Jim"
>}
>```

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

>Example 10
>
>```json
>{
>  "summary": "Sally accepted Joe into the club",
>    "name": "The Club"
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

#### [Class] TentativeAccept

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeAccept`
Notes: | A specialization of Accept indicating that the acceptance is tentative.
Extends: | Accept
Properties: | Inherits all properties from Accept.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeAccept`
비고: | 수락(acceptance)이 잠정적임을 나타내는, Accept의 특화된 경우입니다.
상속함: | Accept
속성: | Accept로부터 모든 속성을 상속받습니다.

>Example 11
>
>```json
>{
>  "summary": "Sally tentatively accepted an invitation to a party",
>    "name": "Going-Away Party for Jim"
>}
>```

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


#### [Class] Add

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Add`
Notes: | Indicates that the `actor` has added the `object` to the `target`. If the `target` property is not explicitly specified, the target would need to be determined implicitly by context. The `origin` can be used to identify the context from which the `object` originated.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Add`
비고: | `actor`가 `object`를 `target`에 추가하였음을 나타냅니다. `target` 속성이 명시적으로 지정되어 있지 않으면, 대상(target)은 컨텍스트에 의해 암시적으로 결정되어야 합니다. `origin`은 `object`가 시작된 컨텍스트를 식별하는데 사용할 수도 있습니다.`
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 12
>
>```json
>{
>  "summary": "Sally added an object",
>}
>```

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

>Example 13
>
>```json
>{
>  "summary": "Sally added a picture of her cat to her cat picture collection",
>    "name": "A picture of my cat",
>    "name": "Camera Roll"
>    "name": "My Cat Pictures"
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


#### [Class] Arrive

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Arrive`
Notes: | An IntransitiveActivity that indicates that the `actor` has arrived at the `location`. The `origin` can be used to identify the context from which the `actor` originated. The `target` typically has no defined meaning.
Extends: | IntransitiveActivity
Properties: | Inherits all properties fom IntransitiveActivity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Arrive`
비고: | `actor`가 `location`에 도착했음(arrived)을 나타내는 IntransitiveActivity입니다. `origin`은 `actor`가 시작된 컨텍스트를 식별하는데 사용할 수도 있습니다. 이 클래스의 경우, `target`은 일반적으로 정의된 의미가 없습니다.
상속함: | IntransitiveActivity
속성: | IntransitiveActivity로부터 모든 속성을 상속받습니다.

>Example 14
>
>```json
>{
>  "summary": "Sally arrived at work",
>    "name": "Work"
>    "name": "Home"
>}
>```

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

#### [Class] Create

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Create`
Notes: | Indicates that the `actor` has created the `object`.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Create`
비고: | `actor`가 `object`를 생성했음(created)을 나타냅니다
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 15
>
>```json
>{
>  "summary": "Sally created a note",
>    "name": "A Simple Note",
>    "content": "This is a simple note"
>}
>```

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

#### [Class] Delete

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Delete`
Notes: | Indicates that the `actor` has deleted the `object`. If specified, the `origin` indicates the context from which the `object` was deleted.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Delete`
비고: | `actor`가 `object`를 삭제했음(deleted)을 나타냅니다. 특별히 지정된 경우, `origin`은 `object`가 삭제된 컨텍스트를 나타냅니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

[//Comment]: # "If specified? 특별히 지정된 경우?"

>Example 16
>
>```json
>{
>  "summary": "Sally deleted a note",
>
>    "name": "Sally's Notes"
>}
>```

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

#### [Class] Follow

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Follow`
Notes: |  Indicates that the `actor` is "following" the `object`. Following is defined in the sense typically used within Social systems in which the actor is interested in any activity performed by or on the object. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Follow`
비고: | `actor`가 `object`를 "따르고(following)" 있음을 나타냅니다. Following은 일반적으로 소셜 시스템 내에서 액터가 주어진 객체에 의해 또는 주어진 객체가 수행하는 모든 액티비티에 관심이 있다 라는 의미로 정의됩니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 17
>
>```json
>{
>  "summary": "Sally followed John",
>}
>```

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

#### [Class] Ignore

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Ignore`
Notes: | Indicates that the `actor` is ignoring the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Ignore`
비고: | `actor`가 `object`를 무시하고(ignoring) 있음을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 18
>
>```json
>{
>  "summary": "Sally ignored a note",
>}
>```

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


#### [Class] Join

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Join`
Notes: | Indicates that the `actor` has joined the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Join`
비고: | `actor`가 `object`에 합류(join)했음을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 19
>
>```json
>{
>  "summary": "Sally joined a group",
>    "name": "A Simple Group"
>}
>```

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

#### [Class] Leave

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Leave`
Notes: | Indicates that the `actor` has left the `object`. The `target` and `origin` typically have no meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Leave`
비고: | `actor`가 `object`를 떠났음(left)을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 20
>
>```json
>{
>  "summary": "Sally left work",
>    "name": "Work"
>}
>```

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

>Example 21
>
>```json
>{
>  "summary": "Sally left a group",
>    "name": "A Simple Group"
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

#### [Class] Like

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Like`
Notes: | Indicates that the `actor` likes, recommends or endorses the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Like`
비고: | `actor`가 `object`를 좋아(likes)하거나, 추천(recommends)하거나 또는 지지(endorses)함을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 22
>
>```json
>{
>  "summary": "Sally liked a note",
>}
>```

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

#### [Class] Offer

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Offer`
Notes: | Indicates that the `actor` is offering the `object`. If specified, the `target` indicates the entity to which the `object` is being offered.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Offer`
비고: | `actor`가 `object`를 제공(offering)하고 있음을 나타냅니다. 특별히 지정된 경우, `origin`은 `object`가 제공하는 개체(entity)를 나타냅니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 23
>
>```json
>{
>  "summary": "Sally offered 50% off to Lewis",
>    "name": "50% Off!"
>}
>```

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


#### [Class] Invite

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Invite`
Notes: | A specialization of Offer in which the `actor` is extending an invitation for the `object` to the `target`.
Extends: | Offer
Properties: | Inherits all properties from Offer.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Invite`
비고: | `actor`가 `object`에 대한 초대(invitation)를 `target`으로 확장하는, Offer의 특화된 경우입니다.
상속함: | Offer
속성: | Offer로부터 모든 속성을 상속받습니다.

>Example 24
>```json
>{
>  "summary": "Sally invited John and Lisa to a party",
>
>    "name": "A Party"
>}
>```

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

#### [Class] Reject

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Reject`
Notes: | Indicates that the `actor` is rejecting the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Reject`
비고: | `actor`가 `object`를 거부(rejecting)함을 나타냅니다. 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 25
>
>```json
>{
>  "summary": "Sally rejected an invitation to a party",
>    "name": "Going-Away Party for Jim"
>}
>```

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

#### [Class] TentativeReject

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeReject`
Notes: | A specialization of Reject in which the rejection is considered tentative.
Extends: | Reject
Properties: | Inherits all properties from Reject.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeReject`
비고: | 거부함(rejection)이 잠정적(tentative)임을 나타내는, Reject의 특화된 경우입니다.
상속함: | Reject
속성: | Reject로부터 모든 속성을 상속받습니다.

>Example 26
>
>```json
>{
>  "summary": "Sally tentatively rejected an invitation to a party",
>      "name": "Going-Away Party for Jim"
>}
>```

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

#### [Class] Remove

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Remove`
Notes: | Indicates that the `actor` is removing the `object`. If specified, the `origin` indicates the context from which the `object` is being removed.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Remove`
비고: | `actor`가 `object`를 제거(removing)하고 있음을 나타냅니다. 특별히 지정된 경우, `origin`은 `object`가 제거되는 컨텍스트를 나타냅니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 27
>
>```json
>{
>  "summary": "Sally removed a note from her notes folder",
>    "name": "Notes Folder"
>}
>```

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

>Example 28
>
>```json
>{
>  "summary": "The moderator removed Sally from a group",
>    "name": "The Moderator"
>    "name": "A Simple Group"
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

#### [Class] Undo

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Undo`
Notes: | Indicates that the `actor` is undoing the `object`. In most cases, the `object` will be an Activity describing some previously performed action (for instance, a person may have previously "liked" an article but, for whatever reason, might choose to undo that like at some later point in time). </br> The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Undo`
비고: | `actor`가 `object`를 실행취소(undoing)하고 있음을 나타냅니다. 대부분의 경우, `object`는 이전에 수행된 일부 작업을 설명하는 액티비티입니다 (예를 들어, 어떤 사람이 특정 기사를 "좋아했을수도(liked)" 있지만, 어떠한 이유에서인지 차후에 그 행동을 실행취소 할 수도 있습니다). </br> 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 29
>
>```json
>{
>  "summary": "Sally retracted her offer to John",
>}
>```

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

#### [Class] Update

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Update`
Notes: | Indicates that the `actor` has updated the `object`. Note, however, that this vocabulary does not define a mechanism for describing the actual set of modifications made to `object`. </br> The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Update`
비고: | `actor`가 `object`를 업데이트(updated) 했음을 나타냅니다. 그러나 이 어휘에서는 `object`에 대한 수정 방법들을 설명하기 위한 메커니즘을 정의하지 않습니다. </br> 이 클래스의 경우, `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 30
>
>```json
>{
>  "summary": "Sally updated her note",
>}
>```

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

[//Comment]: # "'Sally는 그녀의 노트를 새로 갱신했습니다'로도 번역이 가능하나, '갱신'이라는 단어를 적어도 Chapter3 번역본에서는 적어도 아직까지는 사용하지 않았기 때문에 일관성을 위해 '업데이트'로 적었습니다."

#### [Class] View

Description| |
--|--
URI: |` https://www.w3.org/ns/activitystreams#View`
Notes: | Indicates that the `actor` has viewed the object.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#View`
비고: | `actor`가 객체를 보았음(viewed)을 나타냅니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

[//Comment]: # "원문에서도 object가 <code></code>로 둘러싸이지 않았으므로 `백틱`으로 둘러싸지 않았습니다"

>Example 31
>
>```json
>{
>  "summary": "Sally read an article",
>    "name": "What You Should Know About Activity Streams"
>}
>```

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

#### [Class] Listen

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Listen`
Notes: | Indicates that the `actor` has listened to the `object`.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Listen`
비고: | `actor`가 `object`를 청취했음(listened)을 나타냅니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 32
>
>```json
>{
>  "summary": "Sally listened to a piece of music",
>}
>```

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

#### [Class] Read

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Read`
Notes: | Indicates that the `actor` has read the `object`.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Read`
비고: | `actor`가 `object`를 읽었음(read)을 나타냅니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 33
>
>```json
>{
>  "summary": "Sally read a blog post",
>}

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

#### [Class] Move

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Move`
Notes: | Indicates that the `actor` has moved `object` from `origin` to `target`. If the `origin` or `target` are not specified, either can be determined by context.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Move`
비고: | `actor`가 `object`를 `origin`에서 `target`으로 옮겼음(moved)을 나타냅니다. `origin`이나 `target`이 지정되지 않았을 경우, 이들의 값은 컨텍스트에 따라 결정될 수 있습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 34
>
>```json
>{
>  "summary": "Sally moved a post from List A to List B",
>    "name": "List B"
>    "name": "List A"
>}
>```

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

#### [Class] Travel

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Travel`
Notes: | Indicates that the `actor` is traveling to `target` from `origin`. `Travel` is an `IntransitiveObject` whose `actor` specifies the direct object. If the `target` or `origin` are not specified, either can be determined by context.
Extends: | IntransitiveActivity
Properties: | Inherits all properties from IntransitiveActivity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Travel`
비고: | `actor`가 `object`를 `origin`에서 `target`으로 이동중(traveling)임을 나타냅니다. `Travel`은 `actor`가 직접적인 객체(direct object)를 지정하는 `IntransitiveObject` 입니다. `origin`이나 `target`이 지정되지 않았을 경우, 이들의 값은 컨텍스트에 따라 결정될 수 있습니다.
상속함: | IntransitiveActivity
속성: | IntransitiveActivity로부터 모든 속성을 상속받습니다.

>Example 35
>
>```json
>{
>  "summary": "Sally went home from work",
>    "name": "Home"
>    "name": "Work"
>}
>```

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

#### [Class] Announce

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Announce`
Notes: | Indicates that the `actor` is calling the `target`'s attention the `object`. </br> The `origin` typically has no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Announce`
비고: | `actor`가 `target`의 주의를 `object`에 두고 있음을 나타냅니다. </br> 이 클래스의 경우, `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

[//TODO]: # "번역이 올바른건지 확실하지 않습니다. '`actor`가 `target`의 관심을 `object`이라고 부르고 있음을 나타냅니다.' 같은 번역도 가능할 수도 있기는 합니다."

>Example 36
>
>```json
>{
>  "summary": "Sally announced that she had arrived at work",
>    "name": "Work"
>}
>```

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

#### [Class] Block

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Block`
Notes: | Indicates that the `actor` is blocking the `object`. Blocking is a stronger form of Ignore. The typical use is to support social systems that allow one user to block activities or content of other users. The `target` and `origin` typically have no defined meaning.
Extends: | Ignore
Properties: | Inherits all properties from Ignore.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Block`
비고: | `actor`가 `object`를 차단중(blocking)임을 나타냅니다. 차단(Blocking)은 더 강력한 형태의 무시(Ignore)입니다. 이 클래스의 일반적인 용도는, 소셜 시스템에서 한 사용자가 다른 사용자의 액티비티나 콘텐츠를 차단할 수 있는 방법을 지원하는 것입니다. `target`과 `origin`은 일반적으로 정의된 의미가 없습니다.
상속함: | Ignore
속성: | Ignore로부터 모든 속성을 상속받습니다.

>Example 37
>
>```json
>{
>  "summary": "Sally blocked Joe",
>}
>```

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

#### [Class] Flag

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Flag`
Notes: | Indicates that the `actor` is "flagging" the `object`. Flagging is defined in the sense common to many social platforms as reporting content as being inappropriate for any number of reasons.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Flag`
비고: | `actor`가 `object`를 "신고(flagging)" 하고 있음을 나타냅니다. 신고는 일반적으로 여러 소셜 플랫폼에서 콘텐츠를 여러가지 이유로 부적절하다고 보고하는 것 으로 정의됩니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

[//Comment]: # "'flagging'을 '신고'로 번역하였습니다"

>Example 38
>
>```json
>{
>  "summary": "Sally flagged an inappropriate note",
>
>    "content": "An inappropriate note"
>}
>```

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

#### [Class] Dislike

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Dislike`
Notes: | Indicates that the `actor` dislikes the `object`.
Extends: | Activity
Properties: | Inherits all properties from Activity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Dislike`
비고: | `actor`가 `object`를 싫어함(dislikes)을 나타냅니다.
상속함: | Activity
속성: | Activity로부터 모든 속성을 상속받습니다.

>Example 39
>
>```json
>{
>  "summary": "Sally disliked a post",
>}
>```

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

[//Comment]: # "dislike가 '싫어함'으로 사용되는 예시는 Chapter5에서 다룹니다"

#### [Class] Question

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Question`
Notes: | Represents a question being asked. Question objects are an extension of IntransitiveActivity. That is, the Question object is an Activity, but the direct object is the question itself and therefore it would not contain an object property. </br> Either of the anyOf and oneOf properties *MAY* be used to express possible answers, but a Question object *MUST NOT* have both properties.
Extends: | IntransitiveActivity.
Properties: | oneOf | anyOf | closed </br> Inherits all properties from IntransitiveActivity.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Question`
비고: | 묻는 질문(question)을 나타냅니다. Question 객체들은 IntransitiveActivity의 확장입니다. 즉 Question 객체는 Activity지만 직접적인 객체(direct object)는 질문 그 자체이므로 객체 속성을 포함하지 않습니다. </br> anyOf 또는 oneOf 속성중 하나를 사용하여 가능한 답변을 표현 *할 수도* 있지만, Question 객체에는 두 객체 모두 보유하는것을 *절대로 하지 말아야* 합니다.
상속함: | IntransitiveActivity
속성: | oneOf | anyOf | closed </br> IntransitiveActivity로부터 모든 속성을 상속받습니다.

>Example 40
>
>```json
>{
>  "name": "What is the answer?",
>    "name": "Option A"
>    "name": "Option B"
>}
>```

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

>Example 41
>
>```json
>{
>  "name": "What is the answer?",
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

### 3.2 액터 타입 (Actor Types)

Actor types are [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) types that are capable of performing activities.

액터 타입은 액티비티를 수행할 수 있는 [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) 타입입니다.

The core Actor Types include:

핵심 액터 타입은 다음과 같은 타입들을 포함합니다:

- [Application](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-application)
- [Group](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-group)
- [Organization](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-organization)
- [Person](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-person)
- [Service](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-service)

#### [Class] Application

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Application`
Notes: | Describes a software application.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Application`
비고: | 소프트웨어 어플리케이션(application)을 표현합니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 42
>
>```json
>{
>  "name": "Exampletron 3000"
>}
>```

>예시 42
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Application",
>  "name": "예시제조기 3000"
>}
>```

[//Comment]: # "새로운 아이디어는 언제나 환영합니다"

#### [Class] Group

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Group`
Notes: | Represents a formal or informal collective of Actors.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Group`
비고: | 액터들의 공식 또는 비공식 집단을 나타냅니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 43
>
>```json
>{
>  "name": "Big Beards of Austin"
>}
>```

>예시 43
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Group",
>  "name": "Austin의 큰수염"
>}
>```

#### [Class] Organization

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Organization`
Notes: | Represents an organization.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Organization`
비고: | 조직(organization)을 나타냅니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 44
>
>```json
>{
>  "name": "Example Co."
>}
>```

>예시 44
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Organization",
>  "name": "예시 (주)"
>}
>```

#### [Class] Person

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Person`
Notes: | Represents an individual person.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Person`
비고: | 독립적인 사람(person)을 나타냅니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 45

>예시 45
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Person",
>  "name": "Sally Smith"
>}
>```

#### [Class] Service

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Service`
Notes: | Represents a service of any kind.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Service`
비고: | 모든 종류의 서비스(service)를 나타냅니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 46
>
>```json
>{
>  "name": "Acme Web Service"
>}
>```

>예시 46
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Service",
>  "name": "최상의 웹 서비스"
>}
>```

### 3.3 객체와 링크 타입 (Object and Link Types)

All Object Types inherit the properties of the base [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) type. Link Types inherit the properties of the base [Link](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-link) type. Some specific Object Types are subtypes or specializations of more generalized Object Types (for instance, the [Like](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like) Type is a more specific form of the [Activity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity) type).

모든 객체 타입들은 기본 [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) 타입을 상속합니다. 링크 타입들은 기본 [Link](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-link) 타입을 상속합니다. 일부 특정한 객체 타입들은 일반화된 객체 타입의 하위 타입이나 특수화된 경우입니다. (예를 들어, [Like](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like) 유형은 [Activity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity) 유형보다 구체적인 경우입니다).

The Object Types include:

객체 타입은 다음과 같은 타입들을 포함합니다:

- [Article](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-article)
- [Audio](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-audio)
- [Document](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-document)
- [Event](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-event)
- [Image](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-image)
- [Note](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-note)
- [Page](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-page)
- [Place](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-place)
- [Profile](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-profile)
- [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship)
- [Tombstone](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tombstone)
- [Video](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-video)

The Link Types include:

링크 타입은 다음과 같은 타입들을 포함합니다:

- [Mention](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-mention)

#### [Class] Relationship

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Relationship`
Notes: | Describes a relationship between two individuals. The subject and object properties are used to identify the connected individuals.</br> See 5.2 Representing Relationships Between Entities for additional information.
Extends: | Object
Properties: | subject \| object \| relationship </br> Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Relationship`
비고: | 두 개개인 사이의 관계(relationship)을 나타냅니다. 주제 및 객체 속성은 연결된 개인을 식별하는데 사용됩니다. </br> 추가적인 정보는 5.2 엔티티 간의 관계 표현 을 참고하시길 바랍니다.
상속함: | Object
속성: | subject \| object \| relationship </br> Object로부터 모든 속성을 상속받습니다.

>Example 47
>
>```json
>{
>  "summary": "Sally is an acquaintance of John",
>}
>```

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

#### [Class] Article

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Article`
Notes: | Represents any kind of multi-paragraph written work.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Article`
비고: | 모든 종류의 다중-문단으로 쓰여진 작업을 나타냅니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 48
>
>```json
>{
>  "name": "What a Crazy Day I Had",
>  "content": "<div>... you will never believe ...</div>",
>}
>```

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

#### [Class] Document

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Document`
Notes: | Represents a document of any kind.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Document`
비고: | 모든 종류의 문서(document)를 나타냅니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 49
>
>```json
>{
>  "name": "4Q Sales Forecast",
>}
>```

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

#### [Class] Audio

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Audio`
Notes: | Represents an audio document of any kind.
Extends: | Document
Properties: | Inherits all properties from Document.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Audio`
비고: | 모든 종류의 청각(audio) 문서를 나타냅니다.
상속함: | Document
속성: | Document로부터 모든 속성을 상속받습니다.

>Example 50
>
>```json
>{
>  "name": "Interview With A Famous Technologist",
>}
>```

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

#### [Class] Image

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Image`
Notes: | An image document of any kind
Extends: | Document
Properties: | Inherits all properties from Document.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Image`
비고: | 모든 종류의 시각(image) 문서를 나타냅니다.
상속함: | Document
속성: | Document로부터 모든 속성을 상속받습니다.

>Example 51
>
>```json
>{
>  "name": "Cat Jumping on Wagon",
>}
>```

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

[//Comment]: # "의역"

#### [Class] Video

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Video`
Notes: | Represents a video document of any kind.
Extends: | Document
Properties: | Inherits all properties from Document.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Video`
비고: | 모든 종류의 영상(video) 문서를 나타냅니다.
상속함: | Document
속성: | Document로부터 모든 속성을 상속받습니다.

>Example 52
>
>```json
>{
>  "name": "Puppy Plays With Ball",
>}
>```

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

#### [Class] Note

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Note`
Notes: | Represents a short written work typically less than a single paragraph in length.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Note`
비고: | 일반적으로 한 문단 이하로 짧게 쓰여진 작업을 나타냅니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 53
>
>```json
>{
>  "name": "A Word of Warning",
>  "content": "Looks like it is going to rain today. Bring an umbrella!"
>}
>```

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

#### [Class] Page

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Page`
Notes: | Represents a Web Page.
Extends: | Document
Properties: | Inherits all properties from Document.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Page`
비고: | 웹 페이지(Page)를 나타냅니다.
상속함: | Document
속성: | Document로부터 모든 속성을 상속받습니다.

>Example 54
>
>```json
>{
>  "name": "Omaha Weather Report",
>}
>```

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

#### [Class] Event

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Event`
Notes: | Represents any kind of event.
Extends: | Object
Properties: | Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Event`
비고: | 모든 종류의 이벤트(event)를 나타냅니다.
상속함: | Object
속성: | Object로부터 모든 속성을 상속받습니다.

>Example 55
>
>```json
>{
>  "name": "Going-Away Party for Jim",
>}
>```

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

#### [Class] Place

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Place`
Notes: | Represents a logical or physical location. See 5.3 Representing Places for additional information.
Extends: | Object
Properties: | accuracy \| altitude \| latitude \| longitude \| radius \| units </br> Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Place`
비고: | 논리적 또는 물리적 위치를 나타냅니다. 추가적인 정보는 5.3 장소 표시 를 참고하시길 바랍니다.
상속함: | Object
속성: | accuracy \| altitude \| latitude \| longitude \| radius \| units </br> Object로부터 모든 속성을 상속받습니다.

>Example 56
>
>```json
>{
>  "name": "Work"
>}
>```

>예시 56
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "직장"
>}
>```

>Example 57
>
>```json
>{
>  "name": "Fresno Area",
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

#### [Class] Mention

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Mention`
Notes: | A specialized Link that represents an @mention.
Extends: | Link
Properties: | Inherits all properties from Link.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Mention`
비고: | @mention을 나타내는 특수한 링크입니다.
상속함: | Link
속성: | Link로부터 모든 속성을 상속받습니다.

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

#### [Class] Profile

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Profile`
Notes: | A Profile is a content object that describes another Object, typically used to describe Actor Type objects. The describes property is used to reference the object being described by the profile.
Extends: | Object
Properties: | describes </br> Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Profile`
비고: | 프로필(Profile)은 일반적으로 액터 타입 객체를 설명하는데 사용되는, 다른 객체를 설명하는 컨텐츠 객체입니다. describes 속성은 프로필에서 설명하는 객체를 참조하는데 사용됩니다.
상속함: | Object
속성: | describes </br> Object로부터 모든 속성을 상속받습니다.

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

#### [Class] Tombstone

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Tombstone`
Notes: | A Tombstone represents a content object that has been deleted. It can be used in Collections to signify that there used to be an object at this position, but it has been deleted.
Extends: | Object
Properties: | 
formerType | deleted </br> Inherits all properties from Object.

설명| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Tombstone`
비고: | 묘지(Tombstone)는 삭제된 컨텐츠 객체를 나타냅니다. Collections에서 이 위치에 객체가 있었지만, 지금은 삭제된 것을 나타내기 위해 사용할 수 있습니다.
상속함: | Object
속성: | 
이전타입 | deleted </br> Object로부터 모든 속성을 상속받습니다.

>Example 60
>
>```json
>{
>  "name": "Vacation photos 2016",
>}
>```

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
