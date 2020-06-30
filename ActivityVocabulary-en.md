[목차로 돌아가기](ActivityVocabularyContents.md)

[Activity Vocabulary](https://www.w3.org/TR/activitystreams-vocabulary/)
<abbr title="World Wide Web Consortium">W3C</abbr> Recommendation 23 May 2017

**This version:**
- https://www.w3.org/TR/2017/REC-activitystreams-vocabulary-20170523/

**Latest published version:**
- https://www.w3.org/TR/activitystreams-vocabulary/

**Latest editor's draft:**
- http://w3c.github.io/activitystreams/vocabulary/

**Test suite:**
- https://github.com/w3c/activitystreams/tree/master/test

**Implementation report:**
- https://github.com/w3c/activitystreams/tree/master/implementation-reports

**Previous version:**
- https://www.w3.org/TR/2017/PR-activitystreams-vocabulary-20170413/

**Editors:**
- [James M Snell](http://jasnell.me/), IBM
- [Evan Prodromou](https://fuzzy.ai/about), Fuzzy.ai

**Repository:**
- [Github](https://github.com/w3c/activitystreams)
- [Issues](https://github.com/w3c/activitystreams/issues)
- [Commits](https://github.com/w3c/activitystreams/commits/master)

**Test:**
- [Validator](https://as2.rocks/)

Please check the [**errata**](https://github.com/w3c/activitystreams/blob/master/ERRATA.md) for any errors or issues reported since publication.

The English version of this specification is the only normative version. Non-normative translations may also be available.

[Copyright](https://www.w3.org/Consortium/Legal/ipr-notice#Copyright) © 2017 [<abbr title="World Wide Web Consortium">W3C</abbr>](https://www.w3.org/)® (<abbr title="Massachusetts Institute of Technology">[MIT](https://www.csail.mit.edu/)</abbr>, <abbr title="European Research Consortium for Informatics and Mathematics">[ERCIM](https://www.ercim.eu/)</abbr>, [Keio](https://www.keio.ac.jp/), [Beihang](http://ev.buaa.edu.cn/)). <abbr title="World Wide Web Consortium">W3C</abbr> [liability](https://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](https://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks) and [permissive document license](https://www.w3.org/Consortium/Legal/2015/copyright-software-and-document) rules apply.

-----

## Abstract

This specification describes the Activity vocabulary. It is intended to be used in the context of the ActivityStreams 2.0 format and provides a foundational vocabulary for activity structures, and specific activity types.

### Author's Note

_This section is non-normative._

This draft is heavily influenced by the JSON Activity Streams 1.0 specification originally co-authored by Martin Atkins, Will Norris, Chris Messina, Monica Wilkinson, Rob Dolin and James Snell. The author is very thankful for their significant contributions and gladly stands on their shoulders. Some portions of the original text of Activity Streams 1.0 are used in this document.

## Status of This Document

_This section describes the status of this document at the time of its publication. Other documents may supersede this document. A list of current <abbr title="World Wide Web Consortium">W3C</abbr> publications and the latest revision of this technical report can be found in the [<abbr title="World Wide Web Consortium">W3C</abbr> technical reports index](https://www.w3.org/TR/) at https://www.w3.org/TR/._

This document was published by the [Social Web Working Group](https://www.w3.org/Social/WG) as a Recommendation. Comments regarding this document are welcome. Please send them to public-socialweb@w3.org ([subscribe](public-socialweb-request@w3.org), [archives](https://lists.w3.org/Archives/Public/public-socialweb/)).

Please see the Working Group's [implementation report](https://github.com/w3c/activitystreams/tree/master/implementation-reports).

This document has been reviewed by <abbr title="World Wide Web Consortium">W3C</abbr> Members, by software developers, and by other <abbr title="World Wide Web Consortium">W3C</abbr> groups and interested parties, and is endorsed by the Director as a <abbr title="World Wide Web Consortium">W3C</abbr> Recommendation. It is a stable document and may be used as reference material or cited from another document. <abbr title="World Wide Web Consortium">W3C</abbr>'s role in making the Recommendation is to draw attention to the specification and to promote its widespread deployment. This enhances the functionality and interoperability of the Web.

This document was produced by a group operating under the [5 February 2004 <abbr title="World Wide Web Consortium">W3C</abbr> Patent Policy](https://www.w3.org/Consortium/Patent-Policy-20040205/). <abbr title="World Wide Web Consortium">W3C</abbr> maintains a [public list of any patent disclosures](https://www.w3.org/2004/01/pp-impl/72531/status) made in connection with the deliverables of the group; that page also includes instructions for disclosing a patent. An individual who has actual knowledge of a patent which the individual believes contains [Essential Claim(s)](https://www.w3.org/Consortium/Patent-Policy-20040205/#def-essential) must disclose the information in accordance with [section 6 of the <abbr title="World Wide Web Consortium">W3C</abbr> Patent Policy](https://www.w3.org/Consortium/Patent-Policy-20040205/#sec-Disclosure).

This document is governed by the [1 March 2017 <abbr title="World Wide Web Consortium">W3C</abbr> Process Document](https://www.w3.org/2017/Process-20170301/).

## Table of Contents

1\. [Introduction](#1-introduction)

- 1.1 [Conventions](#1.1-conventions)

2\. [Core Types](#2-core-types)

3\. [Extended Types](#3-extended-types)

- 3.1 [Activity Types](#3.1-activity-types)
- 3.2 [Actor Types](#3.2-actor-types)
- 3.3 [Object and Link Types](#3.3-object-and-link-types)

4\. [Properties](#4-properties)

5\. [Implementation Notes](#5-implementation-notes)

- 5.1 [Audience Targeting](#5.1-audience-targeting)
- 5.2 [Representing Relationships Between Entities](#5.2-representing-relationships-between-entities)
- 5.3 [Representing Places](#5.3-representing-places)
- 5.4 [Representing Questions](#5.4-representing-questions)
- 5.5 [Inverse Activities and "Undo"](#5.5-inverse-activities-and-undo)
- 5.6 [Mentions, Tags and Other Common Social Microsyntaxes](#5.6-mentions-tags-and-other-common-social-microsyntaxes)
- 5.7 [Origin and Target](#5.7-origin-and-target)
- 5.8 [Activity Type Motivating Use Cases](#5.8-activity-type-motivating-use-cases)

A\. [Non-normative Ontology Definition](#a-non-normative-ontology-definition)

B\. [Changelog](#b-changelog)

C\. [References](#c-references)

- C.1 [Normative references](#c.1-normative-references)
- C.2 [Informative references](#c.2-informative-references)

## 1. Introduction

[The Activity Streams 2.0 Core Syntax](https://www.w3.org/TR/activitystreams-core/) defines the JSON syntax for Activity Streams. This document defines the vocabulary properties.

The Activity Streams 2.0 Vocabulary defines a set of abstract types and properties that describe past, present and future Activities. The vocabulary is defined in two parts:

1. A Core set of properties describing the generalized structure of an Activity; and
2. An Extended set of properties that cover specific types of Activities and Artifacts common to many social Web application systems.

While not all Activity Streams 2.0 implementations are expected to implement support for the Extended properties, all implementations *MUST* at least be capable of serializing and deserializing the Extended properties in accordance with the [Activity Streams 2.0 Core Syntax](https://www.w3.org/TR/activitystreams-core/).

The key words "*MUST*", "*MUST NOT*", "*REQUIRED*", "*SHALL*", "*SHALL NOT*", " *SHOULD*", "*SHOULD NOT*", "*RECOMMENDED*", "*MAY*", and "*OPTIONAL*" in this document are to be interpreted as described in [RFC2119].

### 1.1 Conventions

Unless otherwise specified, all properties defined as `xsd:dateTime` values *MUST* conform to the rules defined in Activity Streams 2.0 Core, [Section 2.3](https://www.w3.org/TR/activitystreams-core/#dates).

The examples included in this document use the normative JSON serialization defined by this specification.

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

#### [Class] Object

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

#### [Class] Link

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Link`
Notes: | A Link is an indirect, qualified reference to a resource identified by a URL. The fundamental model for links is established by [ RFC5988]. Many of the properties defined by the Activity Vocabulary allow values that are either instances of Object or Link. When a Link is used, it establishes a qualified relation connecting the subject (the containing object) to the resource identified by the href. Properties of the Link are properties of the reference as opposed to properties of the resource.
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


#### [Class] Activity

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

#### [Class] IntransitiveActivity

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

#### [Class] Collection

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

#### [Class] OrderedCollection

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

#### [Class] CollectionPage

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

#### [Class] OrderedCollectionPage

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

#### [Class] Accept

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

#### [Class] TentativeAccept

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

#### [Class] Add

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

#### [Class] Arrive

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

#### [Class] Create

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

#### [Class] Delete

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

#### [Class] Follow

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

#### [Class] Ignore

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


#### [Class] Join

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

#### [Class] Leave

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

#### [Class] Like

Description| |
--|--
URI: |` https://www.w3.org/ns/activitystreams#Like`
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

#### [Class] Offer

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


#### [Class] Invite

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

#### [Class] Reject

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

#### [Class] TentativeReject

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

#### [Class] Remove

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

#### [Class] Undo

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

#### [Class] Update

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

#### [Class] View

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#View`
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


#### [Class] Listen

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

#### [Class] Read

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

#### [Class] Move

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

#### [Class] Travel

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

#### [Class] Announce

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

#### [Class] Block

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

#### [Class] Flag

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

#### [Class] Dislike

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

#### [Class] Question

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Question`
Notes: | Represents a question being asked. Question objects are an extension of IntransitiveActivity. That is, the Question object is an Activity, but the direct object is the question itself and therefore it would not contain an object property. </br></br> Either of the anyOf and oneOf properties *MAY* be used to express possible answers, but a Question object *MUST NOT* have both properties.
Extends: | IntransitiveActivity.
Properties: | oneOf \| anyOf \| closed
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


#### [Class] Application

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

#### [Class] Group

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

#### [Class] Organization

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

#### [Class] Person

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

#### [Class] Service

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

#### [Class] Relationship

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

#### [Class] Article

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

#### [Class] Document

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

#### [Class] Audio

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

#### [Class] Image

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

#### [Class] Video

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

#### [Class] Note

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

#### [Class] Page

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

#### [Class] Event

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

#### [Class] Place

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

#### [Class] Mention

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

#### [Class] Profile

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

#### [Class] Tombstone

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

## 4. Properties

Base URI: `https://www.w3.org/ns/activitystreams#`.

The common properties include:
 [actor](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-actor) |
 [attachment](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-attachment) |
 [attributedTo](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-attributedto) |
 [audience](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-audience) |
 [bcc](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-bcc) |
 [bto](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-bto) |
 [cc](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-cc) |
 [context](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-context) |
 [current](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-current) |
 [first](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-first) |
 [generator](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-generator) |
 [icon](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-icon) |
 [id](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-id) |
 [image](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-image) |
 [inReplyTo](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-inreplyto) |
 [instrument](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-instrument) |
 [last](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-last) |
 [location](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-location) |
 [items](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-items) |
 [oneOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-oneof) |
 [anyOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-anyof) |
 [closed](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-closed) |
 [origin](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-origin) |
 [next](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-next) |
 [object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object) |
 [prev](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-prev) |
 [preview](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-preview) |
 [result](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-result) |
 [replies](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-replies) |
 [tag](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-tag) |
 [target](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-target) |
 [to](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-to) |
 [type](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-type) |
 [url](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-url) |
 [accuracy](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accuracy) |
 [altitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-altitude) |
 [content](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-content) |
 [name](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-name) |
 [duration](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-duration) |
 [height](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-height) |
 [href](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-href) |
 [hreflang](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-hreflang) |
 [partOf](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-partof) |
 [latitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-latitude) |
 [longitude](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-longitude) |
 [mediaType](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-mediatype) |
 [endTime](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-endtime) |
 [published](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-published) |
 [startTime](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-starttime) |
 [radius](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-radius) |
 [rel](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-rel) |
 [startIndex](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-startindex) |
 [summary](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-summary) |
 [totalItems](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-totalitems) |
 [units](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-units) |
 [updated](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-updated) |
 [width](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-width) |
 [subject](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-subject) |
 [relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) |
 [describes](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-describes) |
 [formerType](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-formertype) |
 [deleted](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-deleted)

The "Domain" indicates the type of Object the property term applies to. The "Range" indicates the type of value the property term can have. Certain properties are marked as a "Subproperty Of" another term, meaning that the term is a specialization of the referenced term. For instance, [actor](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-actor) is a subproperty of [attributedTo](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-attributedto). Properties marked as being "Functional" can have only one value. Items not marked as "Functional" can have multiple values.

#### [Class] id

Description| |
--|--
URI: | `@id`
Notes: | Provides the globally unique identifier for an Object or Link.
Domain: | Object \| Link
Range: | `anyURI`
Functional: | True

>Example 61
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "Foo",
>  "id": "http://example.org/foo"
>}
>```

#### [Class] type

Description| |
--|--
URI: | `@type`
Notes: | Identifies the Object or Link type. Multiple values may be specified.
Domain: | Object \| Link
Range: | `anyURI`

>Example 62
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A foo",
>  "type": "http://example.org/Foo"
>}
>```

#### [Class] actor

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#actor`
Notes: | Describes one or more entities that either performed or are expected to perform the activity. Any single activity can have multiple `actor`s. The `actor` *MAY* be specified using an indirect Link.
Domain: | Activity
Range: | Object \| Link
Subproperty Of: | attributedTo

>Example 63
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered the Foo object",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/foo"
>}
>```

>Example 64
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered the Foo object",
>  "type": "Offer",
>  "actor": {
>    "type": "Person",
>    "id": "http://sally.example.org",
>    "summary": "Sally"
>  },
>  "object": "http://example.org/foo"
>}
>```

>Example 65
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally and Joe offered the Foo object",
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

#### [Class] attachment

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#attachment`
Notes: | Identifies a resource attached or related to an object that potentially requires special handling. The intent is to provide a model that is at least semantically similar to attachments in email.
Domain: | Object
Range: | Object \| Link

>Example 66
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Note",
>  "name": "Have you seen my cat?",
>  "attachment": [
>    {
>      "type": "Image",
>      "content": "This is what he looks like.",
>      "url": "http://example.org/cat.jpeg"
>    }
>  ]
>}
>```

#### [Class] attributedTo

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#attributedTo`
Notes: | Identifies one or more entities to which this object is attributed. The attributed entities might not be Actors. For instance, an object might be attributed to the completion of another activity.
Domain: | Link \| Object
Range: | Link \| Object

>Example 67
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Image",
>  "name": "My cat taking a nap",
>  "url": "http://example.org/cat.jpeg",
>  "attributedTo": [
>    {
>      "type": "Person",
>      "name": "Sally"
>    }
>  ]
>}
>```

>Example 68
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Image",
>  "name": "My cat taking a nap",
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

#### [Class] audience

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#audience`
Notes: | Identifies one or more entities that represent the total population of entities for which the object can considered to be relevant.
Domain: | Object
Range: | Object \| Link

>Example 69
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "Holiday announcement",
>  "type": "Note",
>  "content": "Thursday will be a company-wide holiday. Enjoy your day off!",
>  "audience": {
>    "type": "http://example.org/Organization",
>    "name": "ExampleCo LLC"
>  }
>}
>```

#### [Class] bcc

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#bcc`
Notes: | Identifies one or more Objects that are part of the private secondary audience of this Object.
Domain: | Object
Range: | Object \| Link

>Example 70
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered a post to John",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org",
>  "bcc": [ "http://joe.example.org" ]
>}
>```

#### [Class] bto

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#bto`
Notes: | Identifies an Object that is part of the private primary audience of this Object.
Domain: | Object
Range: | Object \| Link

>Example 71
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered a post to John",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org",
>  "bto": [ "http://joe.example.org" ]
>}
>```

#### [Class] cc

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#cc`
Notes: | Identifies an Object that is part of the public secondary audience of this Object.
Domain: | Object
Range: | Object \| Link

>Example 72
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered a post to John",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org",
>  "cc": [ "http://joe.example.org" ]
>}
>```

#### [Class] context

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#context`
Notes: | Identifies the context within which the object exists or an activity was performed.</br></br> The notion of "context" used is intentionally vague. The intended function is to serve as a means of grouping objects and activities that share a common originating context or purpose. An example could be all activities relating to a common project or event.
Domain: | Object
Range: | Object \| Link

>Example 73
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Activities in context 1",
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

#### [Class] current

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#current`
Notes: | In a paged Collection, indicates the page that contains the most recently updated member items.
Domain: | Collection
Range: | CollectionPage \| Link
Functional: | True

>Example 74
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally's blog posts",
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

>Example 75
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally's blog posts",
>  "type": "Collection",
>  "totalItems": 3,
>  "current": {
>    "type": "Link",
>    "summary": "Most Recent Items",
>    "href": "http://example.org/collection"
>  },
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

#### [Class] first

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#first`
Notes: | In a paged Collection, indicates the furthest preceeding page of items in the collection.
Domain: | Collection
Range: | CollectionPage \| Link
Functional: | True

>Example 76
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally's blog posts",
>  "type": "Collection",
>  "totalItems": 3,
>  "first": "http://example.org/collection?page=0"
>}
>```

>Example 77
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally's blog posts",
>  "type": "Collection",
>  "totalItems": 3,
>  "first": {
>    "type": "Link",
>    "summary": "First Page",
>    "href": "http://example.org/collection?page=0"
>  }
>}
>```

#### [Class] generator

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#generator`
Notes: | Identifies the entity (e.g. an application) that generated the object.
Domain: | Object
Range: | Object \| Link

>Example 78
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "content": "This is all there is.",
>  "generator": {
>    "type": "Application",
>    "name": "Exampletron 3000"
>  }
>}
>```

#### [Class] icon

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#icon`
Notes: | Indicates an entity that describes an icon for this object. The image should have an aspect ratio of one (horizontal) to one (vertical) and should be suitable for presentation at a small size.
Domain: | Object
Range: | Image \| Link

>Example 79
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "content": "This is all there is.",
>  "icon": {
>    "type": "Image",
>    "name": "Note icon",
>    "url": "http://example.org/note.png",
>    "width": 16,
>    "height": 16
>  }
>}
>```

>Example 80
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "content": "A simple note",
>  "icon": [
>    {
>      "type": "Image",
>      "summary": "Note (16x16)",
>      "url": "http://example.org/note1.png",
>      "width": 16,
>      "height": 16
>    },
>    {
>      "type": "Image",
>      "summary": "Note (32x32)",
>      "url": "http://example.org/note2.png",
>      "width": 32,
>      "height": 32
>    }
>  ]
>}
>```

#### [Class] image

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#image`
Notes: | Indicates an entity that describes an image for this object. Unlike the icon property, there are no aspect ratio or display size limitations assumed.
Domain: | Object
Range: | Image \| Link

>Example 81
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "A simple note",
>  "type": "Note",
>  "content": "This is all there is.",
>  "image": {
>    "type": "Image",
>    "name": "A Cat",
>    "url": "http://example.org/cat.png"
>  }
>}
>```

>Example 82
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "A simple note",
>  "type": "Note",
>  "content": "This is all there is.",
>  "image": [
>    {
>      "type": "Image",
>      "name": "Cat 1",
>      "url": "http://example.org/cat1.png"
>    },
>    {
>      "type": "Image",
>      "name": "Cat 2",
>      "url": "http://example.org/cat2.png"
>    }
>  ]
>}
>```

#### [Class] inReplyTo

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#inReplyTo`
Notes: | Indicates one or more entities for which this object is considered a response.
Domain: | Object
Range: | Object \| Link

>Example 83
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "content": "This is all there is.",
>  "inReplyTo": {
>    "summary": "Previous note",
>    "type": "Note",
>    "content": "What else is there?"
>  }
>}
>```

>Example 84
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "content": "This is all there is.",
>  "inReplyTo": "http://example.org/posts/1"
>}
>```

#### [Class] instrument

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#instrument`
Notes: | Identifies one or more objects used (or to be used) in the completion of an Activity.
Domain: | Activity
Range: | Object \| Link

>Example 85
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally listened to a piece of music on the Acme Music Service",
>  "type": "Listen",
>  "actor": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "object": "http://example.org/foo.mp3",
>  "instrument": {
>    "type": "Service",
>    "name": "Acme Music Service"
>  }
>}
>```

#### [Class] last

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#last`
Notes: | In a paged Collection, indicates the furthest proceeding page of the collection.
Domain: | Collection
Range: | CollectionPage \| Link
Functional: | True

>Example 86
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A collection",
>  "type": "Collection",
>  "totalItems": 3,
>  "last": "http://example.org/collection?page=1"
>}
>```

>Example 87
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A collection",
>  "type": "Collection",
>  "totalItems": 5,
>  "last": {
>    "type": "Link",
>    "summary": "Last Page",
>    "href": "http://example.org/collection?page=1"
>  }
>}
>```

#### [Class] location

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#location`
Notes: | Indicates one or more physical or logical locations associated with the object.
Domain: | Object
Range: | Object \| Link

>Example 88
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Person",
>  "name": "Sally",
>  "location": {
>    "name": "Over the Arabian Sea, east of Socotra Island Nature Sanctuary",
>    "type": "Place",
>    "longitude": 12.34,
>    "latitude": 56.78,
>    "altitude": 90,
>    "units": "m"
>  }
>}
>```

#### [Class] items

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#items`
Notes: | Identifies the items contained in a collection. The items might be ordered or unordered.
Domain: | Collection
Range: | Object \| Link \| Ordered List of [Object \| Link ]

>Example 89
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
>      "name": "Reminder for Going-Away Party"
>    },
>    {
>      "type": "Note",
>      "name": "Meeting 2016-11-17"
>    }
>  ]
>}
>```

>Example 90
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
>      "name": "Meeting 2016-11-17"
>    },
>    {
>      "type": "Note",
>      "name": "Reminder for Going-Away Party"
>    }
>  ]
>}
>```

#### [Class] oneOf

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#oneOf`
Notes: | Identifies an exclusive option for a Question. Use of `oneOf` implies that the Question can have only a single answer. To indicate that a Question can have multiple answers, use anyOf.
Domain: | Question
Range: | Object \| Link

>Example 91
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

#### [Class] anyOf

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#anyOf`
Notes: | Identifies an inclusive option for a Question. Use of `anyOf` implies that the Question can have multiple answers. To indicate that a Question can have only one answer, use oneOf.
Domain: | Question
Range: | Object \| Link

>Example 92
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "What is the answer?",
>  "anyOf": [
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

#### [Class] closed

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#closed`
Notes: | Indicates that a question has been closed, and answers are no longer accepted.
Domain: | Question
Range: | Object \| Link \| `xsd:dateTime` \| `xsd:boolean`

>Example 93
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Question",
>  "name": "What is the answer?",
>  "closed": "2016-05-10T00:00:00Z"
>}
>```

#### [Class] origin

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#origin`
Notes: | Describes an indirect object of the activity from which the activity is directed. The precise meaning of the origin is the object of the English preposition "from". For instance, in the activity "John moved an item to List B from List A", the origin of the activity is "List A".
Domain: | Activity
Range: | Object \| Link

>Example 94
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally moved a post from List A to List B",
>  "type": "Move",
>  "actor": "http://sally.example.org",
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

#### [Class] next

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#next`
Notes: | In a paged Collection, indicates the next page of items.
Domain: | CollectionPage
Range: | CollectionPage \| Link
Functional: | True

>Example 95
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Page 2 of Sally's blog posts",
>  "type": "CollectionPage",
>  "next": "http://example.org/collection?page=2",
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

>Example 96
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Page 2 of Sally's blog posts",
>  "type": "CollectionPage",
>  "next": {
>    "type": "Link",
>    "name": "Next Page",
>    "href": "http://example.org/collection?page=2"
>  },
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

#### [Class] object

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#object`
Notes: | When used within an Activity, describes the direct object of the activity. For instance, in the activity "John added a movie to his wishlist", the object of the activity is the movie added.</br></br> When used within a Relationship describes the entity to which the subject is related.
Domain: | Activity \| Relationship
Range: | Object \| Link

>Example 97
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally liked a post",
>  "type": "Like",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1"
>}
>```

>Example 98
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Like",
>  "actor": "http://sally.example.org",
>  "object": {
>    "type": "Note",
>    "content": "A simple note"
>  }
>}
>```

>Example 99
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally liked a note",
>  "type": "Like",
>  "actor": "http://sally.example.org",
>  "object": [
>    "http://example.org/posts/1",
>    {
>      "type": "Note",
>      "summary": "A simple note",
>      "content": "That is a tree."
>    }
>  ]
>}
>```

#### [Class] prev

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#prev`
Notes: | In a paged Collection, identifies the previous page of items.
Domain: | CollectionPage
Range: | CollectionPage \| Link
Functional: | True

>Example 100
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Page 1 of Sally's blog posts",
>  "type": "CollectionPage",
>  "prev": "http://example.org/collection?page=1",
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

>Example 101
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Page 1 of Sally's blog posts",
>  "type": "CollectionPage",
>  "prev": {
>    "type": "Link",
>    "name": "Previous Page",
>    "href": "http://example.org/collection?page=1"
>  },
>  "items": [
>    "http://example.org/posts/1",
>    "http://example.org/posts/2",
>    "http://example.org/posts/3"
>  ]
>}
>```

#### [Class] preview

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#preview`
Notes: | Identifies an entity that provides a preview of this object.
Domain: | Link \| Object
Range: | Link \| Object

>Example 102
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Video",
>  "name": "Cool New Movie",
>  "duration": "PT2H30M",
>  "preview": {
>    "type": "Video",
>    "name": "Trailer",
>    "duration": "PT1M",
>    "url": {
>      "href": "http://example.org/trailer.mkv",
>      "mediaType": "video/mkv"
>    }
>  }
>}
>```

#### [Class] result

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#result`
Notes: | Describes the result of the activity. For instance, if a particular action results in the creation of a new resource, the result property can be used to describe that new resource.
Domain: | Activity
Range: | Object \| Link

>Example 103
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally checked that her flight was on time",
>  "type": ["Activity", "http://www.verbs.example/Check"],
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/flights/1",
>  "result": {
>    "type": "http://www.types.example/flightstatus",
>    "name": "On Time"
>  }
>}
>```

#### [Class] replies

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#replies`
Notes: | Identifies a Collection containing objects considered to be responses to this object.
Domain: | Object
Range: | Collection
Functional: | True

>Example 104
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "id": "http://www.test.example/notes/1",
>  "content": "I am fine.",
>  "replies": {
>    "type": "Collection",
>    "totalItems": 1,
>    "items": [
>      {
>        "summary": "A response to the note",
>        "type": "Note",
>        "content": "I am glad to hear it.",
>        "inReplyTo": "http://www.test.example/notes/1"
>      }
>    ]
>  }
>}
>```

#### [Class] tag

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#tag`
Notes: | One or more "tags" that have been associated with an objects. A tag can be any kind of Object. The key difference between `attachment` and `tag` is that the former implies association by inclusion, while the latter implies associated by reference.
Domain: | Object
Range: | Object \| Link

>Example 105
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Image",
>  "summary": "Picture of Sally",
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

#### [Class] target

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#target`
Notes: | Describes the indirect object, or target, of the activity. The precise meaning of the target is largely dependent on the type of action being described but will often be the object of the English preposition "to". For instance, in the activity "John added a movie to his wishlist", the target of the activity is John's wishlist. An activity can have more than one target.
Domain: | Activity
Range: | Object \| Link

>Example 106
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered the post to John",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org"
>}
>```

>Example 107
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered the post to John",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": {
>    "type": "Person",
>    "name": "John"
>  }
>}
>```

#### [Class] to

Description| |
--|--
URI: |` https://www.w3.org/ns/activitystreams#to`
Notes: | Identifies an entity considered to be part of the public primary audience of an Object
Domain: | Object
Range: | Object \| Link

>Example 108
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally offered the post to John",
>  "type": "Offer",
>  "actor": "http://sally.example.org",
>  "object": "http://example.org/posts/1",
>  "target": "http://john.example.org",
>  "to": [ "http://joe.example.org" ]
>}
>```

#### [Class] url

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#url`
Notes: | Identifies one or more links to representations of the object
Domain: | Object
Range: | `xsd:anyURI` \| Link

>Example 109
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Document",
>  "name": "4Q Sales Forecast",
>  "url": "http://example.org/4q-sales-forecast.pdf"
>}
>```

>Example 110
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Document",
>  "name": "4Q Sales Forecast",
>  "url": {
>    "type": "Link",
>    "href": "http://example.org/4q-sales-forecast.pdf"
>  }
>}
>```

>Example 111
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Document",
>  "name": "4Q Sales Forecast",
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

#### [Class] accuracy

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#accuracy`
Notes: | Indicates the accuracy of position coordinates on a Place objects. Expressed in properties of percentage. e.g. "94.0" means "94.0% accurate".
Domain: | Place
Range: | `xsd:float` [>= 0.0f, <= 100.0f]
Functional: | True

>Example 112
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "Liu Gu Lu Cun, Pingdu, Qingdao, Shandong, China",
>  "type": "Place",
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "accuracy": 94.5
>}
>```

#### [Class] altitude

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#altitude`
Notes: | Indicates the altitude of a place. The measurement units is indicated using the units property. If units is not specified, the default is assumed to be "`m`" indicating meters.
Domain: | Object
Range: | `xsd:float`
Functional: | True

>Example 113
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Place",
>  "name": "Fresno Area",
>  "altitude": 15.0,
>  "latitude": 36.75,
>  "longitude": 119.7667,
>  "units": "miles"
>}
>```

#### [Class] content

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#content`
Notes: | The content or textual representation of the Object encoded as a JSON string. By default, the value of `content` is HTML. The mediaType property can be used in the object to indicate a different content type. </br></br> The content *MAY* be expressed using multiple language-tagged values.
Domain: | Object
Range: | `xsd:string` \| `rdf:langString`

>Example 114
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "content": "A <em>simple</em> note"
>}
>```

>Example 115
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "contentMap": {
>    "en": "A <em>simple</em> note",
>    "es": "Una nota <em>sencilla</em>",
>    "zh-Hans": "一段<em>简单的</em>笔记"
>  }
>}
>```

>Example 116
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "mediaType": "text/markdown",
>  "content": "## A simple note\nA simple markdown `note`"
>}
>```

#### [Class] name

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#name`
Notes: | A simple, human-readable, plain-text name for the object. HTML markup *MUST NOT* be included. The name *MAY* be expressed using multiple language-tagged values.
Domain: | Object \| Link
Range: | `xsd:string` \| `rdf:langString`

>Example 117
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Note",
>  "name": "A simple note"
>}
>```

>Example 118
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

#### [Class] duration

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#duration`
Notes: | When the object describes a time-bound resource, such as an audio or video, a meeting, etc, the duration property indicates the object's approximate duration. The value *MUST* be expressed as an `xsd:duration` as defined by [ xmlschema11-2], section 3.3.6 (e.g. a period of 5 seconds is represented as "`PT5S`").
Domain: | Object
Range: | `xsd:duration`
Functional: | True

>Example 119
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Video",
>  "name": "Birds Flying",
>  "url": "http://example.org/video.mkv",
>  "duration": "PT2H"
>}
>```

#### [Class] height

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#height`
Notes: | On a Link, specifies a hint as to the rendering height in device-independent pixels of the linked resource.
Domain: | Link
Range: | `xsd:nonNegativeInteger`
Functional: | True

>Example 120
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

#### [Class] href

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#href`
Notes: | The target resource pointed to by a Link.
Domain: | Link
Range: | `xsd:anyURI`
Functional: | True

>Example 121
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "mediaType": "text/html",
>  "name": "Previous"
>}
>```

#### [Class] hreflang

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#hreflang`
Notes: | Hints as to the language used by the target resource. Value *MUST* be a [[BCP47](https://www.w3.org/TR/activitystreams-vocabulary/#bib-BCP47)] Language-Tag.
Domain: | Link
Range: | [[BCP47](https://www.w3.org/TR/activitystreams-vocabulary/#bib-BCP47)] Language Tag
Functional: | True

>Example 122
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "hreflang": "en",
>  "mediaType": "text/html",
>  "name": "Previous"
>}
>```

#### [Class] partOf

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#partOf`
Notes: | Identifies the Collection to which a CollectionPage objects items belong.
Domain: | CollectionPage
Range: | Link | Collection
Functional: | True

>Example 123
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Page 1 of Sally's notes",
>  "type": "CollectionPage",
>  "id": "http://example.org/collection?page=1",
>  "partOf": "http://example.org/collection",
>  "items": [
>    {
>      "type": "Note",
>      "name": "Pizza Toppings to Try"
>    },
>    {
>      "type": "Note",
>      "name": "Thought about California"
>    }
>  ]
>}
>```

#### [Class] latitude

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#latitude`
Notes: | The latitude of a place
Domain: | Place
Range: | `xsd:float`
Functional: | True

>Example 124
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

#### [Class] longitude

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#longitude`
Notes: | The longitude of a place
Domain: | Place
Range: | `xsd:float`
Functional: | True

>Example 125
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

#### [Class] mediaType

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#mediaType`
Notes: | When used on a Link, identifies the MIME media type of the referenced resource. </br></br> When used on an Object, identifies the MIME media type of the value of the content property. If not specified, the content property is assumed to contain `text/html` content.
Domain: | Link \| Object
Range: | MIME Media Type
Functional: | True

>Example 126
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "hreflang": "en",
>  "mediaType": "text/html",
>  "name": "Next"
>}
>```

#### [Class] endTime

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#endTime`
Notes: | The date and time describing the actual or expected ending time of the object. When used with an Activity object, for instance, the endTime property specifies the moment the activity concluded or is expected to conclude.
Domain: | Object
Range: | `xsd:dateTime`
Functional: | True

>Example 127
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

#### [Class] published

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#published`
Notes: | The date and time at which the object was published
Domain: | Object
Range: | `xsd:dateTime`
Functional: | True

>Example 128
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "A simple note",
>  "type": "Note",
>  "content": "Fish swim.",
>  "published": "2014-12-12T12:12:12Z"
>}
>```

#### [Class] startTime

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#startTime`
Notes: | The date and time describing the actual or expected starting time of the object. When used with an Activity object, for instance, the startTime property specifies the moment the activity began or is scheduled to begin.
Domain: | Object
Range: | `xsd:dateTime`
Functional: | True

>Example 129
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

#### [Class] radius

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#radius`
Notes: | The radius from the given latitude and longitude for a Place. The units is expressed by the units property. If units is not specified, the default is assumed to be "`m`" indicating "meters".
Domain: | Place
Range: | `xsd:float` [>= 0.0f]
Functional: | True

>Example 130
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

#### [Class] rel

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#rel`
Notes: | A link relation associated with a Link. The value *MUST* conform to both the [HTML5] and [RFC5988] "link relation" definitions. </br></br> In the [HTML5], any string not containing the "space" U+0020, "tab" (U+0009), "LF" (U+000A), "FF" (U+000C), "CR" (U+000D) or "," (U+002C) characters can be used as a valid link relation.
Domain: | Link
Range: | [RFC5988] or [HTML5] Link Relation

>Example 131
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Link",
>  "href": "http://example.org/abc",
>  "hreflang": "en",
>  "mediaType": "text/html",
>  "name": "Preview",
>  "rel": ["canonical", "preview"]
>}
>```

#### [Class] startIndex

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#startIndex`
Notes: | A non-negative integer value identifying the relative position within the logical view of a strictly ordered collection.
Domain: | OrderedCollectionPage
Range: | `xsd:nonNegativeInteger`
Functional: | True

>Example 132
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
>      "name": "Density of Water"
>    },
>    {
>      "type": "Note",
>      "name": "Air Mattress Idea"
>    }
>  ]
>}
>```

#### [Class] summary

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#summary`
Notes: | A natural language summarization of the object encoded as HTML. Multiple language tagged summaries *MAY* be provided.
Domain: | Object
Range: | `xsd:string` \| `rdf:langString`

