# Bulk Excel &amp; CSV Exporter for Jira

Export a Jira project or a saved filter to a real Excel (.xlsx) or CSV file, up to
50,000 issues per export.

## Where to find it after installing

The app is a **global page**. Open the **Apps** menu in Jira's top navigation and
choose **Bulk Excel &amp; CSV Exporter for Jira**. There is no per-project setup
and nothing to configure first.

## Running an export

1. Open the app from the **Apps** menu.
2. Choose a **source** &mdash; a **Project** or a **Saved filter**.
3. Choose the project, or the saved filter, from the second list.
4. Choose a **format** &mdash; **Excel (.xlsx)** or **CSV**.
5. Click **Export**.

On a large export the app reports progress as it goes
(*"Fetched 200 issues so far"*), then downloads the file when it is done and
tells you how many issues it wrote.

## What is in the file

Eight columns, in this order:

**Key**, **Summary**, **Status**, **Assignee**, **Priority**, **Type**,
**Created**, **Updated**.

Dates are written in Jira's own ISO format, including the timezone offset.

## Which format to choose

**Choose Excel (.xlsx) unless you have a specific reason not to.** It is the
better file in two ways that matter:

- **Non-English text.** Accented, Greek, Japanese, Chinese and other non-ASCII
  characters are correct in the .xlsx file. **In the CSV they are not**: the CSV
  is written without a byte-order mark, so opening it by double-clicking in Excel
  on Windows renders them as mojibake (`café` becomes `cafÃ©`). If you must use
  CSV with non-ASCII data, import it into Excel with **Data &rarr; From Text/CSV**
  and set the encoding to **UTF-8**, rather than double-clicking the file.
- **Cell values that begin with a symbol.** A Jira summary starting with `=`, `+`,
  `-` or `@` is treated by Excel as a **formula** when the CSV is opened, and is
  evaluated instead of shown. The .xlsx file does not have this behaviour; values
  are written as text. If you export to CSV from a Jira site where summaries are
  not fully under your control, use Excel format instead.

Both of these are fixed in a build that has not yet been released. This page will
be updated when it ships.

## Permissions

Each user exports only the issues they can already see. The app runs the search
as the signed-in user and asks Jira for nothing more than read access to work
items. It cannot show anyone an issue they could not open in Jira.

## Limits and known issues

- **The project list stops at 50 projects.** The app reads one page of projects
  from Jira and does not page beyond it, so on a site with more than 50 projects
  the rest do not appear in the list and nothing on screen says why. If the
  project you want is missing, save a filter for it in Jira and export using the
  **Saved filter** source instead &mdash; that is the reliable workaround today.
- **The saved-filter list stops at 100 filters**, in the same way.
- **An export stops at 50,000 issues.** If a project or filter has more than
  that, the file contains the first 50,000, and the app says the export was cut
  short &mdash; on screen, in the file, and in the file name.
- **A search that matches nothing reports success.** If a saved filter refers to
  a field or value that no longer exists, Jira returns an empty result rather
  than an error, and the app reports *"Exported 0 issues"* as a success. **If you
  see a zero count you did not expect, check the filter in Jira** &mdash; the
  export did not fail, but the query almost certainly did not mean what you
  thought.
- **The columns are fixed.** You cannot add, remove or reorder them, and custom
  fields are not exported.
- **No JQL box.** You export a project or a saved filter. To export an arbitrary
  query, save it as a filter in Jira first.
- **No scheduling, no email delivery, no templates.** This app runs one export
  when you click the button.

## Your data

The file is generated in your browser from data Jira has already sent to your own
session. Nothing is stored and nothing is sent to us or to any third party. The
app makes no outbound network calls.

See [Security](/security/) and the
[privacy policy](/apps-privacy/) for the full detail.

## Support

[bevelpine.support@proton.me](mailto:bevelpine.support@proton.me) &middot;
Mon&ndash;Fri, 09:00&ndash;17:00 BST &middot; [Support](/support/)
