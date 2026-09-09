# Hide from Export for Confluence

Keep content on the page for your team, and remove it from PDF and Word exports.

## Where to find it after installing

There is no admin screen and nothing to configure. In the Confluence **editor**,
type `/` and search for **Hide from Export**, then press Enter to insert the
macro. Type your content **inside** it.

## Using it

1. Edit the page.
2. Type `/` and choose **Hide from Export**.
3. Put the content you want kept out of exports inside the macro body &mdash;
   text, tables, code blocks, or anything else you can place on a page.
4. Publish.

The content stays fully visible and editable on the page. Anyone who can read the
page reads it normally. When the page is exported to PDF or Word, everything
inside the macro is dropped and the rest of the page exports as usual.

An empty macro renders as a single blank line. It is not broken; put something
inside it.

## What is covered

| Path | Covered? |
|---|---|
| **Export to PDF** (page &rarr; &hellip; &rarr; Export &rarr; PDF) | **Yes** |
| **Export to Word** (page &rarr; &hellip; &rarr; Export &rarr; Word) | **Yes** |
| **Space export to HTML** | **Yes** |
| **Browser print / Ctrl+P** | **No &mdash; see below** |

## What it does NOT do

**It does not hide anything from your browser's own print command.** If a reader
presses **Ctrl+P** (or Cmd+P) on the page, or uses the browser's *Print* menu,
the printed page and any PDF produced that way **include the content inside the
macro**, because the browser prints the live page exactly as it appears on
screen.

This app hooks into Confluence's **Export** feature. Browser printing never
reaches Confluence's export at all, so no Confluence macro can intercept it.

**So: this is the right tool for controlling what leaves in an exported
document. It is not a security control, and it is not redaction.** Anyone who can
read the page can read the content &mdash; by looking at it, by copying it, or by
printing the page in their browser. If content must not be seen by someone, do
not put it on a page they can open.

### Other limits

- **No configuration.** There are no settings, no per-macro options, and no way
  to hide from PDF but not Word, or the reverse.
- **No visible marker in the exported file.** The content is dropped silently.
  The export contains no placeholder and no note that anything was removed.
- **No "only print" counterpart.** There is no macro for content that appears
  *only* in exports.
- **Space export to PDF** is not available on every Confluence edition. Where
  Confluence offers it, the same macro applies; we have confirmed space export to
  **HTML**.

## Your data

The app requests **no Atlassian permissions at all** and stores nothing. It reads
the macro's own body from the page context Confluence gives it, and returns an
empty document when Confluence asks it for export content. It makes no outbound
network calls.

See [Security](/security/) and the
[privacy policy](/apps-privacy/) for the full detail.

## Support

[bevelpine.support@proton.me](mailto:bevelpine.support@proton.me) &middot;
Mon&ndash;Fri, 09:00&ndash;17:00 BST &middot; [Support](/support/)
