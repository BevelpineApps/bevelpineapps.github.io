# Security

This page covers the six Bevelpine apps documented on this site. All six run
entirely on Atlassian Forge.

## The short version

| | Read Receipts | Bulk Excel &amp; CSV Exporter | Hide from Export |
|---|---|---|---|
| Atlassian permissions requested | app storage only | read Jira work only | **none** |
| Stores data | acknowledgement records + page settings | **nothing** | **nothing** |
| Outbound network calls | **none** | **none** | **none** |
| Analytics or tracking | none | none | none |
| Third-party services | none | none | none |
| Data leaves Atlassian | **no** | **no** | **no** |

| | Initiative Timeline | User Access Audit | Label Colors |
|---|---|---|---|
| Atlassian permissions requested | read Jira work + app storage | five read-only Jira permissions | read Jira work + app storage |
| Stores data | initiative records, including account IDs | **nothing** | label colours, including an account ID |
| Outbound network calls | **none** | **none** | **none** |
| Analytics or tracking | none | none | none |
| Third-party services | none | none | none |
| Data leaves Atlassian | **no** | **no**, except a CSV a user chooses to download | **no** |

## What each app stores

**Read Receipts for Confluence.** When a reader acknowledges a page, the app
records three things: the reader's Atlassian **account ID**, the **page ID**, and
the **date and time** of the click. For each configured page it also stores that
page's settings &mdash; whether acknowledgement is required, the account IDs of
the people asked to acknowledge, and the account ID of the person managing it.
That is the complete list. The app does not store names, email addresses, or page
content. Names shown in the app are rendered by Confluence itself from account
IDs at display time.

**Bulk Excel &amp; CSV Exporter for Jira.** Stores nothing. The export file is
built in your browser from data Jira has already sent to your own session, and is
handed straight to your browser's downloads. It is never uploaded anywhere.

**Hide from Export for Confluence.** Stores nothing, and requests no Atlassian
permissions at all. It reads the macro's own body from the page context it is
given, and returns an empty document when Confluence asks it for export content.

**Initiative Timeline for Jira.** For each initiative, the app stores its name,
start and end dates, and the Jira issue keys attached to it; when it was created
and last updated; and the Atlassian **account ID** of the person who created it
and of the person who last updated it. It also stores one record noting when it
last checked for data to migrate, and how many records it migrated and skipped.
The account IDs are recorded by the app's server-side code and are never sent to
the page. Issue summaries and statuses are read from Jira each time the page
loads. An initiative is kept until someone deletes it in the app; deleting it
removes its record.

**User Access Audit for Jira.** Stores nothing. The app has no storage
permission and no server-side code, and keeps no record between visits. When a
Jira user runs the audit, the app reads the site's account list, its groups and
their members, and which groups grant which products, and shows the results in
that user's browser. They include each account's display name and account ID,
and the email address where Jira returns it. If the user downloads the CSV, it
is made in their browser and saved to their own computer, and it contains the
same account details. Handle it as personal data.

**Label Colors for Jira** (shown in Jira as Coloured Labels). The app stores one record per coloured label: the
label name, the colour, when it was set, and the Atlassian **account ID** of the
administrator who set it. The account ID is recorded by the app's server-side
code and is never sent to any page. The app reads an issue's labels from Jira
when the issue panel loads. A colour is kept until an administrator removes it
in the app; removing it deletes its record.

## Where data is stored

Read Receipts uses Atlassian's own Forge hosted storage, inside your tenancy.
Initiative Timeline and Label Colors use Forge hosted storage for the app's
installation on your site. Nothing is stored by Bevelpine Apps anywhere else,
for any app.

## Egress

None of the six apps makes an outbound network call. There is no Bevelpine
server, no analytics endpoint, and no third-party service in any of them.

## Identity and authorisation (Read Receipts)

- An acknowledgement always records **the signed-in caller's own identity and a
  server-side timestamp.** Neither can be supplied by the browser. Sending a
  different account ID, page ID, or date in the request does not change what is
  recorded.
- **Who may configure a page is checked on the server** &mdash; on every
  configuration action and on reading the panel, not by hiding buttons. Someone
  who is neither the page's manager nor an invited participant cannot read the
  roster.

## Encryption

Data is protected in transit and at rest by Atlassian Forge's standard controls
&mdash; HTTPS/TLS in transit, encryption of Atlassian-hosted storage at rest.
Bevelpine Apps does not copy data to any other location. A file a user
downloads (an Exporter export, or a User Access Audit CSV) is saved to that
user's own computer, outside those controls.

## Reporting a vulnerability

Email [bevelpine.support@proton.me](mailto:bevelpine.support@proton.me) with
"security" in the subject. We aim to respond within **2 business days** and will
keep you informed.

Please give us a reasonable period to fix an issue before disclosing it publicly.
We will credit you if you would like us to.

## Certifications

**None of these apps currently holds a third-party security certification or
compliance attestation, and none is part of the Atlassian Marketplace Bug Bounty
programme.** We would rather say so plainly than leave it to be inferred.

## Privacy policies

- [Read Receipts for Confluence](/privacy)
- [Bulk Excel &amp; CSV Exporter for Jira, and Hide from Export for Confluence](/apps-privacy/)
- [Initiative Timeline for Jira](/apps-privacy/#initiative-timeline-for-jira)
- [User Access Audit for Jira](/apps-privacy/#user-access-audit-for-jira)
- [Label Colors for Jira](/apps-privacy/#label-colors-for-jira)