>Example 133
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "Cane Sugar Processing",
>  "type": "Note",
>  "summary": "A simple <em>note</em>"
>}
>```

>Example 134
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "Cane Sugar Processing",
>  "type": "Note",
>  "summaryMap": {
>    "en": "A simple <em>note</em>",
>    "es": "Una <em>nota</em> sencilla",
>    "zh-Hans": "一段<em>简单的</em>笔记"
>  }
>}
>```

#### [Class] totalItems

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#totalItems`
Notes: | A non-negative integer specifying the total number of objects contained by the logical view of the collection. This number might not reflect the actual number of items serialized within the Collection object instance.
Domain: | Collection
Range: | `xsd:nonNegativeInteger`
Functional: | True

>Example 135
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
>      "name": "Which Staircase Should I Use"
>    },
>    {
>      "type": "Note",
>      "name": "Something to Remember"
>    }
>  ]
>}
>```

#### [Class] units

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#units`
Notes: | Specifies the measurement units for the radius and altitude properties on a Place object. If not specified, the default is assumed to be "m" for "meters".
Domain: | Place
Range: | "`cm`" \| " `feet`" \| " `inches`" \| " `km`" \| " `m`" \| " `miles`" \| `xsd:anyURI`
Functional: | True

>Example 136
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

#### [Class] updated

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#updated`
Notes: | The date and time at which the object was updated
Domain: | Object
Range: | `xsd:dateTime`
Functional: | True

