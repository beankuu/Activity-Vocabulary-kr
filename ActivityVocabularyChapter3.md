[목차로 돌아가기](ActivityVocabularyContents.md)

## 3. Extended Types

Base URI: `https://www.w3.org/ns/activitystreams#`.

The Activity Streams 2.0 Extended Types include Activity and Object subtypes that are common to many social Web applications. They are divided into three sets:

- [Activity Types](https://www.w3.org/TR/activitystreams-vocabulary/#activity-types)
- [Actor Types](https://www.w3.org/TR/activitystreams-vocabulary/#actor-types)
- [Object Types](https://www.w3.org/TR/activitystreams-vocabulary/#object-types)

Support for specific extended vocabulary types is expected to vary, with implementations only selecting the extended types and properties that make sense within the specific context and requirements of those applications. However, to avoid possible interoperability issues, implementations *MUST* avoid using extension types or properties that unduly overlap with or duplicate the extended vocabulary defined here.

### 3.1 Activity Types

All Activity Types inherit the properties of the base [Activity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity) type. Some specific Activity Types are subtypes or specializations of more generalized Activity Types (for instance, the [Invite](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-invite) Activity Type is a more specific form of the [Offer](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer) Activity Type).

The Activity Types include:

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


**[Class] Accept**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Accept`
Notes: | Indicates that the `actor` accepts the `object`. The `target` property can be used in certain circumstances to indicate the context into which the `object` has been accepted.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 9
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally accepted an invitation to a party",
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
>      "name": "Going-Away Party for Jim"
>    }
>  }
>}
>```
>
>Example 10
>
>```json
>{
>    "@context": "https://www.w3.org/ns/activitystreams",
>    "summary": "Sally accepted Joe into the club",
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
>      "name": "The Club"
>    }
>}
>```

**[Class] TentativeAccept**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeAccept`
Notes: | A specialization of Accept indicating that the acceptance is tentative.
Extends: | Accept
Properties: | Inherits all properties from Accept.

>Example 11
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally tentatively accepted an invitation to a party",
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
>      "name": "Going-Away Party for Jim"
>    }
>  }
>}
>```


**[Class] Add**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Add`
Notes: | Indicates that the `actor` has added the `object` to the `target`. If the `target` property is not explicitly specified, the target would need to be determined implicitly by context. The `origin` can be used to identify the context from which the `object` originated.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 12
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally added an object",
>  "type": "Add",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/abc"
>}
>```
>
>Example 13
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally added a picture of her cat to her cat picture collection",
>  "type": "Add",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Image",
>    "name": "A picture of my cat",
>    "url": "http://example.org/img/cat.png"
>  },
>  "origin": {
>    "type": "Collection",
>    "name": "Camera Roll"
>  },
>  "target": {
>    "type": "Collection",
>    "name": "My Cat Pictures"
>  }
>}
>```


**[Class] Arrive**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Arrive`
Notes: | An IntransitiveActivity that indicates that the `actor` has arrived at the `location`. The `origin` can be used to identify the context from which the `actor` originated. The `target` typically has no defined meaning.
Extends: | IntransitiveActivity
Properties: | Inherits all properties fom IntransitiveActivity.

>Example 14
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally arrived at work",
>  "type": "Arrive",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "location": {
>    "type": "Place",
>    "name": "Work"
>  },
>  "origin": {
>    "type": "Place",
>    "name": "Home"
>  }
>}
>```

**[Class] Create**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Create`
Notes: | Indicates that the `actor` has created the `object`.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 15
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally created a note",
>  "type": "Create",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Note",
>    "name": "A Simple Note",
>    "content": "This is a simple note"
>  }
>}
>```

**[Class] Delete**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Delete`
Notes: | Indicates that the `actor` has deleted the `object`. If specified, the `origin` indicates the context from which the `object` was deleted.
Extends: | Activity
Properties: | Inherits all properties from Activity.


>Example 16
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally deleted a note",
>  "type": "Delete",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1",
>  "origin": {
>    "type": "Collection",
>    "name": "Sally's Notes"
>  }
>}
>```

**[Class] Follow**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Follow`
Notes: |  Indicates that the `actor` is "following" the `object`. Following is defined in the sense typically used within Social systems in which the actor is interested in any activity performed by or on the object. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 17
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally followed John",
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

