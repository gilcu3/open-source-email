FairEmail
=========

Frequently Asked Questions
--------------------------

<a name="FAQ1"></a>
**(1) Which permissions are needed and why?**

* Full network access (INTERNET): to send and receive email
* View network connections (ACCESS_NETWORK_STATE): to monitor internet connectivity changes
* Run at startup (RECEIVE_BOOT_COMPLETED): to start monitoring on device start
* In-app billing (BILLING): to allow in-app purchases
* Foreground service (FOREGROUND_SERVICE): to run a foreground service on Android 9 Pie and later, see also the next question
* Optional: read your contacts (READ_CONTACTS): to autocomplete addresses
* Optional: find accounts on the device (GET_ACCOUNTS): to use [OAuth](https://en.wikipedia.org/wiki/OAuth) instead of passwords

<a name="FAQ2"></a>
**(2) Why is there a permanent notification shown?**

A permanent status bar notification with the number of accounts being synchronized and the number of operations pending is shown
to prevent Android from killing the service that takes care of receiving and sending email.

Most, if not all, other email apps don't show a notification with the "side effect" that new email is often not or late being reported.

<a name="FAQ3"></a>
**(3) What are operations?**

The low priority status bar notification shows the number of pending operations, which can be:

* SEEN: mark message as seen/unseen in remote folder
* ADD: add message to remote folder
* MOVE: move message to another remote folder
* DELETE: delete message from remote folder
* SEND: send message
* ATTACHMENT download attachment

<a name="FAQ4"></a>
**(4) What is a valid security certificate?**

Valid security certificates are officially signed (not self signed) and have matching a host name.

<a name="FAQ5"></a>
**(5) What does 'no IDLE support' mean?**

Without [IMAP IDLE](https://en.wikipedia.org/wiki/IMAP_IDLE) emails need to be periodically fetched,
which is a waste of battery power and internet bandwidth and will delay notification of new emails.

<a name="FAQ6"></a>
**(6) How can I login to Gmail / G suite?**

To login to Gmail / G suite you'll often need an app password, for example when two factor authentication is enabled.
See here for instructions: [https://support.google.com/accounts/answer/185833](https://support.google.com/accounts/answer/185833).

If this doesn't work, see here for more solutions: [https://support.google.com/mail/accounts/answer/78754](https://support.google.com/mail/accounts/answer/78754)

<a name="FAQ7"></a>
**(7) Why are messages in the outbox not moved to the sent folder?**

Messages in the outbox are moved to the sent folder as soon as your provider adds the message to the sent folder.
If this doesn't happen, your provider might not keep track of sent messages or you might be using an SMTP server not related to the provider.
In these cases you can enable the account option *Store sent messages* to let the app move messages from the outbox to the sent folder after sending.

<a name="FAQ8"></a>
**(8) Can I use a Microsoft exchange account?**

If you can use a Microsoft exchange account depends on if the exchange account is accessible via IMAP.
ActiveSync is not supported at this moment.
See here for more information: [https://support.office.com/en-us/article/what-is-a-microsoft-exchange-account-47f000aa-c2bf-48ac-9bc2-83e5c6036793](https://support.office.com/en-us/article/what-is-a-microsoft-exchange-account-47f000aa-c2bf-48ac-9bc2-83e5c6036793)

<a name="FAQ9"></a>
**(9) What are identities?**

Identities represent email addresses you are sending *from*.

Some providers allow you to have multiple email aliases.
You can configure these by setting the email address field to the alias address and setting the user name field to your main email address.

<a name="FAQ10"></a>
**(10) What does 'UIDPLUS not supported' mean?**

The error message *UIDPLUS not supported* means that your email provider does not provide the IMAP [UIDPLUS extension](https://tools.ietf.org/html/rfc4315).
This IMAP extension is required to implement two way synchronization, which is not an optional feature.
So, unless your provider can enable this extension, you cannot use FairEmail for this provider.

<a name="FAQ11"></a>
**(11) Why is STARTTLS for IMAP not supported?**

STARTTLS starts with an unencrypted connection and is therefore not secure.
All known IMAP servers support IMAP with STARTTLS, so there is no need to support STARTTLS for IMAP.
If you encounter an IMAP server that requires STARTTLS, please [create an issue](https://github.com/M66B/open-source-email/issues/new).

<a name="FAQ12"></a>
**(12) What is the difference between Chrome Custom Tabs and WebViews?**

The main difference is that [Chrome Custom Tabs](https://developer.chrome.com/multidevice/android/customtabs) store cookies persistently
and [WebViews](https://developer.android.com/reference/android/webkit/WebView) do not.
The latter is both safer and more inconvenient because you'll need to login to websites each and every time.

Chrome Custom Tabs are used by default, which can be changed in the advanced options in the setup screen.

<a name="FAQ13"></a>
**(13) How does search on server work?**

You can start searching for messages in a folder on the server by using the magnify glass in the action bar of a folder.
The server is requested to search on sender, subject and message text.
The server executes the search request and determines if the search is case sensitive,
if searching will be done on whole words and which messages will be search through.
Results will be shown in real time as they become available from the server.
For performance reasons attachments are not downloaded and shown.
Search on server is a pro feature.

<br>

If you have another question, you can use [this forum](https://forum.xda-developers.com/android/apps-games/source-email-t3824168).

If you have a feature request or found a bug, you can report it [as an issue](https://github.com/M66B/open-source-email/issues).
