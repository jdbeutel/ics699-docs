## 2013-09-02

The [Google+ Platform/API](https://developers.google.com/+/) looks
like it supports
[authentication](https://developers.google.com/+/features/sign-in),
including 2-step verification, and [listing all the
users](https://developers.google.com/+/api/latest/#People) in the
circles that the user chooses to show to the requesting app.  However,
the API does not provide the name of the circles, or who is in which
circle, even though there is a 2-year-old [enhancement request for
that](http://code.google.com/p/google-plus-platform/issues/detail?id=9).
There is an apparently unsanctioned [JavaScript
library](https://github.com/mohamedmansour/google-plus-extension-jsapi) to
get that data via the web, but I don't know how well it works, or
for how long.

Facebook's Graph API, on the other hand, looks like it does provide
access to the name, list_type, and members of the user's [friend
lists](https://developers.facebook.com/docs/reference/api/FriendList/), if
the user grants the "read_friendlists" permission to that Facebook
app.  I don't see any privacy setting or choice of which lists to
provide to an app, so it looks like all or nothing.


## 2013-10-17 [Narayanan, Barocas, Toubiana, Nissenbaum, & Boneh (2012).  A Critical Look at Decentralized Personal Data Architectures](1202.4503v1.pdf)

This position paper reviews attempts to create decentralized social
networks, infomediaries, Vendor Relationship Management systems,
and personal data stores.  It classifies the decentralized architectures as
* self-hosted, i.e., distributed, or
* outsourced, i.e., federated (as opposed to centralized, like Facebook).

It proposes the following axes of a decentralized architecture:

1. locus of data hosting:  remote (centralized), trusted 3rd party
(infomediary), distributed (peer-to-peer), or local (on the user's
device, e.g., a mobile phone).
2. open standards vs. proprietary.
3. open vs. closed-source implementations.
4. data portability: export (by users), API (for 3rd party apps), or none.

It also describes social values: privacy, utility, cost, and innovation.
The central point of this paper is that the design characteristics
have been confused with the values.  A decentralized architecture
does not necessarily lead to the desired values.  For that
matter, in some cases, it precludes them.  For example:

* it limits the utility of a social network, by interfering with
search, collaborative filtering, identification of trending topics,
and detection of fraud and spam.

* it increases the cost, with the loss of economies of scale.

* it reduced innovation, with the time to develop open standards,
or loss of interoperability.

* it can decrease privacy in the general case, as users suffer
cognitive overload in the configuration of their settings and systems.

The paper points out that absolute control over personal data
is impossible in practice, since users must depend on software
and hardware beyond their personal knowledge, whether decentralized
or not.

Finally, it offers recommentations:

1. Consider the economic feasibility of your design.
2. Pay heed to coneptual fidelity.
3. Incorporate other notions of regulability.
4. Offer advantages other than privacy to users.
5. Design with standardization in mind.
6. Target limited feature sets.  (minimum viable product)
7. Work with regulators.

These are all good things to keep in mind for my project,
although the criticism of decentralization does not apply directly,
because I am building a centralized system (web app).
The data is distributed in the sense that each user gets
his own copy, as opposed to my original plan to keep the
data centralized, but the copies are still on a central server.
On the other hand, the architecture could be distributed,
with fully redundant copies of the private data on each user's device,
like a git repo, because the amount of data involved for
each user's private contacts should be small enough to allow that.
Nevertheless, to avoid several of the drawbacks outline by
this paper, I will use a centralized architecture.
