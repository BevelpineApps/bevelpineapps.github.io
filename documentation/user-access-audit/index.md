# User Access Audit for Jira

List the accounts on your Jira site, with the groups each account belongs to and
the Jira products those groups grant, then filter the list and download it as a
CSV file. The app is read-only.

## Where to find it after installing

The app is a **global page**. Open **Apps** in Jira's sidebar and choose
**User Access Audit**. There is nothing to configure first.

## Running the audit

1. Open the app. It first asks Jira whether you hold the **Administer Jira**
   global permission.
2. Click **Run the audit**. The page shows its progress while it reads the
   site's groups, each group's members, and the account list.
3. When it finishes, the page shows a summary. Here is an example from our test
   site:
   - *"Showing all 544 accounts."*
   - *"544 accounts · 544 active · 0 inactive"*
   - *"496 Person · 48 App / integration"*
   - *"35 hold at least one product · 509 hold none · 493 belong to no group"*
   - a count per product;
   - *"31 groups walked · 37 Jira requests · caps: 5000 accounts, 500 groups,
     5000 members per group"*

Click **Run the audit again** to read everything afresh.

## The table

The table has the columns **Name**, **Type**, **Active**, **Product access
(granted via)**, **Groups** and **Account id**.

- **Active** is the active flag Jira reports for the account.
- **Product access** names each product the account's groups grant, and the
  group that grants it, in the form *Jira Software (via group-name)*. Which group
  grants which product is read from Jira's own application-role settings.
- **Email** is shown under the name only where Jira returns it, and the app
  never guesses it.

The table draws at most **200** accounts, 25 to a page. When more accounts match,
the page says so, for example: *"544 of 544 audited accounts match this filter.
Showing the first 200 of them on screen — that is this page's display limit of
200, and the other 344 are NOT drawn below. The CSV contains all 544."*

## Filtering

Above the table you can filter by:

- **Name, email or account id**: free text;
- **Account type**: *All account types*, or one type;
- **Status**: *Active and inactive*, *Active only* or *Inactive only*;
- **Product access**: *Any or no product*, *No product access*, or one product;
- **Group**: *Any or no group*, *In no group at all*, or one group.

The page repeats the text it actually filtered by, and the count that matches,
next to each other, in the form *"Text filter applied: [your text]"* and
*"&lt;n&gt; of &lt;total&gt; audited accounts match this filter."* **Clear text** empties the text box.

## Downloading the CSV

**Download CSV** saves the accounts that match your current filters: all of
them, not only the 200 drawn on screen. The button is unavailable when no account
matches.

- **Filename:** `jira-user-access-audit-YYYY-MM-DD.csv`.
- **Opening lines:** the file starts with lines whose text begins `#`. They
  record:
  - when the file was made;
  - the filters used;
  - how many rows it contains;
  - a *COMPLETE* line saying that everything was loaded;
  - a note that email can be blank;
  - a note that last-login dates are not available.
- **Columns:** `account_id`, `display_name`, `account_type`,
  `account_type_label`, `active`, `email`, `groups`, `products`,
  `product_granted_via` and `in_user_directory`.
- **Format:** UTF-8 with a byte-order mark and Windows line endings.
- **Formula protection:** a value that begins with `=` has an apostrophe put in
  front of it.

## Permissions

The app asks for five Atlassian permissions, all of them read-only:

- **read:user:jira**: read the account list;
- **read:group:jira**: read the site's groups and their members;
- **read:application-role:jira**: read which groups grant which product;
- **read:avatar:jira**: the avatars those endpoints return;
- **read:permission:jira**: ask Jira whether you hold Administer Jira.

It asks for no write permission of any kind. Every call is made from your
browser as you.

## Limits and known issues

- **No last-login or last-active dates.** This app cannot tell you who is
  dormant or who has not logged in recently.
- **It cannot change anyone.** It cannot deactivate, remove, suspend or invite
  an account. It cannot add or remove group memberships.
- **Jira only.** Product access is read from Jira's application roles. The app
  does not describe Confluence access, and does not evaluate project permission
  schemes or issue security.
- **The load is capped** at 5,000 accounts from the account list, 500 groups and
  5,000 members per group.
- **It is not a billing report.** It shows product access, not your invoice.
- **Nothing is remembered.** Each visit starts from scratch. There is no
  history, no comparison with an earlier audit, no scheduling and no alerting.
- **Jira Cloud only.** There is no Server or Data Center version.

## Your data

- **Nothing is stored.** The app has no storage permission and no backend
  function. Everything on screen is read from Jira in your browser session and is
  gone when you leave the page.
- **The CSV is made in your browser** and saved to your own computer. It
  contains account names and account IDs, plus any email addresses Jira
  returned. Handle it as personal data.
- **Egress.** The app makes no outbound network calls.

See the [privacy policy](/apps-privacy/#user-access-audit-for-jira) for the full
detail.

## Support

[bevelpine.support@proton.me](mailto:bevelpine.support@proton.me) &middot;
Mon&ndash;Fri, 09:00&ndash;17:00 BST &middot; [Support](/support/)
