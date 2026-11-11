# HTML Intro: your first web page in 10 minutes

A Claude tutor that takes you from never having seen HTML to a live web page you wrote by
hand. A web page is just a text file. You'll write one, publish it, and change it.

**Never used git or GitHub? Good, this is for you.** There's nothing to install.
Everything happens in your web browser, so it works on a Chromebook too.

## Two words you'll see

- **GitHub** is a website for storing files online. It can also turn your files into a
  web page anyone can visit. A folder of files there is called a **repository**, or
  **repo**. You're reading the front page of one now.
- **git** keeps a history of every change to your files. Each saved change is a
  **commit**. On github.com you make one by clicking a green button, with no commands to
  type.

## Get started

You need two free accounts and about 10 minutes.

### 1. Make a GitHub account

1. Go to [github.com/signup](https://github.com/signup).
2. Enter your email, pick a password, and choose a username. Your username becomes part
   of your page's address (`https://your-username.github.io/...`), so pick one you're
   happy to share.
3. Enter the code GitHub emails you. You can skip any questions it asks after that.

### 2. Make a Claude account

Go to [claude.ai](https://claude.ai) and sign up. The free plan works. Keep it open in a
second browser tab.

### 3. Start the lesson

You'll paste two files into Claude: the **tutor** (how to teach) and the **lesson** (what
to teach). For each one, open it and click **Copy raw file** near the top right. The
button looks like two overlapping squares.

1. In your Claude tab, start a **new chat**.
2. Open [the tutor](.claude/skills/tutor/SKILL.md), click **Copy raw file**, and paste it
   into the message box (Ctrl+V, or Cmd+V on a Mac). Don't press Enter yet.
3. Open [the lesson](.claude/skills/tutor/lessons/html-intro.md), click **Copy raw file**,
   and paste it below the first one.
4. Press Enter.

No copy button? Click **Raw**, select everything (Ctrl+A, or Cmd+A), and copy it (Ctrl+C,
or Cmd+C).

Claude takes it from there. A few tips:

- **Stuck?** Say so, and you'll get a hint.
- **Want the answer?** Say "just tell me."
- **Mistakes are fine.** Browsers are forgiving, and figuring out why is half the fun.
- **Confused by a GitHub screen?** Tell Claude what you see.

## In Claude Code

If you're comfortable with a terminal:

```sh
git clone https://github.com/timander/html-intro.git
cd html-intro
claude
```

Then type `/tutor html-intro`. To use it from any folder, run
`cp -r .claude/skills/tutor ~/.claude/skills/` first.

## Editing

```
.claude/skills/tutor/
├── SKILL.md              how to teach: works for any lesson
└── lessons/
    └── html-intro.md     what to teach: steps, troubleshooting
```

To add a lesson, add a file to `lessons/`. Give it a goal, say which part is the
learner's to figure out and which parts are snags to just help with, then list the steps,
curiosity hooks, and troubleshooting. Add it to the list in the tutor's `description`.
