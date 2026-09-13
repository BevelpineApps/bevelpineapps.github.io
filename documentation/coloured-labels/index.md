# Coloured Labels for Jira

Give a Jira label a colour once for the whole site, then see each issue's labels
as coloured chips in the app's own issue panel. The app never changes the labels
on an issue.

## Where to find it after installing

The app has two parts.

- **The settings page, where colours are set.** Click **Settings** (the gear)
  in Jira's top bar and choose **Marketplace apps**. In the left-hand menu, under
  **Apps**, choose **Coloured Labels**. Only Jira administrators can save or
  remove a colour.
- **The issue panel, where colours are shown.** Open an issue, click the **View
  app actions** button under the issue title, and choose **Coloured Labels**. The
  panel is added to that issue and is still there when the issue is reloaded.
  Other issues need the panel added the same way. To take it off an issue, open
  the panel's **More actions** menu and choose **Remove**.

## Giving a label a colour

On the settings page, under **Give a label a colour**:

1. In **Label**, type the label exactly as it appears in Jira. Capitals matter.
   A label cannot contain spaces, and can be up to 255 characters.
2. In **Colour**, choose one of the 21 colours offered, for example *Green —
   accent-green*. *Default (grey)* is what an uncoloured label looks like. A
   preview chip next to the buttons shows the result.
3. Click **Save colour**.

The page confirms the save, for example *""needs-review" is now coloured"*. Saving
the same label again with a different colour says *"… changed colour"*. The Label
field empties after a successful save.

Nothing is saved, and the page says why, when:

- the label is empty: *"Type the label you want to colour."*
- the label contains a space: *"A Jira label cannot contain spaces, so a mapping
  with a space in it could never match anything."*
- the label is longer than 255 characters, for example: *"Jira refuses a label
  longer than 255 characters … and this one is 256."*

After a refused save, your text stays in the field so you can correct it.

**Colours set on this site** lists the mappings with the columns **Label**,
**How it looks**, **Colour** and **Last changed (UTC)**, and a count such as
*"Showing all 1 mapping."*

## Removing a colour

Click **Remove colour** on a row and confirm. The page says, for example,
*""needs-review" is back to the default colour"*. Issues carrying that label then
show it as *Default (grey)*, like any label with no colour. The label itself is
not touched.

## Reading the panel

- Each label on the issue is shown as a chip. A label with a colour takes that
  colour. A label without one is shown as *Default (grey)*.
- An issue with no labels says *"No labels on this issue."*
- **The panel shows at most 50 labels.** On an issue with more, it shows the
  first 50 and says so, for example *"Showing the first 50 of 51 labels. 1 more
  was not loaded."*
- A label too long for its chip is shortened in the chip, and printed in full
  underneath.
- The panel reads the colours when the issue loads. **An open panel does not
  update when a colour is changed.** Reload the issue to see the change.
- If the colours cannot be loaded, the panel says so, and says that the chips are
  showing the default colour because the colours did not arrive.

## Who can do what

- **Saving or removing a colour needs a Jira administrator.** The app asks Jira,
  on its server and as the person making the change, whether they hold
  **Administer Jira**. It refuses the change before anything is written if they
  do not, or if Jira cannot be asked.
- **Any Jira administrator can change or remove any colour**, including one set
  by somebody else.
- **The list of coloured labels can be read by any user the panel is shown to**,
  because the panel needs it to draw. For each label it holds the label name,
  the colour and when it was set.

## Permissions

The app asks for two Atlassian permissions:

- **read:jira-work**: read an issue's labels, and ask Jira whether the person
  changing a colour is a Jira administrator;
- **storage:app**: store the label-to-colour mappings.

Both Jira reads are made as the person using the app. The app has no write
permission for Jira and never changes an issue.

## Limits and known issues

- **Colours appear only inside this app's panel.** The app does not restyle
  Jira's own Labels field, boards, backlogs, search results, dashboards, emails
  or exports.
- **The panel is added issue by issue.** It does not appear on issues by
  itself.
- **Matching is exact, including capitals.** *High* and *high* are two different
  labels.
- **One set of colours per Jira site.** There are no per-project or per-user
  colours, and no import or export.
- **Two administrators colouring the same label at the same time: the last save
  wins**, and the first is not told. Colours for different labels do not affect
  each other.
- **Only the colours offered can be used.** There is no free colour picker and
  no hex values.
- **The settings page draws at most 200 mappings**, and counts up to 2,000. If
  there are more, the page says the list is not complete.
- **Long unbroken text contains invisible characters.** So that a very long
  label cannot push the page sideways, the app inserts an invisible zero-width
  space (U+200B) every 24 characters into unbroken runs longer than that. This
  happens in the settings table's Label column, in its messages and
  confirmation, and in the panel's full-name lines. A label copied from this app
  and pasted into Jira may therefore not match. Type the label, or copy it from
  Jira itself.
- **Very wide characters can be clipped inside a chip.** The chip is shortened
  to an estimated width, and characters from some scripts are wider than that
  estimate, so such a label can be cut off inside its chip. Its full text is in
  the Label column of the settings table.
- **Jira Cloud only.** There is no Server or Data Center version.

## Your data

The app runs entirely on Atlassian Forge.

- **What is stored.** The mappings are stored in Forge hosted storage for your
  site's installation, one record per coloured label. Each record holds:
  - the label name;
  - the colour;
  - when it was set;
  - the Atlassian **account ID** of the administrator who set it.
- **What is not stored.** The account ID is never sent to any page. The app
  does not store issues or their labels; it reads an issue's labels from Jira
  when the panel loads.
- **Removing a colour** deletes its record.
- **Egress.** The app makes no outbound network calls.

See the [privacy policy](/apps-privacy/#coloured-labels-for-jira) for the full
detail.

## Support

[bevelpine.support@proton.me](mailto:bevelpine.support@proton.me) &middot;
Mon&ndash;Fri, 09:00&ndash;17:00 BST &middot; [Support](/support/)
