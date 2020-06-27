[목차로 돌아가기](ActivityVocabularyContents.md)

## 2. Core Types

The Activity Vocabulary Core Types provide the basis for the rest of the vocabulary.

Base URI: `https://www.w3.org/ns/activitystreams#`.

The Activity Streams 2.0 Core Types include:

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

>Example 1
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Object",
>  "id": "http://www.test.example/object/1",
>  "name": "A Simple, non-specific object"
>}
>```

**[Class] Link**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Link`
Notes: | A Link is an indirect, qualified reference to a resource identified by a URL. The fundamental model for links is established by [ [RFC5988](https://www.w3.org/TR/activitystreams-vocabulary/#bib-RFC5988)]. Many of the properties defined by the Activity Vocabulary allow values that are either instances of Object or Link. When a Link is used, it establishes a qualified relation connecting the subject (the containing object) to the resource identified by the href. Properties of the Link are properties of the reference as opposed to properties of the resource.
Disjoint With: | Object
Properties: | href \| rel \| mediaType \| name \| hreflang \| height \| width \| preview

>Example 2
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "hreflang": "en",
>  "mediaType": "text/html",
>  "name": "An example link"
>}
>```


**[Class] Activity**

URI: | `https://www.w3.org/ns/activitystreams#Activity`
Notes: | An Activity is a subtype of Object that describes some form of action that may happen, is currently happening, or has already happened. The `Activity` type itself serves as an abstract base type for all types of activities. It is important to note that the `Activity` type itself does not carry any specific semantics about the kind of action being taken.
Extends: | Object
Properties: | actor \| object \| target \| result \| origin \| instrument

Inherits all properties from Object.

>Example 3
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Activity",
>  "summary": "Sally did something to a note",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": {
>    "type": "Note",
>    "name": "A Note"
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

>Example 4
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Travel",
>  "summary": "Sally went to work",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "target": {
>    "type": "Place",
>    "name": "Work"
>  }
>}
>```

**[Class] Collection**

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Collection`
Notes: | A `Collection` is a subtype of Object that represents ordered or unordered sets of Object `or` Link instances. </br> Refer to the Activity Streams 2.0 Core specification for a complete description of the `Collection` type.
Extends: | Object
Properties: | totalItems \| current \| first \| last \| items </br>Inherits all properties from Object.

>Example 5
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally's notes",
>  "type": "Collection",
>  "totalItems": 2,
>  "items": [
>    {
>      "type": "Note",
>      "name": "A Simple Note"
>    },
>    {
>      "type": "Note",
>      "name": "Another Simple Note"
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

>Example 6
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally's notes",
>  "type": "OrderedCollection",
>  "totalItems": 2,
>  "orderedItems": [
>    {
>      "type": "Note",
>      "name": "A Simple Note"
>    },
>    {
>      "type": "Note",
>      "name": "Another Simple Note"
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
Properties: | partOf \| next \| prev </br>Inherits all properties from Collection.

>Example 7
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Page 1 of Sally's notes",
>  "type": "CollectionPage",
>  "id": "http://example.org/foo?page=1",
>  "partOf": "http://example.org/foo",
>  "items": [
>    {
>      "type": "Note",
>      "name": "A Simple Note"
>    },
>    {
>      "type": "Note",
>      "name": "Another Simple Note"
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

>Example 8
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Page 1 of Sally's notes",
>  "type": "OrderedCollectionPage",
>  "id": "http://example.org/foo?page=1",
>  "partOf": "http://example.org/foo",
>  "orderedItems": [
>    {
>      "type": "Note",
>      "name": "A Simple Note"
>    },
>    {
>      "type": "Note",
>      "name": "Another Simple Note"
>    }
>  ]
>}
>```
