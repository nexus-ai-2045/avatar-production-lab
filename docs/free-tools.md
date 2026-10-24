# 無料制作ツールの選び方

資料確認日: 2026-09-23。以下は公開配布情報に基づく候補整理で、インストールや実機試験の報告ではない。Blender 5.2.2 / Mac arm64を検討する場合の不確実性も記す。導入時には配布版と利用条件を再確認する。

まず標準のカーブ、Mirror、Shrinkwrap、Data Transfer、Texture Paintで工程を作る。追加ツールは、描き込み、法線編集、リトポロジーなど実際に時間を使っている工程へ絞る。

## 候補と判断

| ツール | 役割・無料範囲 | 対応状況と判断 |
| --- | --- | --- |
| [Ucupaint 2.4.9](https://github.com/ucupumar/ucupaint/releases/tag/2.4.9) | 色とマスクをレイヤー管理する通常版。PSD連携のPlusは含めない | 公式にBlender 5.2対応を明記。5.2.2＋Apple Siliconの個別動作は未確認。描き込みの最初の候補 |
| [Abnormal](https://github.com/bnpr/Abnormal/releases/tag/V1.1.16) | 法線の編集 | 表示名1.1.6、タグV1.1.16。4.5 Vulkan更新を確認したが5.2.2＋Metalは未確認。標準機能で足りない時に検証 |
| [RetopoFlow 3.4.10](https://github.com/CGCookie/retopoflow/releases/tag/3.4.10) | 公式GitHubで無料配布する手動リトポ支援 | 3.4.9で5.0対応。5.2.2＋arm64は未検証。大きな作り直しが必要な時の候補 |
| [PolyQuilt現行フォーク](https://extensions.blender.org/add-ons/polyquilt-fork/) | 手動の面張り・リトポ支援 | 確認した現行版1.46.8は4.5 LTS以降、Metal/Vulkan公式未対応。Macでは保留 |
| [GBH Tool](https://github.com/GixoXYZ/BlenderGBHTool) | 束状の髪の生成・編集 | 2.2.3、最低4.2表記。無料の本制作利用と同梱素材の条件が未解決のため保留 |

PolyQuiltは古いGitHub配布と現在のExtensions配布を区別する。Extensions本文は検索経由で確認できたが直接再取得は失敗したため、利用前の再照合が必要。RetopoFlow 4の対応情報を無料配布の3系に転用しない。

## コードと素材の条件を分ける

- **Ucupaint:** [COPYING](https://github.com/ucupumar/ucupaint/blob/master/COPYING)とmanifestはGPL系。取り込む外部モデル・テクスチャの条件は別。同梱素材全点の権利監査は未実施。
- **Abnormal:** [MIT](https://github.com/bnpr/Abnormal/blob/master/LICENSE)。本資料では自作メッシュの編集用途を候補とし、同梱素材を配布物へ転用しない。
- **RetopoFlow 3:** [3.4.10のLICENSE](https://github.com/CGCookie/retopoflow/blob/3.4.10/RetopoFlow.LICENSE)はコードをGPL-3.0-or-later、非コード素材を別扱いにする。一方manifestはGPL-2.0-or-later表記で不一致がある。ツール利用の候補と、コードや素材の再配布を分ける。
- **PolyQuilt:** 確認したExtensions表示はGPL-3.0-or-later。同梱画像などの個別監査は未実施。
- **GBH Tool:** GPL-2.0-or-later表記と、購入前の教育・試用向けという配布説明がある。これはGPLコードを商用禁止と解釈する意味ではない。ライブラリやサンプル素材を本制作へ組み込む条件を確認できていないため採用保留とする。

このリポジトリには上記ツールのコードや配布アセットを同梱しない。利用者は公式配布から取得する。

## 小さく試す手順

1. 配布URL、タグ、ライセンス、Blender版、OSを記録する。
2. 自作の小メッシュで操作する。既存の制作原本へ直接適用しない。
3. 保存と再読込みを行い、画像・法線・形状が残ることを確かめる。
4. テクスチャはベイク画像、法線は書出し後のモデルでも確認する。
5. 制作時間や見た目が改善した場合に限って本工程へ組み込む。

有効化できたことだけを、対応確認や制作完了としない。

## 出力後の別工程

[lilToon](https://github.com/lilxyzw/lilToon)と[AAO Avatar Optimizer](https://github.com/anatawa12/AvatarOptimizer)はMITのUnity向け候補。後者はVRChat向けの非破壊最適化を支援する。Blenderの造形改善や汎用VRMの最適化を自動で行うものではなく、ここでは導入・動作検証していない。
