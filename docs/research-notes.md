# 制作資料・論文から借りる考え方

資料確認日: 2026-09-23。映画、ゲーム、研究の一次資料を、無料のBlender制作で試せる工程へ結び付ける。新しい資料と長く使える基礎を併記する。以下の応用案は独自の提案であり、論文の再現実験や動作確認結果ではない。

## 法線で顔の影を整理する

Guilty Gear XrdのGDC 2015資料は、セル調の顔で法線を意図的に編集する制作例を説明する。[制作元による講演公開告知](https://www.arcsystemworks.com/guilty-gear-xrds-art-style-the-x-factor-between-2d-and-3d-talk-from-gdc-2015-is-now-available-online/) / [講演資料](https://www.ggxrd.com/Motomura_Junya_GuiltyGearXrd.pdf)

Blenderでは滑らかな補助形状から頬・額へ法線を転送した版と、無加工版を比較する。鼻、まぶた、口内まで一律に転送せず、対象を絞る。光を回し、閉眼や笑顔でも確認する。形状の問題と陰影の問題を分けて直すことが目的になる。PDFの該当本文は検索抽出で確認したが、全スライドの視覚読取りは未実施。

## 最新の映画制作から色面の制御を学ぶ

PixarのSIGGRAPH Talks 2026資料「Coloring Outside the Pipeline」は、『Toy Story 5』のパステル調表現で法線による明暗整理や線の扱いを説明する。[著者所属組織のPDF](https://research.pixar.com/docs/2026.SiggraphTalks.SDW.pdf)

アバターへの応用では、模様やハイライトがモデルに安定して付く表現を先に作る。カメラに依存する線や合成は静止画用として分け、自由視点では全方向での読みやすさを確認する。独自Houdini/Nuke処理を含む事例で、無料Blenderツールの配布ではない。論文本体はCC BY-NC-ND 4.0。画像や制作アセットはここへ転載しない。

## CHARMから編集しやすい髪の表現を借りる

CHARMはSIGGRAPH Asia 2025の髪研究。位置・幅・厚みを制御点で扱う表現が参考になる。[著者プロジェクト](https://hyzcluster.github.io/charm/) / [公式コード](https://github.com/hyz317/CHARM) / [論文v1](https://arxiv.org/html/2509.21114v1)

手作業へ応用するなら、髪全体を高密度にする前に、主要な束をカーブや少数の断面で作る。束の流れ、幅、先細りを直せる原本を保ち、書出し用にメッシュ化してUV・法線・ウェイトを整える。これは生成モデルや最適化手法の再実装ではない。

公開コードはCUDA向け依存を案内し、別途学習済み重みを必要とする。MacのMPS対応、CPU完走、必要メモリと所要時間は未確認。コードとCHARM重みはGPL-3.0表示、依存するMichelangelo重みはLGPL-3.0表示、論文v1はCC BY-NC-SA 4.0で、条件は一律ではない。元の学習用3Dモデルは再配布されない。生成器は研究枠とし、制作の必須工程にしない。

## 変形研究を衣装の診断へ使う

[Direct Delta Mush Skinning and Variants](https://media.contentapi.ea.com/content/dam/ea/seed/presentations/direct-delta-mush-and-variants.pdf)（SIGGRAPH 2019）は変形時の形状保持を扱う。BlenderではCorrective Smoothを比較用に使い、関節の潰れを見つけてウェイトや補助骨の改善目標にする。ただし同モディファイアを論文と同じ実装とは扱わない。

一姿勢で補正を適用しても、全姿勢の補正機能がVRMへ移るわけではない。代表ポーズで比較し、必要な補正を対象アプリで駆動できるか確認する。無料閲覧できる論文と、掲載物や任意コードの再配布許可は別に扱う。

## 顔SDFは限定した試作から

複数方向の白黒の顔影を補間し、影境界を制御する画像を作るMIT実装として[Shadow Threshold Map](https://github.com/akasaki1211/sdf_shadow_threshold_map)がある。作者確認環境はWindowsで、Mac実行は未検証。[Blender用マスク生成コード](https://github.com/ReefSnax/blender-sdf-face-shadow-baker)もMITだが、作者確認は4.5.2であり完成シェーダーではない。

後者は出力先のPNGを先に削除する処理を含むため、試すなら複製モデルと専用の空フォルダを使う。ここでは実行していない。SDFの光角度による判定とMToon標準の陰影は異なるため、画像を挿すだけで同じ表示になるとは扱わない。まず標準材質で成立する顔を作り、効果を比較して採否を決める。

## 公開制作資料の読み方

| 資料 | 取り入れる工程 | 確認範囲と制約 |
| --- | --- | --- |
| [Project Goldの比較シート](https://studio.blender.org/blog/automatic-model-sheets/) | 多方向、透視投影、表情を同条件で比較する | 公式本文を検索経由で確認。テンプレートは未取得・未検証 |
| [Sprite Frightの造形](https://studio.blender.org/blog/sprite-fright-the-illusion-of-simplicity/) | 大きな形と表情を先に整え、細部を選ぶ | 公式本文を検索経由で確認。映画のカメラ依存変形を自由視点へそのまま移さない |
| [Rain v3](https://studio.blender.org/characters/rain/v3/) | 表情を単独・組合せで検査する | Free / CC-BY / Blender 4.1表記を確認。ファイル内部とPythonは未検査・未実行 |
| [2AMの顔解説](https://www.youtube.com/watch?v=uptuXWNWpk0)・[髪解説](https://www.youtube.com/watch?v=LU0BFThJIco) | 形、UV、描画、法線を別工程で考える | 説明欄と章情報のみ。本編未視聴。古い環境の操作互換性と有料配布資産は確認対象外 |

Blender Studioは一部ページの直接取得に失敗しており、会員限定教材全体を無料で確認したものではない。映画・ゲームの実制作資料、研究、個人制作解説は証拠の種類を分ける。掲載の多さや知名度だけで、最良の手法や業界全体の流行とは断定しない。

具体的な制作の順序は[制作工程](workflow.md)、導入候補と未検証点は[無料ツール](free-tools.md)を参照する。
