# Initiative Timeline for Jira

Keep one list of initiatives with start and end dates, attach the Jira
issues that belong to each one by issue key, and see the initiatives as lanes on
a single timeline, each with a % done figure read from Jira.

## Where to find it after installing

The app is a **global page**. Open **Apps** in Jira's sidebar and choose
**Initiative Timeline**. There is nothing to configure first.

## Adding an initiative

At the bottom of the page, under **New initiative**:

1. Enter a **Name**. It is required, and can be up to 120 characters.
2. Optionally enter a **Start date** and an **End date**, written as
   `YYYY-MM-DD` (for example `2026-10-01`).
3. In **Issue keys**, enter the keys of the Jira issues that belong to this
   initiative, separated by commas, spaces or new lines. One initiative can link
   up to 100 keys.
4. Click **Add initiative**.

Before you save, the form tells you what it made of the keys you entered, for
example: *"2 valid key(s) recognised. 1 duplicate(s) collapsed: KAN-3. 1
entry/entries are not issue keys and will be ignored: not-a-key."* Keys are
upper-cased, so `kan-3` and `KAN-3` count as the same key.

After a save the page confirms it, for example *"Added "Mobile app relaunch". 4
issue key(s) linked."*, and the form empties.

The app never finds issues for you. It reads only the keys you enter.

### What the form refuses

Nothing is saved, and the form says why, when:

- the name is empty: *"Name is required."*
- the name is longer than 120 characters: *"Name is 121 characters; the limit
  is 120."*
- a date is not a real date in `YYYY-MM-DD` form: *"Start date "01/10/2026" is
  not a real date. Use YYYY-MM-DD, for example 2026-01-31."*
- the end date is before the start date: *"End date 2026-05-01 is before the
  start date 2026-06-01."*
- there are more than 100 issue keys. The form warns you before you click, and
  the save is refused with a message that names the keys beyond the limit. The
  app does not quietly keep the first 100.

## Reading the page

**The list sentence** at the top says how many initiatives are shown, for
example *"Showing all 5 initiatives."*

**The timeline** has one lane per initiative. Each lane is positioned and sized
by that initiative's own dates, against the span of all the dated initiatives,
which the caption states: *"Timeline spans 2026-01-12 to 2026-12-18 (341 days),
across 5 dated initiatives."* The bars show dates, not progress.

- An initiative with only a start date or only an end date is drawn as a single
  day.
- An initiative with no dates is not drawn. The caption says so, for example
  *"1 initiative has no dates and is listed below the chart instead of drawn on
  it."*

**% done** appears under each lane and on each initiative's card, for example
*"0% done — 0 of 2 linked issue(s) are in a Done status category."* It is the
share of the linked issues that Jira returned whose status is in Jira's **Done**
status category. It is a count of issues, not of story points or hours.

**Keys that Jira did not return** are named on the card and left out of the
percentage, rather than counted as not done:
*"1 of 3: KAN-58. They may have been deleted, moved, or be invisible to you."*
A key that does not exist is reported this way.

**The issue status line** under the timeline says how many of the linked keys
Jira returned, for example *"Issue status: 15 of 16 distinct linked key(s)
returned by Jira, over 1 query and 1 page(s)."*

**Show issues** on a card opens a table of that initiative's issues with the
columns **Issue**, **Summary**, **Status** and **Done?**.

## Editing and deleting

- **Edit** on a card loads that initiative into the form. Change it and click
  **Save changes**. The page confirms it, for example *"Saved "Mobile app
  relaunch". 4 issue key(s) linked."*
- **Delete** on a card asks you to confirm first, then removes the initiative
  and says *"Initiative deleted."* No Jira issue is touched. A deleted
  initiative cannot be recovered.

## Permissions

The app asks for two Atlassian permissions:

- **read:jira-work**, to read the status and summary of the issue keys you
  attach;
- **storage:app**, to store your initiatives.

The app never creates, edits, transitions or deletes anything in Jira.

## Limits and known issues

- **For a moment after the page loads, and after you add an initiative, the page
  can wrongly say that linked issues did not come back from Jira.** The issues
  have not been deleted. The page corrects itself once Jira's answer arrives.
  - When we loaded the page, every card with linked issues briefly said *"No
    progress can be shown: none of the … linked issue(s) came back from Jira"*,
    and the issue status line read *"0 of 0"*. About a second later both were
    correct.
  - After adding an initiative whose issues were not already on the page, the
    new card said none of its issues came back. In our measurements it was
    corrected within about three seconds of clicking **Add initiative**.
  - **What to do:** wait until the issue status line shows the number of keys
    Jira returned, or reload the page. This page will be updated when a fix is
    released.
- **Typing very quickly into the Name field can occasionally drop a
  character.** With keystrokes 80 milliseconds apart, characters were lost in 2
  of 12 attempts. With keystrokes 150 milliseconds apart, none were lost in 11
  attempts. Check the name before you click **Add initiative**. You can correct a
  saved name with **Edit**.
- **The page shows at most 200 initiatives.** If there are more, the page says
  how many it showed and how many exist, for example *"Showing the first 200 of
  208 initiatives. 8 more were not loaded."*
- **One initiative links at most 100 issue keys**, and a name is at most 120
  characters. Longer input is refused, not trimmed.
- **No automatic discovery.** The app does not find issues by epic, parent,
  label, project or JQL. Only the keys you enter are read.
- **Not a scheduling tool.** There are no dependencies, no drag-and-drop (dates
  are typed), no automatic scheduling, no sprints and no capacity planning.
- **One list per Jira site.** There are no per-project or per-person lists, and
  no way to restrict who can see or edit an initiative.
- **Two edits of the same initiative at the same time: the last save wins**,
  and the page that saved first is not told. Saves to different initiatives do
  not affect each other.
- **No history and no undo.**
- **No export and no notifications.** Nothing runs unless someone has the page
  open.
- **Long unbroken text contains invisible characters.** So that a very long
  word cannot push the page sideways, the app inserts an invisible zero-width
  space (U+200B) every 24 characters into unbroken runs longer than that, on the
  cards, in the issue table, in the key-box messages and in the delete
  confirmation. Nothing is removed. But text copied off the page carries those
  characters, so paste it into a plain-text editor before using it as an issue
  key or identifier. On the timeline itself a name with a very long unbroken run
  scrolls sideways inside its label instead.
- **Jira Cloud only.** There is no Server or Data Center version.

## Your data

The app runs entirely on Atlassian Forge.

- **What is stored.** Your initiatives are stored in Forge hosted storage for
  your site's installation. Each initiative record holds:
  - its name, dates and linked issue keys;
  - when it was created and last updated;
  - the Atlassian **account IDs** of the people who created it and last updated
    it.
- Account IDs are never sent to the page. Issue summaries and statuses are read
  from Jira each time the page loads.
- **Egress.** The app makes no outbound network calls.

See the [privacy policy](/apps-privacy/#initiative-timeline-for-jira) for the
full detail.

## Support

[bevelpine.support@proton.me](mailto:bevelpine.support@proton.me) &middot;
Mon&ndash;Fri, 09:00&ndash;17:00 BST &middot; [Support](/support/)
