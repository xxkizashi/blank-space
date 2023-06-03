---
title: "ANSYS Studentのライセンス更新"
date: "2021-02-01"
categories:
  - "Tech"
tags:
  - "ANSYS"
  - "Research"
eyecatch: "/img/eyecatch.jpg"
---

ANSYS Student 2020 R1でFluentを立ち上げたら，エラーメッセージが出た．

## 原因
ANSYS Studentのライセンスには期限がある．  
ダウンロード画面に記載されていた．
- Ansys Student 2020 R1 download for Windows x64 (5.8 GByte): Built-in license valid until 1/31/21
- Ansys Student 2020 R2 download for Windows x64 (6.3 GByte): Built-in license valid until 7/31/21

## 対処方法
再インストールしてバージョンアップする．

## エラーメッセージ
```fluent: error message
ANSYS LICENSE MANAGER ERROR:Capability Fluent Solver does not exist in the ANSYS licensing pool.
The specified license path:
    ANSYSLI_SERVERS: 
    FLEXlm Servers: C:\PROGRA~1\ANSYSI~1\ANSYSS~1\Shared Files\Licensing\student.lic
does not have any licenses for any product. Please make sure the license server has been started correctly.

Hit return to exit.

Unexpected license problem; exiting.
```