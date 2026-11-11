# Lesson: first web page in 10 minutes

**Goal.** The learner has never seen HTML. In about 10 minutes they write a web page by
hand, put it on the internet at a real URL, change it, and watch the change go live. The
point is to pull back the curtain: a web page is just a text file, and they can write one.

**Theirs: the HTML.** They type every character of `public/index.html`. Never edit it
for them. Hints for the ladder:
- "What do you think the browser does with text it doesn't recognize?"
- "Tags come in pairs, like `<b>` and `</b>`. What might a pair for the page's title look
  like?"

Browsers are forgiving: a page with a missing closing tag usually still shows up. That's a
discovery moment: "It still worked. Why do you think the browser let that slide?"

**Snags: GitHub, commits, Pages, and Actions.** Provide the publishing workflow yourself
(Step 4). Explain it in two or three plain sentences, but don't quiz them on YAML. In
Claude Code inside their repo, you may write the workflow file for them.

## The lesson

Everything below works in a web browser on github.com, Chromebooks included. If the
learner would rather work on their own computer with git, adapt the steps.

### Step 0. Peek behind the curtain (30 seconds)

Have them open any website, right-click, and choose **View page source** (or press
Ctrl+U, or Cmd+Option+U on a Mac). Ask: "What do you notice?" Let them react to the wall
of text. Tell them every page on the web comes down to text like that, and in ten minutes
they'll have written their own.

### Step 1. Make a repository (1–2 minutes)

Help them:
1. Sign in to github.com (or create a free account).
2. Go to github.com/new.
3. Name the repository something like `my-first-page`. Choose **Public**, because free
   GitHub Pages hosting needs a public repo. Check **Add a README file**.
4. Click **Create repository**.

One sentence of context: a repository is a folder that remembers every version of its
files.

### Step 2. Lay out the project (1 minute)

Explain the layout they're about to build:

```
my-first-page/
├── README.md                     what this project is (already there)
├── public/
│   └── index.html                the web page: everything in public/ gets published
└── .github/
    └── workflows/
        └── pages.yml             the robot that publishes it (Step 4)
```

Ask one question here: "When you visit a website's address without a file name on the
end, how do you think the server decides which file to show you?" Steer toward: servers
look for a file named `index.html` by default. That's why the file has that name.

Why `public/`? It keeps the published page separate from project files like the README,
which is how real projects are usually set up.

### Step 3. Write the page (3–4 minutes) — Socratic

In the repo, have them click **Add file → Create new file** and type `public/index.html`
as the name. Typing the `/` makes the folder.

Then teach with questions, roughly in this order. Adapt to what they try.

1. "Type `hello world` and nothing else. Do you think that's a web page?" (It is, sort
   of. Browsers will show plain text.) They can commit that and publish it in Step 4,
   then improve it. Seeing *something* live early is motivating.
2. "Look at your browser tab. What does it say at the top? How would you tell the browser
   what to put there?" This is where tags come in. If they need it, give the idea of
   angle-bracket tags in pairs: `<something>` opens, `</something>` closes.
3. Guide them toward the bare-minimum page: an `html` element containing a `head` (with a
   `title`) and a `body` (with the visible text). Ask things like:
   - "If the title isn't part of the page you see, where might it go?"
   - "What's the difference between what's in the tab and what's on the page?"
   - "What do you think wraps around the whole thing?"

The target is about this much, give or take. Don't show it unless they ask:

```html
<html>
<head><title>My first page</title></head>
<body>hello world</body>
</html>
```

Don't push `<!DOCTYPE html>`, `lang`, or `<meta charset>` on them yet. Those make good
"what's next" curiosity later. Bare minimum is the goal.

Commit: have them click **Commit changes** and keep the default "commit directly to the
main branch". One sentence: a commit is a saved snapshot with a note.

### Step 4. Publish it (2 minutes) — you help directly

This is the technical hurdle. Do it for them, or walk them through it click by click.

1. **Turn on Pages first.** Repo **Settings → Pages → Build and deployment → Source:**
   choose **GitHub Actions**. Doing this before adding the workflow saves a failed
   first run.
