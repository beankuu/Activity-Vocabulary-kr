[목차로 돌아가기](ActivityVocabularyContents.md)

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
