# Lesson: from plain HTML to CSS

**Goal.** The learner has a live page from `html-intro` (`docs/index.html`, published
with GitHub Pages). They grow it into a real document, discover that the browser already
styles it, then style it themselves: first the hard way, inside every tag, until they're
sick of it, and then the way the web settled on, with CSS in its own file. The point is
that HTML says *what things are* and CSS says *how they look*, and that split exists
because people tried it the other way first.

**Who.** Finished `html-intro`, or can open and edit `docs/index.html` in their repo. If
they have no page yet, run `html-intro` first.

**Time.** About 30–40 minutes on the core path, mostly because of commit waits. Each
**deeper** branch adds 2–5 minutes. Offer them; don't march through them. If they're
moving fast, combine small tasks into one message.

**Theirs: every character of HTML and CSS.** Hints for the ladder:
- "What do you think the browser does with the line breaks you typed?"
- "Inside the angle brackets, after the tag name, you can add extra information. What
  might tell a link where to go?"
- "A rule needs to say *what* to style and *how*. Which part of `p { color: green; }`
  does each?"

**Words they can't guess.** `href`, `class`, the `.` in front of a class name,
`rel="stylesheet"`, and `<link>`. Let them guess the shape once (they'll often get close,
like `url=` or "give it a name"), praise that, then give the word.

Three discoveries to protect. Let them hit each one before you say anything:
1. Browsers ignore the spacing and line breaks they type.
2. Their page has styling already, and they didn't write any.
3. Broken CSS fails silently. A typo just does nothing, with no error message.

**Snags: editing and committing files, waiting for Pages, opening DevTools.** Pages
takes about a minute to republish, which is too slow for trying out styles. Teach the
fast loop early (Step 1) as a snag: right-click → **Inspect** opens DevTools, where they
can edit the page live. Changes there vanish on refresh, and that's a discovery too
("Why did it go away?"). Try things in DevTools, then put what they like into the file
and commit. Learners forget this and go back to committing every change, so give a
one-line reminder at the start of each styling task in Steps 3–5: "Try it in Inspect
first."

## The lesson

### Step 0. Where we are (1 minute)

Have them open their live page and `docs/index.html` in their repo side by side. Ask:
"Your page has one sentence. What would you want a real page about you, or something you
love, to have?" Note their answer. Use their topic for every example from here on.

### Step 1. Grow the HTML (6–8 minutes)

**Core.** Have them add a few lines of text about their topic: a heading line, two or
three short paragraphs, and a short list. Plain text first, no new tags, each on its own
line. Commit and refresh (or edit in DevTools for speed).

Discovery 1 hits: it all runs together on one line. Ask: "You pressed Enter. Why do you
think the browser ignored it?" Steer toward: HTML describes *what things are*, not where
the line breaks go. The browser decides the layout. So how do you tell it "this is a
paragraph"?

Then guide them with questions. Keep this step moving; the CSS is the main event.
- `<p>` for paragraphs. "What letter might stand for paragraph?"
- Headings and the list as one task: `<h1>` for the main heading, `<h2>` for a section
  (ask "Why do you think there are numbers?"), and `<ul>` around `<li>` items. Let them
  guess what the letters stand for (unordered list, list item). Nesting is the new idea:
  tags inside tags.
- A link: `<a href="https://...">text</a>`. This brings in **attributes**, extra
  information inside the opening tag. "The tag is `a`. How would you tell it *where*
  to go?" One guess, then give them `href`.

Name the parts once they've used them: an **element** is the whole thing, **tags** are
the angle-bracket bits, and an **attribute** is a `name="value"` inside the opening tag.

**Deeper: the tree.** In DevTools, open the **Elements** panel. Ask: "What shape does
this look like?" The browser turned their text into a tree of boxes inside boxes. Then:
"Did you write a `<head>`? Is there one here?" Browsers repair what's missing. If their
`html-intro` page skipped tags, the tree shows the ones the browser added.

**Deeper: block and inline.** "Why does each paragraph start on a new line, but a link
sits inside the sentence?" Some elements stack like blocks, and some flow like words.

