# キレイレポオンライン LINE追加 CV計測ページ

Meta広告 → このクッションページ → LINE友だち追加、の動線で
「LINE追加ボタン押下」をMetaのカスタムコンバージョンとして計測する。

## 仕様
- 単一 `index.html`（静的・GitHub Pages想定）
- Meta Pixel ID: `4301712340144106`（kireirepo-lp と同一ピクセル）
- LINE友だち追加URL: `https://lin.ee/NJjGKkZ`
- ページ表示で `PageView` 発火
- CTAボタン押下で **`LINEFriendAdd`（カスタムイベント）** + `Lead`（標準）を発火 → LINEへ遷移
- `noindex`：通常検索には出さない（広告専用LP）

## Metaでのカスタムコンバージョン設定
1. イベントマネージャー → カスタムコンバージョン → 作成
2. データソース: 上記ピクセル
3. イベント: `LINEFriendAdd` を選択（最初の1回はページでボタンを押すと候補に出る）
4. 名前例: 「LINE友だち追加（広告）」
5. 広告セットの最適化イベントにこのカスタムCVを指定

## GitHub Pagesへのデプロイ
```bash
cd ~/projects/kireirepo-line-cv
git init && git add -A && git commit -m "LINE追加CV計測ページ"
gh repo create ryonamura/kireirepo-line-cv --private --source=. --push
# GitHub → Settings → Pages → Branch: main / root を選択
```
公開URL（例）: `https://ryonamura.github.io/kireirepo-line-cv/`
→ このURLを広告のリンク先に設定する。

## 動作確認
- Meta Pixel Helper（Chrome拡張）で `PageView` と、ボタン押下時の `LINEFriendAdd` / `Lead` を確認
- イベントマネージャー「テストイベント」でもリアルタイム確認可能
