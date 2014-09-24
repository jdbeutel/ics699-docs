contact info sharing web app
============================
ICS MS project status report 2014 April - September  
J. David Beutel  
2014-09-23


Settings Tab
------------

I finished converting the Settings page to
[Angular JS](https://angularjs.org/),
and implementing its UI improvements mentioned in my last status report.

### Interactive Form Validation

[HTML5 form validation](http://www.html5rocks.com/en/tutorials/forms/constraintvalidation/)
was insufficient, even with Angular, because:
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
not understand or expect, but was likely to happen if a user is accessing
the web app from multiple browsers or browser-tabs simultaneously.

[Grails'](https://grails.org/) [Hibernate](http://hibernate.org/orm/)
still uses optimistic locking within a request to prevent race conditions,
but it does not extend through the long cycle to the browser.  So, it is unlikely
to generate an error, only if the user submits multiple simultaneous changes.


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
(To avoid loosing changes on a tab, I am thinking of adding a
confirmation dialog when navigating away from a tab with changes,
since I changed the editing to modal.)


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
they are one-way input fields, authenticating the current password instead
of displaying it.  Without a mode, those fields would seem to force the
user to change the password when changing any other field.
I didn't want to put the password change on a tab of its own,
because that would increase the navigation complexity.

Since the Settings tab uses modal editing and AJAX now,
nesting the modal password update within the editing
of the rest of the fields would cause problems.  The Change Password button
would be confusing if disabled, or worse, hidden, while not in edit mode.
So, I moved it below the Edit button, and gave it its own Save button,
to make it more direct and clear.  It is like a dialog now, within the tab,
but non-blocking, so both sets of fields can be updated independently.
The Change Password button still toggles to 
Cancel Password Change, instead of adding a typical Cancel button.


Hosting
-------

These UI improvements were taking a long time, and I was falling behind schedule,
but I felt that they were crucial to the project.
To illustrate their significance, I tried to host my original prototype
and current project in the cloud, for comparison and constant availability.


### Original Prototype

I got [my original prototype running on Heroku](http://rocky-meadow-9347.herokuapp.com/).
Although I updated some of the software, the UI is as it originally was.
You can try it whenever you like.
It is on a free instance, so it will be available as long as Heroku allows it.
The first time you access it, it will probably show an error
as it times out waiting for a server instance to be spun up.
If you get that error, just reloading the page should work around it.

* login: joe.cool@example.com
* password: password


### Current Project

I also got my current project running on Heroku.
Unfortunately, as I added new features, it kept breaking on Heroku
in a way that was difficult to reproduce or troubleshoot on my development machine.
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

Finally, I gave up on hosting the current version during development.
These attempts and searching for a suitable host had taken a lot of time.
I decided that constant availability was not worth the cost or time to
continue searching for a cost-effective cloud host.
I will just run my project on my development machine for user testing and demos,
and look into hosting again when it is feature complete.


Contacts Tab
------------

I started converting the app's main tab, Contacts, to Angular and AJAX,
from the Prototype JavaScript library.
I also added new features, such as editing, sorting, and paging,
because they had a large impact on the implementation in Angular.
However, I have not finished the conversion of this tab.

### Sorting and Paging

The preferred email, phone, and address that are displayed on the
top-level list were virtual properties on a Person, to be elected
from a Person's available properties or sub-properties, according to the user's
preferences.  But, to implement sorting and paging on those properties
via the database (i.e.,
[GORM criteria](http://grails.org/doc/latest/guide/GORM.html#criteria)),
I need a copy of the preferred property
on the top-level Person, de-normalizing the database.  I was able to
implement that now, since I had changed the app design to make each user
have their own copy of a shared Person.

I added explicit buttons for sorting, showing the selected column
and direction of the sort, instead of using the column headers as
implicit buttons.

For paging, the prototype's default Grails buttons provided a navigation link
to a nearby page of the sorted search results.  With Angular and AJAX, 
however, there is no need for the browser to throw out the contents of the current page.
The initial, limited page size (10 entries) allows the browser to display the results faster,
and hopefully it contains what the user is looking for.  She can add a search term
to quickly narrow down the results.  If there are more matching contacts,
their count is displayed at the bottom of the page, along with a button to Load
or Load More.  If 150 or fewer entries remain, the Load button gets them all,
but over that amount, the Load More button will get the next 100.

When I implemented search, I had to redo the sorting and paging.


### Drilling Down And Editing

Clicking anywhere on the row of a contact expands it to display its details.
Several users tried to do that on the prototype, overlooking the row's expand/collapse button.
Any number of contacts can be expanded at the same time.  Each has name details
that can be further expanded.  Each expanded part can be edited and saved independently.
The new design does not need to indicate which contacts can be edited,
because all the contacts that the user can see will be her own personal copies of them.

Before finishing the conversion of my original prototype,
I started adding the editing of contacts, because it had such
a large impact on the Angular implementation.
The original had editing of the user's profile and registration,
which is like a single contact, but flat and static.

User testing revealed problems in the original with uploading a
photo via a traditional form submit.  When any fields had an error
requiring correction, the photo file also needed to be browsed and selected
again.  That was inconsistent with other fields, which maintained
their changed but un-posted values, and it surprised and confused
users, leading to more errors.  Compounding the problem was that
the photo was required, because the prototype's data-centric design
needed it to let users identify and request access to the single instance
of that Person in the app.  To avoid these issues now, an optional
Upload Photo or Upload New Photo button sends the file independently,
immediately, via AJAX.

For birth date, the original prototype used the Grails default
of three select controls: month, day, and year.
I changed that to a single control, the Angular-UI-Bootstrap date-picker,
a text input field with a button to pop-up a calendar.


### To Do

I have not yet finished the conversion or new features of the Contacts tab.
Here are some of the remaining issues on that tab, 
which I may not have time to resolve in this project.

* listing a contact's connections, and drilling down into them
* bug: when modifications are undone manually, undo the highlighted fields and disable the Save button
* Birth Date
  * display in preferred format
  * separate date from time preference settings
  * bug: after first use, calendar fails to reappear
  * bug: after saving or canceling change, field and Save button remain highlighted on next edit
* photo upload
  * progress bar and Cancel Upload button are not displayed
  * drag-and-drop border does not hug the image or animate to suggest drop-ability
  * making the Edit/Cancel button revert to original photo after uploading a new one
* adding new fields
* displaying more properties
* highlighting and automatically expanding matching search results


Search
------

Search is another new feature that I added to the Contacts tab,
beyond just converting the original prototype to Angular.
I did so because it impacted the Angular implementation,
particularly paging and sorting,
and because it is a central feature of the application.

I thought it would be easy, because I had lots of experience
implementing search in Grails with GORM from a database.
However, I used a search plugin instead of GORM,
because I wanted a full-text search with result highlighting.
That turned out to be fundamentally different from a relational database,
and I discovered that I needed to learn a lot about it.


### Searchable Plugin

Originally I used Grails' ["searchable"
plugin](http://grails.org/plugin/searchable), based on
[Lucene](http://lucene.apache.org/) and
[Compass](http://www.compass-project.org/), because it had the best
rating, with the most Grails users and documentation, and it seemed
to be up to date.  Unfortunately, I could not get it to work as I
expected, to search within related objects, such as a Person's
Places.  Lucene builds its own index and searches on documents,
like [other NoSQL databases](http://en.wikipedia.org/wiki/NoSQL#Document_store)
that have become popular lately.
Each Person document added to the Lucene index needed to be composed
of all the related objects to be searched.

While trying to debug this, I had difficulty seeing what had gone
into the Lucene index, and why.  I tried installing
[Luke](https://code.google.com/p/luke/), a Lucene index browser,
but still could not understand what was going on.  I also found
that development on Compass had halted, with [the
author starting Elasticsearch
instead](http://thedudeabides.com/articles/the_future_of_compass/),
over four years ago.
Compass and Elasticsearch are key, because they map the Hibernate/GORM
entities to Lucene documents.


### Elasticsearch

So, I went with [an Elasticsearch
plugin](http://grails.org/plugin/elasticsearch) instead.  It provides
a nice facade on Lucene, including an API with a REST interface for
browsing and querying the index in JSON.  It has better
[documentation](http://www.elasticsearch.org/guide/) and tools than
Compass and the Searchable plugin.  I read [Elasticsearch: The
Definitive
Guide](http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/index.html)
and
[reference](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/index.html),
and explored the index with
[Sense](http://www.elasticsearch.org/guide/en/marvel/current/#_sense),
a developer console web app that provides good support for that API.

With this new understanding, I finally resolved the issue with
the related objects missing from the search index.
The problem involved the Hibernate session and transaction
in the bootstrap initialization of the test fixture data;
I just needed to flush the session before indexing the data in Elasticsearch,
which was using a separate session, so it saw the object relations
in the database and included them in the Lucene documents that it built.
This was difficult to debug, because Elasticsearch saw the entities
in the database, but just didn't see their relations, and the relations
were flushed to the database after the bootstrap method finished running,
so the problem was not visible afterwards.
This resolution might solve the same issue on Compass and the searchable plugin,
but I will just stay on Elasticsearch.

I also configured Elasticsearch to not analyze any of the searchable fields,
so it would provide only exact matches.  It can use various analyzers,
based on natural language, to find similar or root words in English text.
Contact information is not like English text, but I may try to use
an analyzer in the future to allow matches on typos in names and numbers.

Elasticsearch should be able to highlight the matches within search results,
but I have not gotten that working yet.  I would like to automatically expand
the matches and highlight them in the browser.  Since the app will be searching
only the user's own copies of contacts, there will probably be a limited amount,
which raises the possibility of doing the search entirely within the browser.
All of the user's contacts would need to be sent to the browser for any search,
and the implementation would be different from the current one using
Elasticsearch on the server.  However, initially I would probably try to expand
matches in the browser while continuing to do the search on the server.

Although I had experience with database searches, this search
was more like what I did in an artificial intelligence course.
These frameworks were new for me, and took up a lot of the summer.


Schedule
--------

Unfortunately, I have run out of time on this project,
and could not complete all the features that I had hoped to do
within 6 credit hours.  So, I need to limit the project scope
to just the UI improvements that I could do.

* 2013 Oct - research publications and apps since 2009
* 2013 Nov - redesign
* 2013 Dec - user testing on old prototype
* 2014 Jan - update prototype to current Grails
* 2014 Feb - authentication via Facebook & Google
* 2014 Mar & Apr - redo Settings UI with Angular
* 2014 May & Jun - cloud hosting (Heroku & Jelastic)
* 2014 Jul & Aug - search Contacts
* 2014 May..Sep - redo and edit Contacts UI with Angular
* 2014 Sep - update login page style
* 2014 Oct 2 - limited user testing
* 2014 Oct - write report (due Nov 7)
* 2014 Nov - prepare presentation
* 2014 Dec 4 - present to ICS 690
