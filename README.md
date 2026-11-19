# abao1999.github.io

Personal academic website of Anthony C. Bao, served at <https://abao1999.github.io>.

It is built with [Jekyll](https://jekyllrb.com/) and the [al-folio](https://github.com/alshedivat/al-folio) template (v1.2), in light mode only.
Layouts and styles come from the `al_folio_*` gems pinned in the `Gemfile`, so this repo only holds content and configuration.

## Where things live

| Tab / feature             | Edit                                                                                              |
| ------------------------- | ------------------------------------------------------------------------------------------------- |
| **about**                 | `_pages/about.md` (bio + research statement), `assets/img/prof_pic.jpg` (photo)                   |
| **blog**                  | `_posts/YYYY-MM-DD-title.md`; template for opinion posts in `_drafts/opinion-template.md`         |
| **publications**          | `_bibliography/papers.bib` (`selected={true}` puts a paper on the about page)                     |
| **CV**                    | `_data/cv.yml` (RenderCV format) and `assets/pdf/cv_abao.pdf` (PDF button)                        |
| **teaching**              | `_pages/teaching.md` (page + mentoring), `_teachings/*.md` (one file per course)                  |
| **extra** ▾ travel       | `_data/travel.yml` (trips; entries with `lat`/`lon` get a map marker)                             |
| **extra** ▾ photos       | drop images into `assets/img/photos/` (shown automatically); captions in `_data/photos.yml`       |
| **extra** ▾ open source  | `_data/repositories.yml`, `_pages/repositories.md`                                                |
| News (about page)        | `_news/*.md` (full archive at `/news/`)                                                           |
| Dropdown items           | `_pages/extra.md`                                                                                 |
| Social links              | `_data/socials.yml`                                                                               |
| Co-author / venue links   | `_data/coauthors.yml`, `_data/venues.yml`                                                         |
| Site-wide settings        | `_config.yml`                                                                                     |

Blog posts use `categories: research` or `categories: opinions`.
After the first `opinions` post is published, add `"opinions"` to `display_categories` in `_config.yml` so the filter link appears on the blog page.

## Local preview

Requires Ruby 3.3. On macOS, install it with `brew install ruby@3.3`; it is keg-only and doesn't touch the system Ruby.

```bash
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"
bundle install                  # first time only
bundle exec jekyll serve        # http://localhost:4000  (add --drafts to preview _drafts/)
```

## Deployment

Pushing to `main` runs `.github/workflows/deploy.yml`, which builds the site and publishes it to the `gh-pages` branch.

One-time GitHub setup:

1. **Settings → Actions → General → Workflow permissions:** select _Read and write permissions_.
2. After the first successful **Deploy site** run, go to **Settings → Pages** and set _Source_ to "Deploy from a branch", branch `gh-pages`, folder `/ (root)`.

Never edit the `gh-pages` branch by hand.
