---
name: fc
description: >
  Fetch a web page's full text and images via Firecrawl, then carry out the
  user's request over that content. Trigger this WHENEVER the user's message
  starts with "fc " followed by a URL or domain — e.g. "fc example.com
  summarize in 5 bullets", "fc https://blog.com/post what are the main claims",
  "fc site.com". This replaces WebFetch: use it for ANY url the user hands you
  with the "fc" prefix. Firecrawl extraction is far cleaner than WebFetch.
---

The user's message has the form: `fc <url> <instruction...>`

Do exactly this:

1. Parse the message: the FIRST token after `fc` is the URL (a domain or full
   link). EVERYTHING after the URL is the user's INSTRUCTION.

2. Run this one command and capture its output:
   `~/bin/fc-scrape "<url>"`
   It prints a single line: the path to a local folder. It also copies the
   scrape to Google Drive in the background — do NOT wait on or mention Drive
   unless asked.

3. Read the file `content.md` inside that printed folder. This is the full page
   text. (Images are downloaded into the folder's `images/` subdirectory and
   listed inline in the markdown — read them from there only if the instruction
   needs the actual images.)

4. Carry out the user's INSTRUCTION using `content.md` as the source material,
   and output the result directly in the chat — nothing else.

5. If there is no instruction after the URL, give a concise summary of the page.

Notes:
- Do NOT use WebFetch — `fc-scrape` IS the fetch step.
- If `fc-scrape` errors or content.md is empty, say so plainly and show the
  error; do not silently fall back to WebFetch.
