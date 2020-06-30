[README로 돌아가기](README.md)

# Activity Vocabulary 문서 한글 번역 가이드라인

- 임시로 작성한 문서입니다.
- ActivityPub / ActivityStreams2.0 번역 가이드라인들과 내용이 유사합니다.

## 1. 번역 단어관련

- 타 문서에서는 음차로 번역하나, 이 문서에서는 한글로 번역한 단어가 다수 존재할수도 있습니다.

원문 | 번역 | 비고
-- | -- | --
normative | 표준 | ActivityPub에서는 '규범' 으로도 번역하였습니다
entity | 개체
section | 문단
disjoint of | 서로소
extends | 상속함

### 1-1. 음차를 사용하는 번역

원문 | 번역 | 비고
-- | -- | --
Note | 노트 |
Microsyntax(es) | 마이크로신택스(들)
Ontology | 온톨로지 | ChapterA에서만 짤막하게 등장합니다

### 1-2. 원문 그대로 사용하는 번역

원문 | 비고
-- | --
Activity Streams |

1-2의 표 외에도 대문자로 시작하는 단어의 경우 최대한 원어를 사용했습니다.

## 2. 번역 일관성

@ RFC2119 (Chapter1에 정의되어 있습니다)
- *반드시 (MUST)*
- *절대 하지 말아야 (MUST NOT)*
- *요구한다 (REQUIRED)*"
- *할 것이다 (SHALL)*
- *해서는 안될 것이다 (SHALL NOT)*
- *해야 한다 (SHOULD)*
- *해서는 안된다 (SHOULD NOT)*
- *권장한다 (RECOMMENDED)*
- *할 수도 있다 (MAY)*
- *선택적으로 (OPTIONAL)*

## 3. markdown 등 그 외 관련

@ 원문에 취소선을 적용하지 않았습니다

@ [종합본](ActivityVocabulary.md)에서는

```text
번역본
```

양식을 사용했습니다.

@ 개별 챕터 번역본에서는

```text
원문
번역본
주석
```

양식을 사용했습니다.

@ 예시 관련
- 양식:
> 예시 N번
>
>```json
>{
>   "name": "번역할 문장만"
>}
>```

@ `[WORD](LINK)`
- WORD
  - {번역한 단어}를 사용하되, 의미전달이 애매할 경우는 {번역(원문)}
- LINK
  - 개별 챕터 번역본에서는 원문 링크를 따르기
    - 예: `[Accept](https://www.w3.org/TR/activitystreams-vocabulary/#dfn-accept)`
  - [종합본](ActivityVocabulary.md)에는 최대한 내부링크로
    - 예: `[Accept](#[Class]-Accept)`

@ \`...\`
- 단어 자체가 강조된 부분이므로 번역하지 않고 `백틱`안에 원어 그대로 적기
- 간혹가다 "`object`를... object를..." 처럼 백틱된 단어가 한 문장/문단안에 있는 경우
  - "`object`를... 객체(object)를..." 처럼 해당 `백틱` 이후 첫 등장하는 단어에 번역(원문)으로 적기

@ 주석 양식
- `[//TODO]: # "TODO"`
- `[//Comment]: # "Comment"`
- `[//Link]: # "Link"`
