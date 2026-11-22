# おさかにゃ LP（Square購入導線サイト）

作成: 2026-11-22 [claude] / 引き継ぎ先: Codex・他AI（どのツールでも続行可）

## 目的

- Square オンラインストア（https://native-studio.square.site/）での購入につなげる、おさかにゃ専用のランディングページ。
- 「キャラクターの可愛さを前面に」「ストーリー＋全10キャラの紹介（アンパンマンのキャラ紹介ページ風）」が本人（ユウキ）の指定。
- 本人の最新の好み: **はっきりしたビビッドな配色・太い丸ゴシック・ワクワクする動き**（青い空/海/砂浜＋コーラルの立体ボタン）。島・波の背景表現も希望。

## 構成

- `index.html` — 単一ファイル（CSS/JS内蔵、フレームワークなし、外部はGoogle Fonts `M PLUS Rounded 1c` のみ）。ビルド不要。
- `assets/` — 軽量化済み画像（title / hero-illustration / package-components / component / playing / cats/*.png）。
- 原本（高解像度PNG・説明資料PDF・おさかにゃのうた.mp3）はローカルの `Desktop/NativeStudio/02_制作データ/02_商品紹介/02_おさかにゃ/`（Driveミラー側）にある。リポジトリには入れない。

セクション順: ヘッダー（固定）→ HERO → STORY → GAME POINTS（3つ＋写真ギャラリー）→ CHARACTERS（10匹グリッド＋タップでモーダル）→ PRODUCT（スペック・価格）→ 下部CTA → モバイル固定購入バー。

## 確認方法

```
cd docs/products/osakanya/lp
python -m http.server 8000
# → http://localhost:8000/ をブラウザで開く
```

画像は相対パス参照なので、`index.html` を直接ダブルクリックしても表示できる。

## 確定している事実（変えない）

- 価格: **¥2,200（税込）**
- 人数 2〜4人 ／ 約15分 ／ 8歳以上 ／ 内容物 カード30枚＋チップシート6枚
- キャッチ: 「目指すは、島いちばんのねこ漁師！」／ 「ねこたちの急成長わらしべ釣りバトル」
- 試遊という言葉は使わない方針（「無料プレイ」等を使う）。

## 未完了・次の一手（優先順）

1. **キャラ10匹の紹介文は仮**（`index.html` 末尾の `CATS` 配列: name/role/catch/desc/style）。本人の公式設定に差し替える。画面にも「※仮です」注記あり。差し替えたら注記を消す。
2. **購入リンクをおさかにゃ商品ページの正確なURLへ**（現状はストアトップ。`https://native-studio.square.site/` を `index.html` 内で全置換）。
3. ストーリー文・3つの魅力・スペックの文言は仮。本人確認の上で調整。説明資料PDF（原本フォルダ `01_説明資料/`）と矛盾がないか照合する。
4. 背景の「島・波」表現の強化（現状: 太陽・雲・泡・波ディバイダー）。島のシルエット等を足す案あり。
5. 公開（GitHub Pages / Cloudflare Pages 等のホスティング）。公開・送信は本人確認後に行う。
6. SNS/ストア向けOGP画像・`<meta property="og:*">` の追加、アクセス計測の検討。

## 作業ルール（Native Studio共通）

- 他AIの未コミット変更を戻さない。自分が触ったファイルだけコミット。`git add -A` 禁止。
- 紹介文・告知文の最終版は発信チャット担当、売上/価格/手数料は財務チャット担当の領分。LPの文言は「案」として扱い、確定は本人。
- コード衛生: 同じセレクタの上書きを積まず既存を直す。`!important` を増やさない（本LPは現在0個）。

## 参考

- デザイン参考にしたビビッド案: 本人がアップロードしたTailwind版（`code_artifact.html`）。配色トークン: skyTop #7CE0FF / seaLight #28C7E8 / seaDeep #0B84B8 / coral #FF6B6B / sunny #FFD43B / cocoa #4A3525。
- キャラ紹介の見せ方の参考: https://www.anpanman.jp/about/friend.html


## 2026-11-22 Codex: 公開とスマホ編集

公開先: https://native-studio-game.github.io/osakanya-lp/
公開用GitHub: https://github.com/native-studio-game/osakanya-lp

### スマホから編集する

1. GitHubへログインして https://github.com/native-studio-game/osakanya-lp/edit/main/content.json を開く。
2. `heroCatch`（見出し）、`purchaseUrl`（購入先）、`characters`（10匹の紹介）の引用符内の文章を直す。括弧・カンマ・引用符は残す。
3. 「Commit changes」で保存。mainへ反映するとGitHub Pagesが自動で更新する。
4. 公開ページを再読み込みして確認。反映まで数分かかる場合がある。

本文やデザイン全体: https://github.com/native-studio-game/osakanya-lp/edit/main/index.html
更新状況: https://github.com/native-studio-game/osakanya-lp/actions

公開用リポジトリをWebの正本とする。スマホで編集した後は、先に公開用リポジトリの最新を取得し、このフォルダへ反映してからPCで変更する。古いローカルファイルで上書きしない。

`content.json` を読み込むためローカル確認はHTTPサーバーを使用する。直接ダブルクリックは非対応になった。
キャラクター文章は仮注記を維持。購入先は今はストアトップ。今回の公開は本人指示による暫定公開で、公式設定への置換は別作業。
