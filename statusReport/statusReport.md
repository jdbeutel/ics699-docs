contact info sharing web app
============================
ICS MS project status report  
J. David Beutel  
2013-12-10


delay
-----

I started my ICS 699 project at the end of August,
but was interrupted on September 6 when I was hit by a truck
and broke my thumb.  I needed surgery on September 16 to fix it.
This took time to arrange and recover from, and will still take
time to manage, so the schedule was postponed by a month.


research
--------

I found five publications since 2009 that referenced references from my
earlier projects, and looked interesting.  However, they did not provide
answers to the design issues of my current project.  Mainly they provided
examples of what my final report might look like for this project.
One also supported my decision to not use a decentralized architecture
for the app.  It is tempting, because it would mirror the data model,
but it would just complicate the project for no real benefit.


design
------

I updated the design of my previous project to the distributed data model
that I suggested in my proposal.  My previous design was like Wikipedia,
where users collaborate to keep the same instance of data up to date.
My new design is more like Github, when users fork their own copy
of the data and share updates to it.  Forking is more complicated,
but it matches better with what users do in the real world with their
own physical address books or smartphones.  Although the model is
distributed, I will still be implementing it on a centeralized
architecture.

The Wikipedia model was oriented around who can view or edit each
instance of data.  The UI included a color key on expansion toggle
buttons to indicate that zooming in will reveal editable data.
It also displayed the owner of the data, if not the current user.

In the Github model, the user can edit all the data she can see,
because she gets her own copy of it.  Just like the real world,
if the user has access to some data, then she can choose with whome
to share that data.

AngularJS, Grails 2.3, REST...
