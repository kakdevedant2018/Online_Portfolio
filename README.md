# Vedant Kakde — Portfolio

Source for my personal portfolio site, served by GitHub Pages from the
`gh-pages-branch` branch of this repository:

**https://kakdevedant2018.github.io/Online_Portfolio/**

A static single page — no build step is required to deploy it. `index.html`
plus the `css`, `js`, `libs` and `images` folders are the whole site.

## What's on it

| Section | Content |
| --- | --- |
| About | Short professional summary |
| Experience | SDET and QA Engineer roles at Amagi Media Labs, and the TEPL engineering internship |
| Education | PG Diploma in Big Data Analytics (CDAC Bengaluru), B.Tech Electrical Engineering (Bajaj Institute of Technology, Wardha) |
| Projects | The three projects with real, published code — the RAG Q&A support bot, the DGA detection model, and the containerised Flask API |
| Skills | Languages, test automation tooling, cloud and CI/CD, and the AI/LLM tooling I actually work with |
| Contact | Email, LinkedIn, GitHub, and the resume PDF |

Each project card links to its own repository rather than describing work that
cannot be inspected.

## Editing it

Everything that changes between versions of this site is content in
`index.html`:

- **Lead** — `#lead-content`: name, the role line, and the Download Resume
  button, which points at `Vedant_Kakde_Resume.pdf` in the repository root.
  Replacing the resume means replacing that file, keeping the same name, or
  updating the two links that reference it (the lead button and the contact
  section).
- **Experience** — each entry is a `<div data-date="...">` inside
  `#experience-timeline`, holding an `<h3>` employer, an `<h4>` role, and one
  or more `<p>`. `js/scripts.js` reads `data-date` and renders the timeline
  marker from it, so the date lives in the attribute, not in the markup.
- **Education** — a `.education-block` per entry.
- **Projects** — a `.project` per entry. These carry the extra `no-image`
  class, which switches `.project-info` from absolute positioning to a plain
  block; that is what lets a card render without a thumbnail. Add
  `<div class="project-image"><img src="..."></div>` and drop `no-image` to go
  back to the image layout.
- **Skills** — a flat `<li>` list; each item renders as a chip.
- **Contact** — an `.optional-section`, which is also the hook for adding
  further sections such as certifications.

The template styles no `.project-info a`, so links inside a project card use
the `btn-rounded-white` class the template provides for buttons. A bare anchor
there would render in the browser's default link blue against the dark
background.

### Rebuilding the assets

`gulpfile.js` expects a Sass source at `scss/styles.scss` and minifies
`js/scripts.js` into `js/scripts.min.js`. **The Sass source is not in this
repository** — only the compiled `css/styles.css` is. So styling changes have
to be made directly in `css/styles.css`, and `gulp styles` will fail until the
source is restored. `gulp scripts` still works for the JavaScript:

```bash
npm install
npx gulp scripts
```

## Deploying

GitHub Pages serves this repository from `gh-pages-branch`, so anything merged
into that branch is published. Work on a branch and open a pull request if you
want a chance to look at the change before it goes live.

## Credits

Built on the [devfolio](https://github.com/RyanFitzgerald/devfolio) template by
Ryan Fitzgerald, used under the MIT License — see [LICENSE.md](LICENSE.md). The
layout and stylesheet are his work; the content is mine.
