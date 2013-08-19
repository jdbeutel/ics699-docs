contact info sharing web app
============================
ICS MS project proposal  
J. David Beutel  
2013-08-09

For my ICS 699 project, I would like to implement a contact information
sharing web application.  It will enable friends and family to collaborate
in maintaining their address books.  The biggest challenge is how to
manage the privacy of third-party information.


Background
----------

I normally don't use postal addresses, until I
send out a bunch of holiday cards.  Then the Post Office returns a few,
because the addressee has moved during the year, so I sometimes need to
contact friends or relatives to get the updated address.  Phone numbers
and email addresses also change occassionally.  With this app, one person
can automatically share an update with friends or family.

I have done several class projects leading up to this one:

* Spring 2009 ICS 667:  Agile Usage-Centered Design of a
Social Networking Contact Book
* Fall 2009 ICS 668:  Managing Privacy for Transitive Sharing on a
Social Networking Site (literature review)
* Spring 2010 ICS 664:  We'll Call You (partial UI prototype)


Tentative Schedule
------------------

* 2013 Sep - research relevant publications and apps since 2009
* 2013 Oct - design for below issues
* 2013 Nov - update prototype to current Grails
* 2013 Nov - authentication via Facebook, Google, etc
* 2013 Nov - email/notifications
* 2014 Dec - history/edit/add info
* 2014 Jan - permissions/privacy
* 2014 Feb - duplicates/unify/link
* 2014 Feb - import/export/sync
* 2014 Mar - user testing
* 2014 Apr - revisions and retesting
* 2014 May - write report


Issues
------

### privacy ###

This kind of sharing raises privacy concerns.  A phone number or home
address connects to the physical world, so most people don't want
theirs to be public.  Deciding how to share ones own contact information with
a second party is straightforward; several apps already support this,
such as Facebook, Google, Plaxo, and Viadeo.  (See examples below.)
This limitation encourages the spread of these networks,
but there is little possibility of getting all of ones contacts
to join the same network and manage their own contact information,
whether due to choosing other networks, or to privacy concerns.

This forces one to manage other people's contact information
in ones own address book.  Why shouldn't one collaborate in this?
Sharing a third party's contact information with second parties
involves some wicked problems.  Suppose that my grandmother does not
use the app, so I input her address myself.  I know that she would
want my brother to have her new address, and I trust him to share it
appropriately, but how far does that trust go?  If he shares it with
his wife, can she share it with her friends?  If my grandmother finally
starts using the app, and asserts her privacy preferences, do they apply
to the information that other users have input about her?  Who owns
that information?  What cognative model and UI would support this?


### unification ###

Different users will have different relations to the same contact.
If the app lacks good support for that, then it will not sustain the
collaboration that makes it worth-while.

When a user imports his address book, some of his contacts will be in
different social groups.  They are all related to him, but not all to
each other.  If one of these contacts becomes a user, she must be able
to import her address book too, which will have only some overlap with
the first user's.  The app must recognize which contacts refer to the
same identity, for these two users to be able to share their updates.
A user may manually link or confirm an identity, to accept updates.
On the other hand, the more hops separate two users, the less information
they will want to share about a contact.

At the logical extreme, suppose that a user who I do not know also inputs
my grandmother's address.  We cannot share this information, because we
have no reason to trust each other.  So, the app cannot have a single
copy of my grandmother's address that we all update, like a wiki.
It needs to have two separate contacts for this same identity.

Now suppose that someone we both know starts using the app, and we both
share my grandmother's address with him.  He doesn't want two copies
in his address book.  So, each user needs his own copy, receiving optional
update advice that ripples through related copies.  This allows the data
to be distributed (although it will be centralized in my web app).
Each update advice can come with some level of trust, based on the
relation it came from, and be applied automatically (with history
to rollback if necessary), or after confirmation of the notification.


### identity ###

The app will need to identify contacts and users.

##### contacts #####

Contact identity, for unification, will be based on name 
and location.  Matches can be approximate or historical.
The user can confirm via linking.

##### users #####

The basis of a user's identity is their email address:
a ticket mailed in an invitation to that address links the new user
to the contact information containing that address.
Supporting authentication via Facebook, Google, etc. would allow
for stronger authentication.

Users input their own contact information, and can share it with
a higher level of trust than third parties can.
There is no absolute trust, however, since impersonation is easy.
A user can always assign a contact an email address that he controls.
The app could at least warn about suspicious identity,
such as two users with the same name and location.


Examples
--------

### Google ###


#### Google+ ####

A user's Profile in Google+ allows sharing of the user's own home and
work contact information, with a nice UI, especially for privacy settings.
The granularity with whom to share is good, integrating with "circles"
(i.e., groups), and allowing for individuals.  However, the granularity
of what to share is limited to all home or all work contact information.
For example, one cannot share ones home phone number with one group
and home address with a different group.  Also, Google+ does not
accept third-party contact information.

![Google+ profile example](proposal/Google+ - Profile - Contact Info - David Beutel.png)


#### Gmail Contacts ####

On the other hand, the Contact Manager in Gmail does allow third-party
contacts, in "My Contacts".  The user can input anyone.  However, it
does not support sharing that third-party data.  Second-party data
from the user's Google+ circles is also displayed, though.
Here is a circle named "Following".

![Gmail contact manager example](proposal/Gmail - Contact Manager - Following circle.png)

Any Google+ profile contact information that the second party shares
with the user, whether publicly, individually, or via the second party's
own circles, is displayed at the bottom.  The user can add more
information himself in the top part of the page, which adds the
contact to the "My Contacts" group, in addition to any circles.
Google does not support sharing any of that information with anyone else.
Although Google allows it to be exported, or synchronized with smart phones,
the assumption is that those are not for some other user.

![Gmail contact example](proposal/Gmail - Contact Manager - Luke Daley.png)


#### HTC Android ####

linking, notes...
