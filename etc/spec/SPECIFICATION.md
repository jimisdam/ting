# Ting

June 15, 2015 - September 6, 2015

dionyziz for the Ting team.

Ting is a chat platform. It runs on ting.gr. This document specifies how it works.

# Workflow
People on ting exchange messages. Messages can be exchanged either in channels
(known as "tings"), or privately. Channels are public and can be looked at by
anyone, where they can see the messages exchanged. Privates are messages
exchanged directly between two people and can only be viewed by these people.
Channels and privates are collectively referred to as conversations.

Ting is a website that works both on desktop and on mobile.

Ting consists of serveral screens:

* The login screen
* The chat screen
* The settings screen

These are described below. When the user enters the URL ting.gr on their
browser, they are taken to the Login screen. If they enter www.ting.gr, they
are redirected to ting.gr and appropriate URL parameters are appended.

When the user enters the URL ting.gr/channel, where channel is any
valid channel name, the user is taken to the Login screen with the active
conversation set to the channel specified in the URL. When the user enters
the URL ting.gr/u/user, where user is any valid user name, the user is taken
to the Login screen with the active conversation set to a private with the
user specified.

However, if the user has stored credentials, then the Login screen is skipped
and the user is taken directly to the Chat screen.

The active conversation remains until the web page is refreshed, a different
URL is visited, or the active channel is manually changed. When the active
conversation is changed, the URL is changed to reflect that.

Once a user enters ting, they can then see who is online on the platform among
the recent people they had a conversation with.

The users can exchange messages in multiple channels. Messages exchanged are
per-channel. Each message sent to a channel is delivered only to the selected
channel.

Message history is stored in a per-conversation basis. When a user makes a
conversation active, they are shown some of the messages history.

# Channels
If no conversation is specified in the URL, the default channel name is used,
which is the channel name "ting". Channel names are validated as follows upon
visiting a ting URL:

1. The channel name is at least 1 character and at most 20.
2. The channel name must consist of only the following characters:
 - The lower-case and upper-case latin characters a-z and A-Z.
 - The numbers 0-9.
 - The symbols _ . -

If an invalid channel is specified, the user is redirected to the default
channel and the URL shown is ting.gr without a channel name. The same applies
if an invalid username is specified.

There is no notion of creating or destroying a channel. A channel exists purely
because of the messages exchanged within it.

# UX foundation
The UX is in Greek. The text towards the user will be informal. Singular
form is used for everything. Informal words are preferred over formal words.
For example, the word "πληκτρολόγησε" should be replaced by "γράψε". The goal
is to make the user feel at ease, relaxed, and in a friendly environment.

# Target audience
The target audience for Ting is teenagers from Greece aged 12 - 21 years old.
The purpose of the chat is to bring people close together and allow strangers
who live in the same country and are of similar age to get to know each other.
We should make it a point in the UX to avoid the purpose of many other chat
rooms which is romantic or sexual interest, and focus on directing the user to
make friendly, public conversations.

# Login screen
Ting users are authenticated by having their machine remember their credentials
when they register and when they login. Registering is done by entering only a
username.

If a user wants to keep their username, they have to enter a password by
editing their user account through the Settings screen.

The Login screen can be either a Simple Login screen or a Password Login
screen. The Simple Login screen is shown by default.

## Simple Login

The Simple Login screen consists of only a modal window with the heading
"Ting", a textbox, a button, and a link.

