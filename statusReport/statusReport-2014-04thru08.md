contact info sharing web app
============================
ICS MS project status report 2014 April - August  
J. David Beutel  
2014-09-16


Finished The Settings Tab
-------------------------

I finished converting the Settings page to Angular JS,
and its UI improvements mentioned in my last status report.

### Interactive Form Validation

HTML5 form validation with Angular was insufficient, because:
* it cannot confirm matching passwords, etc.
* browsers do not treat an AJAX request the same as a form submit
* Safari (including iPad/iPhone) provides no UI for this validation

So, to render immediate, friendly feedback on user input, I added 
[the interactive form validation from Webshim](http://afarkas.github.io/webshim/demos/index.html#Forms).
I think this provides a crucial improvement in usability,
going beyond Angular.
It is based on the
[HTML5 constraint validation API](http://www.whatwg.org/specs/web-apps/current-work/#constraints),
so follows the standards as much as practical.


### No Optimistic Locking

I eliminated optimistic locking on the user level, allowing the last post to win,
because users will be editing only their own copies of the data.
This eliminates an error from the server that the users would
not understand or expect.  Grails still uses optimistic locking within
a request to prevent race conditions, but it does not extend through
the long cycle to the browser.


### Single-Page App 

I converted all the tabbed pages to Angular templates within a
single-page application, using Angular's basic routing module
to change tabs.  Each tab and its contents are loaded via AJAX.

For a complex tab like the Contacts, where the user may have dug
down to particular entries, or been editing them, I handled that
as state within the tab, not reflected in the route or URL.  Angular's
basic routing can do only a single level like this, and even its
multi-level routing alternatives seemed to provide no way to specify
multiple entries, so the user cannot bookmark specific contacts.
This is a trade-off for viewing multiple contacts on the same
page.

The single-page app design avoids refreshing the whole page
when navigating between tabs, providing a smoother transition.
This could have prevented form changes from being discarded by
navigating to a different tab, but I reload the tab contents via AJAX.
I'm thinking of adding a confirmation dialog for loosing changes.


### Modal Editing

I added Edit and Cancel buttons.  They show the user what she can do,
and make it easier to view her information without accidentally updating it.
Updates should only be purposeful, because they may generate notices
to other users.  Modified input fields still enable the Save button,
and highlight both in yellow, to make updates explicit.  Manually reverting
an input field to its original value still undoes the highlight, and disables
the Save button if no other input fields have changes, but the user
can accomplish that more easily now by just clicking the Cancel button.

Initially I made the input fields disabled when not in editing mode,
to show that they could be edited by clicking the Edit button.  However,
in brief user testing with Professor Robertson in May, this proved confusing.
Since all input fields start disabled, with no enabled fields for comparison,
they all looked editable, with the box affordance, and just a darker shade of
background that does not objectively or independently suggest that they
are disabled.  The Edit button at the bottom was easily overlooked,
leading to frustration.  So, at his suggestion, the fields are now displayed
as plain text, with no editing affordance, while clicking the Edit button
unambiguously reveals what can be edited.


### Independent Password Editing

In my original prototype, the Settings page used modal JavaScript
to expand password update fields that were submitted with the rest
of the form fields.  They were modal from the beginning, because 
they are one-way fields, authenticating the current password instead
of displaying it.  Without a mode, those fields would seem to force the
user to change the password when changing any other field.
Also, I didn't want to put the password change on a tab of its own,
because that would increase the navigation complexity.

Since the Settings tab uses modal editing and AJAX now,
I did not want to nest the modal password update within the editing
of the rest of the fields.  I thought that the Change Password button
would be confusing if disabled, or worse, hidden, while not in edit mode.
So, I moved it below the Edit button, and gave it its own Save button,
to make it more direct and clear.  It is like a dialog now, within the page,
but non-blocking, so both sets of fields can be updated independently.
The Change Password button still toggles to 
Cancel Password Change, instead of adding a typical Cancel button.


Hosting
-------

These UI improvements were taking a long time, and I was falling behind schedule,
but I felt that they were crucial to the project.
To highlight their significance, I tried to host my original prototype
and current project in the cloud, for comparison and constant availability.


### Original Prototype

I got [my original prototype running on Heroku](http://rocky-meadow-9347.herokuapp.com/).
Although I updated some of the software, the UI is the same.
You can try it whenever you like.
It is on a free instance, so it will be available as long as Heroku allows it.
The first time you access it, it will probably show an error
as it times out waiting for a server instance to be spun up.
Reloading the page should work around that.

* login: joe.cool@example.com
* password: password


### Current Project

I also got my current project running on Heroku.
Unfortunately, as I added new features, it kept breaking on Heroku
in a way that was difficult to reproduce or troubleshoot locally.
Besides Heroku's incompatibility, I think that I had also reached the
limits of what I could do in the amount of memory that Heroku provides for free.

Next, I tried Jelastic, which was not free, but promised to not
charge for resources for the time when the app was not being used.
It worked a lot better than Heroku, and was simpler and easier to
deploy a Java web app (which Grails produces).  Unfortunately, I
discovered that all the Jelastic providers actually charge for a
minimum set of resources constantly, despite the app not being used.
Jelastic has the capability of automatically hibernating an environment
that has not been used for some period of time, but the providers
have a policy of only allowing that for free trial accounts.

These attempts and searching for a suitable host had taken a lot of time.
Finally I decided that constant availability of my current project in development
was not worth the cost or time to continue searching for a cost-effective cloud host.
I will just run my project on my development machine for user testing and demos,
and look into hosting again when it is feature complete.


Contacts Tab
------------

I started converting the app's main tab, Contacts, to Angular.

### Sorting and Paging

The preferred email, phone, and address that are displayed on the
top-level list were virtual properties on a Person, to be elected
from a Person's available properties according to the user's
preferences.  But, to implement sorting and paging on those properties
via the database (i.e., GORM criteria), I had to de-normalize the
database by copying those properties.  This should not be a problem,
since each user will have their own copy of a shared Person.

I added explicit buttons for sorting, showing the selected column
and direction of the sort, instead of using the column headers as
implicit buttons.

For paging, the default Grails buttons provide a navigation link
to a nearby page of the sorted search results.  With Angular and AJAX, 
however, there is no need for the browser to throw out the contents of the current page.
The initial, limited page size (10) allows the browser to display the results faster,
and hopefully it contains what the user is looking for.  She can add a search term
to quickly narrow down the results.  If there are more matching contacts,
their count is displayed at the bottom of the page, along with a button to Load
or Load More.  If the remainder is 150 or less, the Load button gets them all,
but over that amount, the Load More button will get 100 more.

When I implemented search, I had to redo the sorting and paging.


### Digging Down



### Editing



### To Do


Search
------



Schedule
--------

