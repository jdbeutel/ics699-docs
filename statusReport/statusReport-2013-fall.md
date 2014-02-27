contact info sharing web app
============================
ICS MS project status report  
J. David Beutel  
2013-12-10


Delay
-----

I started my ICS 699 project at the end of August, but was interrupted
September 6 when hit by a truck (breaking my thumb).  It required
surgery on September 16.  This took time to arrange and recover from,
so we postponed the schedule by a month.  June is my current target
to finish the project.


Research
--------

To update my literature review from 2009, I found [five
publications](../newResearch) since then that referenced the
same references, and looked interesting.  However, when I [read
them](../newResearch/notes.md), they did not provide answers to the design
issues of my current project.

The best use I can make of the new research, I think, is as examples of
what my final report might look like for this project.  One also supported
my decision to not use a decentralized architecture for the app.  I am
tempted by such an architecture, because it would mirror the data model,
but it would just complicate the project for no real benefit.

I could continue researching, but I had to go on with the project.
I doubt that I am overlooking any important research.


Design
------

I updated the design of my previous project to the distributed data model
that I suggested in my proposal.  It still seems better, so far.
My previous design was like Wikipedia, where users collaborate
to keep the same instance of data up to date.  My new design is more like
Github, when users fork their own copy of the data and share updates.
Forking is more complicated, but it matches better with what users do
in the real world with their own physical address books or smartphones.
Although the model is distributed, I will still be implementing it on
a centralized architecture.


### Data Model

The Wikipedia model was oriented around who can view or edit each
instance of data.  The UI included a color key on expansion toggle
buttons to indicate that zooming in will reveal editable data.
It also displayed the owner of the data, if other than the current user.
It was complicated by managing transitive access to the data,
such as friend-of-a-friend, potentially revoking access to the
user who provided the data in the first place.

In the Github model, the user can edit all the data she can see,
because she gets her own copy of it.  Just like the real world,
if the user has access to some data, then she can choose with whom
to share that data, directly.

When data is shared, each copy retains the ID of the original, along
with its own ID.  This forms a set across transitive copies of the data,
allowing the app to group together updates for the same original ID.
The user can share her updates with a subset, or whichever users she
chooses.  Updates offered to a shared group display which members have
accepted or rejected them.  If a user hijacks a shared contact, like a
hijacked email thread, by filling in the wrong data, or data for another
contact, then peer pressure comes into play.  The other users
can reject such updates, or contact the transgressor out-of-band.

Besides sets of copies, there may be duplicate data,
input by multiple users, or imported from multiple sources.
Like contacts on an HTC smartphone, the app can suggest duplicates,
and the user can link them by confirming.  The app updates the
linked data with each other, so the user can choose to let
missing data be filled in, or inconsistent data be unifed.
Data that are linked are displayed together.  Duplicate data
can provide different streams of updates from different sources,
and share updates with different groups.


### Privacy

The contacts in my previous model were discoverable, exposing
name and city to the public, like on Facebook, so users could
send access requests to the (hidden) owner of the single instance
of contact data.  On the other hand, the owner of the data
had full control over it, even if it came from other users,
which I expected to increase privacy, but raised issues of
fairness and expectations of the conceptual model.
In my new model, the contacts are not discoverable; each user
has her own contacts, and can choose to share them as she wishes.
The app supports offers, but not requests, to share data.
If users make requests, they will need to be out-of-band,
outside the app.


### Editing UI

Since the app will be used more to read than to write,
I am going with a more conventional mode for editing.
The data will not be in input fields until the user presses
the Edit button.  Then Edit becomes Save, a Cancel link is added,
and the collapse buttons are disabled, preventing the user from
hiding unsaved data.  Changed input fields and the Save button
will still be highlighted in yellow.  If possible, warn the
user about closing a tab or navigating off a page with unsaved data.

After Cancel, a Redo button appears.  Likewise, after Save,
an Undo button appears.  The undo period is limited to 10 minutes,
after which other users may receive update notifications,
and email may be sent.  After that timeout, the change can
still be undone via history, although other users may have already
accepted that change.


Implementation
--------------

I have just started updating my previous prototype to Grails 2.3.
For my current project, I am planning to make a single-page
AJAX app, using AngularJS and REST features in Grails 2.3.


Updated Schedule
------------------

* 2013 Oct - research publications and apps since 2009
* 2013 Nov - design for below issues
* 2013 Dec - update prototype to current Grails
* 2013 Dec - authentication via Facebook, Google, etc
* 2014 Jan - email/notifications
* 2014 Jan - history/edit/add info
* 2014 Feb - permissions/privacy
* 2014 Mar - duplicates/unify/link
* 2014 Mar - import/export/sync
* 2014 Apr - user testing
* 2014 May - revisions and retesting
* 2014 Jun - write report
