# Security

This page covers all three Bevelpine apps. All three run entirely on Atlassian
Forge, inside your own Atlassian tenancy.

## The short version

| | Read Receipts | Bulk Excel &amp; CSV Exporter | Hide from Export |
|---|---|---|---|
| Atlassian permissions requested | app storage only | read Jira work only | **none** |
| Stores data | acknowledgement records + page settings | **nothing** | **nothing** |
| Outbound network calls | **none** | **none** | **none** |
| Analytics or tracking | none | none | none |
| Third-party services | none | none | none |
| Data leaves Atlassian | **no** | **no** | **no** |

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

## Where data is stored

Read Receipts uses Atlassian's own Forge hosted storage, inside your tenancy.
Nothing is stored by Bevelpine Apps anywhere else, for any app.

## Egress

None of the three apps makes an outbound network call. There is no Bevelpine
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
Bevelpine Apps does not copy data to any other location.

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
