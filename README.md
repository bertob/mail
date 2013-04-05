# Rethinking the email experience

I want a better email interface. So I'm designing one.
Everything in this project is work in progress and subject to drastic change.

## Concepts

Some of the basic ideas this project is based on:

* Our inbox is already a to-do list. Might as well make it a good one.
* Folders are cool, but hard to manage. Let's make them smarter.
* Drag and drop > buttons

## UI elements

### Sidebar

Problems in current implementations:
* When emails are organized in conversations, the name __Inbox__ is not entirely correct, because this folder contains emails from other people as well as the user's replies to these emails.
* Similarly, separating __Inbox__ and __Sent__ does not make a lot of sense because the inbox also contains messages from the user. At that point, wouldn't it be simpler to just have one folder with all these messages?
* I never really understood what the __Drafts__ folder is for. Mine is almost always empty, except for the rare occasions when I start writing a message one day and finish it the next day. Is it really necessary to have an top-level folder that only ever contains a handful of messages, even in the worst of cases? I'd personally rather have these messages in my main conversation folder as to-do items. That has the added benefit that I don't forget about them as easily.
* __Starred__
* The __Spam__ folder is another example for something we rarely use, but that should always be quickly accessible in the few cases when something accidentally got flagged as spam and we need to restore it. But since spam email is essentially not counting as real, existing email, why can't it be in the same location as deleted email, since in a way, the effect of deleting and flagging as spam is essentially the same (move to separate folder, don't make it show up in search results etc.)
* __Trash__
* __Folders__  and __Filters__ are cool, but underused by most people. That is mostly due to the fact that few people know about them and they are fairly complicated to set up and handle.

I think the classic email folders can be simplified to just these two:
* __Conversations__ combines the following folders:
	* Inbox
	* Sent
	* Drafts
	* All messages
* __Trash__ also contains spam emails. New emails that have been flagged as spam appear on top, in a separate section similar to the "New" section in "Conversations". This makes it easy to restore emails that have been accidentally flagged as spam by the spam filter.

### Conversation List

Conversations are organized in 2 sections:
* __Active Conversations__:
	* New messages
	* Drafts for new messages
	* Conversations with open response drafts
* __History__:
	* All other conversations (even if they only contain sent messages with no response)

* When one or more conversations from the list are selected, a set of actions (e.g. delete, mark as spam, move to History, etc.) is available from the panel on top of the Conversation list.
* Selecting multiple conversations works just like on the desktop: Ctrl + Click individual conversations to add them to the selection or use Shift + Click for selecting all messages between two specific conversations. 
* Messages in the __Active__ category can be reordered by dragging and dropping, so it can be used as a to-do list. Thus, no priority system is required.
* When a message is opened it is not automatically marked as read. The user has to drag it into __History__ to remove it from the to-do list.
* The person who wrote the most recent message in a thread is visually highlighted in the List.
* Unread messages appear at the top ot the __Active__ column.


### Single Conversation

* Behaves similarly to the Gmail web interface
* Only the most important information about a message is shown:
	* Sender's name
	* Recipient(s)' name
	* Time OR date and how many days ago that was (for messages older than a day)
	* Message
* More detailed information is available from the "more" triangle menu next to the recipient's name
* All actions on a single message are available via a top right menu on every message
* In threads with many message, older messages in the thread are automatically collapsed and can be uncollapsed (like in Gmail)

### Compose View

* No formatting via UI. Formatting is possible via Markdown, but generally not recommended.
* Attachments can be added by dragging and dropping files on the compose view.
