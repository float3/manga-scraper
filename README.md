# What is this?

This is supposed to produce [tachiyomi](https://tachiyomi.org) compatible manga https://tachiyomi.org/help/guides/local-manga/#folder-structure

# Please report manga sites that don't work!

- vagabond-chapters.com doesn't work anymore, it looks like they added some anti bot measures, potentially because I used them for testing

# Requirements

```cmd
pip install -r requirements.txt
```

# Running

```cmd
python scraper.py URL FOLDER START_CHAPTER MAX_CHAPTERS
```

All four arguments are required. If `URL` contains a `{chapter}` placeholder it
is substituted with each chapter number in turn:

```cmd
python scraper.py "https://example.com/manga/some-title-chapter-{chapter}" C:\Manga\SomeTitle\ 1 300
```

If no `{chapter}` placeholder is present the scraper instead follows the
**next chapter** link on each page, starting from the URL you give it. It still
needs both chapter numbers — `START_CHAPTER` names the folder the first page is
written to, and `MAX_CHAPTERS` is how many pages it will follow before stopping:

```cmd
python scraper.py "https://example.com/manga/some-title-chapter-1" C:\Manga\SomeTitle\ 1 300
```

Images that already exist on disk are skipped, so an interrupted run can be
repeated.
