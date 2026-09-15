# 東海大学 荒井堅太研究室 ホームページ  —  GitHub Pages 運用マニュアル

## サイト構成
- 本体: index.html 1ファイルのみ（全画像を内蔵・外部依存なし）
- 公開: GitHub Pages（無料） + 独自ドメイン www.tokai-arai-lab.com（DNS管理: Cloudflare）
- CNAME ファイル = GitHub Pages に「www.tokai-arai-lab.com で公開」を指示する設定ファイル

## 毎回の更新フロー（慣れれば約1分）
1. Genspark で修正依頼 → 修正後の index.html を配信で受け取る
2. GitHub でリポジトリを開く → [Add file] → [Upload files]
3. 新しい index.html をドラッグ&ドロップ（同名なので上書きコミットされます）
4. [Commit changes] を押す → GitHub Pages が自動で再ビルド・公開（1〜3分）
5. https://www.tokai-arai-lab.com で確認

※ 更新は必ず「同じ index.html を1枚だけ上書き」。
※ GitHub には全履歴が残るので、過去バージョンへの復元もいつでも可能。

## 初回セットアップ（1回だけ・約15分）
1. GitHub で新規リポジトリ作成（例: tokai-arai-lab ／ Public）
2. [Add file] → [Upload files] → このフォルダの3ファイル（index.html / README.md / CNAME）をまとめてアップロード
3. Settings → Pages → Source を「Deploy from a branch」→ branch: main / root を選択 → Save
4. Settings → Pages → Custom domain: www.tokai-arai-lab.com を入力 → Save
   （CNAME ファイルがあるので GitHub が自動検証。DNS 追加を求められたら手順5へ）
5. Cloudflare ダッシュボード（dash.cloudflare.com）で DNS レコードを変更:
   - www レコード: CNAME → <あなたのGitHubユーザー名>.github.io（既存のWix向け www レコードを置き換え）
   - apex（tokai-arai-lab.com）: GitHub Pages 用 A レコード 4件に変更
     （185.199.108.153 / 185.199.109.153 / 185.199.110.153 / 185.199.111.153）
   - 古い Wix 向けレコードは削除
6. GitHub Pages 画面で Enforce HTTPS が ON になるまで待つ（数分）
7. https://www.tokai-arai-lab.com が新サイトに切り替わることを確認

## 注意
- 切り替え確認後に、Wix のホスティング契約は解約して OK（DNS は Cloudflare が担うためドメイン自体は維持）
- 解約前に Wix 側のメール・その他サービスがないことを必ず確認
