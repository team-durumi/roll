---
title: "기록 기술 표준 스키마 구현"
date: 2021-12-10T14:35:00+09:00
draft: true
---

[ISAD(G)](https://www.ica.org/en/isadg-general-international-standard-archival-description-second-edition)    
General International Standard Archival Description - Second edition

[ICA](https://www.ica.org)    
INTERNATIONAL COUNCIL ON ARCHIVES     
CONSEIL INTERNATIONAL DES ARCHIVES

- 사람용 pdf: https://www.ica.org/sites/default/files/CBPS_2000_Guidelines_ISAD%28G%29_Second-edition_EN.pdf
- 기계용 xml schema: https://gist.github.com/anarchivist/826364

## 구조 Archival Description

### 기술계층 Level of description

```
Fonds
Sub-fonds
Series
Sub-series
File
Item
```

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
