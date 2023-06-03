---
title: "ANSYS Fluentのバッチ処理"
date: "2021-01-30"
categories:
  - "Tech"
tags:
  - "ANSYS"
  - "Research"
eyecatch: "/img/eyecatch.jpg"
---

ANSYS Fluent (2020 R1) で複数条件の解析を回す必要があったため，バッチ処理方法について色々調べた．
その時のメモ．    

注意：  
case fileを一括で作成できていない（やり方がよく分からない）．
非常に面倒くさいが手動で一つ一つ条件を変更している．

## 手順
1. case fileを用意する．  
   `C:\作業フォルダ\プロジェクト名\プロジェクト名_files\dp0\FFF\Fluent\` 
1. journal fileを上記のディレクトリに入れる．
1. `ANSYS Workbench > 解析実行`を選択  
   この時 "Upstream data of this cell has changed. Do you want to refresh this cell using upstream mesh and setting?" と聞かれるが，"いいえ"を選択
1. Fluentで`ファイル > 読み込み > ジャーナル`を選択
1. journal file(.jou)を実行

## journal fileの具体例
所々に "yes" があるのは，ファイルを保存するのかどうかをFluent側が毎度確認してくるから．
```journal: example.jou
/file/read-case FFF_He_300K_Cu10um_04MPa.cas.gz
/solve/initialize/initialize-flow
/solve/iterate 1000
/file/write-case FFF_He_300K_Cu10um_04MPa.cas
yes
/file/write-data FFF_He_300K_Cu10um_04MPa.dat
yes


/file/read-case FFF_He_300K_Cu5um_04MPa.cas.gz
yes
/solve/initialize/initialize-flow
/solve/iterate 1000
/file/write-case FFF_He_300K_Cu5um_04MPa.cas
yes
/file/write-data FFF_He_300K_Cu5um_04MPa.dat
yes


exit
```

## 参考
- [dynamicsoar's log - journal file を使った CUI での Fluent の実行について](https://dynamicsoar.hatenablog.com/entry/2017/05/23/121205)
- [東京工業大学学術国際情報センター - ANSYS Fluent使用方法](https://helpdesk.t3.gsic.titech.ac.jp/manuals/ansys/fluent/)
- [rescale - ANSYS Fluent Batch Tutorials](https://docs.rescale.com/articles/ansys-fluent-batch-tutorials/#ansys-fluent-in-batch-mode)