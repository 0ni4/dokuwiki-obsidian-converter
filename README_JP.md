# DokuWiki to Obsidian Converter - Enhanced

> Note: このREADMEはAIによって生成され、チェックされてから投稿されています。

このプロジェクトは、DokuWikiのデータを[Obsidian](https://obsidian.md/)形式に変換するPythonスクリプトです。

**元のプロジェクト**: [ReactiveMatter/dokuwiki-obsidian](https://github.com/ReactiveMatter/dokuwiki-obsidian)

## 改善点

このフォークでは、following の改善を加えました：

### 1. **日本語ファイル名・フォルダ名対応 🌏**
   - URL エンコードされたファイル/フォルダ名を正しくデコード

### 2. **テーブル変換の改善 📊**
   - DokuWiki テーブル形式（`^` と `|`）を Markdown テーブルに完全変換
   - ヘッダー行のないテーブルもサポート
   - 自動的に区切り行（`| --- |`）を挿入

### 3. **画像リンク処理の修正 🖼️**
   - DokuWiki形式 `{{:filename.jpeg:?1000}}` から画像ファイル名を正しく抽出
   - サイズ指定（`?1000`）を削除して元サイズで表示
   - Obsidian形式 `![[filename.jpeg]]` に変換

### 4. **内部リンク変換 🔗**
   - DokuWiki内部リンク形式を Obsidian リンク形式に変換
   - 例: `[[page:subpage]]` → `[[Page/Subpage]]`

## 使用方法

```bash
python3 dokuwiki-obsidian.py --src /path/to/dokuwiki/data --dst /path/to/output --overwrite 2
```

### パラメータ

- `--src` : DokuWikiの`data`フォルダへのパス（必須）
  - このフォルダには`pages`フォルダが含まれている必要あり
- `--dst` : 出力先フォルダ（デフォルト: `output`）
- `--overwrite` : 上書き動作を指定（デフォルト: 0）
  - `0`: 既存ファイルを上書きしない
  - `1`: 常に上書きする
  - `2`: ソースファイルが新しい場合かつハッシュが異なる場合のみ上書き

## 変換内容

### DokuWiki形式 → Markdown形式の変換例

#### 見出し
```
====== H1見出し ======  →  # H1見出し
===== H2見出し =====    →  ## H2見出し
```

#### テーブル
```
^ ヘッダー1 ^ ヘッダー2 ^
| データ1 | データ2 |

↓

| ヘッダー1 | ヘッダー2 |
|----------|----------|
| データ1 | データ2 |
```

#### 画像
```
{{:image.jpeg:?300}}  →  ![[image.jpeg]]
```

#### リンク
```
[[内部ページ]]  →  [[内部ページ]]
[[http://example.com|リンク]]  →  [リンク](http://example.com)
```

#### イタリック
```
//イタリック//  →  *イタリック*
```

#### 削除線
```
<del>text</del>  →  ~~text~~
```

## 出力結果

変換後のファイルは以下の構造で出力されます：

```
output/
├── 設計.md
├── ログ.md
├── Pages/
│   ├── Page1.md
│   ├── Page2.md
├── media/
│   ├── images/
│   │   └── image.jpeg
```

## 機能

- ✅ 日本語ファイル名完全対応
- ✅ Markdown テーブル自動生成
- ✅ DokuWiki プラグイン対応
  - indexmenu: 削除
  - include/section: 埋め込みリンク変換
  - WRAP/div/block: ブロックノート変換
- ✅ メディアファイルの自動コピー
- ✅ ファイル更新日時の保持
- ✅ コンテンツハッシュによる変更検知

## 必要な環境

- Python 3.6以上

## ライセンス

このプロジェクトは元のプロジェクトと同じライセンスに従います。

## 関連リンク

- [DokuWiki](https://www.dokuwiki.org/)
- [Obsidian](https://obsidian.md/)
- [元のプロジェクト](https://github.com/ReactiveMatter/dokuwiki-obsidian)
