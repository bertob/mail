# Rethinking the email experience

I want a better email interface. So I'm designing one.

## Accounts Column

Problems in current implementations:
* When emails are organized in conversations, the name __Inbox__ is not entirely correct, because this folder contains emails from other people as well as the user's replies to these emails.
* Similarly, separating __Inbox__ and __Sent__ does not make a lot of sense because the inbox also contains messages from the user. At that point, wouldn't it be simpler to just have one folder with all these messages?
* I never really understood what the __Drafts__ folder is for. Mine is almost always empty, except for the rare occasions when I start writing a message one day and finish it the next day. So the maximum number of drafts is always 

I think the classic email folders can be simplified to this:
* __Conversations__ combines the following views:
	* Inbox
	* Sent
	* Drafts
	* All messages
* __Starred__ behaves as expected.
* __Trash__ also contains spam emails. New emails that have been flagged as spam appear on top, in a separate section similar to the "New" section in "Conversations". Thus, emails that have been accidentally flagged as spam, can be discovered and unflagged easily.

## Conversation List

Conversations are organized in 2 sections that are arranged vertically:
* __Active Conversations__:
	* New messages
	* Drafts for new messages
	* Conversations with open response drafts
* __History__:
	* All other conversations (even if they only contain sent messages with no response)

Notes:
* Messages in the __Active__ category can be reordered by dragging, so it can be used as a to-do list. Thus, no priority system is required.
* When a message is opened it is not automatically marked as read. The user has to drag it into __History__ to remove it from the to-do list.
* The person who wrote the most recent message in a thread is visually highlighted in the List.
* Unread messages appear at the top ot the __Active__ column.


## Single Conversation

* Behaves similarly to the Gmail web interface
* Only the most important information about a message is shown:
	* Sender's name
	* Recipient(s)' name
	* Time OR date and how many days ago that was (for messages older than a day)
	* Message
* More detailed information is available from the "more" triangle menu next to the recipient's name
* All actions on a single message are available via a top right menu on every message
* In threads with many message, older messages in the thread are automatically collapsed and can be uncollapsed (like in Gmail)

## Compose View

* No formatting via UI. Formatting is via Markdown, but it is generally not recommended.
* Attachments can be added by dragging and dropping files on the compose view.
