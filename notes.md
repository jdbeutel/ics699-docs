2013-09-02

The [Google+ Platform/API](https://developers.google.com/+/)
looks like it supports
[authentication](https://developers.google.com/+/features/sign-in),
including 2-step verification, and [listing all the
users](https://developers.google.com/+/api/latest/#People) in the
circles that the user chooses to show to the requesting app.  However,
the API does not provide the name of the circles, or who is in which
circle, even though there is a 2-year-old [enhancement request for
that](http://code.google.com/p/google-plus-platform/issues/detail?id=9).
There is an apparently unsanctioned [JavaScript
library](https://github.com/mohamedmansour/google-plus-extension-jsapi)
to get that data via the web, but I don't know how well it works,
or for how long.

Facebook's Graph API, on the other hand, looks like it does provide access
to the name, list_type, and members of the user's
[friend lists](https://developers.facebook.com/docs/reference/api/FriendList/),
if the user grants the "read_friendlists" permission to that Facebook app.
I don't see any privacy setting or choice of which lists to provide to an app,
so it looks like all or nothing.
