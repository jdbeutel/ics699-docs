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


## 2013-10-24 [Cutillo, Molva, & Strufe (2009).  Safebook: A Privacy-Preserving Online social Network Leveraging on Real-Life Trust](safebook.pdf)

This article describes a distributed social network system.
It suggests that "a realistic compromise between privacy
and performance is feasible."  Privacy seems to be of utmost importance
to its authors.  It is the kind of system that the previous paper
warned against.

The article assumes "the protection of the user's privacy
to be the main objective for SNS."  That seems oxymoronic to me.
It has several more requirements like that, of dubious origin
and justification.  It lists a number of security objectives
and attacks.

The article describes a three-layer architecture:
* social network
* application services
* communication and transport

Each user in the network has his own server peer,
organized into a "matryoshka" structure to provide anonymity and
redundancy.  Adjacent nodes are trusted, personal contacts
in the real world, mirroring data for high availability, 
and forming shells like an onion router (i.e., TOR).
At a safe distance of hops away, the node's existance is
published at an entry point on the matroyshka's outer shell.
(However, since the node's true identity is supposed to be unknown
to all but its adjacent nodes, I do not know how the middle or
outer shells avoid routing back to a node on the inner shell.)

To avoid attacks related to identity, the system depends on
a trusted identification service.  It uses an out-of-band
process and "set of properties that uniquely identify a party in
real life, such as full name, birth date, birth place, and so on."
It hashes that to provide a unique node identifier and pseudonym.
The article claims that this does not pose a privacy threat,
because the service "cannot trace users or their messages;
nor can it peek into their privatae data."  Still, it seems contradictory
to me for a system to require real-life identification, but put such
complexity into the matroyshka structure for the sake of pseudonymity.
How popular would a pseudonymous social network be, anyway? 
Users would need to interact with others a lot using their pseudonym,
to generate interest.  (I suppose there are some examples of that,
however, such as Twitter.)

Over all, this article's system seems like a solution looking for a real
problem.  I doubt that enough users would ever go to this much trouble,
to allow anything like this article to work.  However, my project paper
might look like this article, describing a recently built prototype.
Hopefully its specification will be more realistic.


## 2013-10-29 [Shakimov, Lim, Caceres, Cox, Li, Liu, & Varshavsky (2011).  Vis-a-Vis: Privacy-Preserving Online Social Networking via Virtual Individual Servers](comsnets11.pdf)

This article describes another distributed social networking system.
Its authors implemented a prototype of a location-based online
social network (OSN), such as Foursquare.  Each user has his own
virtual individual server (VIS), running in a cloud such as
Amazon EC2 or Rackspace.  A user can create a group, administered
by his VIS, which other users can join, to share location updates
and "check-ins" with each other.

An elegant aspect of the design is its dual use of the location data.
Users can disclose their locations with varying degrees of vagueness.
Their VISs then self-organize into a location tree, so the network
topology reflects their physical location, minimizing latency.

Experimental results compare latency between centralized and
distributed versions of this OSN.  Of course, the centralized version
is faster for all operations, by orders of magnitude for some.
However, the article points out that the last mile 3G connection to
smart-phones is even slower, so the decentralized slowness is not
an order of magnitude slower than that, and not even significantly
slower for certain operations.  However, those smart-phones were
just terminals, with the distributed VIS still in the cloud.  These
results suggest to me that a VIS hosted in a smart-phone would have
untenable latency, despite the elegant design of the self-organizing
location tree, unless perhaps there were enough to form a mesh
network.  The distributed possibilities are tantalizing, but impractical.

I have several concerns about the design.  First of all, I cannot
imagine enough users paying to host their own VIS.  If they were willing
to pay for OSN services, to avoid advertising and maintain IP rights,
it would be much cheaper to subscribe to a centralized OSN that features
such a business model (as the cloud computing utilities do).
The authors assume that the hosts have a Trusted Platform Module (TPM)
that can prove to users and other nodes that the correct software
is executing.  I do not understand what that would accomplish,
besides passing the buck.  I think they are trying to mitigate the
storage of unencrypted data in the cloud, which enables services
such as range queries over location data, but given this hosting,
I do not see the point of making the servers individual.

My second concern is with the integration of major OSNs, such as
Facebook.  Vis-a-Vis has a browser extension to rewrite Facebook
pages, filling in hooks to Vis-a-Vis.  That sounds like a
maintenance nightmare, as Facebook changes its page designs.

My final concern is with the maintenance of groups.
A group descriptor includes the owner's public key
and the name of the group (visible to group members),
distributed out of band.  This avoid naming conflicts,
but doesn't it lead to many overlapping groups?
Suppose I have a group of friends at school or work,
and not all of them know each other.  Each member
would have a somewhat different group of their own friends.
In Vis-a-Vis, each would need to join the group of
each of their friends, and each of their friends would
need to join their group.  Is everyone posting their
check-ins to their own group, and looking at check-ins
from everyone else's group?

My project paper might look like this article, as well.
It does not include an experiment, but it will have an
architecture, implementation, and evaluation.
