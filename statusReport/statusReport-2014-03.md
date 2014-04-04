contact info sharing web app
============================
ICS MS project status report 2014 March
J. David Beutel  
2014-04-03


Conversion to AngularJS
-----------------------

I spent a lot of time in March learning AngularJS and converting to it.
I have not finished yet, but I will continue, because I still think
that my project will be much better with Angular.

### Replacing Prototype

I completed the Angular tutorial and converted my project's old
JavaScript (based on the Prototype library) to Angular, starting
with the Settings page.  However, this update of the existing
JavaScript was superficial, because it had only the following
functionality:
* a button to expand and collapse the change password section
* highlighting modified input fields
* enabling and highlighting the save button for modifications

It still reloaded the whole page to display input validation error
messages, like a traditional web app, not the way that an Angular
web app is supposed to work.

### AJAX, JSON, & REST

Next I converted that page to the Angular style, using AJAX, and
on the server side, converted its Grails controller to REST and
JSON.  The server sends the static page, and the Angular controller
gets the data to fill in and initially display.  The save button
posts another AJAX request, without reloading the page.  A successful
response resets the modification highlighting and updates the model's
version numbers for optimistic locking, while an error response
just displays the error messages from the server.

An optimistic locking failure is a special case, displaying the
newer data from the server and an error message from the client.
I am thinking about eliminating this optimistic locking on the user
level, allowing the last post to win, because users will be editing
only their own copies of the data, but for this conversion I left
it in.

### Angular Form Validation

I also learned about the native Angular support for form modification
and validation, using that instead of my initial conversion.
However, I found that the modification support was not quite what I need, because 
after an input field is modified once, Angular still considers
it to be modified after it is changed back to its original value.
Modifications in my project are more significant, because they
generate notifications, so I don't want any false indicators.
I implemented another Angular directive to handle modifications
properly within the native Angular form support.  It was harder
to do, because it was tightly integrated with the Angular framework.

For form validation, I planned to use the new support in HTML5.
[User testing shows](http://alistapart.com/article/inline-validation-in-web-forms)
that this kind of immediate feedback is a better UI than the
traditional page reload.  The server still needs to do all the same
validation, to prevent hacking at least, but it need not render
nice, user-friendly error messages, since the browser will have
already done that and prevented the form submit.  Unfortunately,
I found some problems with HTML5 forms:
* browsers do not treat an AJAX request the same as a form submit
* Safari (including iPad/iPhone) provides no UI for this validation
* some of my validation, such as the matching password confirmation,
cannot be done with HTML5 form validation.

So, I will look for a good way to do this
[form validation UI](http://www.html5rocks.com/en/tutorials/forms/constraintvalidation/)
with Angular.  One possibility is
[this extension of Angular](https://github.com/nelsonomuto/angular-ui-form-validation).
Another possibility is
[the form support in Webshim](http://afarkas.github.io/webshim/demos/index.html#Forms),
which is based on the
[HTML5 constraint validation API](http://www.whatwg.org/specs/web-apps/current-work/#constraints).


### Additional Work

After finishing the form validation UI, the last issue for the Settings page
is converting all the pages to Angular templates, within a 
single-page app, using Angular's routing module.  Since the navigation is
no longer following links and reloading pages, the user can no longer discard
changes to the Settings form by navigating away from the page, so I think it
might need a reset or cancel button or link.  Given that, maybe I should
make it fully modal, with an edit button to start?  I'll consider that along
with the design for the contact list.

Finally, I need to redo the contact list with expanding details in Angular.
They are read-only in the prototype, so my March schedule did not include
editing them.



Schedule
--------

I am behind my tentative schedule again.  I had hoped to finish the
Angular redo in March, and do email/notifications.
But, I am not going to revise my schedule yet.
I will continue the Angular work for another two weeks,
and then revise based on my progress then (before my trip to Japan).

The items that my current schedule has for April
are history/edit/add info and permissions/privacy.
These are closely related to the contact list,
so hopefully my Angular work will provide some insight.
