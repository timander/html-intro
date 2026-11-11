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

### 3. Copy the lesson

The lesson is a set of instructions that turns Claude into your tutor.

1. Open [the lesson file](.claude/skills/html-intro/SKILL.md).
2. Near the top right of the file, click **Copy raw file**. The button looks like two
   overlapping squares.

No copy button? Click **Raw**, select everything (Ctrl+A, or Cmd+A on a Mac), and copy it
(Ctrl+C, or Cmd+C).

### 4. Start

1. In your Claude tab, start a **new chat**.
2. Paste (Ctrl+V, or Cmd+V on a Mac) and press Enter.

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

Then type `/html-intro`. To use it from any folder, run
`cp -r .claude/skills/html-intro ~/.claude/skills/` first.

## Editing the lesson

Everything lives in one file: [SKILL.md](.claude/skills/html-intro/SKILL.md). It holds
the teaching rules, the steps, and the publishing workflow the tutor hands out.
