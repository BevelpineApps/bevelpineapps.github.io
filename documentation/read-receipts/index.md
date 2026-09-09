# Read Receipts for Confluence

Require read acknowledgement on any Confluence page, and see who has read it and
who hasn't.

## Where to find it after installing

The app adds an item to the **byline** of every Confluence page &mdash; the row
under the page title, next to the author's name. It is labelled
**Acknowledgement**. There is no admin screen to visit and nothing to switch on
first.

## Requiring acknowledgement on a page

1. Open the page.
2. In the byline under the page title, click **Acknowledgement**.
3. Switch **Requires acknowledgement** on.
4. Under **Who must acknowledge this page**, add the people who need to read it.
   Only the people you add here count as outstanding.
5. Click **Save who must acknowledge**.

The first person to configure a page manages it. The panel always shows who that
is, under **Managed by**.

## How readers acknowledge

Anyone who still needs to acknowledge the page sees a banner at the top:
*"This page requires a read acknowledgement."* They click **I have read this
page**. That records their Atlassian identity and a server-side timestamp. There
is no second step, and a reader can only acknowledge as themselves.

## Seeing who has read it

The **Who has acknowledged** panel on the page shows:

- **Acknowledged** &mdash; everyone who has confirmed, with the date each did it.
- **Not yet** &mdash; the people you nominated who have not confirmed. This is
  your chase list. It is not everyone who can view the page, and not the space
  members.

## Things worth knowing

- Acknowledgements are written once and are never edited or overwritten.
- Switching the requirement off does not delete existing records. They are still
  there when you switch it back on.
- Someone who acknowledges **without** being nominated still appears under
  **Acknowledged**. They will not appear under **Not yet**, because that list is
  drawn only from the people you nominated.
- Configuration is **per page**. There is no way to require acknowledgement across
  a whole page tree today.

## Limits and known issues

### The panel reads the first 100 acknowledgements per page

This is the one limit you need to plan around, and it does more than truncate a
list.

The panel loads **the first 100 acknowledgement records** for a page. When there
are more than 100, the panel shows a warning that the lists are incomplete
&mdash; but the **Not yet** list is calculated by subtracting the
acknowledgements it loaded from the people you nominated. So **someone whose
acknowledgement sits beyond the first 100 is shown under "Not yet" even though
they have acknowledged the page.**

**What that means in practice:** on a page with more than 100 acknowledgements,
the "Not yet" list is not a reliable chase list and must not be used as a
compliance record. It can name people who have complied.

**Until this is fixed, keep the nominated list for any one page under 100
people.** If you need more than that, split the audience across several pages
&mdash; for example one page per team or per site &mdash; and each page's panel
stays accurate.

A fix that pages through the full set is written and tested but is **not yet in
the released version**. This page will be updated when it ships.

### Other limits

- **Per page only.** No page-tree or space-wide acknowledgement.
- **No email reminders.** The app does not notify or chase anyone. The panel is
  the chase list, and you do the chasing.
- **No export.** There is no CSV or PDF export of the acknowledgement record; you
  read it from the panel.
- **No page-version tracking.** An acknowledgement records that a person clicked
  the button on that page, not which revision of the page they saw. If you edit
  the page substantially, existing acknowledgements are not invalidated and
  readers are not asked again.
- **No deadlines or due dates.**

## Your data

The app runs entirely on Atlassian Forge. Acknowledgements are stored in Forge
hosted storage inside your own Atlassian tenancy. The app makes no outbound
network calls and its only declared permission is access to its own storage.

See [Security](/security/) and the
[privacy policy](/privacy) for the full detail.

## Support

[bevelpine.support@proton.me](mailto:bevelpine.support@proton.me) &middot;
Mon&ndash;Fri, 09:00&ndash;17:00 BST &middot; [Support](/support/)
