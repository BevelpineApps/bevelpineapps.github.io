# Label Colors for Jira

Give a Jira label a color once for the whole site, then see each issue's labels
as colored chips in the app's own issue panel. The app never changes the labels
on an issue.

## Where to find it after installing

The app has two parts.

- **The settings page, where colors are set.** Click **Settings** (the gear)
  in Jira's top bar and choose **Marketplace apps**. In the left-hand menu, under
  **Apps**, choose **Label Colors**.
- **The issue panel, where colors are shown.** Open an issue, click the **View
  app actions** button under the issue title, and choose **Label Colors**. The
  panel is added to that issue and is still there when the issue is reloaded.
  Other issues need the panel added the same way. To take it off an issue, open
  the panel's **More actions** menu and choose **Remove**.

## Giving a label a color

On the settings page, under **Give a label a color**:

1. In **Label**, type the label exactly as it appears in Jira. Capitals matter.
   A label cannot contain spaces, and can be up to 255 characters.
2. In **Color**, choose one of the 21 colors offered, for example *Green —
   accent-green*. *Default (gray)* is what an uncolored label looks like. A
   preview chip next to the buttons shows the result.
3. Click **Save color**.

The page confirms the save, for example *"needs-review" is now colored*. Saving
the same label again with a different color says *"… changed color"*. The Label
field empties after a successful save.

Nothing is saved, and the page says why, when:

- the label is empty: *"Type the label you want to color."*
- the label contains a space: *"A Jira label cannot contain spaces, so a mapping
  with a space in it could never match anything."*
- the label is longer than 255 characters, for example: *"Jira refuses a label
  longer than 255 characters … and this one is 256."*

After a refused save, your text stays in the field so you can correct it.

**Colors set on this site** lists the mappings with the columns **Label**,
**How it looks**, **Color** and **Last changed (UTC)**, and a count such as
*"Showing all 1 mapping."*

## Removing a color

Click **Remove color** on a row and confirm. The page says, for example,
*"needs-review" is back to the default color*. Issues carrying that label then
show it as *Default (gray)*, like any label with no color. The label itself is
not touched.

## Reading the panel

- Each label on the issue is shown as a chip. A label with a color takes that
  color. A label without one is shown as *Default (gray)*.
- An issue with no labels says *"No labels on this issue."*
- **The panel shows at most 50 labels.** On an issue with more, it shows the
  first 50 and says so, for example *"Showing the first 50 of 51 labels. 1 more
  was not loaded."*
- A label too long for its chip is shortened in the chip, and printed in full
  underneath.
- The panel reads the colors when the issue loads. **An open panel does not
  update when a color is changed.** Reload the issue to see the change.
- If the color mapping cannot be loaded, the panel says so, and says that the
  chips are showing the default color because the mapping did not arrive.

## Permissions

The app asks for two Atlassian permissions:

- **read:jira-work**: read an issue's labels;
- **storage:app**: store the label-to-color mappings.

The app has no write permission for Jira and never changes an issue.

## Limits and known issues

- **Colors appear only inside this app's panel.** The app does not restyle
  Jira's own Labels field, boards, backlogs, search results, dashboards, emails
  or exports.
- **The panel is added issue by issue.** It does not appear on issues by
  itself.
- **Matching is exact, including capitals.** *High* and *high* are two different
  labels.
- **One set of colors per Jira site.** There are no per-project or per-user
  colors, and no import or export.
- **Two saves of a color for the same label at the same time: the last save
  wins**, and the page that saved first is not told. Colors for different labels do not affect
  each other.
- **Only the colors offered can be used.** There is no free color picker and
  no hex values.
- **The settings page draws at most 200 mappings.** If there are more, the page
  says the list is not complete.
- **Long unbroken text contains invisible characters.** So that a very long
  label cannot push the page sideways, the app inserts an invisible zero-width
  space (U+200B) every 24 characters into unbroken runs longer than that. This
  happens in the settings table's Label column, in its messages and
  confirmation, and in the panel's full-name lines. A label copied from this app
  and pasted into Jira therefore does not match. Type the label, or copy it from
  Jira itself.
- **Very wide characters can be clipped inside a chip.** The chip is shortened
  to an estimated width, and characters from some scripts are wider than that
  estimate, so such a label can be cut off inside its chip. Its full text is in
  the Label column of the settings table.
- **Jira Cloud only.** There is no Server or Data Center version.

## Your data

The app runs entirely on Atlassian Forge.

- **What is stored.** The mappings are stored in Forge hosted storage for your
  site's installation, one record per colored label. Each record holds:
  - the label name;
  - the color;
  - when it was set;
  - the Atlassian **account ID** of the administrator who set it.
- The account ID is never sent to any page. The app reads an issue's labels
  from Jira when the panel loads.
- **Removing a color** deletes its record.
- **Egress.** The app makes no outbound network calls.

See the [privacy policy](/apps-privacy/#label-colors-for-jira) for the full
detail.

## Support

[bevelpine.support@proton.me](mailto:bevelpine.support@proton.me) &middot;
Mon&ndash;Fri, 09:00&ndash;17:00 BST &middot; [Support](/support/)