**Deeper: where it came from.** In 1989 Tim Berners-Lee, at CERN, proposed the web as a
way for scientists to share linked documents. The first website is still online. Have
them visit `info.cern.ch/hypertext/WWW/TheProject.html` and View page source. Ask: "How
different is it from yours?" HTML was built to describe documents: headings, paragraphs,
lists, links. It had almost no say over looks.

### Step 2. Who styled this? (2 minutes)

**Core.** Ask: "Your heading is big and bold. Did you tell it to be?" Let them sit with
it (discovery 2). Then have them Inspect the heading and look at the **Styles** panel.
At the bottom is a rule from the **user agent stylesheet**: the browser's built-in
styles. Every browser ships default looks for every element.

Ask: "So if the browser has its own styles, do you think you could write your own?"

**Deeper: different defaults.** "Would every browser make `<h1>` exactly the same size?"
Not always. Mostly the same, but not guaranteed. That's one reason designers write their
own styles instead of trusting defaults.

### Step 3. Style it the hard way (5–6 minutes)

Make them feel this. Don't hurry it.

**Core.** Give the idea: any element can take a `style` attribute. Show the shape once,
on something that isn't theirs: `style="color: red"`. Then the tasks, one at a time:
1. "Make your heading a color you like."
2. "Make every paragraph and list item dark blue." (Each element needs its own
   `style`.)
3. "Give the paragraphs a different font: `font-family: Georgia`, or anything you like.
   How many places did you have to change?"

Discovery 3 often shows up here. `style="color=red"` or a missing colon just does
nothing. Ask: "No error, no warning. Why do you think the browser stays quiet?" Steer
toward: the browser skips CSS it doesn't understand and keeps going. That keeps old pages
working when new features arrive, and it means mistakes are silent.

Explain the syntax once they've used it: `property: value`, separated by semicolons.

Then the pain:
4. "Your friend says dark blue is ugly. Make it all green." Let them change every one.
5. Ask: "How did that feel? What if your site had 20 pages?" Then: "What do you wish you
   could write instead?" Let them invent it. Anything like "all paragraphs: green" means
   they've just designed CSS. Tell them so.

**Deeper: the 1990s did it worse.** Before CSS, browser makers added looks straight into
HTML: `<font color="red">`, `<center>`. Have them try one. It still works. Ask: "Why
would a browser in 2026 still understand a tag from 1995?" Browsers almost never break
old pages. Then picture a whole site written like that. People called it tag soup.

### Step 4. Pull the style out: the `<style>` block (5 minutes)

**Core.** Ask: "You want one sentence that says 'all paragraphs are green'. Where in your
page would rules that apply to the whole page belong?" Steer toward the `<head>`: it
holds things *about* the page, like the title.

Guide them to a `<style>` element in the head, and to the shape of a **rule**:

```css
p {
  color: green;
}
```

Let them try to write that from their wish in Step 3. The ladder:
1. "What part says *which* elements?"
2. "The property-and-value pairs are the same as before. What might wrap around them?"
3. "`p { ... }`. Fill in the middle."

Name the parts once it works: **selector** (`p`), **declaration** (`color: green`), and
together, a **rule**.

