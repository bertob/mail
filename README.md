# Rethinking the email experience
-------------------------------
I want a better email interface. So I'm designing one.

## Accounts Column

* **Conversations** combines the following views:
	* Inbox
	* Sent
	* Drafts
	* All messages
* **Starred** behaves as expected.
* **Trash** also contains spam emails. New emails that have been flagged as spam appear on top, in a separate section similar to the "New" section in "Conversations". Thus, emails that have been accidentally flagged as spam, can be discovered and unflagged easily.

## Conversation List

Conversations are organized in 2 sections that are arranged vertically:
* **Active Conversations**:
	* New messages
	* Drafts for new messages
	* Conversations with open response drafts
* **History**:
	* All other conversations (even if they only contain sent messages with no response)

Notes:
* Messages in the **Active** category can be reordered by dragging, so it can be used as a to-do list. Thus, no priority system is required.
* When a message is opened it is not automatically marked as read. The user has to drag it into **History** to remove it from the to-do list.
* The person who wrote the most recent message in a thread is visually highlighted in the List.
* Unread messages appear at the top ot the **Active** column.


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