>Example 137
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "name": "Cranberry Sauce Idea",
>  "type": "Note",
>  "content": "Mush it up so it does not have the same shape as the can.",
>  "updated": "2014-12-12T12:12:12Z"
>}
>```

#### [Class] width

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#width`
Notes: | On a Link, specifies a hint as to the rendering width in device-independent pixels of the linked resource.
Domain: | Link
Range: | `xsd:nonNegativeInteger`
Functional: | True

>Example 138
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

#### [Class] subject

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#subject`
Notes: | On a Relationship object, the `subject` property identifies one of the connected individuals. For instance, for a Relationship object describing "John is related to Sally", `subject` would refer to John.
Domain: | Relationship
Range: | Link \| Object
Functional: | True

>Example 139
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally is an acquaintance of John's",
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

#### [Class] relationship

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#relationship`
Notes: | On a Relationship object, the `relationship` property identifies the kind of relationship that exists between subject and object.
Domain: | Relationship
Range: | Object

>Example 140
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally is an acquaintance of John's",
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

#### [Class] describes

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#describes`
Notes: | On a Profile object, the `describes` property identifies the object described by the Profile.
Domain: | Profile
Range: | Object
Functional: | True

>Example 141
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "summary": "Sally's profile",
>  "type": "Profile",
>  "describes": {
>    "type": "Person",
>    "name": "Sally"
>  },
>  "url": "http://sally.example.org"
>}
>```

#### [Class] formerType

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#formerType`
Notes: | On a Tombstone object, the `formerType` property identifies the type of the object that was deleted.
Domain: | Tombstone
Range: | Object
Functional: | False