**[Class] Ignore**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Ignore`
Notes: | Indicates that the `actor` is ignoring the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 18
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally ignored a note",
>  "type": "Ignore",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1"
>}
>```


**[Class] Join**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Join`
Notes: | Indicates that the `actor` has joined the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 19
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally joined a group",
>  "type": "Join",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Group",
>    "name": "A Simple Group"
>  }
>}
>```

**[Class] Leave**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Leave`
Notes: | Indicates that the `actor` has left the `object`. The `target` and `origin` typically have no meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 20
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally left work",
>  "type": "Leave",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Place",
>    "name": "Work"
>  }
>}
>```

>Example 21
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally left a group",
>  "type": "Leave",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Group",
>    "name": "A Simple Group"
>  }
>}
>```

**[Class] Like**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Like`
Notes: | Indicates that the `actor` likes, recommends or endorses the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 22
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally liked a note",
>  "type": "Like",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1"
>}
>```

**[Class] Offer**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Offer`
Notes: | Indicates that the `actor` is offering the `object`. If specified, the `target` indicates the entity to which the `object` is being offered.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 23
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered 50% off to Lewis",
>  "type": "Offer",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "http://www.types.example/ProductOffer",
>    "name": "50% Off!"
>  },
>  "target": {
>    "type": "Person",
>    "name": "Lewis"
>  }
>}
>```


**[Class] Invite**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Invite`
Notes: | A specialization of Offer in which the `actor` is extending an invitation for the `object` to the `target`.
Extends: | Offer
Properties: | Inherits all properties from Offer.

>Example 24
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally invited John and Lisa to a party",
>  "type": "Invite",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Event",
>    "name": "A Party"
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

**[Class] Reject**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Reject`
Notes: | Indicates that the `actor` is rejecting the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 25
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally rejected an invitation to a party",
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
>      "name": "Going-Away Party for Jim"
>    }
>  }
>}
>```

**[Class] TentativeReject**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeReject`
Notes: | A specialization of Reject in which the rejection is considered tentative.
Extends: | Reject
Properties: | Inherits all properties from Reject.

>Example 26
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally tentatively rejected an invitation to a party",
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
>      "name": "Going-Away Party for Jim"
>    }
>  }
>}
>```

**[Class] Remove**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Remove`
Notes: | Indicates that the `actor` is removing the `object`. If specified, the `origin` indicates the context from which the `object` is being removed.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 27
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally removed a note from her notes folder",
>  "type": "Remove",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1",
>  "target": {
>    "type": "Collection",
>    "name": "Notes Folder"
>  }
>}
>```

>Example 28
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "The moderator removed Sally from a group",
>  "type": "Remove",
>  "actor": {
>    "type": "http://example.org/Role",
>    "name": "The Moderator"
>  },
>  "object": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "origin": {
>    "type": "Group",
>    "name": "A Simple Group"
>  }
>}
>```

**[Class] Undo**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Undo`
Notes: | Indicates that the `actor` is undoing the `object`. In most cases, the `object` will be an Activity describing some previously performed action (for instance, a person may have previously "liked" an article but, for whatever reason, might choose to undo that like at some later point in time). </br></br> The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 29
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally retracted her offer to John",
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

**[Class] Update**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Update`
Notes: | Indicates that the `actor` has updated the `object`. Note, however, that this vocabulary does not define a mechanism for describing the actual set of modifications made to `object`. </br></br> The `target` and `origin` typically have no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 30
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally updated her note",
>  "type": "Update",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/notes/1"
>}
>```

**[Class] View**

Description| |
--|--
URI: |` https://www.w3.org/ns/activitystreams#View`
Notes: | Indicates that the `actor` has viewed the object.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 31
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally read an article",
>  "type": "View",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Article",
>    "name": "What You Should Know About Activity Streams"
>  }
>}
>```


**[Class] Listen**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Listen`
Notes: | Indicates that the `actor` has listened to the `object`.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 32
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally listened to a piece of music",
>  "type": "Listen",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/music.mp3"
>}
>```

**[Class] Read**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Read`
Notes: | Indicates that the `actor` has read the `object`.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 33
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally read a blog post",
>  "type": "Read",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/posts/1"
>}
>```

**[Class] Move**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Move`
Notes: | Indicates that the `actor` has moved `object` from `origin` to `target`. If the `origin` or `target` are not specified, either can be determined by context.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 34
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally moved a post from List A to List B",
>  "type": "Move",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/posts/1",
>  "target": {
>    "type": "Collection",
>    "name": "List B"
>  },
>  "origin": {
>    "type": "Collection",
>    "name": "List A"
>  }
>}
>```

**[Class] Travel**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Travel`
Notes: | Indicates that the `actor` is traveling to `target` from `origin`. `Travel` is an `IntransitiveObject` whose `actor` specifies the direct object. If the `target` or `origin` are not specified, either can be determined by context.
Extends: | IntransitiveActivity
Properties: | Inherits all properties from IntransitiveActivity.

