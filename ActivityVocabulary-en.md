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

- 1.1 [Conventions](#11-conventions)

2\. [Core Types](#2-core-types)

3\. [Extended Types](#3-extended-types)

- 3.1 [Activity Types](#31-activity-types)
- 3.2 [Actor Types](#32-actor-types)
- 3.3 [Object and Link Types](#33-object-and-link-types)

4\. [Properties](#4-properties)

5\. [Implementation Notes](#5-implementation-notes)

- 5.1 [Audience Targeting](#51-audience-targeting)
- 5.2 [Representing Relationships Between Entities](#52-representing-relationships-between-entities)
- 5.3 [Representing Places](#53-representing-places)
- 5.4 [Representing Questions](#54-representing-questions)
- 5.5 [Inverse Activities and "Undo"](#55-inverse-activities-and-"undo")
- 5.6 [Mentions, Tags and Other Common Social Microsyntaxes](#56-mentions-tags-and-other-common-social-microsyntaxes)
- 5.7 [Origin and Target](#57-origin-and-target)
- 5.8 [Activity Type Motivating Use Cases](#58-activity-type-motivating-use-cases)

A\. [Non-normative Ontology Definition](#a-non-normative-ontology-definition)

B\. [Changelog](#b-changelog)

C\. [References](#c-references)

- C.1 [Normative references](#c1-normative-references)
- C.2 [Informative references](#c2-informative-references)

## 1. [Introduction](#table-of-contents)

[The Activity Streams 2.0 Core Syntax](https://www.w3.org/TR/activitystreams-core/) defines the JSON syntax for Activity Streams. This document defines the vocabulary properties.

The Activity Streams 2.0 Vocabulary defines a set of abstract types and properties that describe past, present and future Activities. The vocabulary is defined in two parts:

1. A Core set of properties describing the generalized structure of an Activity; and
2. An Extended set of properties that cover specific types of Activities and Artifacts common to many social Web application systems.

While not all Activity Streams 2.0 implementations are expected to implement support for the Extended properties, all implementations *MUST* at least be capable of serializing and deserializing the Extended properties in accordance with the [Activity Streams 2.0 Core Syntax](https://www.w3.org/TR/activitystreams-core/).

The key words "*MUST*", "*MUST NOT*", "*REQUIRED*", "*SHALL*", "*SHALL NOT*", " *SHOULD*", "*SHOULD NOT*", "*RECOMMENDED*", "*MAY*", and "*OPTIONAL*" in this document are to be interpreted as described in [RFC2119].

### 1.1 [Conventions](#1-introduction)

Unless otherwise specified, all properties defined as `xsd:dateTime` values *MUST* conform to the rules defined in Activity Streams 2.0 Core, [Section 2.3](https://www.w3.org/TR/activitystreams-core/#dates).

The examples included in this document use the normative JSON serialization defined by this specification.

## 2. [Core Types](#table-of-contents)

The Activity Vocabulary Core Types provide the basis for the rest of the vocabulary.

Base URI: `https://www.w3.org/ns/activitystreams#`.

The Activity Streams 2.0 Core Types include:

- [Object](#class-object)
- [Link](#class-link)
- [Activity](#class-activity)
- [IntransitiveActivity](#class-intransitiveactivity)
- [Collection](#class-collection)
- [OrderedCollection](#class-orderedcollection)
- [CollectionPage](#class-collectionpage)
- [OrderedCollectionPage](#class-orderedcollectionpage)

#### [Class] [Object](#2-core-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Object`
Notes: | Describes an object of any kind. The Object type serves as the base type for most of the other kinds of objects defined in the Activity Vocabulary, including other Core types such as [Activity](#class-activity), [IntransitiveActivity](#class-intransitiveactivity), [Collection](#class-collection) and [OrderedCollection](#class-orderedcollection).
Disjoint With: | [Link](#class-link)
Properties: | [attachment](#class-attachment) \| [attributedTo](#class-attributedto) \| [audience](#class-audience) \| [content](#class-content) \| [context](#class-context) \| [name](#class-name) \| [endTime](#class-endtime) \| [generator](#class-generator) \| [icon](#class-icon) \| [image](#class-image) \| [inReplyTo](#class-inreplyto) \| [location](#class-location) \| [preview](#class-preview) \| [published](#class-published) \| [replies](#class-replies) \| [startTime](#class-starttime) \| [summary](#class-summary) \| [tag](#class-tag) \| [updated](#class-updated) \| [url](#class-url) \| [to](#class-to) \| [bto](#class-bto) \| [cc](#class-cc) \| [bcc](#class-bcc) \| [mediaType](#class-mediatype) \| [duration](#class-duration)

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

#### [Class] [Link](#2-core-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Link`
Notes: | A Link is an indirect, qualified reference to a resource identified by a URL. The fundamental model for links is established by [ [RFC5988](#rfc5988)]. Many of the properties defined by the Activity Vocabulary allow values that are either instances of [Object](#class-object) or [Link](#class-link). When a [Link](#class-link) is used, it establishes a [qualified relation](http://patterns.dataincubator.org/book/qualified-relation.html) connecting the subject (the containing object) to the resource identified by the [href](#class-href). Properties of the [Link](#class-link) are properties of the reference as opposed to properties of the resource.
Disjoint With: | [Object](#class-object)
Properties: | [href](#class-href) \| [rel](#class-rel) \| [mediaType](#class-mediatype) \| [name](#class-name) \| [hreflang](#class-hreflang) \| [height](#class-height) \| [width](#class-width) \| [preview](#class-preview)

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

#### [Class] [Activity](#2-core-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Activity`
Notes: | An Activity is a subtype of [Object](#class-object) that describes some form of action that may happen, is currently happening, or has already happened. The `Activity` type itself serves as an abstract base type for all types of activities. It is important to note that the `Activity` type itself does not carry any specific semantics about the kind of action being taken.
Extends: | [Object](#class-object)
Properties: | [actor](#class-actor) \| [object](#class-object) \| [target](#class-target) \| [result](#class-result) \| [origin](#class-origin) \| [instrument](#class-instrument) </br> Inherits all properties from [Object](#class-object).

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

#### [Class] [IntransitiveActivity](#2-core-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#IntransitiveActivity`
Notes: | Instances of `IntransitiveActivity` are a subtype of `Activity` representing intransitive actions. The [object](#class-object) property is therefore inappropriate for these activities.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity) except `object`.

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

#### [Class] [Collection](#2-core-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Collection`
Notes: | A `Collection` is a subtype of [Object](#class-object) that represents ordered or unordered sets of [`Object`](#class-object) or [`Link`](#class-link) instances. </br> Refer to the [Activity Streams 2.0 Core](https://www.w3.org/TR/activitystreams-core/#collection) specification for a complete description of the `Collection` type.
Extends: | [Object](#class-object)
Properties: | [totalItems](#class-totalitems) \| [current](#class-current) \| [first](#class-first) \| [last](#class-last) \| [items](#class-items) </br> Inherits all properties from [Object](#class-object).

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

#### [Class] [OrderedCollection](#2-core-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollection`
Notes: | A subtype of [Collection](#class-collection) in which members of the logical collection are assumed to always be strictly ordered.
Extends: | [Collection](#class-collection)
Properties: | Inherits all properties from [Collection](#class-collection).

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

#### [Class] [CollectionPage](#2-core-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#CollectionPage`
Notes: | Used to represent distinct subsets of items from a `Collection`. Refer to the [Activity Streams 2.0 Core](https://www.w3.org/TR/activitystreams-core/#dfn-collectionpage) for a complete description of the `CollectionPage` object.
Extends: | [Collection](#class-collection)
Properties: | [partOf](#class-partof) \| [next](#class-next) \| [prev](#class-prev) </br> Inherits all properties from [Collection](#class-collection).

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

#### [Class] [OrderedCollectionPage](#2-core-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#OrderedCollectionPage`
Notes: | Used to represent ordered subsets of items from an `OrderedCollection`. Refer to the [Activity Streams 2.0 Core](https://www.w3.org/TR/activitystreams-core/#dfn-orderedcollectionpage) for a complete description of the `OrderedCollectionPage` object.
Extends: | [OrderedCollection](#class-orderedcollection) \| [CollectionPage](#class-collectionpage)
Properties: | [startIndex](#class-startindex) </br> Inherits all properties from [OrderedCollection](#class-orderedcollection) and [CollectionPage](#class-collectionpage).

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

## 3. [Extended Types](#table-of-contents)

Base URI: `https://www.w3.org/ns/activitystreams#`.

The Activity Streams 2.0 Extended Types include Activity and Object subtypes that are common to many social Web applications. They are divided into three sets:

- [Activity Types](#31-activity-types)
- [Actor Types](#32-actor-types)
- [Object Types](#33-object-and-link-types)

Support for specific extended vocabulary types is expected to vary, with implementations only selecting the extended types and properties that make sense within the specific context and requirements of those applications. However, to avoid possible interoperability issues, implementations *MUST* avoid using extension types or properties that unduly overlap with or duplicate the extended vocabulary defined here.

### 3.1 [Activity Types](#3-extended-types)

All Activity Types inherit the properties of the base [Activity](#class-activity) type. Some specific Activity Types are subtypes or specializations of more generalized Activity Types (for instance, the [Invite](#class-invite) Activity Type is a more specific form of the [Offer](#class-offer) Activity Type).

The Activity Types include:

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

#### [Class] [Accept](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Accept`
Notes: | Indicates that the `actor` accepts the `object`. The `target` property can be used in certain circumstances to indicate the context into which the `object` has been accepted.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [TentativeAccept](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeAccept`
Notes: | A specialization of Accept indicating that the acceptance is tentative.
Extends: | [Accept](#class-accept)
Properties: | Inherits all properties from [Accept](#class-accept).

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

#### [Class] [Add](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Add`
Notes: | Indicates that the `actor` has added the `object` to the `target`. If the `target` property is not explicitly specified, the target would need to be determined implicitly by context. The `origin` can be used to identify the context from which the `object` originated.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Arrive](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Arrive`
Notes: | An [IntransitiveActivity](#class-intransitiveactivity) that indicates that the `actor` has arrived at the `location`. The `origin` can be used to identify the context from which the `actor` originated. The `target` typically has no defined meaning.
Extends: | [IntransitiveActivity](#class-intransitiveactivity)
Properties: | Inherits all properties fom [IntransitiveActivity](#class-intransitiveactivity).

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

#### [Class] [Create](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Create`
Notes: | Indicates that the `actor` has created the `object`.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Delete](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Delete`
Notes: | Indicates that the `actor` has deleted the `object`. If specified, the `origin` indicates the context from which the `object` was deleted.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).


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

#### [Class] [Follow](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Follow`
Notes: |  Indicates that the `actor` is "following" the `object`. Following is defined in the sense typically used within Social systems in which the actor is interested in any activity performed by or on the object. The `target` and `origin` typically have no defined meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Ignore](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Ignore`
Notes: | Indicates that the `actor` is ignoring the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Join](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Join`
Notes: | Indicates that the `actor` has joined the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Leave](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Leave`
Notes: | Indicates that the `actor` has left the `object`. The `target` and `origin` typically have no meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Like](#3.1-activity-types)

Description| |
--|--
URI: |` https://www.w3.org/ns/activitystreams#Like`
Notes: | Indicates that the `actor` likes, recommends or endorses the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Offer](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Offer`
Notes: | Indicates that the `actor` is offering the `object`. If specified, the `target` indicates the entity to which the `object` is being offered.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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


#### [Class] [Invite](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Invite`
Notes: | A specialization of [Offer](#class-offer) in which the `actor` is extending an invitation for the `object` to the `target`.
Extends: | [Offer](#class-offer)
Properties: | Inherits all properties from [Offer](#class-offer).

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

#### [Class] [Reject](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Reject`
Notes: | Indicates that the `actor` is rejecting the `object`. The `target` and `origin` typically have no defined meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [TentativeReject](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#TentativeReject`
Notes: | A specialization of [Reject](#class-reject) in which the rejection is considered tentative.
Extends: | [Reject](#class-reject)
Properties: | Inherits all properties from [Reject](#class-reject).

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

#### [Class] [Remove](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Remove`
Notes: | Indicates that the `actor` is removing the `object`. If specified, the `origin` indicates the context from which the `object` is being removed.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Undo](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Undo`
Notes: | Indicates that the `actor` is undoing the `object`. In most cases, the `object` will be an [Activity](#class-activity) describing some previously performed action (for instance, a person may have previously "liked" an article but, for whatever reason, might choose to undo that like at some later point in time). </br> The `target` and `origin` typically have no defined meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Update](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Update`
Notes: | Indicates that the `actor` has updated the `object`. Note, however, that this vocabulary does not define a mechanism for describing the actual set of modifications made to `object`. </br> The `target` and `origin` typically have no defined meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [View](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#View`
Notes: | Indicates that the `actor` has viewed the object.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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


#### [Class] [Listen](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Listen`
Notes: | Indicates that the `actor` has listened to the `object`.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Read](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Read`
Notes: | Indicates that the `actor` has read the `object`.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Move](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Move`
Notes: | Indicates that the `actor` has moved `object` from `origin` to `target`. If the `origin` or `target` are not specified, either can be determined by context.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Travel](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Travel`
Notes: | Indicates that the `actor` is traveling to `target` from `origin`. `Travel` is an `IntransitiveObject` whose `actor` specifies the direct object. If the `target` or `origin` are not specified, either can be determined by context.
Extends: | [IntransitiveActivity](#class-intransitiveactivity)
Properties: | Inherits all properties from [IntransitiveActivity](#class-intransitiveactivity).

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

#### [Class] [Announce](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Announce`
Notes: | Indicates that the `actor` is calling the `target`'s attention the `object`. </br> The `origin` typically has no defined meaning.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Block](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Block`
Notes: | Indicates that the `actor` is blocking the `object`. Blocking is a stronger form of [Ignore](#class-ignore). The typical use is to support social systems that allow one user to block activities or content of other users. The `target` and `origin` typically have no defined meaning.
Extends: | [Ignore](#class-ignore)
Properties: | Inherits all properties from [Ignore](#class-ignore).

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

#### [Class] [Flag](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Flag`
Notes: | Indicates that the `actor` is "flagging" the `object`. Flagging is defined in the sense common to many social platforms as reporting content as being inappropriate for any number of reasons.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Dislike](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Dislike`
Notes: | Indicates that the `actor` dislikes the `object`.
Extends: | [Activity](#class-activity)
Properties: | Inherits all properties from [Activity](#class-activity).

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

#### [Class] [Question](#3.1-activity-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Question`
Notes: | Represents a question being asked. Question objects are an extension of [IntransitiveActivity](#class-intransitiveactivity). That is, the Question object is an Activity, but the direct object is the question itself and therefore it would not contain an [object](#class-object) property. </br> Either of the [anyOf](#class-anyof) and [oneOf](#class-oneof) properties *MAY* be used to express possible answers, but a Question object *MUST NOT* have both properties.
Extends: | [IntransitiveActivity](#class-intransitiveactivity).
Properties: | [oneOf](#class-oneof) \| [anyOf](#class-anyof) \| [closed](#class-closed) </br> Inherits all properties from [IntransitiveActivity](#class-intransitiveactivity).

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

### 3.2 [Actor Types](#3-extended-types)

Actor types are [Object](#class-object) types that are capable of performing activities.

The core Actor Types include:

- [Application](#class-application)
- [Group](#class-group)
- [Organization](#class-organization)
- [Person](#class-person)
- [Service](#class-service)


#### [Class] [Application](#3.2-actor-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Application`
Notes: | Describes a software application.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

>Example 42
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Application",
>  "name": "Exampletron 3000"
>}
>```

#### [Class] [Group](#3.2-actor-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Group`
Notes: | Represents a formal or informal collective of Actors.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

>Example 43
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Group",
>  "name": "Big Beards of Austin"
>}
>```

#### [Class] [Organization](#3.2-actor-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Organization`
Notes: | Represents an organization.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

>Example 44
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Organization",
>  "name": "Example Co."
>}
>```

#### [Class] [Person](#3.2-actor-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Person`
Notes: | Represents an individual person.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

>Example 45
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Person",
>  "name": "Sally Smith"
>}
>```

#### [Class] [Service](#3.2-actor-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Service`
Notes: | Represents a service of any kind.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

>Example 46
>
>```json
>{
>  "@context": "https://www.w3.org/ns/activitystreams",
>  "type": "Service",
>  "name": "Acme Web Service"
>}
>```

### 3.3 [Object and Link Types](#3-extended-types)

All Object Types inherit the properties of the base [Object](#class-object) type. Link Types inherit the properties of the base [Link](#class-link) type. Some specific Object Types are subtypes or specializations of more generalized Object Types (for instance, the [Like](#class-like) Type is a more specific form of the [Activity](#class-activity) type).

The Object Types include:

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

The Link Types include:

- [Mention](#class-mention)

#### [Class] [Relationship](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Relationship`
Notes: | Describes a relationship between two individuals. The [subject](#class-subject) and [object](#class-object) properties are used to identify the connected individuals.</br> See [5.2 Representing Relationships Between Entities](#52-representing-relationships-between-entities) for additional information.
Extends: | [Object](#class-object)
Properties: | [subject](#class-subject) \| [object](#class-object) \| [relationship](#class-relationship) </br> Inherits all properties from [Object](#class-object).

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

#### [Class] [Article](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Article`
Notes: | Represents any kind of multi-paragraph written work.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

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

#### [Class] [Document](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Document`
Notes: | Represents a document of any kind.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

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

#### [Class] [Audio](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Audio`
Notes: | Represents an audio document of any kind.
Extends: | [Document](#class-document)
Properties: | Inherits all properties from [Document](#class-document).

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

#### [Class] [Image](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Image`
Notes: | An image document of any kind
Extends: | [Document](#class-document)
Properties: | Inherits all properties from [Document](#class-document).

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

#### [Class] [Video](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Video`
Notes: | Represents a video document of any kind.
Extends: | [Document](#class-document)
Properties: | Inherits all properties from [Document](#class-document).

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

#### [Class] [Note](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Note`
Notes: | Represents a short written work typically less than a single paragraph in length.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

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

#### [Class] [Page](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Page`
Notes: | Represents a Web Page.
Extends: | [Document](#class-document)
Properties: | Inherits all properties from [Document](#class-document).

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

#### [Class] [Event](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Event`
Notes: | Represents any kind of event.
Extends: | [Object](#class-object)
Properties: | Inherits all properties from [Object](#class-object).

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

#### [Class] [Place](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Place`
Notes: | Represents a logical or physical location. See [5.3 Representing Places](#53-representing-places) for additional information.
Extends: | [Object](#class-object)
Properties: | [accuracy](#class-accuracy) \| [altitude](#class-altitude) \| [latitude](#class-latitude) \| [longitude](#class-longitude) \| [radius](#class-radius) \| [units](#class-units) </br> Inherits all properties from [Object](#class-object).

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

#### [Class] [Mention](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Mention`
Notes: | A specialized [Link](#class-link) that represents an @mention.
Extends: | [Link](#class-link)
Properties: | Inherits all properties from [Link](#class-link).

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

#### [Class] [Profile](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Profile`
Notes: | A Profile is a content object that describes another Object, typically used to describe [Actor Type](#32-actor-types) objects. The [describes](#class-describes) property is used to reference the object being described by the profile.
Extends: | [Object](#class-object)
Properties: | [describes](#class-describes) </br> Inherits all properties from [Object](#class-object).

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

#### [Class] [Tombstone](#3.3-object-and-link-types)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#Tombstone`
Notes: | A Tombstone represents a content object that has been deleted. It can be used in [Collection](#class-collection)s to signify that there used to be an object at this position, but it has been deleted.
Extends: | [Object](#class-object)
Properties: | [formerType](#class-formertype) \| [deleted](#class-deleted) </br> Inherits all properties from [Object](#class-object).

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

## 4. [Properties](#table-of-contents)

Base URI: `https://www.w3.org/ns/activitystreams#`.

The common properties include:
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

The "Domain" indicates the type of Object the property term applies to. The "Range" indicates the type of value the property term can have. Certain properties are marked as a "Subproperty Of" another term, meaning that the term is a specialization of the referenced term. For instance, [actor](#class-actor) is a subproperty of [attributedTo](#class-attributedto). Properties marked as being "Functional" can have only one value. Items not marked as "Functional" can have multiple values.

#### [Class] [id](#4-properties)

Description| |
--|--
URI: | `@id`
Notes: | Provides the globally unique identifier for an [Object](#class-object) or [Link](#class-link).
Domain: | [Object](#class-object) \| [Link](#class-link)
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

#### [Class] [type](#4-properties)

Description| |
--|--
URI: | `@type`
Notes: | Identifies the [Object](#class-object) or [Link](#class-link) type. Multiple values may be specified.
Domain: | [Object](#class-object) \| [Link](#class-link)
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

#### [Class] [actor](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#actor`
Notes: | Describes one or more entities that either performed or are expected to perform the activity. Any single activity can have multiple `actor`s. The `actor` *MAY* be specified using an indirect [Link](#class-link).
Domain: | [Activity](#class-activity)
Range: | [Object](#class-object) \| [Link](#class-link)
Subproperty Of: | [attributedTo](#class-attributedto)

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

#### [Class] [attachment](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#attachment`
Notes: | Identifies a resource attached or related to an object that potentially requires special handling. The intent is to provide a model that is at least semantically similar to attachments in email.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [attributedTo](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#attributedTo`
Notes: | Identifies one or more entities to which this object is attributed. The attributed entities might not be Actors. For instance, an object might be attributed to the completion of another activity.
Domain: | [Link](#class-link) \| [Object](#class-object)
Range: | [Link](#class-link) \| [Object](#class-object)

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

#### [Class] [audience](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#audience`
Notes: | Identifies one or more entities that represent the total population of entities for which the object can considered to be relevant.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [bcc](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#bcc`
Notes: | Identifies one or more Objects that are part of the private secondary audience of this Object.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [bto](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#bto`
Notes: | Identifies an Object that is part of the private primary audience of this Object.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [cc](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#cc`
Notes: | Identifies an Object that is part of the public secondary audience of this Object.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [context](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#context`
Notes: | Identifies the context within which the object exists or an activity was performed.</br> The notion of "context" used is intentionally vague. The intended function is to serve as a means of grouping objects and activities that share a common originating context or purpose. An example could be all activities relating to a common project or event.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [current](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#current`
Notes: | In a paged [Collection](#class-collection), indicates the page that contains the most recently updated member items.
Domain: | [Collection](#class-collection)
Range: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
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

#### [Class] [first](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#first`
Notes: | In a paged [Collection](#class-collection), indicates the furthest preceeding page of items in the collection.
Domain: | [Collection](#class-collection)
Range: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
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

#### [Class] [generator](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#generator`
Notes: | Identifies the entity (e.g. an application) that generated the object.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [icon](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#icon`
Notes: | Indicates an entity that describes an icon for this object. The image should have an aspect ratio of one (horizontal) to one (vertical) and should be suitable for presentation at a small size.
Domain: | [Object](#class-object)
Range: | [Image](#class-image) \| [Link](#class-link)

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

#### [Class] [image](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#image`
Notes: | Indicates an entity that describes an image for this object. Unlike the icon property, there are no aspect ratio or display size limitations assumed.
Domain: | [Object](#class-object)
Range: | [Image](#class-image) \| [Link](#class-link)

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

#### [Class] [inReplyTo](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#inReplyTo`
Notes: | Indicates one or more entities for which this object is considered a response.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [instrument](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#instrument`
Notes: | Identifies one or more objects used (or to be used) in the completion of an [Activity](#class-activity).
Domain: | [Activity](#class-activity)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [last](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#last`
Notes: | In a paged [Collection](#class-collection), indicates the furthest proceeding page of the collection.
Domain: | [Collection](#class-collection)
Range: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
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

#### [Class] [location](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#location`
Notes: | Indicates one or more physical or logical locations associated with the object.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [items](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#items`
Notes: | Identifies the items contained in a collection. The items might be ordered or unordered.
Domain: | [Collection](#class-collection)
Range: | [Object](#class-object) \| [Link](#class-link) \| Ordered List of [ [Object](#class-object) \| [Link](#class-link) ]

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

#### [Class] [oneOf](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#oneOf`
Notes: | Identifies an exclusive option for a Question. Use of `oneOf` implies that the Question can have only a single answer. To indicate that a Question can have multiple answers, use [anyOf](#class-anyof).
Domain: | [Question](#class-question)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [anyOf](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#anyOf`
Notes: | Identifies an inclusive option for a Question. Use of `anyOf` implies that the Question can have multiple answers. To indicate that a Question can have only one answer, use [oneOf](#class-oneof).
Domain: | [Question](#class-question)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [closed](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#closed`
Notes: | Indicates that a question has been closed, and answers are no longer accepted.
Domain: | [Question](#class-question)
Range: | [Object](#class-object) \| [Link](#class-link) \| `xsd:dateTime` \| `xsd:boolean`

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

#### [Class] [origin]

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#origin`
Notes: | Describes an indirect object of the activity from which the activity is directed. The precise meaning of the origin is the object of the English preposition "from". For instance, in the activity "John moved an item to List B from List A", the origin of the activity is "List A".
Domain: | [Activity](#class-activity)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [next](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#next`
Notes: | In a paged [Collection](#class-collection), indicates the next page of items.
Domain: | [CollectionPage](#class-collectionpage)
Range: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
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

#### [Class] [object](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#object`
Notes: | When used within an [Activity](#class-activity), describes the direct object of the activity. For instance, in the activity "John added a movie to his wishlist", the object of the activity is the movie added.</br> When used within a [Relationship](#class-relationship) describes the entity to which the [subject](#class-subject) is related.
Domain: | [Activity](#class-activity) \| [Relationship](#class-relationship)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [prev](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#prev`
Notes: | In a paged [Collection](#class-collection), identifies the previous page of items.
Domain: | [CollectionPage](#class-collectionpage)
Range: | [CollectionPage](#class-collectionpage) \| [Link](#class-link)
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

#### [Class] [preview](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#preview`
Notes: | Identifies an entity that provides a preview of this object.
Domain: | [Link](#class-link) \| [Object](#class-object)
Range: | [Link](#class-link) \| [Object](#class-object)

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

#### [Class] [result](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#result`
Notes: | Describes the result of the activity. For instance, if a particular action results in the creation of a new resource, the result property can be used to describe that new resource.
Domain: | [Activity](#class-activity)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [replies](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#replies`
Notes: | Identifies a [Collection](#class-collection) containing objects considered to be responses to this object.
Domain: | [Object](#class-object)
Range: | [Collection](#class-collection)
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

#### [Class] [tag](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#tag`
Notes: | One or more "tags" that have been associated with an objects. A tag can be any kind of Object. The key difference between `attachment` and `tag` is that the former implies association by inclusion, while the latter implies associated by reference.
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [target](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#target`
Notes: | Describes the indirect object, or target, of the activity. The precise meaning of the target is largely dependent on the type of action being described but will often be the object of the English preposition "to". For instance, in the activity "John added a movie to his wishlist", the target of the activity is John's wishlist. An activity can have more than one target.
Domain: | [Activity](#class-activity)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [to](#4-properties)

Description| |
--|--
URI: |` https://www.w3.org/ns/activitystreams#to`
Notes: | Identifies an entity considered to be part of the public primary audience of an Object
Domain: | [Object](#class-object)
Range: | [Object](#class-object) \| [Link](#class-link)

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

#### [Class] [url](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#url`
Notes: | Identifies one or more links to representations of the object
Domain: | [Object](#class-object)
Range: | `xsd:anyURI` \| [Link](#class-link)

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

#### [Class] [accuracy](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#accuracy`
Notes: | Indicates the accuracy of position coordinates on a [Place](#class-place) objects. Expressed in properties of percentage. e.g. "94.0" means "94.0% accurate".
Domain: | [Place](#class-place)
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

#### [Class] [altitude](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#altitude`
Notes: | Indicates the altitude of a place. The measurement units is indicated using the [units](#class-units) property. If [units](#class-units) is not specified, the default is assumed to be "`m`" indicating meters.
Domain: | [Object](#class-object)
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

#### [Class] [content](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#content`
Notes: | The content or textual representation of the Object encoded as a JSON string. By default, the value of `content` is HTML. The [mediaType](#class-mediatype) property can be used in the object to indicate a different content type. </br> The content *MAY* be expressed using multiple language-tagged values.
Domain: | [Object](#class-object)
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

#### [Class] [name](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#name`
Notes: | A simple, human-readable, plain-text name for the object. HTML markup *MUST NOT* be included. The name *MAY* be expressed using multiple language-tagged values.
Domain: | [Object](#class-object) \| [Link](#class-link)
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

#### [Class] [duration](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#duration`
Notes: | When the object describes a time-bound resource, such as an audio or video, a meeting, etc, the [duration](#class-duration) property indicates the object's approximate duration. The value *MUST* be expressed as an `xsd:duration` as defined by [ [xmlschema11-2](#xmlschema11-2)], section 3.3.6 (e.g. a period of 5 seconds is represented as "`PT5S`").
Domain: | [Object](#class-object)
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

#### [Class] [height](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#height`
Notes: | On a [Link](#class-link), specifies a hint as to the rendering height in device-independent pixels of the linked resource.
Domain: | [Link](#class-link)
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

#### [Class] [href](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#href`
Notes: | The target resource pointed to by a [Link](#class-link).
Domain: | [Link](#class-link)
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

#### [Class] [hreflang](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#hreflang`
Notes: | Hints as to the language used by the target resource. Value *MUST* be a [[BCP47](#BCP47)] Language-Tag.
Domain: | [Link](#class-link)
Range: | [[BCP47](#BCP47)] Language Tag
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

#### [Class] [partOf](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#partOf`
Notes: | Identifies the [Collection](#class-collection) to which a [CollectionPage](#class-collectionpage) objects items belong.
Domain: | [CollectionPage](#class-collectionpage)
Range: | [Link](#class-link) \| [Collection](#class-collection)
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

#### [Class] [latitude](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#latitude`
Notes: | The latitude of a place
Domain: | [Place](#class-place)
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

#### [Class] [longitude](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#longitude`
Notes: | The longitude of a place
Domain: | [Place](#class-place)
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

#### [Class] [mediaType](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#mediaType`
Notes: | When used on a [Link](#class-link), identifies the MIME media type of the referenced resource. </br> When used on an [Object](#class-object), identifies the MIME media type of the value of the [content](#class-content) property. If not specified, the [content](#class-content) property is assumed to contain `text/html` content.
Domain: | [Link](#class-link) \| [Object](#class-object)
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

#### [Class] [endTime](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#endTime`
Notes: | The date and time describing the actual or expected ending time of the object. When used with an [Activity](#class-activity) object, for instance, the [endTime](#class-endtime) property specifies the moment the activity concluded or is expected to conclude.
Domain: | [Object](#class-object)
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

#### [Class] [published](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#published`
Notes: | The date and time at which the object was published
Domain: | [Object](#class-object)
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

#### [Class] [startTime](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#startTime`
Notes: | The date and time describing the actual or expected starting time of the object. When used with an [Activity](#class-activity) object, for instance, the [startTime](#class-starttime) property specifies the moment the activity began or is scheduled to begin.
Domain: | [Object](#class-object)
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

#### [Class] [radius](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#radius`
Notes: | The radius from the given latitude and longitude for a Place. The units is expressed by the [units](#class-units) property. If [units](#class-units) is not specified, the default is assumed to be "`m`" indicating "meters".
Domain: | [Place](#class-place)
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

#### [Class] [rel](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#rel`
Notes: | A link relation associated with a [Link](#class-link). The value *MUST* conform to both the [HTML5](#HTML5) and [RFC5988](#RFC5988) "link relation" definitions. </br> In the [HTML5](#HTML5), any string not containing the "space" U+0020, "tab" (U+0009), "LF" (U+000A), "FF" (U+000C), "CR" (U+000D) or "," (U+002C) characters can be used as a valid link relation.
Domain: | [Link](#class-link)
Range: | [RFC5988](#RFC5988) or [HTML5](#HTML5) Link Relation

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

#### [Class] [startIndex](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#startIndex`
Notes: | A non-negative integer value identifying the relative position within the logical view of a strictly ordered collection.
Domain: | [OrderedCollectionPage](#class-orderedcollectionpage)
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

#### [Class] [summary](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#summary`
Notes: | A natural language summarization of the object encoded as HTML. Multiple language tagged summaries *MAY* be provided.
Domain: | [Object](#class-object)
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

#### [Class] [totalItems](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#totalItems`
Notes: | A non-negative integer specifying the total number of objects contained by the logical view of the collection. This number might not reflect the actual number of items serialized within the [Collection](#class-collection) object instance.
Domain: | [Collection](#class-collection)
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

#### [Class] [units](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#units`
Notes: | Specifies the measurement units for the [radius](#class-radius) and [altitude](#class-altitude) properties on a [Place](#class-place) object. If not specified, the default is assumed to be "`m`" for "meters".
Domain: | [Place](#class-place)
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

#### [Class] [updated](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#updated`
Notes: | The date and time at which the object was updated
Domain: | [Object](#class-object)
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

#### [Class] [width](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#width`
Notes: | On a [Link](#class-link), specifies a hint as to the rendering width in device-independent pixels of the linked resource.
Domain: | [Link](#class-link)
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

#### [Class] [subject](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#subject`
Notes: | On a [Relationship](#class-relationship) object, the `subject` property identifies one of the connected individuals. For instance, for a Relationship object describing "John is related to Sally", `subject` would refer to John.
Domain: | [Relationship](#class-relationship)
Range: | [Link](#class-link) \| [Object](#class-object)
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

#### [Class] [relationship](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#relationship`
Notes: | On a [Relationship](#class-relationship) object, the `relationship` property identifies the kind of relationship that exists between [subject](#class-subject) and [object](#class-object).
Domain: | [Relationship](#class-relationship)
Range: | [Object](#class-object)

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

#### [Class] [describes](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#describes`
Notes: | On a [Profile](#class-profile) object, the `describes` property identifies the object described by the Profile.
Domain: | [Profile](#class-profile)
Range: | [Object](#class-object)
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

#### [Class] [formerType](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#formerType`
Notes: | On a [Tombstone](#class-tombstone) object, the `formerType` property identifies the type of the object that was deleted.
Domain: | [Tombstone](#class-tombstone)
Range: | [Object](#class-object)
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

#### [Class] [deleted](#4-properties)

Description| |
--|--
URI: | `https://www.w3.org/ns/activitystreams#deleted`
Notes: | On a [Tombstone](#class-tombstone) object, the `deleted` property is a timestamp for when the object was deleted.
Domain: | [Tombstone](#class-tombstone)
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

## 5. [Implementation Notes](#table-of-contents)

### 5.1 [Audience Targeting](#5-implementation-notes)

Conceptually, every Object has both a Primary and Secondary audience. The Primary audience consists of those entities directly involved or owning the object. The Secondary audience consists of the collection of entities sharing an interest in the object but who might not be directly involved (e.g."followers").

For instance, suppose a social network of three individuals: Bob, Joe and Jane. Bob and Joe are each friends with Jane but are not friends with one another. Bob has chosen to "follow" activities for which Jane is directly involved. Jane shares a file with Joe.

In this example, Jane and Joe are each directly involved in the file sharing activity and together make up the Primary Audience for that event. Bob, having an interest in activities involving Jane, is the Secondary Audience. Knowing this, a system that produces or consumes the activity can intelligently notify each person of the event.

While there are means (based on the action type, actor, object and target of the activity) to infer the primary audience for many types of activities, heuristics do not work in every case and do not provide a means of identifying the secondary audience. The [to](#class-to), [cc](#class-cc), [bto](#class-bto) and [bcc](#class-bcc) properties *MAY* be used within an Object to explicitly identify the Primary and Secondary audiences.

The prototypical use case for an Object containing these properties is the publication and redistribution of objects through an intermediary. That is, an event source generates the object and publishes it to the intermediary which determines a subset of items to display to specific individual users or groups. Such a determination can be made, in part, by identifying the Primary and Secondary Audiences for each object.

When the event source generates the object and specifies values for the `to` and `cc` fields, the intermediary *SHOULD* redistribute that object with the values of those fields intact, allowing any processor to see who the object has been targeted to. This is precisely the same model used by the `to` and `cc` fields in email systems.

There are situations, however, in which disclosing the identity of specific members of the audience may be inappropriate. For instance, a user may not wish to let other users know that they are interested in various topics, individuals or types of events. To support this option, an implementation generating an object *MAY* use the `bto` and `bcc` properties to list entities to whom the object should be privately targeted. When an intermediary receives an object containing these properties, it *MUST* remove those values prior to redistributing the object. The intent is that systems *MUST* consider entities listed within the `bto` and `bcc` properties as part of the Primary and Secondary audience but *MUST NOT* disclose that fact to any other party.

Audience targeting information included within an Object only describes the intent of the object creator. With clear exception given to the appropriate handling of `bto` and `bcc`, this specification leaves it up to implementations to determine how the audience targeting information is used.

#### 5.1.1 [Audience and Context](#51-audience-targeting)

_This section is non-normative._

Activities are rarely isolated events. Often, multiple individual activities will be performed around a similar context or audience. For instance, a collaborators working on a shared project might perform multiple related activities in the process of achieving some goal. Such activities can be logically grouped together using the [context](#class-context) property, and scoped to a particular audience using the [audience](#class-audience) property.

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

### 5.2 [Representing Relationships Between Entities](#5-implementation-notes)

The [Relationship](#class-relationship) object is used to represent relationships between individuals. It can be used, for instance, to describe that one person is a friend of another, or that one person is a member of a particular organization. The intent of modeling Relationship in this way is to allow descriptions of activities that operate on the relationships in general, and to allow representation of Collections of relationships.

For instance, many social systems have a notion of a "friends list". These are the collection of individuals that are directly connected within a person's social graph. Suppose we have a user, Sally, with direct relationships to users Joe and Jane. Sally follows Joe's updates while Sally and Jane have a mutual relationship.

Using the [Relationship](#class-relationship) object, we can model these relationships as:

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

The [relationship](#class-relationship) property specifies the kind of relationship that exists between the two individuals identified by the [subject](#class-subject) and [object](#class-object) properties. Used together, these three properties form what is commonly known as a " [reified statement](http://patterns.dataincubator.org/book/reified-statement.html)" where [subject](#class-subject) identifies the subject, [relationship](#class-relationship) identifies the predicate, and [object](#class-object) identifies the object.

While use of reified statements can be problematic and confusing in certain situations, their use within the Activity Streams vocabulary to describe relationships provides a straightforward mechanism of describing changes to an individual's social graph. For instance, to indicate that Sally has created a new relationship to user Matt, an implementer can use the [Relationship](#class-relationship) object together with the [Create](#class-create) activity:

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

#### 5.2.1 [Modeling "friend requests"](#52-representing-relationships-between-entities)

_This section is non-normative._

One common use case for many social platforms is the establishment of symmetrical "friend" relationships, in which one user initially extends a request to another user to establish a new connection. Once the connection is made, both users automatically begin receiving notifications about activities performed by the other, and the established relationship becomes visible in either user's "friends list".

The initial "friend request" can be modeled by composing the [Offer](#class-offer) and [Relationship](#class-relationship) object types as in the following example:

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

1. The optional [result](#class-result) property is used within the `Accept` activity to identify the additional activities that occurred as a result of the accept.
2. The optional [context](#class-context) property is used to relate the various activities back to a common reference point, which in this example is the relationship being established. The `context` allows an implementation to efficiently group related activities together for display or analytic purposes.

### 5.3 [Representing Places](#5-implementation-notes)

_This section is non-normative._

The [Place](#class-place) object is used to represent both physical and logical locations. While numerous existing vocabularies exist for describing locations in a variety of ways, inconsistencies and incompatibilities between those vocabularies make it difficult to achieve appropriate interoperability between implementations. The `Place` object is included within the Activity vocabulary to provide a minimal, interoperable starting point for describing locations consistently across Activity Streams 2.0 implementations.

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

Or, by [longitude](#class-longitude) and [latitude](#class-latitude):

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

The `Place` object can also describe an area around a given point using the [radius](#class-radius) property, the [altitude](#class-altitude) of the location, and a degree of [accuracy](#class-accuracy).

While publishers are not required to use these specific properties and *MAY* make use of other mechanisms for describing locations, consuming implementations that support the [Place](#class-place) object *MUST* support the use of these properties.

### 5.4 [Representing Questions](#5-implementation-notes)

_This section is non-normative._

The [Question](#class-question) object can be used to express various types of inquiries.

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

Multiple-choice questions or "polls" are also supported using either the [oneOf](#class-oneof) or [anyOf](#class-anyof) properties:

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

Responses to questions are expressed as [Objects](#class-object) containing an [inReplyto](#class-inreplyto) property referencing the Question.

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

Because [Question](#class-question) objects are also instances of [Activity](#class-activity), the [result](#class-result) property can be used to express the results or outcome of the Question (as appropriate):

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

### 5.5 [Inverse Activities and "Undo"](#5-implementation-notes)

_This section is non-normative._

Several of the core [Activity types](#31-activity-types) are defined as natural inversions of one another. These include:

- [Accept](#class-accept) and [Reject](#class-reject),
- [Arrive](#class-arrive) and [Leave](#class-leave),
- [Join](#class-join) and [Leave](#class-leave),
- [Create](#class-create) and [Delete](#class-delete),
- [Like](#class-like) and [Dislike](#class-dislike)

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

The [Undo](#class-undo) activity type is defined to provide the specific ability to undo or cancel out a prior activity. The appropriate interpretation for the following, then, is that Sally liked John's note at one point but has explicitly redacted that like later on.

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

### 5.6 [Mentions, Tags and Other Common Social Microsyntaxes](#5-implementation-notes)

_This section is non-normative._

Many social software systems use special text-based microsyntaxes that allow users to define special addressing for notifications, linking, or categorization within objects. For example, including text such as "`@username`" within an object's content will often route the object to a special "mentions" or "inbox" stream for a particular user. Likewise, including text such as " `#topic`" within the object's content will often mark the object as being related to the topic "`topic`". Such mechanisms are commonly referred to as "mentions" and "hashtags", respectively.

While such microsyntaxes *MAY* be used within the values of the [content](#class-content), [name](#class-name), and [summary](#class-summary) properties on an Activity Streams [Object](#class-object), implementations *SHOULD NOT* be required to parse the values of those properties in order to determine the appropriate routing of notifications, categorization or linking between objects. Instead, publishers *SHOULD* make appropriate use of the vocabulary terms provided specifically for these purposes.

For example, suppose that an author wishes to send a note of thanks to another user named "@sally" with a hashtag of "#givingthanks". A typical way this message would appear within the content of a note is shown below:

<div align="center"><em>
Figure 1 A simple note with a mention an a hashtag:
</em></div>

"Thank you @sally for all your hard work! #givingthanks"

A typical social software implementation would typically render such a content such that "`@sally`" is replaced with a hyperlink to "@sally"'s social profile page and "`#givingthanks`" is replaced with a hyperlink to a listing of other notes that have been "tagged" with the same topic. Most implementations would also send a special notification to sally letting her know that a note mentioning her has been created.

The following illustrates an equivalent Activity Streams [Note](#class-note) object:

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

The `to` property indicates that the user "@sally" is to be considered part of the [primary audience](#51-audience-targeting) of the note and should therefore receive notification. The `tag` property associates the Note with a reference to " `http://example.org/tags/givingthanks`". Note that the `content` still includes the "`@sally`" and " `#givingthanks`" microsyntaxes but that consuming implementations are not required to parse those in order to make the appropriate associations.

In the case a publisher wishes to indicate a mention without an associated notification, the publisher can use the [Mention](#class-mention) object type as a value of the [tag](#class-tag) property.

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

### 5.7 [Origin and Target](#5-implementation-notes)

The [origin](#class-origin) and [target](#class-target) properties of an Activity respectively identify the entities from which and to which the action is directed. For instance, in the English statement, "Sally moved the file from Folder A to Folder B", the `origin` is "Folder A" and the `target` is "Folder B". This activity is illustrated in the example below:

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

### 5.8 [Activity Type Motivating Use Cases](#5-implementation-notes)

_This section is non-normative._

The [Activity types](#31-activity-types) defined in this vocabulary have been primarily selected to address the commonly implemented social use cases described below.

#### 5.8.1 [Content Management](#58-activity-type-motivating-use-cases)

The Content Management use case primarily deals with activities that involve the creation, modification or deletion of content. This includes, for instance, activities such as "John created a new note", "Sally updated an article", and "Joe deleted the photo".

Relevant Activities:

- [Create](#class-create)
- [Delete](#class-delete)
- [Update](#class-update)

#### 5.8.2 [Collection Management](#58-activity-type-motivating-use-cases)

The Collection Management use case primarily deals with activities involving the management of content within collections. Examples of collections include things like folders, albums, friend lists, etc. This includes, for instance, activities such as "Sally added a file to Folder A", "John moved the file from Folder A to Folder B", etc.

Relevant Activities:

- [Add](#class-add)
- [Move](#class-move)
- [Remove](#class-remove)

#### 5.8.3 [Reactions](#58-activity-type-motivating-use-cases)

The Reactions use case primarily deals with reactions to content. This can include activities such as liking or disliking content, ignoring updates, flagging content as being inappropriate, accepting or rejecting objects, etc.

Relevant Activities:

- [Accept](#class-accept)
- [Block](#class-block)
- [Dislike](#class-dislike)
- [Flag](#class-flag)
- [Ignore](#class-ignore)
- [Like](#class-like)
- [Reject](#class-reject)
- [TentativeAccept](#class-tentativeaccept)
- [TentativeReject](#class-tentativereject)

#### 5.8.4 [Event RSVP](#58-activity-type-motivating-use-cases)

The Event RSVP use case primarily deals with invitations to events and RSVP type responses.

Relevant Activities:

- [Accept](#class-accept)
- [Ignore](#class-ignore)
- [Invite](#class-invite)
- [Reject](#class-reject)
- [TentativeAccept](#class-tentativeaccept)
- [TentativeReject](#class-tentativereject)

#### 5.8.5 [Group Management](#58-activity-type-motivating-use-cases)

The Group Management use case primarily deals with management of groups. It can include, for instance, activities such as "John added Sally to Group A", "Sally joined Group A", "Joe left Group A", etc.

Relevant Activities:

- [Add](#class-add)
- [Join](#class-join)
- [Leave](#class-leave)
- [Remove](#class-remove)

#### 5.8.6 [Content Experience](#58-activity-type-motivating-use-cases)

The Content Experience use case primarily deals with describing activities involving listening to, reading, or viewing content. For instance, "Sally read the article", "Joe listened to the song".

Relevant Activities:

- [Listen](#class-listen)
- [Read](#class-read)
- [View](#class-view)

#### 5.8.7 [Geo-Social Events](#58-activity-type-motivating-use-cases)

The Geo-Social Events use case primarily deals with activities involving geo-tagging type activities. For instance, it can include activities such as "Joe arrived at work", "Sally left work", and "John is travel from home to work".

Relevant Activities:

- [Arrive](#class-arrive)
- [Leave](#class-leave)
- [Travel](#class-travel)

#### 5.8.8 [Notification](#58-activity-type-motivating-use-cases)

The Notification use case primarily deals with calling attention to particular objects or notifications.

Relevant Activities:

- [Announce](#class-announce)

#### 5.8.9 [Questions](#58-activity-type-motivating-use-cases)

the Questions use case primarily deals with representing inquiries of any type. See [5.4 Representing Questions](#54-representing-questions) for more information.

Relevant Activities:

- [Question](#class-question)

#### 5.8.10 [Relationship Management](#58-activity-type-motivating-use-cases)

The Relationship Management use case primarily deals with representing activities involving the management of interpersonal and social relationships (e.g. friend requests, management of social network, etc). See [5.2 Representing Relationships Between Entities](#52-representing-relationships-between-entities) for more information.

Relevant Activities:

- [Accept](#class-accept)
- [Add](#class-add)
- [Block](#class-block)
- [Create](#class-create)
- [Delete](#class-delete)
- [Follow](#class-follow)
- [Ignore](#class-ignore)
- [Invite](#class-invite)
- [Reject](#class-reject)

#### 5.8.11 [Negating Activity](#58-activity-type-motivating-use-cases)

The Negating Activity use case primarily deals with the ability to redact previously completed activities. See [5.5 Inverse Activities and "Undo"](#55-inverse-activities-and-"undo") for more information.

Relevant Activities:

- [Undo](#class-undo)

#### 5.8.12 [Offers](#58-activity-type-motivating-use-cases)

The Offers use case deals with activities involving offering one object to another. It can include, for instance, activities such as "Company A is offering a discount on purchase of Product Z to Sally", "Sally is offering to add a File to Folder A", etc.

Relevant Activities:

- [Offer](#class-offer)

## A. [Non-normative Ontology Definition](#table-of-contents)

_This section is non-normative._

A non-normative turtle definition of the Activity Streams 2.0 vocabulary is provided [here](https://www.w3.org/ns/activitystreams-owl) and/or at [the namespace](https://www.w3.org/ns/activitystreams) as a convenience for implementers wishing to use RDF mechanisms for processing Activity Streams 2.0. Note, however, that this document provides the normative definition of the Activity Streams 2.0 vocabulary.

## B. [Changelog](#table-of-contents)

_This section is non-normative._

The following notable changes have been made to this document since the previous candidate recommendation of [2016-12-15](https://www.w3.org/TR/2016/CR-activitystreams-vocabulary-20161215/#changelog).

- Removed the four normative [relationship](#class-relationship) values for lack of implementation. Changed examples to use terms from the [Relationship](http://vocab.org/relationship/) vocabulary.
- Removed process sections, especially those noting exit criteria and at-risk features.
- Fixed a typo in [deleted](#class-deleted) range.
- Added `datetime` and `boolean` to range of [closed](#class-closed) property.
- Set the domain of the [first](#class-first), [last](#class-last), and [current](#class-current) properties to [Collection](#class-collection).

## C. [References](#table-of-contents)

### C.1 [Normative references](#c-references)

#### [BCP47]

- Tags for Identifying Languages. A. Phillips; M. Davis. IETF. September 2009. IETF Best Current Practice. URL: https://tools.ietf.org/html/bcp47 

#### [RFC2119]

- Key words for use in RFCs to Indicate Requirement Levels. S. Bradner. IETF. March 1997. Best Current Practice. URL: https://tools.ietf.org/html/rfc2119 

#### [RFC5988]

- Web Linking. M. Nottingham. IETF. October 2010. Proposed Standard. URL: https://tools.ietf.org/html/rfc5988

#### [xmlschema11-2]

- W3C XML Schema Definition Language (XSD) 1.1 Part 2: Datatypes. David Peterson; Sandy Gao; Ashok Malhotra; Michael Sperberg-McQueen; Henry Thompson; Paul V. Biron et al. W3C. 5 April 2012. W3C Recommendation. URL: https://www.w3.org/TR/xmlschema11-2/

### C.2 [Informative references](#c-references)

#### [HTML5]

- HTML5. Ian Hickson; Robin Berjon; Steve Faulkner; Travis Leithead; Erika Doyle Navara; Theresa O'Connor; Silvia Pfeiffer. W3C. 28 October 2014. W3C Recommendation. URL: https://www.w3.org/TR/html5/