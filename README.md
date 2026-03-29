# DokuWiki to Obsidian Converter

**Original Project**: [ReactiveMatter/dokuwiki-obsidian](https://github.com/ReactiveMatter/dokuwiki-obsidian)

**[日本語版README](./README_JP.md)**

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

## License

See original repository for license details.

## References

- [DokuWiki](https://www.dokuwiki.org/)
- [Obsidian](https://obsidian.md/)
- [Original Project](https://github.com/ReactiveMatter/dokuwiki-obsidian)