>Example 142
>```json
>{
>"@context": "https://www.w3.org/ns/activitystreams",
>"summary": "This image has been deleted",
>"type": "Tombstone",
>"formerType": "Image",
>"url": "http://example.org/image/2"
>}
>```

#### [Class] deleted

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#deleted`
Notes: | On a Tombstone object, the `deleted` property is a timestamp for when the object was deleted.
Domain: | Tombstone
Range: | `xsd:dateTime`
Functional: | True

>Example 143
>
>```json
>{
>"@context": "https://www.w3.org/ns/activitystreams",
>"summary": "This image has been deleted",
>"type": "Tombstone",
>"deleted": "2016-05-03T00:00:00Z"
>}
>```

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

While such microsyntaxes *MAY* be used within the values of the [content](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-content), [name](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-name), and [summary](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-summary) properties on an Activity Streams [Object](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-object), implementations *SHOULD NOT* be required to parse the values of those properties in order to determine the appropriate routing of notifications, categorization or linking between objects. Instead, publishers *SHOULD* make appropriate use of the vocabulary terms provided specifically for these purposes.

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

## A. Non-normative Ontology Definition

_This section is non-normative._

A non-normative turtle definition of the Activity Streams 2.0 vocabulary is provided [here](https://www.w3.org/ns/activitystreams-owl) and/or at [the namespace](https://www.w3.org/ns/activitystreams) as a convenience for implementers wishing to use RDF mechanisms for processing Activity Streams 2.0. Note, however, that this document provides the normative definition of the Activity Streams 2.0 vocabulary.

## B. Changelog

_This section is non-normative._

The following notable changes have been made to this document since the previous candidate recommendation of [2016-12-15](https://www.w3.org/TR/2016/CR-activitystreams-vocabulary-20161215/#changelog).

- Removed the four normative [relationship](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-relationship) values for lack of implementation. Changed examples to use terms from the [Relationship](http://vocab.org/relationship/) vocabulary.
- Removed process sections, especially those noting exit criteria and at-risk features.
- Fixed a typo in [deleted](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-deleted) range.
- Added `datetime` and `boolean` to range of [closed](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-closed) property.
- Set the domain of the [first](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-first), [last](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-last), and [current](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-current) properties to [Collection](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-collection).

## C. References

### C.1 Normative references

[BCP47]
- Tags for Identifying Languages. A. Phillips; M. Davis. IETF. September 2009. IETF Best Current Practice. URL: https://tools.ietf.org/html/bcp47 

[RFC2119]
- Key words for use in RFCs to Indicate Requirement Levels. S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119 

[RFC5988]
- Web Linking. M. Nottingham. IETF. October 2010. Proposed Standard. URL: https://tools.ietf.org/html/rfc5988 

[xmlschema11-2]
- W3C XML Schema Definition Language (XSD) 1.1 Part 2: Datatypes. David Peterson; Sandy Gao; Ashok Malhotra; Michael Sperberg-McQueen; Henry Thompson; Paul V. Biron et al. W3C. 5 April 2012. W3C Recommendation. URL: https://www.w3.org/TR/xmlschema11-2/ 

### C.2 Informative references

[HTML5]
- HTML5. Ian Hickson; Robin Berjon; Steve Faulkner; Travis Leithead; Erika Doyle Navara; Theresa O'Connor; Silvia Pfeiffer. W3C. 28 October 2014. W3C Recommendation. URL: https://www.w3.org/TR/html5/