>Example 35
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally went home from work",
>  "type": "Travel",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "target": {
>    "type": "Place",
>    "name": "Home"
>  },
>  "origin": {
>    "type": "Place",
>    "name": "Work"
>  }
>}
>```

**[Class] Announce**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Announce`
Notes: | Indicates that the `actor` is calling the `target`'s attention the `object`. </br></br> The `origin` typically has no defined meaning.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 36
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally announced that she had arrived at work",
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
>      "name": "Work"
>    }
>  }
>}
>```

**[Class] Block**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Block`
Notes: | Indicates that the `actor` is blocking the `object`. Blocking is a stronger form of Ignore. The typical use is to support social systems that allow one user to block activities or content of other users. The `target` and `origin` typically have no defined meaning.
Extends: | Ignore
Properties: | Inherits all properties from Ignore.

>Example 37
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally blocked Joe",
>  "type": "Block",
>  "actor": "http://sally.example.org",
>  "object": "http://joe.example.org"
>}
>```

**[Class] Flag**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Flag`
Notes: | Indicates that the `actor` is "flagging" the `object`. Flagging is defined in the sense common to many social platforms as reporting content as being inappropriate for any number of reasons.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 38
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally flagged an inappropriate note",
>  "type": "Flag",
>  "actor": "http://sally.example.org",
>  "object": {
>    "type": "Note",
>    "content": "An inappropriate note"
>  }
>}
>```

**[Class] Dislike**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Dislike`
Notes: | Indicates that the `actor` dislikes the `object`.
Extends: | Activity
Properties: | Inherits all properties from Activity.

>Example 39
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally disliked a post",
>  "type": "Dislike",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1"
>}
>```

**[Class] Question**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Question`
Notes: | Represents a question being asked. Question objects are an extension of IntransitiveActivity. That is, the Question object is an Activity, but the direct object is the question itself and therefore it would not contain an object property. </br></br> Either of the anyOf and oneOf properties *MAY* be used to express possible answers, but a Question object *MUST NOT* have both properties.
Extends: | IntransitiveActivity.
Properties: | oneOf | anyOf | closed
Inherits all properties from IntransitiveActivity. 

>Example 40
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "What is the answer?",
>  "oneOf": [
>    {
>      "type": "Note",
>      "name": "Option A"
>    },
>    {
>      "type": "Note",
>      "name": "Option B"
>    }
>  ]
>}
>```

>Example 41
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "What is the answer?",
>  "closed": "2016-05-10T00:00:00Z"
>}
>```

### 3.2 Actor Types

Actor types are [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) types that are capable of performing activities.

The core Actor Types include:

- [Application](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-application)
- [Group](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-group)
- [Organization](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-organization)
- [Person](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-person)
- [Service](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-service)


**[Class] Application**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Application`
Notes: | Describes a software application.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 42
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Application",
>  "name": "Exampletron 3000"
>}
>```

**[Class] Group**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Group`
Notes: | Represents a formal or informal collective of Actors.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 43
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Group",
>  "name": "Big Beards of Austin"
>}
>```

**[Class] Organization**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Organization`
Notes: | Represents an organization.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 44
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Organization",
>  "name": "Example Co."
>}
>```

**[Class] Person**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Person`
Notes: | Represents an individual person.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 45
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Person",
>  "name": "Sally Smith"
>}
>```

**[Class] Service**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Service`
Notes: | Represents a service of any kind.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 46
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Service",
>  "name": "Acme Web Service"
>}
>```

### 3.3 Object and Link Types

All Object Types inherit the properties of the base [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) type. Link Types inherit the properties of the base [Link](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-link) type. Some specific Object Types are subtypes or specializations of more generalized Object Types (for instance, the [Like](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like) Type is a more specific form of the [Activity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity) type).