![Login screen](http://i.imgur.com/FirJeIL.jpg)
*Image: The simple login screen*

The placeholder text in the textbox is "Διάλεξε ένα ψευδώνυμο". The textbox is
focused by default when the screen is visited. The placeholder text is hidden
when the user starts typing some text, unless the text is cleared. Pressing the
Enter key when the keyboard is focused on the textbox is equivalent to pressing
the button.

The button has the text "Μπες". Upon clicking the button, the username entered
is verified as follows:

1. The username is at least 1 character and at most 20.
2. The username must consist of only the following characters:
 - The lower-case and upper-case latin characters a-z and A-Z.
 - The lower-case and upper-case greek characters α-ω and Α-Ω.
 - The numbers 0-9.
 - The symbols . , / ? ~ ! @ # $ % ^ & * ( ) - _ = + [ ] { } \ | ' " ` ; :
3. The username must not be reserved.

The username is also validated for form, but not for reservation, as the
username is being typed.

All usernames are not reserved by default. If the username is valid, the
username is reserved and the user is taken to the Chat screen. The username is
then associated with that user. The user's credentials are then stored on the
machine they used to login. The next time the user accesses ting, the
credentials are used to skip the Login screen. Once a username becomes
reserved, no other user is allowed to use it, even if the user is not currently
online.

When the user logs in with an unreserved username, they are assigned a random
avatar from a predefined set of avatars. They can later modify this avatar from
the settings page.

If the username is invalid, the textbox border is changed to red, the
content text color is changed to red and an appropriate error is displayed as
follows:

1. If the username field is empty, the error message is "Γράψε ένα ψευδώνυμο."
2. If the username field is too large, the error message is "Το ψευδώνυμο
   πρέπει να είναι έως 20 γράμματα."
3. If the username field contains forbidden characters, the error message is
   "Το ψευδώνυμο πρέπει να περιλαμβάνει μόνο γράμματα, αριθμούς ή σύμβολα."
4. If the username is reserved, the error message is "Το ψευδώνυμο
   το έχει άλλος."

The error message is displayed above the textbox.

![Simple login screen error](http://i.imgur.com/se80ce8.jpg)
*Image: An error logging in using the simple login screen*

Below the username textbox, a link allowing the user to login with their
reserved username is displayed, entitled "Έχω ήδη ψευδώνυμο". Clicking that
link changes the Simple Login screen into the Password Login screen.

## Password Login

The Password Login screen allows the user to login with a username and a
password of a reserved username. It is identical to the Simple Login screen,
except it contains a password input underneath the username input and it
doesn't contain a link at the bottom. The placeholders for the input boxes here
are "Το ψευδώνυμό σου" for the username input and "Ο κωδικός σου" for the
password input.

![Password login screen](http://i.imgur.com/L47eF0G.jpg)
*Image: The password login screen*

The username is validated as above for form, but not for reservation. In
addition:

1. If the username is reserved but the password is incorrect, the error message
   is "Ο κωδικός είναι λάθος."
2. If the username is not reserved, the error message is "Το ψευδώνυμο δεν
   υπάρχει. [Χρησιμοποίησέ το]".

Clicking the link in the non-reservation case logs the user in with the
unreserved username without a password, similar to the way they would have
logged in using the Simple Login screen.

![Password login screen error](http://i.imgur.com/vBdQAZ5.jpg)
*Image: An error logging in using the password login screen*

If the username and password combination is correct, the user is logged in with
the reserved username. Notice that it is possible to login with the same
reserved username in different devices simultaneously.

## Mobile Login

On mobile, the whole screen is used to display the login windows for both the
simple and the password login screens.

![Mobile login screen](http://i.imgur.com/nUfvfVz.jpg)
*Image: The mobile login screen*

On mobile, care should be taken to ensure the button is visible while the
username is being entered.

# Chat screen
The chat screen consists of the following elements:

1. A top bar
2. A recent conversations list
3. A chat history
4. A message area

![Chat screen](http://i.imgur.com/4kl8upL.jpg)
*Image: The chat screen*

## Top bar

The top bar is located at the top and takes up the whole screen horizontally.
On mobile, there is no top bar.

On the top left, it has the text "ting".
On the right, it has an icon with the avatar of the user.

![User menu](http://i.imgur.com/WoPGg2s.jpg)
*Image: The user menu*

Clicking the avatar icon pops up a menu with two options: Settings and Log out.
Clicking on Settings takes the user to the Settings screen.

## Logging out

Clicking Log out in the user menu logs the user out and wipes their user
credentials from their machine.

If the user has a password associated with their account, then the username
remains reserved. If no password is associated with their account, then Log out
also frees up the username for future use. However, before wiping out the
account, the user is shown a modal giving them a last chance of reserving their
username.

The user reservation modal has a label, a textbox, a button, a link, all
appearing the one below the other.

![User reservation modal](http://i.imgur.com/0SxifIu.jpg)
*Image: The user reservation modal*

Hitting the ESC key or pressing the browser back button closes the modal and
cancels the log out procedure. The label states "Κράτα το ψευδώνυμό σου". The
textbox has a placeholder of "Διάλεξε έναν κωδικό" and the button has a title
of "Αποθήκευση". Typing a password and clicking "Αποθήκευση" permanently
reserves the username with the password entered and logs the user out. The form
can also be submitted by hitting the Enter key. If the form is submitted
without entering a password, the following error message appears above the
password textbox:

"Πληκτρολόγησε έναν κωδικό."

The link below the textbox is labelled "Όχι τώρα". Clicking the link logs the
user out without reserving the username.

After logging out, the Ting application is replaced with the following text:

"Τα λέμε! [Ξαναμπές]"

Clicking the button takes the user back to the Ting application and allows them
to start over with logging in anew.

![Logged out](http://i.imgur.com/EIn4gJw.jpg)
*Image: Logged out of ting*

## Main chat screen

Below the top bar, the screen is split in two areas vertically. The left area
contains the recent list and the right area is split horizontally in two
smaller areas. The top portion is the larger and is the chat history. The
bottom portion is the message area. The portions are not resizable. If the
active conversation is a private message, there is an additional area above the
message area, the user information area.

## Recent conversations

The recent conversations list contains a list of recently used channels and
recently accessed private message partners. Recent conversations are shown from
most recent to least recent, one below the other. There is one currently active
conversation at a time. That conversation may not always be shown at the top of
the recent conversation list; see the rules below for the ordering of recent
conversations. Recent conversations that are channels simply display the
channel name. Recent conversations that are privates display the person's
avatar, their name, and their online status. The online status is displayed
with a green dot on the right of their name in case they are online.

Recent conversations are reordered based on the following strategy: Initially,
when a user first uses ting, the recent conversations list only includes the
conversation they are accessing, usually the Ting channel. A new item is added
to the conversation list when a new conversation becomes active. If a
conversation that becomes active when it's already in the list, it is brought
to the top of the list. If a new conversation is added to the list and the list
contains more than 50 items, then the oldest conversation is removed from the
recent conversations list ("milk" strategy).

A conversation becomes active and is either added to the list or reordered to
be at the top in the following events:

1. When the user activates the conversation by clicking it and remains within
the conversation for 4 seconds.
2. When a message of user-interest is received in a conversation (see below).
3. When the user starts typing a message within the conversation even if they
do not send the message.

If the list of conversations is too long to fit, a vertical scrollbar is
displayed on the right-hand side of the nick list.

## Searching conversations

At the top of the recent conversations list is a searchbox. The searchbox
allows the user to type in order to filter items from the recent conversation
list. When no text is entered in the search box, the text box has the
placeholder text "Βρες ανθρώπους ή tings". As soon as the user starts typing,
the placeholder text disappears unless they clear their text. While there is
text in the search textbox, an "X" is shown at the right of the textbox, which
allows the user to clear their search text. While typing, the recent
conversations list is filtered by the search text through a prefix-match test.

## Unread messages and messages of interest

Conversations with unread messages are also highlighted, but in a different
color. Unread messages are any messages of user-interest which have not been
viewed by the user yet. Activating a conversation with unread messages marks
their messages as read. Messages of user-interest are defined as any received
message in a private conversation, or any message mentioning the user's name
prefixed with an `@` in a channel.

If there are unread messages in the active conversation when the user is not
active (has switched to another tab or window), the window title gets prepended
with the count of unread messages in parentheses. When the user is active
again, the count is removed from the title and the previously unread messages
are marked as read.

## Message history

The message history contains a list of messages posted by everyone in the
active conversation. The messages are displayed in chronological order from top
to bottom. When the user enters a conversation, the message history consists of
the most recent 100 messages exchanged by the users priorly and is stored on
the server.

If there are less messages than the chat history can fit, the messages are
displayed at the bottom of the chat history area. Otherwise, a vertical
scrollbar is shown.

Every time a message is posted by someone, a new chat message is appended to
the bottom of the chat history area, and the area is scrolled towards the
bottom to make the new message visible. This happens unless the user has
scrolled upwards into the history enough to read older messages. In that case,
a new message being posted does not affect the scrolling position of the
history area.

When the user scrolls upwards and reaches the top of the displayed messages,
there is a button with the prompt "Δες παλαιότερα μυνήματα" if there are older 
messages to show. In case there are not older messages to show, the button
should not appear. Clicking the button diplays 100 older messages (if more than
100 older messages exist), otherwise it displays the remaining of older
messsages.

For efficiency reasons, very old messages can be removed from the chat history.

## Message formatting

Each message posted has the following form: "[avatar] [username] Message",
where username contains the username of the person making the post and Message
contains the text posted. The message is displayed in a comicbook-like bubble
indicating that someone is speaking. Messages of user-interest in channels are
highlighted in orange. Messages sent and received are displayed in different
style; sent messages are displayed in blue and received messages are shown in
gray.

If a text is too long to fit in one line, it is wrapped around to the next
line. No horizontal scrollbar is ever displayed in the history area.

## User information

The user information area is shown above the message history area in case the
currently active conversation is a private. The user information area shows the
partner's avatar and username. Below the username, the age, the sex, and the
location of the user are shown, if they are available.

## Sending a message

The message area is a textbox. The textbox is focused by default when the user
enters the Chat screen. The textbox has the placeholder "Γράψε ένα μήνυμα...".
When the user starts typing some text, the placeholder is hidden, unless the
text the user entered is deleted, in which case the placeholder text reappears.
If a user enters a long message, the text is wrapped within the textbox.
Horizontal scrollbars never appear in the message area.

When a user enters a non-empty message and presses the Enter key, the message
is sent. There is no separate button to send a chat. When a message is sent by
a user, it is delivered to everyone else who is currently online in the chat in
the active channel. The textbox in the message area is then cleared, but
remains focused. The message appears immediately on the side of the sending
party.

## Mobile

On mobile, the chat screen is separated into two different screens. These are
the recent conversations screen and the mobile chat screen. The semantics are
similar to the above desktop version, with the mobile differences described
below.

In the recent conversations screen, the text "Ting" is displayed at the top.
Next to it, on the right, is a cog icon. Clicking the cog icon displays a
pop-up menu with two options, Settings and Log out, with similar semantics as
the desktop top bar.

Below the mobile top bar, a list of recent conversations appears. While in the
recent conversations screen on mobile, no active conversation is highlighted.
Tapping a recent conversation changes it to the active conversation and
switches to the mobile chat screen.

![Mobile recent conversations screen](http://i.imgur.com/YuXy3Ra.jpg)
*Image: The mobile recent conversations screen*

In the screen above, you can see a list of recent conversations, of which the
most recent conversation is the channel "chicken", and the second most recent
conversation is the channel "ting". The next two more recent conversations are
two private conversations with the users "gtklocker", who is online, and
"vitsalis", who is offline. The least recent conversation is the channel
"party".

In the mobile chat screen, a list of messages appears, which is rendered
similar to the desktop version. At the top of the list, the name of the
conversation appears in a separate title bar, along with a back button on the
left, which allows the user to return to the recent conversation list screen.

![Mobile chat screen](http://i.imgur.com/jECW8Jn.jpg)
*Image: The mobile chat screen*

# Message Formatting

In messages, smileys are replaced by their respective images. The list of
supported emoticons is
[taken from Skype](https://github.com/kof/emoticons/blob/master/support/skype/emoticons.json).

Web links are formatted to be clickable.

Dragging and dropping an image file from the user's computer into the messages
history or into the message form allows the user to upload an image. While
dragging the file over the website, the history and the message form are
overlayed with a screen with the following text indicating that the user can
drop the image to upload it:

"Άφησε την εικόνα για να την ανεβάσεις"

Dropping the image over this area uploads the image and immediately sends it as
a separate message. This does not affect any text the user may be currently
entering on the text box.

![Image Uploader](http://i.imgur.com/GDkryfj.jpg)
*Image: Image Uploader*

# Typing
Ting provides a different approach from usual chat platforms when it comes to
notifications about typing. Users can see each other typing in real time. This
works as follows.

Messages in ting are separated into persistent and non-persistent. Persistent
messages are messages that have been sent. Non-persistent messages are messages
that are currently being typed, but have not been sent yet (the Enter key has
not been pressed by the user.). A non-persistent message of a user that disconnects
is deleted. Users can see both persistent and non-persistent
messages and both are communicated on the network in real time.

When a user starts typing a message in a channel, they reserve a position in
the channel's history. Figuring out this position is critical for a smooth user
experience and is determined by the following rules.

* This position is maintained among other people who are currently typing, as
well as persistent messages that have been sent. When nobody is typing and a
user starts typing, this position becomes the end of the existing persistent
messages.

* When several users are typing and a user starts typing, their position becomes
at the end among the existingly typing users and after all persistent messages.

* When a user stops typing and erases their typed message, their position is
lost and their message is not persisted.

* When a user makes a message persistent by hitting the enter key, that
message's position in the history remains as-is among other users who are
typing. That is, it is not posted at the end of persistent messages, but
potentially among messages that have not yet been made persistent yet.

The user interface for this algorithm is different depending on whether the
current user or a remote user is typing. The non-persisted message of the
current user is displayed as "..." in the history portion of the chat. The full
message is displayed in the textarea as it is being typed. The "..." servers to
indicate to the user their current position among other typing users. Remote
non-persistent messages are displayed by the text being added in real time as
the user types, in their designated location.

Non-persistent messages are differentiated from persistent messages by showing
them as "ghosts", in a more transparent color. Additionally, the text of a
non-persistent message is slowly flashing by becoming more and less trasparent
to indicate that the message is ephemeral and currently changing.

![Desktop chat typing](http://i.imgur.com/9MdtAgp.jpg)
*Image: Desktop chat screen while typing*

![Mobile chat typing](http://i.imgur.com/IjDrJlY.jpg)
*Image: Mobile chat screen while typing*

# Settings screen
The settings screen allows a user to specify details about their user profile.

It consists of a form at the top and a save button with the title "Αποθήκευση"
at the bottom.

The form has the user's avatar displayed on the left. Below it is a button with
the title "Αλλαγή της εικόνας μου". Clicking it pops up a window allowing the
user to select a new avatar. The avatar is uploaded and displayed in the avatar
location within the settings. Before displaying it, the avatar is first cropped
into a square and then resized to fit the avatar size.

It is also possible for the user to upload an avatar by dragging a file onto
their avatar within their settings. While dragging a file over the screen, the
avatar location is changed into the text "Άφησε την εικόνα εδώ".

If the uploaded file is not a valid avatar, then the error message "Δοκίμασε
κάποια άλλη εικόνα" is displayed.

Next to the avatar, the username is displayed.

Below the avatar and the username, there are five labels associated with their
respective inputs. The inputs are prefilled with the settings the user has
entered previously.

The first label is "Password". The input is a text box. If the user has left
this field empty, a warning text appears above the label and the field stating:
"Διάλεξε έναν κωδικό ώστε να μην χάσεις την πρόσβαση στο λογαριασμό σου".

The next label is "E-mail" with a text box input.

The next label for the date of birth is "Ημερομηνία γέννησης". The input
consists of three select fields, for the day, the month, and the year. All
fields contain the range of valid numbers for days, months, and years
respectively, as well as the "-" option. The days allow selecting from 1 to 31
ascending, the months from 1 to 12 ascending, and the years from 1920 to the
current year descending.

The next label for the gender is "Φύλο". The input consists of a select field
with three options "Αγόρι", "Κορίτσι" and "-".

The next label for the location is "Περιοχή". The input is a select box
listing all the major cities of Greece as well as the option "-".

Clicking the save button validates the form as follows:

1. The e-mail address is validated for form with a simple validation algorithm
and not exhaustively. It must contain an `@` symbol. It must contain at least
one alphanumeric character before the `@` sumbol. It must contain at least
three characters after the `@` symbol, one of which must be a `.`. The e-mail
must be at most 128 characters. The user can also leave the e-mail address
empty if they do not wish to associate an e-mail address with their account.

2. The date of birth must be a valid date.

If the form fails to validate, the following error messages are displayed above
their respective fields and the fields are highlighted in red:

1. "Γράψε ένα έγκυρο e-mail" if the e-mail address is invalid.
2. "Δώσε μία έγκυρη ημερομηνία γέννησης" if the date of birth is invalid.

Otherwise, the form is saved and the user is taken back to the Chat screen.

Notice that multiple users can share the same e-mail address.

# TODO
This specification is limited. It will be extended with the following features in future editions:

* Voice
* Channel moderation
* Subscription to channels
* Timestamps
