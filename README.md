<h1 align="center">ViMemory — Landing Page</h1>

<p align="center">
  <em>One memory every model reads from. This is the page that gives it away.</em>
</p>

---

This is the marketing site for [ViMemory](https://vimemory.xyz) — a self-hosted memory layer that every AI model can read from and write to. Hit a limit in one model, switch to another, and your context follows you.

The page's job is simple: tell the story honestly, capture an email, and hand over the build (key + endpoint + docs + the open-source repos). No framework, no build step, no `node_modules`. Two HTML files and three images.

## What's in here

```
index.html          The landing page
install.html        Non-tech install guide (you paste one prompt into Claude/ChatGPT, it sets up for you)
architecturevi.png  The "under the hood" diagram
rasyacta.png        The hero flow image (Claude → ViMemory → opencode)
welcome-email.md    Copy for the Loops welcome email + setup notes
```

That's the whole thing. Open `index.html` in a browser. It works.

## Stack

No stack. That's the point.

- **HTML + CSS + a little vanilla JS** — single-file, no dependencies.
- **Geist** (display) + **Inter** (body) + **Space Mono** (labels), via Google Fonts.
- **[Loops](https://loops.so)** for email capture — the form posts to a Loops form endpoint, double opt-in keeps the dummy emails out.

If you were expecting a Next.js monorepo here, this isn't it. A landing page is text, a form, and two images. Don't make it more than that.

## The form

`index.html` has one form. It POSTs to a Loops form endpoint (`no-cors`, so it works from any origin), drops the contact into a mailing list, and Loops fires the welcome email after the user confirms.

To point it at your own Loops account, change one line near the bottom of `index.html`:

```js
var LOOPS_ENDPOINT = "https://app.loops.so/api/newsletter-form/YOUR_FORM_ID";
```

And the mailing list ID it subscribes to:

```js
body.append('mailingLists', 'YOUR_LIST_ID');
```

Two things Loops handles, not the page: **double opt-in** (turn it on — it's what filters throwaway emails) and the **welcome email** (copy lives in `welcome-email.md`).

## Deploy

Drag the folder onto any static host — Cloudflare Pages, Netlify, Vercel, GitHub Pages. There's nothing to build.

```
# or just open it
open index.html
```

## FAQ

**Where's the actual product?**
Not here. This is the front door. The gateway lives at [arya-wtf/vimemory](https://github.com/arya-wtf/vimemory), the local connector at [arya-wtf/vimemory-localmcp](https://github.com/arya-wtf/vimemory-localmcp).

**Why no framework?**
A static page that loads instantly and never breaks beats a clever one that needs a build pipeline to show a paragraph of text.

**Can I edit the copy?**
It's all right there in `index.html` and `install.html`, in plain HTML. No CMS, no components to hunt through.

**Why does the landing page list the bad parts of the product?**
Because honesty converts the right people and repels the wrong ones. Read the page.

## Built by

A working build by **[Elux Space](https://www.elux.space)**. We don't just design it. We build it.

## License

[MIT](LICENSE).
