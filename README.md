# ecoses042.github.io

Personal academic homepage of **Minsoo Song** — M.S. student in the School of Software,
Soongsil University, and a member of the [Natural Language Processing Lab](https://sites.google.com/view/ssu-nlp/home).

**Live site:** <https://ecoses042.github.io>

Built with [Jekyll](https://jekyllrb.com/) and served by GitHub Pages. The layout follows the
[researcher](https://github.com/ankitsultana/researcher) theme; the repository was originally
forked from [jglovier/resume-template](https://github.com/jglovier/resume-template).

## Repository layout

Files that actually build the site:

| Path | Purpose |
| --- | --- |
| `index.md` | The entire page content (Biography, Research Interests, Publications, Education, Work Experiences, Links) |
| `_config.yml` | Site title/description/URL, top navigation, footer settings |
| `_layouts/default.html` | The only layout in use — navbar, content slot, optional footer |
| `css/main.scss` | Sass entry point; imports `_sass/_style.scss` |
| `_sass/_style.scss` | Site styling; imports `vars`, `typography`, `tables` |
| `images/` | Profile photo and affiliation logos |
| `cv.tex` → `Minsoo_Song_CV.pdf` | LaTeX source and the compiled CV linked from the navbar |
| `Gemfile`, `Dockerfile`, `.travis.yml` | Local build tooling |

Leftovers from the upstream template that are **not** referenced by any page:
`_data/*.yml`, `_layouts/resume.html`, `_includes/*.html`,
`_sass/_base.scss`, `_layout.scss`, `_mixins.scss`, `_normalize.scss`, `_resume.scss`,
and the design sources in `_assets/`.

## Updating the site

- **Content** (publications, education, experience, bio) → edit `index.md`.
  It is Markdown with inline HTML for links, the profile picture, and affiliation logos.
- **Navigation, site title, footer** → edit the `nav:` list and related keys in `_config.yml`.
- **Styling** → edit `_sass/_style.scss`.
- **CV** → edit `cv.tex`, compile it, and overwrite `Minsoo_Song_CV.pdf` at the repository root.
  LaTeX build artifacts (`*.aux`, `*.log`, `*.out`, `*.synctex.gz`) are gitignored.

Pushing to `main` publishes the site through GitHub Pages.

## Running locally

```bash
bundle install
bundle exec jekyll serve
# open http://localhost:4000
```

With Docker:

```bash
docker image build -t homepage .
docker run --rm --name homepage -v "$PWD":/home/app --network host homepage
```

## License

Code and styles are MIT licensed — see [LICENSE](LICENSE) and
[THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md).
Site content (text, CV, photographs) is © Minsoo Song and is not covered by that license.
