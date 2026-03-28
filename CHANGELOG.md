# Changelog

## [Enhanced] - 2026-03-29

### Added
- 🌏 Complete Japanese character support for filenames and folder names
  - URL-encoded characters now properly decoded
  - Example: `%E6%8A%80` → `技`
- 📊 Improved table conversion with headerless table support
- 🖼️ Fixed image link extraction from DokuWiki format
- ✅ Comprehensive table handling with automatic separator insertion
- 📝 Enhanced error handling and logging

### Fixed
- Image filenames no longer appear as empty in embedded links
  - Issue: `{{:20250216-212302.jpeg:?1000}}` was converting to `![[]]`
  - Solution: Proper handling of trailing colons and size specifications
- Table conversion for tables starting with `|` (without header row)
  - First row now correctly treated as header with separator
- Image size specifications now properly removed
  - Example: `![[image | 300]]` now correctly becomes `![[image]]`

### Improved
- Better URL parsing and decoding for media paths
- More robust table cell splitting and cleanup
- Simplified image link generation (removed unnecessary size specifications)

## [Original] - (before fork)

### Features
- DokuWiki to Markdown conversion
- Basic table support
- Media file copying
- Plugin support (indexmenu, include, WRAP)
- File overwrite modes (0, 1, 2)

## Migration Guide for Existing Users

If you're upgrading from the original version, note:

1. **Japanese filenames** will now be decoded correctly
   - Old: `%E6%8A%80%E8%A1%93%E7%9A%84%E3%83%A1%E3%83%A2/...`
   - New: `技術的メモ/...`

2. **Image links** are now simpler
   - Old: `![[image.jpeg | 300]]`
   - New: `![[image.jpeg]]` (no size specifications)

3. **Tables** are better supported
   - Old: `| Header |` might not generate separator row
   - New: Always generates proper Markdown table with separator

To upgrade, simply replace your `dokuwiki-obsidian.py` file with the new version.
