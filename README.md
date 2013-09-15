# Rethinking the email experience

I want a better email interface. So I'm designing one.

### Warning:
__Everything here is work in progress and subject to drastic change.__

![UI mockup](https://raw.github.com/bertob/mail/master/export/main_window_mockup.png)

## Concepts

Some of the basic ideas this project is based on:

* The inbox is already a to-do list. Might as well make it a good one.
* Folders are cool, but hard to manage. Let's make them smarter.
* Drag and drop is better than buttons (When the action is moving something from one place to another, eg. deleting, )

## UI elements

### Sidebar

Problems in current implementations:

* When emails are organized in conversations, the name __Inbox__ is not very descriptive, because this folder contains emails from other people as well as the user's replies to these emails.
* To the same point, when some of the user's messages are already in the inbox, why not move the rest of them there to and have __one complete history__, instead of two partial ones? Why is there a need for a separate __Sent__ folder?
* I never really understood what the __Drafts__ folder is for. Mine is almost always empty, except for the rare occasions when I start writing a message one day and finish it the next day. Is it really necessary to have an top-level folder that only ever contains a handful of messages, even in the worst of cases? I'd personally rather have these messages in my main conversation folder as to-do items. That has the added benefit that I don't forget about them as easily.
* I think that the main reason why there is a __Starred__ category in most email clients today is because the custom folder systems are implemented badly. If it was simple and easy to add an email to a custom group, why would anyone want to use a this limited way to organize emails with only 2 different states?
* The __Spam__ folder is another example for something I rarely use, but that should still be quickly accessible (in case something automatically got flagged as spam and needs to be restored because it isn't spam). But since spam emails are not counting as real, existing emails, why can't they be in the same location as deleted email, since in a way, the effect of deleting and flagging as spam is essentially the same (move to separate folder, don't make it show up in search results etc.)
* __Folders__  and __Filters__ are cool, but underused by most people. That is mostly due to the fact that few people know about them and they are fairly complicated to set up and handle.

I think the traditional email folders can be simplified to just these two:

* __Conversations__, which combines the following:
	* Inbox
	* Sent
	* Drafts
	* All messages
* __Deleted__, which contains everything that would go into __Trash__, as well as __Spam__. New emails that have been flagged as spam appear on top, in a separate section similar to the "Active" section in "Conversations". This makes it easy to restore emails that have been accidentally flagged as spam by the spam filter.
* In addition, there are also __custom folders__, which can be set up by the user. These can also replace the __Starred__ category, because the user can just create a folder "Imporant" and use that instead of a dedicated, top level folder. That said, I've gotten the impression that not a lot of people use the star feature anyway, so I don't consider it a high priority.

### Conversation List

Problems in current implementations:
* I feel like most email clients today either make items in the conversations column too big (eg. Sparrow, Geary), so that only 5 items or so fit on the screen at a time, or too small (eg. Thunderbird, Gmail and most other webmail providers) so that they become hard to process visually because there are so many and there's so little space between them.
I think there is a sweet spot between these two extremes where there are enough messages on the screen to allow for an efficient workflow, but not so many that it gets confusing. Something like of 10-15 messages would be perfect in my opinion.

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

Additionally, there is a __New Messgage__ area on top of everything else. It is used to start writing new messages, but this can be done in different ways:

* Clicking the __Recipients__ label or any of the whitespace inside the area will open a compose dialog with the recipient field active
* Clicking the __New Message__ (Subject) label will open a compose dialog with subject field active
* Clicking the __Attachment icon__ will open a compose dialog AND directly the file chooser, to add an attachment to the message.
* __Dragging and dropping files__ from the file manager on the area will open a compose dialog and directly attach these files to the message



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
* Reply and Forward buttons are always visible, floating on top of the scrolling area with the messages in the bottom center of the pane

### Compose View

* No formatting via UI. Formatting is possible via Markdown, but generally not recommended.
* Attachments can be added by dragging and dropping files on the compose view.
* After clicking the "Send" button, the __Undo__ button displays a label that allows the user to undo the action for 5 seconds, with a progress bar directly on the button. After 5 seconds the message is sent.

### Settings

The settings dialog is a single window with 4 sections:

* __General__: general settings for the application, such as notifications, spell check and the language of the interface.
* __Accounts__: Add, remove and manage email accounts
* __Folders__: Add and remove folders, set up the rules by which conversations are automatically moved to them
* __Filters__: More general filters, which allow for additional actions (not just auto-moving conversations to folders), such as delete, forward and auto-reply to messages.
