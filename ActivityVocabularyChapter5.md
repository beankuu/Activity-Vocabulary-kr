[목차로 돌아가기](ActivityVocabularyContents.md)

## 5. Implementation Notes

### 5.1 Audience Targeting

Conceptually, every Object has both a Primary and Secondary audience. The Primary audience consists of those entities directly involved or owning the object. The Secondary audience consists of the collection of entities sharing an interest in the object but who might not be directly involved (e.g."followers").

For instance, suppose a social network of three individuals: Bob, Joe and Jane. Bob and Joe are each friends with Jane but are not friends with one another. Bob has chosen to "follow" activities for which Jane is directly involved. Jane shares a file with Joe.

In this example, Jane and Joe are each directly involved in the file sharing activity and together make up the Primary Audience for that event. Bob, having an interest in activities involving Jane, is the Secondary Audience. Knowing this, a system that produces or consumes the activity can intelligently notify each person of the event.

While there are means (based on the action type, actor, object and target of the activity) to infer the primary audience for many types of activities, heuristics do not work in every case and do not provide a means of identifying the secondary audience. The [to](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-to), [cc](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-cc), [bto](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-bto) and [bcc](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-bcc) properties *MAY* be used within an Object to explicitly identify the Primary and Secondary audiences.

The prototypical use case for an Object containing these properties is the publication and redistribution of objects through an intermediary. That is, an event source generates the object and publishes it to the intermediary which determines a subset of items to display to specific individual users or groups. Such a determination can be made, in part, by identifying the Primary and Secondary Audiences for each object.

When the event source generates the object and specifies values for the `to` and `cc` fields, the intermediary *SHOULD* redistribute that object with the values of those fields intact, allowing any processor to see who the object has been targeted to. This is precisely the same model used by the `to` and `cc` fields in email systems.

There are situations, however, in which disclosing the identity of specific members of the audience may be inappropriate. For instance, a user may not wish to let other users know that they are interested in various topics, individuals or types of events. To support this option, an implementation generating an object *MAY* use the `bto` and `bcc` properties to list entities to whom the object should be privately targeted. When an intermediary receives an object containing these properties, it *MUST* remove those values prior to redistributing the object. The intent is that systems *MUST* consider entities listed within the `bto` and `bcc` properties as part of the Primary and Secondary audience but *MUST NOT* disclose that fact to any other party.

Audience targeting information included within an Object only describes the intent of the object creator. With clear exception given to the appropriate handling of `bto` and `bcc`, this specification leaves it up to implementations to determine how the audience targeting information is used.

#### 5.1.1 Audience and Context

_This section is non-normative._

Activities are rarely isolated events. Often, multiple individual activities will be performed around a similar context or audience. For instance, a collaborators working on a shared project might perform multiple related activities in the process of achieving some goal. Such activities can be logically grouped together using the [context](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-context) property, and scoped to a particular audience using the [audience](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-audience) property.

For instance, the following shows two related activities that share a common `context` and `audience`:

>Example 144
>
>```json
>{
> "@context": "https://www.w3.org/ns/activitystreams",
> "summary": "Activities in Project XYZ",
> "type": "Collection",
> "items": [
>   {
>     "summary": "Sally created a note",
>     "type": "Create",
>     "id": "http://activities.example.com/1",
>     "actor": "http://sally.example.org",
>     "object": {
>      "summary": "A note",
>       "type": "Note",
>       "id": "http://notes.example.com/1",
>       "content": "A note"
>     },
>     "context": {
>       "type": "http://example.org/Project",
>       "name": "Project XYZ"
>     },
>     "audience": {
>       "type": "Group",
>       "name": "Project XYZ Working Group"
>     },
>     "to": "http://john.example.org"
>   },
>   {
>     "summary": "John liked Sally's note",
>     "type": "Like",
>     "id": "http://activities.example.com/1",
>     "actor": "http://john.example.org",
>     "object": "http://notes.example.com/1",
>     "context": {
>       "type": "http://example.org/Project",
>       "name": "Project XYZ"
>     },
>     "audience": {
>       "type": "Group",
>       "name": "Project XYZ Working Group"
>     },
>     "to": "http://sally.example.org"
>   }
> ]
>}
>```

### 5.2 Representing Relationships Between Entities

The [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) object is used to represent relationships between individuals. It can be used, for instance, to describe that one person is a friend of another, or that one person is a member of a particular organization. The intent of modeling Relationship in this way is to allow descriptions of activities that operate on the relationships in general, and to allow representation of Collections of relationships.

