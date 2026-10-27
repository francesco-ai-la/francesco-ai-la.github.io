# Francesco Loiola — personal site

Static personal website. Hand-written HTML + one stylesheet. **No build step, no
framework, no dependencies.** Keep it that way — this site should still work
untouched in ten years.

- Live at https://francesco-ai-la.github.io
- Served by GitHub Pages from `main`, repo root. Pushing to `main` publishes.
- Local clone folder is named `francescoloiola.github.io` (an older name); the
  repo is `francesco-ai-la/francesco-ai-la.github.io`. Not a problem.

## Structure

```
index.html      Home — name, one-paragraph intro, nav to Work / Life / Contact
  work.html         Work — day job line, then Selected Work (AI / VR / Non-sexy businesses)
    data-ai-value-strategy-consultant.html   Essay: on my job title
    cinematic-scene-creation-with-ai.html    Project writeup (AnimateDiff / ComfyUI)
  life.html         Life — Art / Presence / Sul vivere
    motorcycle.html    Essay: riding
    philosophy.html    Essay: on being a philosopher one day
  contact.html      Email only
style.css       The entire stylesheet
assets/         resume.pdf, photos, video
```

## Page conventions

Every page follows the same skeleton. Copy an existing page rather than writing
one from scratch — `philosophy.html` is the cleanest template.

- `<title>` is `Page Name - Francesco Loiola` (hyphen, not em dash). Home is just
  `Francesco Loiola`.
- Everything lives inside a single `<main>`, which `style.css` caps at 600px.
- One `<h1>` per page, matching the page name.
- `<nav>` goes at the **bottom**, after the content, with back-links using `←`:
  a sub-page links to its parent then Home, e.g.
  `<a href="life.html">← Life</a><br /><a href="index.html">← Home</a>`.
- Lead paragraph on section pages uses `class="intro"`.
- Short vertical lists use `<p class="list">` with `<br />`, or `<ul class="list">`
  when items carry links and descriptions (see `work.html`).
- External links get `target="_blank" rel="noopener noreferrer"`. Internal ones don't.

### Required `<head>`

```html
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Page Name - Francesco Loiola</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Crimson+Pro:wght@400;500&display=swap" rel="stylesheet">
<link rel="stylesheet" href="style.css" />
```

All eight pages now use exactly this head, differing only in the title. If you
add a page, copy it verbatim. The viewport meta is not optional: without it
phones lay the page out at an assumed 980px and zoom out to ~38%, and the
`max-width: 640px` media query in `style.css` never fires.

Remaining drift: `data-ai-value-strategy-consultant.html` is still the only page
with a `<footer>`. Either give every page one or drop it — ask first.

## Style

- Crimson Pro serif, black on white, links in `--sinatra-blue` (`#4A90E2`).
- Add new rules to `style.css` under the existing comment sections
  (Base / Text / Headings / Links / Navigation / Media / Dividers). No inline
  styles, no per-page `<style>` blocks.
- Nav and footer are duplicated by hand across pages — when one changes, change
  it in **every** page.

## Voice

First person, plain, declarative. Short paragraphs. Direct opinions stated
without hedging ("Art is the highest human achievement"). Occasional dry aside
in parentheses. Italian references and phrases appear untranslated. Prefers
concrete specifics — bike model, price, road — over adjectives.

**Do not rewrite Francesco's prose unless asked.** When adding a page, draft in
this voice and expect edits. Never insert marketing language, em-dash-heavy
rhythm, or LLM filler ("delve", "it's not just X, it's Y").

## Working agreement

- Preview visually before proposing a change is done:
  `python3 -m http.server 8000` and open the page in the browser pane. Check
  mobile width (375px) too.
- Both the browser pane and GitHub Pages cache aggressively. When a change looks
  like it did not apply, load the page with a `?fresh=1` query before concluding
  anything is broken — this has produced two false alarms already.
- Check every internal link still resolves after renaming or adding a page.
- Commit in small, single-purpose changes with plain-language messages.
- **Pushing to `main` is pre-authorized** (Francesco, 2026-08-31). Push changes
  he has asked for without stopping to confirm, and say what went live. This
  covers ordinary content and style edits only — it is not blanket approval for
  the exceptions below.
- Still ask first for: deleting or renaming existing pages, rewriting prose he
  did not ask to have changed, force-pushing or rewriting history, and anything
  touching `assets/resume.pdf`.
- Never touch the custom-domain setup (`CNAME`) or repo settings without asking.
- Pages usually redeploys within a minute. After a push, verify the change is
  actually live at https://francesco-ai-la.github.io rather than assuming.
