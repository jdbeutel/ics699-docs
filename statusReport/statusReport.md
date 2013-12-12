contact info sharing web app
============================
ICS MS project status report  
J. David Beutel  
2013-12-10


delay
-----

I started my ICS 699 project at the end of August, but was interrupted
September 6 when hit by a truck (breaking my thumb).  It required
surgery on September 16.  This took time to arrange and recover from,
so we postponed the schedule by a month.  June is my current target
to finish the project.


research
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


design
------

I updated the design of my previous project to the distributed data model
that I suggested in my proposal.  Thinking it through, it still seems
better.  My previous design was like Wikipedia, where users collaborate
to keep the same instance of data up to date.  My new design is more like
Github, when users fork their own copy of the data and share updates.
Forking is more complicated, but it matches better with what users do
in the real world with their own physical address books or smartphones.
Although the model is distributed, I will still be implementing it on
a centralized architecture.

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

implementation
--------------

I have just started updating my previous prototype to Grails 2.3.
For my current project, I am planning to make a single-page
AJAX app, using AngularJS and REST features in Grails 2.3.