For instance, many social systems have a notion of a "friends list". These are the collection of individuals that are directly connected within a person's social graph. Suppose we have a user, Sally, with direct relationships to users Joe and Jane. Sally follows Joe's updates while Sally and Jane have a mutual relationship.

Using the [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) object, we can model these relationships as:

>Example 145
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally's friends list",
>  "type": "Collection",
>  "items": [
>    {
>      "summary": "Sally is influenced by Joe",
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
>      "summary": "Sally is a friend of Jane",
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

While use of reified statements can be problematic and confusing in certain situations, their use within the Activity Streams vocabulary to describe relationships provides a straightforward mechanism of describing changes to an individual's social graph. For instance, to indicate that Sally has created a new relationship to user Matt, an implementer can use the [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) object together with the [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create) activity:

>Example 146
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally became a friend of Matt",
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

Implementations may reuse existing vocabularies that have been developed for the purpose of describing relationships, or create their own guided by requirements of their particular implementation. Existing vocabularies include the " [Friend of a Friend](http://xmlns.com/foaf/spec/)" and " [Relationship](http://vocab.org/relationship/)" vocabularies.

#### 5.2.1 Modeling "friend requests"

_This section is non-normative._

One common use case for many social platforms is the establishment of symmetrical "friend" relationships, in which one user initially extends a request to another user to establish a new connection. Once the connection is made, both users automatically begin receiving notifications about activities performed by the other, and the established relationship becomes visible in either user's "friends list".

The initial "friend request" can be modeled by composing the [Offer](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer) and [Relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) object types as in the following example:

>Example 147
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "id": "http://example.org/connection-requests/123",
>  "summary": "Sally requested to be a friend of John",
>  "type": "Offer",
>  "actor": "acct:sally@example.org",
>  "object": {
>    "summary": "Sally and John's friendship",
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

>Example 148
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally and John's relationship history",
>  "type": "Collection",
>  "items": [
>    {
>      "summary": "John accepted Sally's friend request",
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
>      "summary": "John followed Sally",
>      "id": "http://example.org/activities/123",
>      "type": "Follow",
>      "actor": "acct:john@example.org",
>      "object": "acct:sally@example.org",
>      "context": "http://example.org/connections/123"
>    },
>    {
>      "summary": "Sally followed John",
>      "id": "http://example.org/activities/124",
>      "type": "Follow",
>      "actor": "acct:sally@example.org",
>      "object": "acct:john@example.org",
>      "context": "http://example.org/connections/123"
>    },
>    {
>      "summary": "John added Sally to his friends list",
>      "id": "http://example.org/activities/125",
>      "type": "Add",
>      "actor": "acct:john@example.org",
>      "object": "http://example.org/connections/123",
>      "target": {
>        "type": "Collection",
>        "summary": "John's Connections"
>      },
>      "context": "http://example.org/connections/123"
>    },
>    {
>      "summary": "Sally added John to her friends list",
>      "id": "http://example.org/activities/126",
>      "type": "Add",
>      "actor": "acct:sally@example.org",
>      "object": "http://example.org/connections/123",
>      "target": {
>        "type": "Collection",
>        "summary": "Sally's Connections"
>      },
>      "context": "http://example.org/connections/123"
>    }
>  ]
>}
>```

As illustrated in this example, accepting the "friend request" results in four additional activities including: John following Sally, Sally following John, John adding the relationship with Sally to his collection of Connections, and Sally adding the relationship with John to her collection of Connections.

In this example,

1. The optional [result](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-result) property is used within the `Accept` activity to identify the additional activities that occurred as a result of the accept.
2. The optional [context](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-context) property is used to relate the various activities back to a common reference point, which in this example is the relationship being established. The `context` allows an implementation to efficiently group related activities together for display or analytic purposes.

### 5.3 Representing Places

_This section is non-normative._

The [Place](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-place) object is used to represent both physical and logical locations. While numerous existing vocabularies exist for describing locations in a variety of ways, inconsistencies and incompatibilities between those vocabularies make it difficult to achieve appropriate interoperability between implementations. The `Place` object is included within the Activity vocabulary to provide a minimal, interoperable starting point for describing locations consistently across Activity Streams 2.0 implementations.

The `Place` object is intentionally flexible. It can, for instance, be used to identify a location simply by name:

>Example 149
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "San Francisco, CA"
>}
>```

Or, by [longitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-longitude) and [latitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-latitude):

>Example 150
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "San Francisco, CA",
>  "longitude": "122.4167",
>  "latitude": "37.7833"
>}
>```

The `Place` object can also describe an area around a given point using the [radius](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-radius) property, the [altitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-altitude) of the location, and a degree of [accuracy](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accuracy).

While publishers are not required to use these specific properties and *MAY* make use of other mechanisms for describing locations, consuming implementations that support the [Place](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-place) object *MUST* support the use of these properties.

### 5.4 Representing Questions

_This section is non-normative._

The [Question](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question) object can be used to express various types of inquiries.

For instance, simple open-ended questions similar to those posted to crowd-sourced question and answer websites:

>Example 151
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "A question about robots",
>  "id": "http://help.example.org/question/1",
>  "type": "Question",
>  "content": "I'd like to build a robot to feed my cat. Should I use Arduino or Raspberry >Pi?"
>}
>```

Multiple-choice questions or "polls" are also supported using either the [oneOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-oneof) or [anyOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-anyof) properties:

>Example 152
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "id": "http://polls.example.org/question/1",
>  "name": "A question about robots",
>  "type": "Question",
>   "content": "I'd like to build a robot to feed my cat. Which platform is best?",
>   "oneOf": [
>     {"name": "arduino"},
>     {"name": "raspberry pi"}
>   ]
> }
>```

Responses to questions are expressed as [Objects](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) containing an [inReplyto](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-inreplyto) property referencing the Question.

>Example 153
>
>```json
>{
> "@context": "https://www.w3.org/ns/activitystreams",
> "attributedTo": "http://sally.example.org",
> "inReplyTo": "http://polls.example.org/question/1",
> "name": "arduino"
>}
>```

Because [Question](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question) objects are also instances of [Activity](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-activity), the [result](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-result) property can be used to express the results or outcome of the Question (as appropriate):

Example 154

>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "A question about robots",
>  "id": "http://polls.example.org/question/1",
>  "type": "Question",
>   "content": "I'd like to build a robot to feed my cat. Which platform is best?",
>   "oneOf": [
>     {"name": "arduino"},
>     {"name": "raspberry pi"}
>   ],
>   "replies": {
>     "type": "Collection",
>     "totalItems": 3,
>     "items": [
>       {
>         "attributedTo": "http://sally.example.org",
>         "inReplyTo": "http://polls.example.org/question/1",
>         "name": "arduino"
>       },
>       {
>         "attributedTo": "http://joe.example.org",
>         "inReplyTo": "http://polls.example.org/question/1",
>         "name": "arduino"
>       },
>       {
>         "attributedTo": "http://john.example.org",
>         "inReplyTo": "http://polls.example.org/question/1",
>         "name": "raspberry pi"
>       }
>     ]
>   },
>   "result": {
>     "type": "Note",
>     "content": "Users are favoriting &quot;arduino&quot; by a 33% margin."
>   }
> }
> ```

