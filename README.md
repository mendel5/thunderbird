# thunderbird-how-to
How to configure Mozilla Thunderbird

## Config Editor

### Open the Config Editor
`Edit` --> `Preferences` --> `General` --> Scroll to bottom --> `Config Editor`

### Default sorting
Change the default sort order to "Date" with the newest emails on top (descending)
```
mailnews.default

mailnews.default_news_sort_order
to 2

mailnews.default_news_sort_type
to 18

mailnews.default_news_view_flags
to 0
// this disables "Threaded view"

mailnews.default_sort_order
to 2

mailnews.default_sort_type
to 18

mailnews.default_view_flags
to 0
// this disables "Threaded view"
```

Links:
- https://superuser.com/questions/13518/change-the-default-sorting-order-in-thunderbird
- https://www.badpenguin.org/thunderbirds-default-sort/

### Check all folders
Check all folders for new messages (necessary when emails are sorted into multiple folders based on server-side rules):
```
mail.server.default.check_all_folders_for_new
to true

mail.imap.use_status_for_biff
to false
```

Links:
- http://kb.mozillazine.org/How_do_I_check_for_new_messages_in_other_folders

### Encryption in transit
```
security.tls.version.min
to 4

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

### Names instead of "Me"
In the standard configuration of Thunderbird, the name in emails sent to or from yourself are sometimes displayed as "Me" instead of the actual name. This can be changed to show the actual name:

`Edit` --> `Preferences` --> `General` --> scroll down to `Reading & Display`:
```
Display name: Show only display name for people in my address book
to false (Uncheck the checkbox)
```

Links:
- https://support.mozilla.org/en-US/kb/names-bug-no-email-addresses-are-displayed

## Addons
- https://addons.thunderbird.net/en-US/thunderbird/addon/xpunge/
- https://addons.thunderbird.net/en-US/thunderbird/addon/manually-sort-folders/
- https://addons.thunderbird.net/en-US/thunderbird/addon/removedupes/


## Other
`File` --> `Subscribe`
