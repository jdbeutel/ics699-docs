contact info sharing web app
============================
ICS MS project proposal  
J. David Beutel  
2013-08-09

For my ICS 699 project, I would like to implement a contact info sharing
web app.  It will enable friends and family to collaborate in maintaining
their address books.  I normally don't use postal addresses until I
send out holiday cards.  Then the Post Office returns a few because
the addressee has moved, so I need to contact friends or relatives to
get the updated address.  With this app, only one person would need to
update the address, benefitting everyone else who is sharing it.

Privacy concerns are raised by contact info, such as phone number or
home address, that connects online identity to the physical world.
Deciding how to share ones own contact info with a second party is
straightforward; several apps already support this, such as plaxo.com
or viadeo.com.  But, sharing a second party's contact info with a third
party involves some wicked problems.  Suppose that my grandmother does
not use the app, so I input her address myself.  I know that she would
want my brother to have her new address, and I trust him to share it
appropriately, but how far does that trust go?  If he shares it with
his wife, can she share it with her friends?  Is there a single copy
of my grandmother's address that we can all update, or do we each get
our own copy, receiving optional update advice that ripples through
related copies?  If my grandmother finally starts using the app, and
asserts her privacy preferences, do they override the data that other
users have input about her?

Different users will have different relations to the same contact.
If the app lacks good support for that, then it will not sustain the
collaboration that makes it worth-while.


Background
----------

I have done several class projects in this direction:

* Spring 2009 ICS 667:  Agile Usage-Centered Design of a Social Networking Contact Book
* Fall 2009 ICS 668:  Managing Privacy for Transitive Sharing on a Social networking Site (literature review)
* Spring 2010 ICS 664:  We'll Call You (partial UI prototype)


Issues
------

* privacy
* identity
* unification


Tentative Schedule
------------------

* look for relevant publications since 2009
* update prototype to current Grails
* authentication via Facebook, Google, etc
* email
* history
* permissions
* duplicates/unify/link
* import/export/sync


Scope
-----

* no mobile