### 5.5 Inverse Activities and "Undo"

_This section is non-normative._

Several of the core [Activity types](https://www.w3.org/TR/activitystreams-vocabulary/#activity-types) are defined as natural inversions of one another. These include:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept) and [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject),
- [Arrive](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-arrive) and [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave),
- [Join](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-join) and [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave),
- [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create) and [Delete](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-delete),
- [Like](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like) and [Dislike](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-dislike)

It is important to note that these types of activities are semantically distinct from one another and have no direct relationship on the other. That is, for example, if an actor "likes" a note at one point in time then later "dislikes" it, the "dislike" activity does not "undo" or negate out the prior "like".

The appropriate interpretation for the following is that Sally first liked, then later disliked John's note:

>Example 155
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "History of John's note",
>  "type": "Collection",
>  "items": [
>    {
>      "summary": "Sally liked John's note",
>      "type": "Like",
>      "actor": "http://sally.example.org",
>      "id": "http://activities.example.com/1",
>      "published": "2015-11-12T12:34:56Z",
>      "object": {
>        "summary": "John's note",
>        "type": "Note",
>        "id": "http://notes.example.com/1",
>        "attributedTo": "http://john.example.org",
>        "content": "My note"
>      }
>    },
>    {
>      "summary": "Sally disliked John's note",
>      "type": "Dislike",
>      "actor": "http://sally.example.org",
>      "id": "http://activities.example.com/2",
>      "published": "2015-12-11T21:43:56Z",
>      "object": {
>        "summary": "John's note",
>        "type": "Note",
>        "id": "http://notes.example.com/1",
>        "attributedTo": "http://john.example.org",
>        "content": "My note"
>      }
>    }
>  ]
> }
>```

The [Undo](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-undo) activity type is defined to provide the specific ability to undo or cancel out a prior activity. The appropriate interpretation for the following, then, is that Sally liked John's note at one point but has explicitly redacted that like later on.

>Example 156
>
>```json
>{
> "@context": "https://www.w3.org/ns/activitystreams",
> "summary": "History of John's note",
> "type": "Collection",
> "items": [
>   {
>     "summary": "Sally liked John's note",
>     "type": "Like",
>     "id": "http://activities.example.com/1",
>     "actor": "http://sally.example.org",
>     "published": "2015-11-12T12:34:56Z",
>     "object": {
>       "summary": "John's note",
>       "type": "Note",
>       "id": "http://notes.example.com/1",
>       "attributedTo": "http://john.example.org",
>       "content": "My note"
>     }
>   },
>   {
>     "summary": "Sally no longer likes John's note",
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

### 5.6 Mentions, Tags and Other Common Social Microsyntaxes

_This section is non-normative._

Many social software systems use special text-based microsyntaxes that allow users to define special addressing for notifications, linking, or categorization within objects. For example, including text such as "`@username`" within an object's content will often route the object to a special "mentions" or "inbox" stream for a particular user. Likewise, including text such as " `#topic`" within the object's content will often mark the object as being related to the topic "`topic`". Such mechanisms are commonly referred to as "mentions" and "hashtags", respectively.

While such microsyntaxes *MAY* be used within the values of the [content](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-content), [name](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-name), and [summary](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-summary) properties on an Activity Streams [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object), implementations *SHOULD NOT* be required to parse the values of those properties in order to determine the appropriate routing of notifications, categorization or linking between objects. Instead, publishers SHOULD make appropriate use of the vocabulary terms provided specifically for these purposes.

For example, suppose that an author wishes to send a note of thanks to another user named "@sally" with a hashtag of "#givingthanks". A typical way this message would appear within the content of a note is shown below:

<div align="center"><em>
Figure 1 A simple note with a mention an a hashtag:
</em></div>

"Thank you @sally for all your hard work! #givingthanks"

A typical social software implementation would typically render such a content such that "`@sally`" is replaced with a hyperlink to "@sally"'s social profile page and "`#givingthanks`" is replaced with a hyperlink to a listing of other notes that have been "tagged" with the same topic. Most implementations would also send a special notification to sally letting her know that a note mentioning her has been created.

The following illustrates an equivalent Activity Streams [Note](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-note) object:

>Example 157
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "A thank-you note",
>  "type": "Note",
>  "content": "Thank you <a href='http://sally.example.org'>@sally</a>
>      for all your hard work!
>      <a href='http://example.org/tags/givingthanks'>#givingthanks</a>",
>  "to": {
>    "name": "Sally",
>    "type": "Person",
>    "id": "http://sally.example.org"
>  },
>  "tag": {
>    "id": "http://example.org/tags/givingthanks",
>    "name": "#givingthanks"
>  }
>}
>```

The `to` property indicates that the user "@sally" is to be considered part of the [primary audience](https://www.w3.org/TR/activitystreams-vocabulary/#audienceTargeting) of the note and should therefore receive notification. The `tag` property associates the Note with a reference to " `http://example.org/tags/givingthanks`". Note that the `content` still includes the "`@sally`" and " `#givingthanks`" microsyntaxes but that consuming implementations are not required to parse those in order to make the appropriate associations.

In the case a publisher wishes to indicate a mention without an associated notification, the publisher can use the [Mention](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-mention) object type as a value of the [tag](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tag) property.

>Example 158
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "A thank-you note",
>  "type": "Note",
>  "content": "Thank you @sally for all your hard work! #givingthanks",
>  "tag": [
>    {
>      "type": "Mention",
>      "href": "http://example.org/people/sally",
>      "name": "@sally"
>    },
>    {
>      "id": "http://example.org/tags/givingthanks",
>      "name": "#givingthanks"
>    }
>  ]
>}
>```

### 5.7 Origin and Target

The [origin](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-origin) and [target](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-target) properties of an Activity respectively identify the entities from which and to which the action is directed. For instance, in the English statement, "Sally moved the file from Folder A to Folder B", the `origin` is "Folder A" and the `target` is "Folder B". This activity is illustrated in the example below:

>Example 159
>
>```json
>{
>    "@context": "https://www.w3.org/ns/activitystreams",
>    "summary": "Sally moved the sales figures from Folder A to Folder B",
>    "type": "Move",
>    "actor": "http://sally.example.org",
>    "object": {
>      "type": "Document",
>      "name": "sales figures"
>    },
>    "origin": {
>      "type": "Collection",
>      "name": "Folder A"
>    },
>    "target": {
>      "type": "Collection",
>      "name": "Folder B"
>    }
>  }
>```

The `origin` property is applicable to any type of activity for which the English preposition "from" can be considered applicable in the sense of identifying the origin, source or provenance of the activity's `object`.

The `target` property is applicable to any type of activity for which the English preposition "to" can be considered applicable in the sense of identifying the indirect object or destination of the activity's `object`.

### 5.8 Activity Type Motivating Use Cases

_This section is non-normative._

The [Activity types](https://www.w3.org/TR/activitystreams-vocabulary/#activity-types) defined in this vocabulary have been primarily selected to address the commonly implemented social use cases described below.

#### 5.8.1 Content Management

The Content Management use case primarily deals with activities that involve the creation, modification or deletion of content. This includes, for instance, activities such as "John created a new note", "Sally updated an article", and "Joe deleted the photo".

Relevant Activities:

- [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create)
- [Delete](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-delete)
- [Update](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-update)

#### 5.8.2 Collection Management

The Collection Management use case primarily deals with activities involving the management of content within collections. Examples of collections include things like folders, albums, friend lists, etc. This includes, for instance, activities such as "Sally added a file to Folder A", "John moved the file from Folder A to Folder B", etc.

Relevant Activities:

- [Add](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-add)
- [Move](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-move)
- [Remove](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-remove)

#### 5.8.3 Reactions

The Reactions use case primarily deals with reactions to content. This can include activities such as liking or disliking content, ignoring updates, flagging content as being inappropriate, accepting or rejecting objects, etc.

Relevant Activities:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept)
- [Block](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-block)
- [Dislike](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-dislike)
- [Flag](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-flag)
- [Ignore](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-ignore)
- [Like](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-like)
- [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject)
- [TentativeAccept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativeaccept)
- [TentativeReject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativereject)

#### 5.8.4 Event RSVP

The Event RSVP use case primarily deals with invitations to events and RSVP type responses.

Relevant Activities:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept)
- [Ignore](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-ignore)
- [Invite](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-invite)
- [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject)
- [TentativeAccept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativeaccept)
- [TentativeReject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tentativereject)

#### 5.8.5 Group Management

The Group Management use case primarily deals with management of groups. It can include, for instance, activities such as "John added Sally to Group A", "Sally joined Group A", "Joe left Group A", etc.

Relevant Activities:

- [Add](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-add)
- [Join](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-join)
- [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave)
- [Remove](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-remove)

#### 5.8.6 Content Experience

The Content Experience use case primarily deals with describing activities involving listening to, reading, or viewing content. For instance, "Sally read the article", "Joe listened to the song".

Relevant Activities:

- [Listen](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-listen)
- [Read](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-read)
- [View](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-view)

#### 5.8.7 Geo-Social Events

The Geo-Social Events use case primarily deals with activities involving geo-tagging type activities. For instance, it can include activities such as "Joe arrived at work", "Sally left work", and "John is travel from home to work".

Relevant Activities:

- [Arrive](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-arrive)
- [Leave](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-leave)
- [Travel](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-travel)

#### 5.8.8 Notification

The Notification use case primarily deals with calling attention to particular objects or notifications.

Relevant Activities:

- [Announce](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-announce)

5.8.9 Questions

the Questions use case primarily deals with representing inquiries of any type. See [5.4 Representing Questions](https://www.w3.org/TR/activitystreams-vocabulary/#questions) for more information.

Relevant Activities:

- [Question](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-question)

#### 5.8.10 Relationship Management

The Relationship Management use case primarily deals with representing activities involving the management of interpersonal and social relationships (e.g. friend requests, management of social network, etc). See [5.2 Representing Relationships Between Entities](https://www.w3.org/TR/activitystreams-vocabulary/#connections) for more information.

Relevant Activities:

- [Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept)
- [Add](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-add)
- [Block](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-block)
- [Create](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-create)
- [Delete](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-delete)
- [Follow](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-follow)
- [Ignore](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-ignore)
- [Invite](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-invite)
- [Reject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-reject)

#### 5.8.11 Negating Activity

The Negating Activity use case primarily deals with the ability to redact previously completed activities. See [5.5 Inverse Activities and "Undo"](https://www.w3.org/TR/activitystreams-vocabulary/#inverse) for more information.

Relevant Activities:

- [Undo](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-undo)

#### 5.8.12 Offers

The Offers use case deals with activities involving offering one object to another. It can include, for instance, activities such as "Company A is offering a discount on purchase of Product Z to Sally", "Sally is offering to add a File to Folder A", etc.

Relevant Activities:

- [Offer](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-offer)
