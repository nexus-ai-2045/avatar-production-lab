<!-- repo-preflight:review-record -->

# 公開範囲とレビュー条件

状態: 公開済み

このリポジトリは 無料ツールを中心としたBlenderアバター制作の調査・検証・再現手順 を対象とします。

## 公開対象

- README、利用条件、セキュリティと変更手順、公開前レビュー記録
- docs/ の汎用制作資料。モデル・画像・コードは含まない。

## 公開対象外

- secret / token / 個人の絶対 path / アカウント情報
- 公開・push・merge・visibility 変更を自動実行する機能

## 判定上の停止線

`readiness_scan.py` の `status: pass` はローカルで機械検査できた範囲だけを示す。公開・push・merge・visibility 変更は人が別に判断する。

## レビュー記録 (2026-09-23)

- bootstrap_repo.py のローカル初期化を使用。対象と内容を提示し、2026-09-23に初回作成・pushのGOを受領。リポプリの検査後に実行し、作成後の状態はAPIで照合する。
