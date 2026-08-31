Security Policy — Read Receipts for Confluence
Last updated: 31/08/2026

This page describes the security practices for Read Receipts for Confluence, published by Bevelpine Apps.

What the app stores

The app stores the minimum needed to do its job, and nothing else. It records three things when a reader acknowledges a page: the reader's Atlassian account ID, the page ID, and the date and time of the click. For each configured page it also stores the page settings: whether acknowledgement is required, the account IDs of the people asked to acknowledge, and the account ID of the person managing the page.

The app does not read or store page content.

Where data is stored

All data is stored inside Atlassian's Forge platform (the app's own Forge storage), within Atlassian's infrastructure. Nothing is stored by Bevelpine Apps outside Atlassian.

Data handling and egress

The app makes no outbound network calls. It does not send any data to third parties, and it uses no analytics or tracking. Data is handled only by Atlassian's platform.

Encryption

Data is protected in transit and at rest by Atlassian Forge's standard security controls (HTTPS/TLS in transit; encryption of Atlassian-hosted storage at rest). Bevelpine Apps does not copy data to any other location.

Vulnerability management

If you discover a security issue, please report it to bevelpine.support@proton.me. We aim to respond within 2 business days and will keep you informed.

Security certifications

Read Receipts for Confluence does not currently hold third-party security certifications or compliance attestations.
