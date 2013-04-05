# Rethinking the email experience

I want a better email interface. So I'm designing one.

### Warning:
__Everything in this project is work in progress and subject to drastic change.__

## Concepts

Some of the basic ideas this project is based on:

* The inbox is already a to-do list. Might as well make it a good one.
* Folders are cool, but hard to manage. Let's make them smarter.
* Drag and drop > buttons
* Undo should be available for every user action.

## UI elements

### Sidebar

Problems in current implementations:
* When emails are organized in conversations, the name __Inbox__ is not very descriptive, because this folder contains emails from other people as well as the user's replies to these emails.
* To the same point, when some of the user's messages are already in the inbox, why not move the rest of them there to and have __one complete history__, instead of two partial ones? Why is there a need for a separate __Sent__ folder?
* I never really understood what the __Drafts__ folder is for. Mine is almost always empty, except for the rare occasions when I start writing a message one day and finish it the next day. Is it really necessary to have an top-level folder that only ever contains a handful of messages, even in the worst of cases? I'd personally rather have these messages in my main conversation folder as to-do items. That has the added benefit that I don't forget about them as easily.
* __Starred__
* The __Spam__ folder is another example for something I rarely use, but that should still be quickly accessible (in case something automatically got flagged as spam and needs to be restored because it isn't spam). But since spam emails are not counting as real, existing emails, why can't they be in the same location as deleted email, since in a way, the effect of deleting and flagging as spam is essentially the same (move to separate folder, don't make it show up in search results etc.)
* __Trash__
* __Folders__  and __Filters__ are cool, but underused by most people. That is mostly due to the fact that few people know about them and they are fairly complicated to set up and handle.

I think the traditional email folders can be simplified to just these two:
* __Conversations__, which combines the following:
	* Inbox
	* Sent
	* Drafts
	* All messages
* __Deleted__, which contains everything that would go into __Trash__, as well as __Spam__. New emails that have been flagged as spam appear on top, in a separate section similar to the "New" section in "Conversations". This makes it easy to restore emails that have been accidentally flagged as spam by the spam filter.
* In addition, there are also custom folders, which can be set up by the user. These can also replace the __Starred__ category, because the user can just create a folder "Imporant" and use that instead of a dedicated, top level folder. That said, I've gotten the impression that not a lot of people use the star feature anyway, so I don't consider it a high priority.

### Conversation List

Conversations are organized in 2 sections:
__Active Conversations__:
* New/unread/to-do messages
* Drafts for new messages
* Conversations with open response drafts
__History__:
* All other conversations (even if they only contain sent messages with no response)

* Selecting multiple conversations works just like on the desktop: Ctrl + Click individual conversations to add them to the selection or use Shift + Click for selecting all messages between two specific conversations.
* Conversations can be moved from/to the Active and History sections, to folders or the trash via drag and drop.
* When more than one conversation is selected, they all show up in the Conversation pane on the right, one above the other. The conversations can be reordered by the user, single messages in all conversations can be collapsed/uncollapsed.
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
* After clicking the "Send" button, a little notification appears on top of the Conversation List that allows the user to undo the action for 5 seconds. After 5 seconds the message is sent.

