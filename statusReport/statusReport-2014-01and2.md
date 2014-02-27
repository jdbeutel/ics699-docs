contact info sharing web app
============================
ICS MS project status report 2014 January & February  
J. David Beutel  
2014-02-26


User Testing
------------

I did some user testing of the old prototype
while at my mother's on the mainland over the New Year's break.

### Format

* 4 users, from my immediate family, 1 male, 3 female, ages 50s, 60s, & 90s.
* I worked with each individually, for about an hour,
without each seeing any others doing this.
* I described the scenario to the user that she had received an email
from me, offering to share contact information for family and friends,
with a link to the page that I showed her in the browser of my Mac.
* The page was the login page of the prototype, with a link to register.
* I asked the users to explore the app, thinking out loud,
while I took notes.

### Results

* Most users tried to login before registering.  The login requests
an email address as an identifier, and for the password some tried
to use their email password, even though they had not registered
yet.  To mitigate this, my new app will send an email with a link
directly to the registration page, not the login page.  The
registration page will have an "I already signed up" link to the
login page.  The login page will still have a link to "sign up",
for users who arrive by URL or search engine.
* The registration form caused several problems.
The worst was that it required a profile image,
which users were unsure about how to select,
and any validation error required the image file to be selected again,
because the original selection was forgotten.
This will not be a problem with my new app, 
because it will not require any image for registration
(allowing essentially anonymous users, as the model is oriented
around the user, not an objective method for discovering other users).
* The password confirmation also caused some difficulties,
although that illustrated its necessity.  My new app will
ameliorate that by not obscuring the password input characters,
and providing ways to register and authenticate with existing
accounts and single sign-on (such as Google or Facebook).
* One user got stuck in the registration,
and I helped her complete it, but used the wrong name.
She was then able to navigate to her profile and correct her own name.
But, then she tried to navigate with the browser forwards and backwards buttons,
which failed to show the results of her editing and saving, confusing her.
I am not sure how to avoid this issue.
* Many users tried clicked in the middle of the contact lines
to get more details, before learning that they had to click
the [>] buttons on the left edge to expand the details.
(Some users had recently started
using Windows 8, with its flat design.)  To improve this,
my new app will expand for clicking anywhere on the line.
* The user in her 90s had very little computer experience.
For example, she was unsure how to use the Shift key to type the @ symbol
in her email address.  I moved the test to the browser on her own
computer, but she still could not explore the app on her own.
I am not going to constrain the design of my new app for such users.



Implementation
--------------

For user testing, I upgraded my previous prototype to Grails 1.3.9
and modified it to run in mainland timezones.
For my new app, I continued updating the prototype to Grails 2.3,
using [the same code repository](https://github.com/jdbeutel/ics699-bendy).
Several app components, such as authentication, are still using older options
for backwards compatibility.

I started a new app as a sandbox for using new authentication plugins,
based on Spring Security 2,
in [a new code repository](https://github.com/jdbeutel/ics699-ss2).
I added email confirmation for registration,
and registration and authentication by Google or Facebook account.
I still need to migrate this to my original app,
replacing its old authentication component.

I made both those Github repos private, like this ics699-docs repo,
to avoid worrying about leaking sensitive information during
project development.  However, I also externalized the
sensitive information, such as passwords and secret keys for
sending email and authenticating with Google and Facebook, to avoid committing
it to the repo, so I can eventually make the code repos public again.

I am planning to make a primarily single-page
AJAX app, using AngularJS and REST features in Grails 2.3.
I attended an AngularJS hackfest on Feb 13,
where I tried a small sample,
but I need to go through AngularJS tutorials in detail.


Updated Schedule
------------------

I am behind my tentative schedule, and need to update it.

I have done most of the December tasks,
updating the prototype to current Grails,
and authentication via Facebook & Google.
I have also made a little progress on some January and February tasks,
sending a confirmation email for registration,
and finding that the Spring Security Access Control List
plugin may help me implement permissions.

However, I did not get a lot done in February.
I was busy updating my work project to the current version
of Grails.  (This should help my MS project, too.)

I would like to extend my schedule by two months,
through August, and work on reimplementing the UI in AngularJS
next.  Redoing the UI now will allow me to implement
the additional features in the new UI, with less to redo later.

* 2013 Oct - research publications and apps since 2009
* 2013 Nov - design for below issues
* 2013 Dec - user testing on old prototype
* 2014 Jan - update prototype to current Grails
* 2014 Feb - authentication via Facebook, Google, etc
* 2014 Mar - redo UI with AngularJS
* 2014 Mar - email/notifications
* 2014 Apr - history/edit/add info
* 2014 Apr - permissions/privacy
* 2014 May - duplicates/unify/link
* 2014 May - import/export/sync
* 2014 Jun - user testing
* 2014 Jul - revisions and retesting
* 2014 Aug - write report
