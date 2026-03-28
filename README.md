# DokuWiki to Obsidian Converter - Enhanced

This project is an improved Python script that converts [DokuWiki](https://www.dokuwiki.org/) data to [Obsidian](https://obsidian.md/) format.

**Original Project**: [ReactiveMatter/dokuwiki-obsidian](https://github.com/ReactiveMatter/dokuwiki-obsidian)

**[日本語版README](./README_JP.md)**

## Key Improvements in This Version

### 1. **Full Japanese Character Support 🌏**
   - Correctly decode URL-encoded filenames and folders
   - Example: `%E6%8A%80%E8%A1%93%E7%9A%84%E3%83%A1%E3%83%A2` → `技術的メモ`

### 2. **Enhanced Table Conversion 📊**
   - Complete DokuWiki table format conversion (`^` and `|`) to Markdown
   - Support for headerless tables
   - Automatic separator row insertion

### 3. **Fixed Image Link Processing 🖼️**
   - Properly extract filenames from `{{:filename.jpeg:?1000}}`
   - Remove size specifications and display at original size
   - Convert to Obsidian format `![[filename.jpeg]]`

### 4. **Improved Link Conversion 🔗**
   - Convert DokuWiki internal links to Obsidian format
   - Full namespace path conversion

## Usage

```bash
python3 dokuwiki-obsidian.py --src /home/user/dokuwiki/data --dst /home/user/obsidian --overwrite 2
```

### Parameters

- `--src`: DokuWiki `data` folder path **(required)**
  - Must contain a `pages` subfolder
- `--dst`: Output destination folder (default: `output`)
- `--overwrite`: Overwrite behavior (default: 0)
  - `0`: Don't overwrite existing files
  - `1`: Always overwrite
  - `2`: Only overwrite if source is newer and hash differs

## Features

- ✅ Complete Japanese character support (including file/folder names)
- ✅ DokuWiki syntax conversion
  - Headings (====== to #)
  - Lists and indentation
  - Tables (with/without headers)
  - Bold, italic, strikethrough
  - Internal/external links
- ✅ Plugin support
  - indexmenu (removed)
  - include/section (converted to embedded links)
  - WRAP/div/block (converted to block quotes)
- ✅ Media file handling
  - Automatic copying of media files
  - Image link conversion with size handling
- ✅ Smart file overwriting
  - Hash-based change detection
  - Modification time preservation

## Conversion Examples

### Headings
```
====== H1 ======  →  # H1
===== H2 =====    →  ## H2
```

### Tables
```
^ Header1 ^ Header2 ^
| Data1 | Data2 |
↓
| Header1 | Header2 |
|---------|---------|
| Data1 | Data2 |
```

### Images
```
{{:image.jpeg:?300}}  →  ![[image.jpeg]]
```

### Internal Links
```
[[namespace:page]]  →  [[Namespace/Page]]
```

## Requirements

- Python 3.6+

## Dependencies

Only uses Python built-in modules - no external packages required!

## License

See original repository for license details.

## Contributing

Bug reports and feature requests welcome!

## References

- [DokuWiki](https://www.dokuwiki.org/)
- [Obsidian](https://obsidian.md/)
- [Original Project](https://github.com/ReactiveMatter/dokuwiki-obsidian)
