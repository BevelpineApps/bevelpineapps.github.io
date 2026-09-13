# Bevelpine Apps

We build small, focused Atlassian apps. Each one does a single job, runs
entirely on Atlassian Forge, and makes no outbound network calls.

## Our apps

### Read Receipts for Confluence

Know who has read your policies and who hasn't, with dates. Require read
acknowledgement on any Confluence page, name who must read it, and see who has
confirmed and who has not.

[Documentation](/documentation/read-receipts/) &middot;
[Privacy policy](/privacy) &middot;
[Security](/security/) &middot;
[Support](/support/)

### Bulk Excel &amp; CSV Exporter for Jira

Export any Jira project or saved filter to a real Excel (.xlsx) or CSV file, up to
50,000 issues per export.

[Documentation](/documentation/bulk-excel-csv-exporter/) &middot;
[Privacy policy](/apps-privacy/) &middot;
[Security](/security/) &middot;
[Support](/support/)

### Hide from Export for Confluence

Keep content on the page and remove it from PDF and Word exports. Wrap the
content in the macro; it stays visible and editable for your team, and the export
drops it.

[Documentation](/documentation/hide-from-export/) &middot;
[Privacy policy](/apps-privacy/) &middot;
[Security](/security/) &middot;
[Support](/support/)

### Initiative Timeline for Jira

Keep a shared list of initiatives with dates, attach Jira issues to each one by
issue key, and see them as lanes on one timeline with a % done figure read from
Jira.

[Documentation](/documentation/initiative-timeline/) &middot;
[Privacy policy](/apps-privacy/#initiative-timeline-for-jira) &middot;
[Security](/security/) &middot;
[Support](/support/)

### User Access Audit for Jira

List the accounts on your Jira site with their groups and the products those
groups grant, filter the list, and download it as CSV. Read-only.

[Documentation](/documentation/user-access-audit/) &middot;
[Privacy policy](/apps-privacy/#user-access-audit-for-jira) &middot;
[Security](/security/) &middot;
[Support](/support/)

### Coloured Labels for Jira

Give a Jira label a colour once for the whole site, and see each issue's labels
as coloured chips in the app's own issue panel.

[Documentation](/documentation/coloured-labels/) &middot;
[Privacy policy](/apps-privacy/#coloured-labels-for-jira) &middot;
[Security](/security/) &middot;
[Support](/support/)

## How we build

- **Everything runs on Atlassian Forge.**
- **No outbound calls.** No analytics, no tracking, no third-party services, and
  no data sent to any service outside your Atlassian site. A file a user
  downloads (an Exporter export, or a User Access Audit CSV) is made in the
  browser and saved to that user's own computer.
- **The permissions each app asks for.** Read Receipts asks only for access to
  its own storage. The Exporter asks only to read Jira work. Hide from Export
  asks for nothing at all. Initiative Timeline and Coloured Labels ask to read
  Jira work and for their own storage. User Access Audit asks for five
  read-only Jira permissions.
- **We publish what each app does not do**, on every documentation page.

## Contact

Support: [bevelpine.support@proton.me](mailto:bevelpine.support@proton.me)
&middot; Mon&ndash;Fri, 09:00&ndash;17:00 BST. We aim to reply within 2 business
days.
