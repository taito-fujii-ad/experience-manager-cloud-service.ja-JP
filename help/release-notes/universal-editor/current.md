---
title: ユニバーサルエディター 2025.03.10 リリースノート
description: ユニバーサルエディターの 2025.03.10 リリースのリリースノートです。
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b3c98f5e41dbc5e1714d0ed418a317199c735b73
workflow-type: ht
source-wordcount: '200'
ht-degree: 100%

---


# ユニバーサルエディター 2025.03.10 リリースノート {#release-notes}

ユニバーサルエディターの 2025年3月10日（PT）リリースのリリースノートです。

>[!TIP]
>
>Adobe Experience Manager as a Cloud Service の最新のリリースノートについて詳しくは、[このページ](/help/release-notes/release-notes-cloud/release-notes-current.md)を参照してください。

## 新機能 {#what-is-new}

* **コンポーネントの移動：**[コンテナ間でコンポーネントを移動](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components)すると、ターゲットコンテナのコンポーネントフィルターが確認されるようになりました。
   * コンテナ間でコンポーネントを移動するために、ターゲットコンテナーと宛先コンテナーの両方に同じ[フィルター定義](/help/implementing/universal-editor/filtering.md)を指定する必要がなくなりました。
* **ロックされたページ**：ユニバーサルエディターサービスでは、[ページのロックステータス](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page)を確認し、ロックされていないページや、ユーザーによってロックされているページにのみ書き込みを行います。

## その他の改善点 {#other-improvements}

* ヘッドレスキャンバスの検証を正しくするための修正を行いました。

## 非推奨（廃止予定） {#deprecation}

* npm または `https://unviersal-editor-service.experiencecloud.live/corslib/*` 経由で提供される `universal-editor-cors` ライブラリは使用しないでください。
   * 代わりに、`https://universal-editor-service.adobe.io/cors.js` を指すスクリプトタグを使用してください。
   * ユニバーサルエディターで使用するページを適切に実装する方法について詳しくは、[AEM 開発者向けのユニバーサルエディターの概要](/help/implementing/universal-editor/developer-overview.md)を参照してください。
   * 間違った方法を使用した場合、ユーザーには 1 日に 1 回非推奨（廃止予定）メッセージが表示されます。