2. **Add the workflow.** **Add file → Create new file**, name it
   `.github/workflows/pages.yml`, and paste in the workflow from the end of this lesson.
   Commit it.
3. Explain in plain words: "This file tells GitHub: every time you commit to main, take
   the `public` folder and publish it as a website. GitHub runs it on its own computers."
4. Open the **Actions** tab and watch the run. A yellow dot means running and a green
   check means done. It takes about a minute.
5. Their page is at `https://USERNAME.github.io/REPO-NAME/`. The URL also appears in the
   run's summary and under Settings → Pages.

Give them a moment: their words are on the internet, and anyone can visit that URL.

### Step 5. Change it, republish, refresh (2 minutes)

1. Have them open `public/index.html`, click the pencil (Edit), and change something.
   Ask: "What would you like the page to say?" or "Can you make one word bold? What tag
   do you guess makes text **b**old?"
2. Commit. Ask: "What do you think happens now, without you pressing any publish button?"
   (The workflow runs again on its own.)
3. Watch Actions go green, then refresh the page. If the old version still shows, have
   them wait 30 seconds or do a hard refresh (Ctrl+Shift+R, or Cmd+Shift+R on a Mac).

That loop — edit, commit, it publishes, refresh — is how real websites get updated.

### Wrap-up (30 seconds)

What they did: wrote HTML by hand, used version control, and ran an automated deploy
pipeline. Those are real developer workflows.

Curiosity hooks:
  - "Right-click your own page and View page source. Look familiar?"
  - "Right-click any element on a big site and choose **Inspect**. What can you change?"
  - "What do you think `<h1>`, `<p>`, `<a href="...">`, or `<img src="...">` do? Try one."
  - "Add `<!DOCTYPE html>` as the very first line. What's that for? Look it up."

## Troubleshooting (help directly)

| What they see | Likely cause | Fix |
| --- | --- | --- |
| Pages option missing or greyed out in Settings | Repo is private on a free plan | Settings → General → Danger Zone → change visibility to Public |
| Workflow fails at "Configure Pages" or "Deploy", or a 404 says Pages isn't enabled | Source isn't set to GitHub Actions | Settings → Pages → Source → GitHub Actions, then Actions tab → the run → **Re-run all jobs** |
| Site shows a 404 page | `index.html` is not inside `public/`, or the name is off (`Index.html`, `index.htm`, `index.html.txt`) | Rename or move it to exactly `public/index.html` (names are case-sensitive) |
| Workflow never ran | File isn't at exactly `.github/workflows/pages.yml` (missing dot, or `workflow` singular) | Rename the file; the commit triggers a run |
| Workflow error about YAML | Indentation got mangled when pasting | Paste the file again; YAML cares about spaces |
| Page shows the tags as text | File isn't named `.html` (maybe `.txt`) | Rename to `index.html` |
| Old version still showing | Browser cache or the deploy is still running | Wait for the green check, then hard refresh |
| Tab title shows the file name or URL | No `<title>`, or it's not inside `<head>` | A good Socratic moment, not a snag: ask where the title belongs |

## The workflow: `.github/workflows/pages.yml`

Each action is pinned to a commit SHA, with its version in a comment, so a changed or
compromised action can't sneak into the learner's repo. Update both together.

```yaml
# Publishes the public/ folder to GitHub Pages every time you commit to main.
# One-time setup: Settings → Pages → Source → GitHub Actions.
name: Publish to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch: # adds a "Run workflow" button on the Actions tab

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: true

jobs:
  deploy:
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/checkout@3d3c42e5aac5ba805825da76410c181273ba90b1 # v7.0.1
        with:
          persist-credentials: false
      - uses: actions/configure-pages@45bfe0192ca1faeb007ade9deae92b16b8254a0d # v6.0.0
      - uses: actions/upload-pages-artifact@fc324d3547104276b827a68afc52ff2a11cc49c9 # v5.0.0
        with:
          path: public
      - id: deployment
        uses: actions/deploy-pages@368f82528645a54fb793d4d04e342629a3f51346 # v5.0.1
```
