# HTML Intro: your first web page in 10 minutes

A Claude tutor that takes someone who has never seen HTML from zero to a live web page
they wrote by hand, in about ten minutes. The goal isn't to teach all of HTML. It's to
pull back the curtain: a web page is just a text file, and you can write one, publish it,
and change it.

## What the learner does

1. **Peeks behind the curtain.** Opens View page source on a real site.
2. **Creates a GitHub repository.**
3. **Writes `public/index.html` by hand.** Plain HTML only: no JavaScript, images, or
   anything external.
4. **Publishes it with GitHub Actions and GitHub Pages.** The tutor provides the
   workflow and handles this hurdle.
5. **Edits, commits, refreshes.** They watch the change go live on its own.

They end up with roughly this much HTML. The tutor doesn't show it; it guides them to it:

```html
<html>
<head><title>My first page</title></head>
<body>hello world</body>
</html>
```

Everything happens in the browser on github.com, so it works on a Chromebook. No installs.

## How it teaches

- **Socratic on the HTML.** The tutor asks one question at a time and never writes the
  learner's HTML for them. When they're stuck, it climbs a hint ladder: a guiding
  question, then a partial answer, then a near-answer. Struggling a little builds the
  thinking and curiosity that make it stick.
- **"Just tell me" always works.** Ask for the answer and you get it straight away.
- **Hands-on with the plumbing.** Repos, commits, the Pages setting, the Actions workflow,
  and troubleshooting aren't the lesson, so the tutor just helps with them.
- **Mistakes are welcome.** Browsers are forgiving. When a sloppy page still works, the
  tutor turns that into a "why do you think that happened?" moment.

## Use it

**In any Claude chat (claude.ai, the desktop app, the mobile app):** open
[PROMPT.md](PROMPT.md), copy everything below the comment line, and paste it into a new
chat. That's the easiest route for a true beginner.

**In Claude Code:** the same lesson is a skill in
[.claude/skills/html-intro/](.claude/skills/html-intro/). Run `claude` in this folder and
type `/html-intro`. To use it from anywhere, copy the folder to `~/.claude/skills/`:

```sh
cp -r .claude/skills/html-intro ~/.claude/skills/
```

## Files

```
html-intro/
├── README.md                          this file
├── PROMPT.md                          paste-anywhere prompt (generated)
├── make-prompt.sh                     rebuilds PROMPT.md from the skill
└── .claude/skills/html-intro/
    ├── SKILL.md                       the lesson and tutoring rules
    └── pages.yml                      the GitHub Pages workflow the tutor hands out
```

`SKILL.md` and `pages.yml` are the source. After editing either one, run
`./make-prompt.sh` to rebuild `PROMPT.md`.

The workflow pins each GitHub Action to a commit SHA, with the version in a comment. That
stops a changed or compromised action from sneaking into the learner's repo. To update an
action, replace both the SHA and the version comment.