Then the payoff: "Change green to purple once. What happened?" Have them move their
styles into rules and delete the inline `style` attributes. Don't chase every last one:
a leftover (often the heading's color from Step 3) becomes a discovery in Step 5.

**Core: one paragraph that's different.** "Make just *one* paragraph stand out. How can
a rule point at only that one?" Steer toward the `class` attribute (`<p class="note">`)
and the `.note` selector. "Why do you think it's a dot?" (It's just the chosen symbol for
"class." It's fine to say so.)

**Deeper: the cascade.** Have them leave one inline `style="color: red"` on a paragraph
while the `<style>` block says purple. Ask: "Who wins? Why?" Then add `p` and `.note`
rules that disagree. Steer toward: the more specific rule wins, and later rules beat
earlier ones when they're equally specific. That's the *cascading* in Cascading Style
Sheets. In DevTools, crossed-out declarations in the Styles panel are the ones that lost.

### Step 5. Pull it out again: a stylesheet file (5 minutes)

**Core.** Ask: "If you made a second page, how would it get the same look?" Let them see
the problem: copy the `<style>` block, and you're back to changing everything twice.

Snag help: **Add file → Create new file**, name it `docs/style.css`. Then theirs: move
the rules there (the CSS only, no `<style>` tag). Ask: "What does the file need now?
What's the HTML have to say?"

Give the shape if they need it, in the head:
`<link rel="stylesheet" href="style.css">`

Then the payoff: have them make `docs/about.html` with a little HTML and the same
`<link>`, and link the two pages to each other with `<a href="about.html">`. Change one
color in `style.css`, commit, refresh both. "One change, two pages. How many pages could
this work for?"

If an inline style survived on `index.html`, the two pages won't match: say, a purple
heading on one and a black heading on the other. Let them spot it and ask: "Why doesn't
the about page match?" The fix is theirs: move it into `style.css`. It's the whole reason
for the stylesheet, learned from their own page.

**Deeper: why the split matters.** In 1994 Håkon Wium Lie proposed CSS, and the first
version became a web standard in 1996. The idea: the HTML says what things are, the CSS
says how they look, and either can change without touching the other. In 2003 a site
called CSS Zen Garden proved it: one HTML page, hundreds of completely different designs,
only the CSS swapped. Have them visit `csszengarden.com` and click through a few designs.
Ask: "What's the same on every one?"

**Deeper: how the browser draws a page.** It reads the HTML into the tree they saw, reads
the CSS, matches each rule's selector to elements in the tree, works out where every box
goes (layout), then paints the pixels. Ask: "Which step do you think happens again when
you change a color in DevTools?"

### Step 6. Boxes (optional, 3–5 minutes)

Offer this as a deeper step if they're still curious; skip it if they're ready to stop.

Ask: "Everything on the page is a rectangle. Do you believe that?" Have them add
`border: 2px solid black` to `p`. Then `padding: 10px` and `margin: 30px`. "What's the
difference between padding and margin?" In DevTools, the box diagram in the Styles
panel (or Computed tab) shows content, padding, border, and margin as nested boxes.

### Wrap-up (1 minute)

What they did: structured a document with HTML, found the browser's hidden default
styles, styled it the old way until it hurt, then moved style into a rule, a block, and a
shared file, which is how the web has worked since the late 1990s. They saw the cascade
decide who wins.

Curiosity hooks:
- "Try `p:hover { color: orange; }`. What do you think the colon does?"
- "Look up `display: flex`. What happens when you put it on your list?"
- "Open DevTools on a site you use every day. How many stylesheets does it load?"
- "Can CSS change the page when the screen is small? Look up 'media queries'."
- "Pick a CSS Zen Garden design you love. Can you copy one trick from it?"

## Troubleshooting (help directly)

| What they see | Likely cause | Fix |
| --- | --- | --- |
| Change doesn't show on the live page | Pages is still publishing, or browser cache | Wait a minute, then hard refresh (Ctrl+Shift+R, or Cmd+Shift+R on a Mac) |
| DevTools edits disappeared | Refreshing reloads the file from GitHub | Expected: DevTools is for trying. Put the change in the file and commit |
| A style does nothing | Typo, `=` instead of `:`, missing semicolon between declarations, or misspelled property | Good discovery moment first. Then: Inspect the element. A struck-through or yellow-warning line in Styles shows the broken declaration |
| `.note` rule does nothing | The HTML says `class="note"` but the CSS says `note` (missing dot), or the reverse | Selector needs the dot; the attribute doesn't |
| Stylesheet not applied | `href` doesn't match the file name or folder, or the `<link>` is outside `<head>` | Both files must be in `docs/`, and `href="style.css"` matches the name exactly (case-sensitive) |
| Link to `about.html` gives a 404 | File isn't in `docs/`, or the name differs | Move or rename it to `docs/about.html` |
| The CERN page or Zen Garden won't load | Site down or blocked | Skip it. The point survives without it |
