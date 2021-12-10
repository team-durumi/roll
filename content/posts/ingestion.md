---
title: "입수"
date: 2021-12-07T16:48:00+09:00
draft: true
---

## 전제, 가설

전통적인 기록 관리개념이 있던 없던 사람을 수많은 자료를 한꺼번에 메모리(머리)에 올릴 수 없다.
디지털 파일을 차곡차고 쌓거나 원래 있던 엉망진창 많은 파일을 정리하려고 할 때
다시 찾아볼 수 있도록 기억의 단위(디렉토리, access to memory)를
만들어 유사한 자료나 파일을 넣는 방식으로 구조화해서 정리하게 된다.
그런데 폴더 위계 구조는 정리하는 사람의 정신 상태에 따라 다르고 임의적이다.
어쨌든 원천 데이터 형식은 디렉토리, 파일이라고 가정할 때,
우리가 여기서 얻을 수 있는 정보는 기록 정보의 구조, 분류 방식(책으로 치면 목차?),
파일(본문내용 및 메타데이터?)이다.

## 기본 개념

- 아이템 item: 하나의 식별자를 가지고 사람이 다시 조회해야하는 주요 기록 정보를 말한다.
- (다중)분류체계 classification: 수많은 기록들을 정리하고, 바라보고, 분류하는 기준이다.
- 기술계층 aggregation: 기록의 덩어리 행정적 목적? 행정 단위에 맞게 대강의 양을 측정하기 위한 묶음?
- tree -- branch(trail) -- leaf 가지에는 N개의 나무잎이 달려있지만 잎에는 더 달리는게 없다.
- 컴포넌트 component: 아이템 item에 첨부하는 디지털 파일들?

## 질문

### 아이템은 디렉토리인가 파일인가?

```
# database
leaf 디렉토리 => item 
leaf 디렉토리/files => component with item_id 

# markdown
leaf 디렉토리/_index.md
leaf 디렉토리/{{ item_id }}-{{ seq }}.md ?
```

## 파일 구조 정보 추출

아이템 => 파일인 경우 파일 목록만, 
아이템 => 디렉토리, 컴포넌트 => 파일인 경우 파일 + 디렉토리 목록을 만든다.

```bash
# nfs 디렉토리 
$ cd ./nas/

# leaf 디렉토리 목록 (원하지 않는 폴더 제외, 중간 폴더 제외)
# sort -V: natural sort of (version) numbers within text
$ find . -type d ! -ipath '*@eaDir*' ! -ipath '*#recycle*' -exec sh -c '(ls -p "{}"|grep />/dev/null)||echo "{}"' \; | sort -V > ../items.txt

# 파일 목록
$ find . -type f ! -ipath '*@eaDir*' ! -ipath '*#recycle*' | sort -V > ../components.txt

# migration
$ benthos create file/bloblang/stdout > migration.yml
```
