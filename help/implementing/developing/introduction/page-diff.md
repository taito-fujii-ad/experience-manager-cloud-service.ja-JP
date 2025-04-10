---
title: 開発とページの差分
description: ページの差分機能の仕組みと開発者への影響の説明
exl-id: 03c08616-2203-4b90-bed6-4836266e2507
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 100%

---

# 開発とページの差分 {#developing-and-page-diff}

## 機能概要 {#feature-overview}

コンテンツの作成は反復的なプロセスです。効率的に作成するには、ある反復から別の反復へと何が変わったかを確認できることが必要です。あるページバージョンを見てから別のページバージョンを見るのは非効率的であり、エラーが発生しやすくなります。作成者は、現在のページと前のバージョンを並べて比較する際に、差分が強調表示されるようにしたいと考えています。

ページの差分機能を使用すると、ユーザーは現在のページをローンチや以前のバージョンなどと比較できます。このユーザー機能について詳しくは、[ページの差分](/help/sites-cloud/authoring/sites-console/page-diff.md)を参照してください。

## 操作の詳細 {#operation-details}

ページのバージョンを比較する場合、差分を検出しやすくするために、比較対象となる以前のバージョンが AEM によってバックグラウンドで再作成されます。この以前のバージョンは、[並べて比較するための](/help/sites-cloud/authoring/sites-console/page-diff.md)コンテンツのレンダリングに必要です。

この再作成操作は AEM の内部でおこなわれるもので、ユーザーに対しては透過的であり、ユーザーの介入は必要ありません。ただし、管理者が CRXDE Lite などでリポジトリを閲覧している場合は、再作成されたこれらのバージョンがコンテンツ構造内に表示されます。

コンテンツを比較すると、比較対象のページまでのツリー全体が次の場所に再作成されます。

`/tmp/versionhistory/`

クリーンアップタスクが自動的に実行されて、この一時コンテンツがクリーンアップされます。

## 制限事項 {#limitations}

差分は DOM 比較を使用してクライアントサイドで実行されるので、差分処理が簡単になります。ただし、デベロッパーが考慮する必要がある制限事項はいくつかあります。

* この機能では、AEM 製品の名前空間にない CSS クラスが使用されます。同じ名前の付いた他のカスタム CSS クラスまたはサードパーティの CSS クラスがページに含まれている場合、差分の表示に影響が及ぶ可能性があります。

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* 差分はクライアントサイドでページの読み込み時に実行されるので、クライアントサイドの差分サービスが実行された後に DOM を調整しても、その効果はありません。このプロセスは、次の項目に影響を与える場合があります。

   * AJAX を使用してコンテンツを取り込むコンポーネント
   * 単一ページアプリケーション
   * ユーザーインタラクションに対して DOM を操作する JavaScript ベースのコンポーネント。
