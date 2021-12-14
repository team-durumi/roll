---
title: "기록 기술 표준 스키마 구현"
date: 2021-12-10T14:35:00+09:00
draft: true
---

## ISAD(G) 요약 -- 구조 Archival Description

item 
- id
- title
- created_at

taxonomy_term
- 


1. 식별: 기술단위를 식별하는데 필요한 필수 정보
  * 1) 참조코드: 국가코드 + 기록기관코드 + 기록식별자 -- id
  * 2) 제목 -- title
  * 3) 일자: timestamp -- created_at, updated_at
  * 4) 기술계층: 아마도 aggregation 참조 아이디? --
  * 5) 기술단위의 규모와 유형: 설명 문자열 -- extent

등록 식별자 = system generated
외부 식별자 = 참조코드: 국가코드 + 기록기관코드 + 기록식별자

2. 배경: 기술단위의 출처 및 관리이력에 관한 정보
  * 6) 생산자명
  * 7) 행정연혁/개인이력
  * 8) 기록물 이력
  * 9) 수집/이관의 직접적 출처

3. 내용과 구조: 기술단위의 주제와 정리에 관한 정보
  * 10) 범위와 내용
  * 11) 평가, 폐기, 처리일정 정보
  * 12) 추가수집예상기록물
  * 13) 정리체계
  * 14) 색인어

4. 열람과 이용조건: 기술단위의 이용조건에 관한 정보
  * 15) 접근환경
  * 16) 이용환경
  * 17) 자료의 언어
  * 18) 물리적 특성과 기술적 요구조건
  * 19) 검색도구

5. 관련자료: 기술단위와 밀접히 관련된 자료에 관한 정보
  * 20) 원본의 존재와 위치
  * 21) 사본의 존재와 위치
  * 22) 관련 기술단위
  * 23) 출판주기

6. 주기: 어떤 영역에도 기술할 수 없는 정보
  * 24) 추가설명

7. 기술통제: 언제, 어떻게, 누구에 의해 기술되었는가에 관한 정보
  * 25) 기술담당자
  * 26) 규칙과 협약
  * 27) 기술일자

### 기술계층 Level of description

- 퐁 (fonds): 퐁 존중 (출처와 원질서 존중)
- 레코드 그룹 (record group) => 다중 분류체계, 카탈로그 (요새는 잘 쓰지 않음)
- 시리즈 (series)
- 철 (file)
- 건 (item)

### 기술 요소 코드 정리

- identity
  * isad:reference
  * isad:title
  * isad:date
  * isad:descriptionlevel
  * isad:extent
- context
  * isad:creator
  * isad:adminbiohistory
  * isad:archivalhistory
  * isad:acqinfo
- content_structure
  * isad:scopecontent
  * isad:appraisaldestruction
  * isad:accruals
  * isad:arrangement
- conditions_access_use
  * isad:accessrestrictions
  * isad:reprorestrictions
  * isad:languagescripts
  * isad:phystech
  * isad:findingaids
- allied_materials
  * isad:existencelocation_originals
  * isad:existencelocation_copies
  * isad:relatedunits
  * isad:publication
- notes
  * isad:note
- description_control
  * isad:archivistsnote
  * isad:rulesconventions
  * isad:descriptionsdate

&nbsp;

### 주요 엔터티 분류?

- 분류체계 (Classification Scheme),
- # 집합체 (Aggregation),
- 기록 (Record),
- 컴포넌트 (Digital media file) -- 보존영역: 원본파일, 업무영역: 가공파일

- 업무 (Task),
- 행위자 (Actor)?? -- 기증자, 생산자
- 용어사전 (glossary) -- 사건, 화학물질 등 기타? -- taxonomy_term?

### 참고

- [기록학개론](https://www.archives.go.kr/archivesdata/upFile/palgan/1398041084851.pdf)
- [전자기록관리시스템 재설계 모형](https://www.archives.go.kr/next/common/archivedata/render.do?filePath=2F757046696c652F70616c67616e2F32303137313232395f303030362e706466)
- [서울기록원 기술계층 예시](https://archives.seoul.go.kr/catalog/result?regclass=RC_ITEM&hasFacetChild=true&query=&reQuery=&acspoint=&contributor=&lastField=level&pageSize=10&pageSort=createdateup&levels=Series)
- [국가기록원 평가/기술](https://www.archives.go.kr/next/manager/narration.do)
- [ISAD(G)](https://www.ica.org/en/isadg-general-international-standard-archival-description-second-edition)    
  * [pdf](https://www.ica.org/sites/default/files/CBPS_2000_Guidelines_ISAD%28G%29_Second-edition_EN.pdf)
  * [xml_schema](https://gist.github.com/anarchivist/826364)
- [ICA](https://www.ica.org) | INTERNATIONAL COUNCIL ON ARCHIVES | CONSEIL INTERNATIONAL DES ARCHIVES
- [moreq2010](https://www.moreq.info/)
- [moreq2010-specs](https://www.moreq.info/files/moreq2010_vol1_v1_1_en.pdf)

- [ISO 15489-1:2016](https://www.iso.org/standard/62542.html)
- [국가 표준 KS X ISO15489-1](https://e-ks.kr/streamdocs/view/sd;streamdocsId=72059211113286614)
- [국가기술표준원](https://www.kats.go.kr/)
- [국가기록원 영구기록물 기술지침](https://www.archives.go.kr/archivesdata/upFile/palgan/1358150301640.pdf)
- [국가기록원 기록관리 표준](https://www.archives.go.kr/next/data/standardCondition.do)

- [오픈소스기록관리소프트웨어포럼](https://osasf.net/)
- [omeka/omeka-s](https://github.com/omeka/omeka-s/blob/develop/application/data/install/schema.sql)
- [artefactual/atom](https://github.com/artefactual/atom/blob/qa/2.x/data/sql/lib.model.schema.sql)

