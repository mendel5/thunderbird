# thunderbird
How to configure Mozilla Thunderbird.

Apply all these changes before setting up any email accounts.

See also / Siehe auch:
- https://github.com/mendel5/email/
- https://github.com/mendel5/outlook/

## Open the config editor
- English: `Edit` --> `Preferences` (not: `Account Settings`) --> `General` --> Scroll to bottom --> `Config Editor`
- German: `Extras` --> `Einstellungen` (nicht: `Konten-Einstellungen`) --> `Allgemein` --> Nach ganz unten scrollen --> `Konfiguration bearbeiten`

## Change default sorting: Sort by date, newest on top, not threaded
Change the default sort order to "date" with the newest emails on top (descending).
```
Copy this:
mailnews.default
```

```
For email folders:

Set
mailnews.default_sort_order
to 2.
// The value 2 means to sort in a descending order (newest on top).

Set
mailnews.default_sort_type
to 18.
// The value 18 means to sort by the column "date".

Set
mailnews.default_view_flags
to 0.
// This disables "threaded view".
```

```
For RSS feeds and other news feeds (whatever that might be):

Set
mailnews.default_news_sort_order
to 2.
// The value 2 means to sort in a descending order (newest on top).

Set
mailnews.default_news_sort_type
to 18.
// The value 18 means to sort by the column "date".

Set
mailnews.default_news_view_flags
to 0.
// This disables "threaded view".
```

Links:
- https://superuser.com/questions/13518/change-the-default-sorting-order-in-thunderbird
- https://www.badpenguin.org/thunderbirds-default-sort/
- http://kb.mozillazine.org/Mail_and_news_settings

## Disable threaded view for single folders
How to disable `Threaded view` for a single folder (not recommended):
- See also the section above that explains how to disable the threaded view for all folders by default (recommended).
- Tags: group, sort, order, thread, Gruppierung, Sortierung, Thema, Themen
- English: `View` --> `Sort by` --> `Unthreaded`
- German: `Ansicht` --> `Sortieren nach` --> `Nicht gruppiert`

## Check all folders for new messages
How to check all folders for new messages. This is necessary when emails are sorted into multiple folders based on server-side rules.
```
Set
mail.server.default.check_all_folders_for_new
to true.

Set
mail.imap.use_status_for_biff
to false.
```

Links:
- http://kb.mozillazine.org/How_do_I_check_for_new_messages_in_other_folders

## Encryption in transit
How to adjust the minimum TLS version for encryption in transit.
```
Set
security.tls.version.min
to 4.

Other options:
0 = SSL3.0
1 = TLS1.0
2 = TLS1.1
3 = TLS1.2
4 = TLS1.3
```

Links:
- https://support.mozilla.org/en-US/kb/thunderbird-78-faq
- https://www.thunderbird-mail.de/lexicon/entry/240-security-tls-version/
- https://www.privacy-handbuch.de/handbuch_31k.htm
- https://www.heise.de/news/IETF-erklaert-TLS-Urvaeter-1-0-und-1-1-als-veraltet-5997963.html
- https://datatracker.ietf.org/doc/rfc7568/
- https://datatracker.ietf.org/doc/rfc8996/

## Names instead of "Me"
In the standard configuration of Thunderbird, the name in emails sent to or from yourself is sometimes displayed as "Me" instead of the actual name.
This can be changed to show the actual name.

`Edit` --> `Preferences` --> `General` --> scroll down to `Reading & Display`:
```
Set
Display name: Show only display name for people in my address book
to false (Uncheck the checkbox).
```

Links:
- https://support.mozilla.org/en-US/kb/names-bug-no-email-addresses-are-displayed

## Email offline storage
todo

## Folder subscriptions
How to check or change the subscription of individual folders.
- `File` --> `Subscribe`
- `Datei` --> `Abonnieren`

## Folder names: Avoid dots
When naming a folder in an email account, it is recommended to avoid dots/periods (`.`) in the name of the folder.

The reason for this is that a dot (`.`) is commonly interpreted as a hierarchy separator in email folder names.

Examples:
- Instead of giving a folder the name `Emails from Mr. John Doe` it should be named `Emails from Mr John Doe`.
- Instead of giving a folder the name `Invoices, receipts, etc.` it should be named `Invoices, receipts, etc`.

## Formatting: Plain text and HTML
### Introduction
Sending emails in a plain text format is generally preferred over sending emails in an HTML format.
The reason for this is that plain text emails avoid a lot of issues that HTML emails can cause.

However, sometimes it's necessary to use HTML formatting in emails.
HTML allows the sender to use different formatting options, for example bold, underline, italics or different font sizes.
These formatting options are very helpful when the content of an email is long and complex and requires structuring different parts of the email.

For example, an email might consist of multiple sections and each section contains multiple paragraphs.
Adding a formatted section heading above each section provides the reader with a visual structure and improves readability.
Typical sections could be: Introduction, Main part (part A, part B, part C, etc.) and Conclusion/Summary.

**Summary: Using HTML formatting in emails provides the reader with a visual structure and logical hierarchy. This improves readability and makes it easier to quickly understand the contents of an email.**
Basically, this applies the more general question of "why to use formatting in a text" to emails.

Links:
- https://kb.mozillazine.org/Mail_content_types
- https://useplaintext.email/

### HTML paragraph line spacing
todo

## Addons
- https://addons.thunderbird.net/en-US/thunderbird/addon/xpunge/
- https://addons.thunderbird.net/en-US/thunderbird/addon/manually-sort-folders/
- https://addons.thunderbird.net/en-US/thunderbird/addon/removedupes/
