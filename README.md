# HTML Intro: your first web page in 10 minutes

A Claude tutor that takes someone who has never seen HTML from zero to a live web page
they wrote by hand, in about ten minutes. The goal isn't to teach all of HTML. It's to
pull back the curtain: a web page is just a text file, and you can write one, publish it,
and change it.

**Never used git or GitHub? Good, this is for you.** You don't need to install anything.
Everything happens in your web browser, so it works on a Chromebook too.

## Two words you'll see

- **GitHub** is a website for storing files (usually code) online. It can also turn
  your files into a web page anyone can visit. That's how your page will go live.
- **git** is the tool GitHub is built on. It keeps a history of every change to your
  files. Each saved change is called a **commit**. On github.com you make commits by
  clicking a green button, so you never have to type a git command.

A folder of files on GitHub is called a **repository**, or **repo** for short. This page
you're reading is the front page of a repo.

## Get started (in a web browser)

You need two free accounts and about 10 minutes.

### 1. Make a GitHub account

1. Go to [github.com/signup](https://github.com/signup).
2. Enter your email, pick a password, and choose a username.
   Your username becomes part of your web page's address, like
   `https://your-username.github.io/...`, so pick one you're happy to share.
3. Check your email and enter the code GitHub sends you.
4. If GitHub asks you questions about how you'll use it, you can skip them.

Stay signed in. You'll come back to this tab during the lesson.

### 2. Make a Claude account

1. Go to [claude.ai](https://claude.ai) and sign up. The free plan works.
2. Leave it open in a second browser tab.

### 3. Copy the lesson prompt

The "prompt" is a set of instructions that turns Claude into your tutor.

1. Open [PROMPT.md](PROMPT.md) (click the link, or click `PROMPT.md` in the file list at
   the top of this page).
2. Near the top right of the file, find the **Copy raw file** button. It looks like two
   overlapping squares. Click it.
3. That copies the whole file. The first two lines are notes for people editing this
   repo. They're harmless, so you can leave them in.

No copy button? Click **Raw**, then select everything (Ctrl+A, or Cmd+A on a Mac) and
copy it (Ctrl+C, or Cmd+C).

### 4. Start the lesson

1. Go to your Claude tab and start a **new chat**.
2. Paste the prompt into the message box (Ctrl+V, or Cmd+V on a Mac).
3. Press Enter.

Claude takes it from there. It will walk you through:

1. **Peeking behind the curtain.** Seeing the hidden text behind a real website.
2. **Making your own GitHub repo.**
3. **Writing `public/index.html` by hand.** Plain HTML only.
4. **Publishing it.** Claude gives you a small file that tells GitHub to put your page
   online, and helps you set it up.
5. **Editing, saving, refreshing.** You change your page and watch the change go live.

You'll end up with roughly this much HTML. Claude won't show it to you; it will guide you
there with questions:

```html
<html>
<head><title>My first page</title></head>
<body>hello world</body>
</html>
```

### Tips for the lesson

- **Stuck? Say so.** Claude gives hints, one small step at a time.
- **Want the answer? Say "just tell me."** You'll get it right away, no lecture.
- **Mistakes are fine.** Browsers are forgiving. A messy page often still works, and
  figuring out why is part of the fun.
- **GitHub screens confusing?** Tell Claude what you see. It will help you click through.

## How it teaches

- **Socratic on the HTML.** The tutor asks one question at a time and never writes the
  learner's HTML for them. When they're stuck, it climbs a hint ladder: a guiding
  question, then a partial answer, then a near-answer. Struggling a little builds the
  thinking and curiosity that make it stick.
- **"Just tell me" always works.** Ask for the answer and you get it straight away.
- **Hands-on with the plumbing.** Repos, commits, the Pages setting, the Actions workflow,
  and troubleshooting aren't the lesson, so the tutor just helps with them.
- **Mistakes are welcome.** When a sloppy page still works, the tutor turns that into a
  "why do you think that happened?" moment.

## Optional: run it in Claude Code

This is for people comfortable with a terminal. Beginners should use the browser steps
above.

1. **Install git.** On a Mac, open Terminal and run `git --version`. If git isn't
   installed, your Mac offers to install it. On Windows, download it from
   [git-scm.com](https://git-scm.com).
2. **Install Claude Code.** Follow the steps at
   [docs.claude.com/en/docs/claude-code](https://docs.claude.com/en/docs/claude-code).
3. **Download this repo** ("cloning" makes a copy on your computer):

   ```sh
   git clone https://github.com/timander/html-intro.git
   cd html-intro
   ```

4. **Start the lesson:**

   ```sh
   claude
   ```

   Then type `/html-intro` and press Enter.

To use the lesson from any folder, copy the skill to your personal Claude Code skills:

```sh
cp -r .claude/skills/html-intro ~/.claude/skills/
```

## For maintainers

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
