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
Tags: synchronize, synchronization, offline storage, offline availability

By default, Thunderbird downloads all emails in an email account so that they are available offline.
Sometimes this is helpful, sometimes this is not helpful.

The setting can be changed as follows:
- Go to the Menu bar, click on `Tools`, click on `Account Settings`.
- Select the email address that you want to configure (in the left pane).
- Within that email address, go to `Synchronization & Storage`.
- In the section `Message Synchronizing`, deactivate/uncheck the checkmark `Keep messages in all folders for this account on this computer`.
- A pop-up asks you if you are sure about this change. Confirm the change by clicking on `Save`.

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

## Formatting, font sizes, etc.
Formerly called: *Formatting: Plain text and HTML*

### Introduction
Is it better to send emails in a plain text format or in an HTML format?
The answer depends on who the recipient is.
- When communicating in a business context, it is generally preferred to send emails in an HTML format. Many business people use email clients from Microsoft (Microsoft Outlook, Microsoft 365 on the web) and when sending to these recipients/email clients, it is preferred to send emails in an HTML format.
- When communicating with tech/IT people who might read emails in their terminal or who are unlikely to use Microsoft email clients, it is preferred to send emails in a plain text format.

Sending emails in a plain text format can lead to issues with line breaks after 78-80 characters per line in Outlook, Gmail and other email clients (the 80 characters limit per line comes from RFC 2822).
For example, when you write a plain text email in your email client, there might be no line breaks being shown after 80 characters per line, but the recipient might still see the line breaks.
This is very annoying, because it breaks the assumption of "what you see is what you get" where it is expected that the sender and the recipient should see the same thing.

Therefore, using HTML formatting in emails can have some advantages.
HTML not only avoids the line break issue, it also allows the sender to use different formatting options, for example bold, underline, italics or different font sizes.
These formatting options are very helpful when the content of an email is long and complex and requires structuring different parts of the email.

For example, an email might consist of multiple sections and each section might contain multiple paragraphs.
Adding a formatted section heading above each section provides the reader with a visual structure and improves readability.
Typical sections could be: Introduction, Main part (part A, part B, part C, etc.) and Conclusion/Summary.

**Summary**:
- 1: Using HTML formatting (like bold) in emails provides the reader with a visual structure and logical hierarchy. This improves readability and makes it easier to quickly understand the contents of an email. Basically, this applies the more general question of "why to use formatting in a text" to emails.
- 2: Using the HTML sending format can help to make sure that the "what you see is what you get" assumption holds true. This means that what the sender wants the recipient to see and what the recipient actually sees is as similar to each other as possible.

Note:
Always try to understand whether the word "formatting" refers to (a) using or not using formatting such as bold or italics and (b) which format the email is sent in, independent of using bold, italics, etc.

An email that is sent as plain text cannot use formatting like bold.
An email that is sent as HTML can use formating like bold, but is does not have to. Even when not using bold formatting, sending an email in an HTML format has the benefit of avoiding the line break issue.

Links:
- https://kb.mozillazine.org/Mail_content_types
- https://useplaintext.email/ (when sending to tech/IT people)

### Settings for HTML format (general settings)
Tags: HTML paragraph line spacing, single line spacing, double line spacing
- Go to the Menu bar, click on `Tools`, click on `Settings`.
- Click on `Composition`.
- In the section `HTML Style`, set these settings:
  - Font: `Variable Width` (Tag: font name).
  - Size: `Medium` (Tag: font size).
  - Activate/Set the checkmark for `Use reader's default colors` (Tag: font color).
  - Deactivate/Uncheck the checkmark for `Use Paragraph format instead of Body Text by default` (Tag: paragraph, body text, line spacing).

### Sending format (general settings)
- Go to the Menu bar, click on `Tools`, click on `Settings`.
- Click on `Composition`.
- Regarding the section `Sending Format`:
  - The default setting is `Automatic`. When this setting is active and a message is composed without any formatting, it will be sent in a plain text format only. Recipients who use Microsoft Outlook might see strange line breaks in the email body text that were not intended to be there by the sender.
  - To fix this problem, select the setting `Both HTML and Plain Text` or `Only HTML`. When the setting `Both HTML and Plain Text` is active, recipients with Microsoft email clients will most likely see the HTML formatted email by default.

### Default format when writing a new email: HTML or plain text (account settings per email address)
- Go to the Menu bar, click on `Tools`, click on `Account Settings`.
- Select the email address that you want to configure (in the left pane).
- Within that email address, go to `Composition & Addressing`.
- In the section `Composition`, check or uncheck the checkmark `Compose messages in HTML format`.
  - If the checkmark is checked, the default email format will be HTML. If you want to send a single email in plain text format, you can hold `Shift` while clicking on `New Message`.
  - If the checkmark is unchecked, the default email format will be plain text. If you want to send a single email in HTML format, you can hold `Shift` while clicking on `New Message`.

### Plain text: format flowed
Tag: format=flowed, format-flowed

(better ignore this section)

When sending emails in a plain text format, using `format=flowed` can sometimes help to avoid issues, but sometimes it can also cause issues.

In the default configuration of Thunderbird, the value `mailnews.send_plaintext_flowed` is set to `true`.

It is possible to edit this in the Config Editor:
```
Set
mailnews.send_plaintext_flowed
to false.

```

Links:
- https://www.fastmail.com/blog/format-flowed/
- https://wiki.openstack.org/wiki/MailingListEtiquette#Thunderbird
- https://joeclark.org/ffaq.html

## Addons
Tags: addons, add-ons, plugins, extensions

Add-ons for Mozilla Thunderbird
- https://addons.thunderbird.net/en-US/thunderbird/addon/xpunge/
- https://addons.thunderbird.net/en-US/thunderbird/addon/manually-sort-folders/
- https://addons.thunderbird.net/en-US/thunderbird/addon/removedupes/