The Object Types include:

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

- [Mention](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-mention)

**[Class] Relationship**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Relationship`
Notes: | Describes a relationship between two individuals. The subject and object properties are used to identify the connected individuals.</br></br> See 5.2 Representing Relationships Between Entities for additional information.
Extends: | Object
Properties: | subject \| object \| relationship </br></br> Inherits all properties from Object.

>Example 47
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally is an acquaintance of John",
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

**[Class] Article**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Article`
Notes: | Represents any kind of multi-paragraph written work.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 48
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Article",
>  "name": "What a Crazy Day I Had",
>  "content": "<div>... you will never believe ...</div>",
>  "attributedTo": "http://sally.example.org"
>}
>```

**[Class] Document**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Document`
Notes: | Represents a document of any kind.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 49
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Document",
>  "name": "4Q Sales Forecast",
>  "url": "http://example.org/4q-sales-forecast.pdf"
>}
>```

**[Class] Audio**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Audio`
Notes: | Represents an audio document of any kind.
Extends: | Document
Properties: | Inherits all properties from Document.

>Example 50
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Audio",
>  "name": "Interview With A Famous Technologist",
>  "url": {
>    "type": "Link",
>    "href": "http://example.org/podcast.mp3",
>    "mediaType": "audio/mp3"
>  }
>}
>```

**[Class] Image**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Image`
Notes: | An image document of any kind
Extends: | Document
Properties: | Inherits all properties from Document.

>Example 51
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Image",
>  "name": "Cat Jumping on Wagon",
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

**[Class] Video**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Video`
Notes: | Represents a video document of any kind.
Extends: | Document
Properties: | Inherits all properties from Document.

>Example 52
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Video",
>  "name": "Puppy Plays With Ball",
>  "url": "http://example.org/video.mkv",
>  "duration": "PT2H"
>}
>```

**[Class] Note**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Note`
Notes: | Represents a short written work typically less than a single paragraph in length.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 53
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Note",
>  "name": "A Word of Warning",
>  "content": "Looks like it is going to rain today. Bring an umbrella!"
>}
>```

**[Class] Page**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Page`
Notes: | Represents a Web Page.
Extends: | Document
Properties: | Inherits all properties from Document.

>Example 54
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Page",
>  "name": "Omaha Weather Report",
>  "url": "http://example.org/weather-in-omaha.html"
>}
>```

**[Class] Event**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Event`
Notes: | Represents any kind of event.
Extends: | Object
Properties: | Inherits all properties from Object.

>Example 55
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Event",
>  "name": "Going-Away Party for Jim",
>  "startTime": "2014-12-31T23:00:00-08:00",
>  "endTime": "2015-01-01T06:00:00-08:00"
>}
>```

**[Class] Place**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Place`
Notes: | Represents a logical or physical location. See 5.3 Representing Places for additional information.
Extends: | Object
Properties: | accuracy \| altitude \| latitude \| longitude \| radius \| units </br></br> Inherits all properties from Object.

>Example 56
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Work"
>}
>```

>Example 57
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Fresno Area",
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "radius": 15,
>  "units": "miles"
>}
>```

**[Class] Mention**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Mention`
Notes: | A specialized Link that represents an @mention.
Extends: | Link
Properties: | Inherits all properties from Link.

>Example 58
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Mention of Joe by Carrie in her note",
>  "type": "Mention",
>  "href": "http://example.org/joe",
>  "name": "Joe"
>}
>```

**[Class] Profile**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Profile`
Notes: | A Profile is a content object that describes another Object, typically used to describe Actor Type objects. The describes property is used to reference the object being described by the profile.
Extends: | Object
Properties: | describes </br></br> Inherits all properties from Object.

>Example 59
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Profile",
>  "summary": "Sally's Profile",
>  "describes": {
>    "type": "Person",
>    "name": "Sally Smith"
>  }
>}
>```

**[Class] Tombstone**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Tombstone`
Notes: | A Tombstone represents a content object that has been deleted. It can be used in Collections to signify that there used to be an object at this position, but it has been deleted.
Extends: | Object
Properties: | 
formerType | deleted </br></br> Inherits all properties from Object.

>Example 60
>
>```json
>{
>  "type": "OrderedCollection",
>  "totalItems": 3,
>  "name": "Vacation photos 2016",
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
