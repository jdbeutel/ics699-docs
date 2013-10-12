# Squicciarini, Shehab, & Paci (2009), Collective Privacy Management in Social Networks

They implemented a bidding system between shared owners of Facebook photos to determine each photo's visibility.  It was a proof-of-concept FB app called Private Box, which FB users could opt into.  (I cannot find any sign of it on FB or Google today, however; there is a Private Box FB page, but it's for a New Zealand post office service.)  The shared owners default to whichever FB users are tagged on the photo, but must be approved by the actual owner.  These co-owners are actually stakeholders, because they appear in the photo.  The bidding system is a "Clarke-Tax mechanism", to prevent users from gaming the system.  The photo is visible to owners-only until all owners bid.  Then the privacy setting with the greatest collective good ("social welfare"), defined in terms of each owner's bid, wins the auction.  The bids are in terms of fiat points, but I am not sure how users get those points to begin with.

They detailed a generic algorithm for all this in mathematical set notation.  I guess the set notation was just supposed to make the explanation easier to understand, since they didn't seem to build anything on top of it, but I found it a rather awkward and unusual way to describe an algorithm.  The visibility choice in their FB app did not fully implement this algorithm; it was limited by FB constraints to either friends or co-owners-only, lacking a choice of public; however, I'm not sure if by "friends" they also mean "friends-of-friends".  The algorithm went into some detail about how it could take into consideration multiple hops of various types of relations, such as friend-of-friend or co-worker-of-friend.

For ease of use, they proposed an algorithm for an inference technique to base the default bid on the user's previous bids on photos with similar content tags (not id tags).  They did not implement this, however.

I can't find the quotes now, but I think they said that owners are not allowed to change their bids, and somewhere else said that owners can be added later.  How could that be after the bidding is done?  Would all the owners just re-bid?

It has a good section on related work.  I'm interested in how Carminati et al. "extended their previously proposed model [using client cryptographic certificates] to make access control decisions using a completely decentralized and collaborative approach."  (B. Carminati and E. Ferrari.  Privacy-aware collaborative access control in web-based social networks.  In DBSec, pages 81-96, 2008.)  "Their proposed work is orthogonal to the work proposed in this paper.  Our analysis of collaborative privacy management does not relate to the privacy of users' relationships.  Rather, we focus on collaborative approaches for privacy protection of users' shared content."  

Other interesting references:

K. K. Gollu, S. Saroiu, and A. Wolman.  A social networking-based access control scheme for personal content.  In Proceedings of the 21st ACM Symposium on Operating Systems Principles (SOSP '07)- Work-in-Progress Session, 2007.

R. Gross and A. Acquisti.  Information revelation and privacy in online social networks.  In Workshop on Privacy in the Electronic Society, 2005.

M. Hart, R. Johnson, and A. Stent.  More content - less control: Access control in the Web 2.0.  In IEEE Web 2.0 Privacy and Security Workshop, 2007.


# Besmer, Lipford, Shehab, & Cheek (2009).  Social Applications: Exporing A More Secure Framework.

They propose more granular access control settings for FB apps, implement a prototype user interface, and perform a small user test on it.  Note that this is dealing with another kind of transitivity, besides photos, in that an app allowed by user A can also access user A's friends' data by default, if user A's friends allow user A to see their data.  The prototype makes users more aware of the profile data that an app is requesting access to (similar to OAuth) as well as of what decisions their friends have already made about it (to advise and help the decision).  By limiting an app's access, a user protects his own data and the data of his friends who are not concerned about their own privacy.

The user study was on 17 students.  In its results, the paper described the behavior of users as falling into two groups of about the same size:  those who bothered to customize privacy settings (motivated), and those who did not (unmotivated).  It also used a survey and observed behavior to categorize the users with Westin's method, into privacy fundamentalists, pragmatists, or unconcerned.  It classified all of the unmotivated users as pragmatists, while most of the motivated users were fundamentalists (with 2 pragmatists and 1 unconcerned).

Lipford and Besmer have also published some other interesting papers in this area.

I didn't find much of interest in the related work section.  One reference that sounds interesting, by the authors of the previous paper, is Shehab M., Squicciarini A. and Ahn G., Beyond User-to-User Access Control for Online Social Networks, ICICS 2008, October, 2008, Birmingham, UK.


# Besmer & Lipford (2009).  Tagged Photos: Concerns, Perceptions, and Protections

Same authors as above, very short paper (6 pages) "Spotlight on Works in Progress".  They performed a user study of 3 focus groups totalling 14 FB users mostly between ages 18 to 24, all found on campus.  Interesting results:

* "participants were often keenly aware of specific individuals or groups of people who they were concerned of seeing an unwanted photo of them.  Family members such as parents and siblings comprised most of the perceived threat.  In no case did a participant express concern about a stranger finding their photos, and deriving their personal location or personal information from them."

* "Participants expressed a great deal of concern over their lack of control in removing photos from Facebook and from friends' profiles.  While participants could untag to remove a reference to themselves, the photo remains close to them because it is cross-linked to others in the photo and remains accessible from other profiles."  "Despite being insufficient, untagging was viewed positively since other methods required negotiation and time."

* "Another commonly cited concern was photos containing 'incriminating evidence'.  This most frequent example cited by participants was being intoxicated."

* "Participants were also aware and interested in shaping their identity based upon their associations with different people, and noted that they untagged photos in order to disassociate from certain groups."

* "Participants perceived that the photo uploader is the owner regardless of those in the image.  Several indicated that their perception is based on the current model on social network sites where the owner has more controls over that image.  For example, if someone other than the owner tries to tag the photo, the owner is sent a request to approve that tag."  [I didn't know that.]  "Participants also expressed that the person who has the photo has the right to do what they want with it, including post it online; and they were hesitant to take away these rights, even if it violated their own privacy."

* "Participants also felt that there was a 'moral obligation' of the owner to protect the privacy of those in the photo."

The paper goes on to suggest that a social network allow users tagged in a photo to request of the photo owner that certain individuals, groups, or networks be restricted from viewing it.  The user can define groups or choose from recent selections.  The request would tell the photo owner how many people the tagged user wants to restrict, but not reveal their identities, to provide the user some privacy and avoid blackmail.  (The tagged user previews the request before sending.)  Sending the request also temporarily untags the user, until the owner decides whether to honor the request.  If not, the user can still permanently untag himself from the photo.  "We believe this proposed mechanism will reflect the users' perceptions of the photo owner and the rights associated with being one.  It also helps to reflect the 'moral obligation' of the owner to protect the tagged users.  Our aim was to relieve some tension on a user over untagging and place more tension on the owner to comply with the request."  Users can also keep a watch list of photos they have requested restrictions on.  This makes them easy to review, check who has been prevented from seeing each, and add new requests if necessary [or drop old ones that become unnecessary, I assume].

One thing not clear in the suggestion is whether or not the restricted individuals are chosen from the set that currently has access.  On the one hand, limiting choices like that could reveal who other users want to restrict (e.g., if there's only one other user in the photo), and unwanted users could gain access later by friending someone or having their restriction dropped by another user.  On the other hand, including users who do not have access to the photo widens the choices to several hundred million FB users.


# Olson, Grudin, & Horvitz (2005).  A Study of Preferences for Sharing and Privacy

This "Late Breaking Results: Short Papers" is only 4 pages, but has some interesting results on general privacy preferences and expectations.  First they conducted a general survey to identify pieces of information as well as kinds of people to whom users may be concerned about disclosing them.  They obtained 170 examples from 83 people.

Then they found 30 people to come into their lab for a 2-hour user study.  The participants' median age was 35, and they worked at companies ranging from 20 to over 150,000 employees in occupations spanning a wide spectrum, because this study's concern is information sharing and privacy in the workplace.  The 30 participants filled out grids of 40 types of information by 19 types of people, filling in each cell with a scale of 1 to 5 or "N/A" "how comfortable they would be with sharing each particular type of information with each type of person without knowing what that person would do with it."  Finally, various cluster analyses were performed on the grids to find people and information that participants rated in similar ways.

The clusters may help a system default access control settings to an intuitive and useful level, while allowing users to go into finer details or exceptions when necessary.  "We found that peoples' willingness to share depends on who they are sharing the information with."

One interesting access control method it mentioned in particular as a possibility is "a policy of _informing_ the person requesting access, at the time of an attempted access, that there is an audit trail of accesses--and then logging the accesses for the owners' later review."

Unfortunately, the access control in this paper is not transitive; it's conventional.  If this paper becomes necessary anyway, it references details several times in a paper by the same authors the year before, Toward understanding preferences for sharing and privacy, MSR Technical Report 2004-138.  ftp://ftp.research.microsoft.com/pub/tr/TR-2004-138.pdf


# Nov & Wattal (2009).  Socail Computing Privacy Concerns: Antecedents & Effects

They analyzed survey responses of 192 Flickr users regarding privacy concerns at a community-specific and Internet level, correlated with the way those users were actually sharing photos on Flickr:
* number of public photos:  sharing indicator
* number of contacts:  network centrality
* ratio of public to all photos (including private):  measure of restrictive privacy settings

They conclude that the privacy relationships between a user and her community are not the same as between a commercial entity on the Internet (such as an e-commerce site).  They recommend that SNS designers "act in order to decrease users' privacy concerns."  In particular, they "highlight the importance of sharing norms and the sense of trust in other community members - both of which can be encouraged through design and ongoing operation of social computing communities."

This short, 4-page, paper has unsurprising results and obvious conclusions, which don't seem to offer much help with my particular research issue.  It looks at sharing photos, but not between specific users, and never transitively.  The "restrictive privacy setting" is such a basic, binary measure that it sheds no light on the detailed settings I want to research.


# Kwasny, Caine, Rogers, & Fisk (2008).  Privacy and Technology: Folk Definitions and Perspectives

They held 5 focus groups (26 Georgia Tech students, and 6 women aged 65-80), with a privacy belief questionnaire (Likert scale) at least 24 hours prior to classify them as one of three Westin privacy concerns.  Focus groups were of similar age and gender to encourage disclosure.  Each group started by writing each member's definition of privacy, and then discussed 6 scenarios.  The researchers intend to hold more focus groups of older adults.

They classified most participants, 82%, as "privacy pragmatists", perhaps skewed because most were younger adults.  5 were "privacy fundamentalists", and 3 of those were older adults (half).  Most participants defined privacy as involving "other people" and "information".

The biggest difference with age was that "older adults tended to define privacy in terms of space instead of information."  They "mentioned private information as something official that they are given".  Younger adults brought up ideas of control, decisions, non/disclosure, the right to privacy, multual respect, and personal information; they tended to define privacy mostly in terms of the desire to limit disclosures to others.

Regarding gender differences, women "were more likely to talk about privacy involving others", and only women brought up topics of "respect", "seclusion", "the 'personal' nature of privacy", "safety", and "having to protect one's privacy".  On the other hand, men mentioned "convenience", "freedom", "anonymous", "comfort", and "not being seen or heard".

Unfortunately, this short paper doesn't seem relevant to my research issue either.


# Gross & Acquisti (2005).  Information Revelation and Privacy in Online Social Networks

In this paper, from the ICS 668 bibliography, the authors note with some alarm that university students in general do not seem concerned about their privacy.  (I imagine some dismay by the author from the Data Privacy Lab, Ralph Gross.)  They do not attempt to discover why, but offer several simultaneous hypotheses:
* pragmatic disclosure as signaling, expecting benefits that exceed the perceived costs
* acceptance (ignorance?) of default privacy settings, as an interface design issue
* "peer pressure and herding behavior"
* myopic privacy attitudes (young people not thinking ahead)
* "the sense of protection offered by the (perceived) bounds of a campus community"

Most CMU undergraduates (62%) were using Facebook, disclosing personal information to all CMU users and their friends:
* real name: 89%
* identifiable profile photo: 55% (90.8% * 61%)
* fully identified and presumably accurate birth date: 86% (87.8% * 98.5%)
* home town: 72%
* current address: 51%

Very few CMU users had increased their privacy settings.  98.8% left their profile searchable by the public (1.2% limiting searches to CMU users), and 99.94% left it viewable by all CMU users (0.06% limiting viewing to friends or friends of friends).

The paper lists privacy implications:
* stalking (revealing likely location via home address and course schedule, as well as AIM online status)
* re-identification via demographics or photo recognition, linking datasets without explicit identifiers but with more personal information
* identity theft by guessing SSN from hometown and birth date (assumes assignment at birth?  I'm not sure how credible a threat this is)
* building a digital dossier for potential use throughout adult life

Finally it notes that Facebook security can be easily circumvented by somehow briefly getting control of any email address at a given school, manipulating users via social engineering (what school has no students would for a few bucks?), or using advanced search features to deduce other data which can be searched but not viewed.

This is a nicely written, clear, straightforward paper, but I'm not sure how applicable it is to my research issue.  Its Facebook demographic was considerably more narrow than my concern, or even than Facebook today, and I tend to agree with the explanatory hypotheses, which depend heavily on that 18- to 24-year-old university student demographic.  Also, it is entirely concerned with how and what information individuals reveal about themselves and the consequences that could have for themselves, not third parties (besides potential security holes with respect to the individual).


# Joinson (2008).  'Looking at', 'Looking up' or 'Keeping up with' People?  Motives and Uses of Facebook

This study, from the course bibliography, identified 7 factors in how and why people use Facebook:  social connection, shared identities, photographs, content, social investigation, social network surfing, and status updates.  Then it looked at significant relations between those factors and the frequency of visits, total time spent, and number of "friends" on Facebook.  It found that users made repeated visits for surveillance, but spent longer per visit for content.  Unexpectedly, users motivated by "social connection" did not have more friends, and users motivated by "content" (apps and games) had fewer friends.  Perhaps the gamers are busy playing instead of finding new friends.  (Or, I would guess, friends don't appreciate the game spam.)

The study concludes that different users have different reasons for being on Facebook.  The biggest reason is 'keeping in touch', which has two sides: surveillance (seeing "what old contacts and friends are 'up to', how they look and how they behave"), and self-presentation (for social capital building, to "invest in and maintain ties with distant friends and contacts").  Social connectivity and perpetual contact motivated younger (and female) users more than older (and male) users.  Another motivation is 'social search' or 'social browsing':  looking up people met offline, or 'virtual people watching' online.

The different goals lead to different privacy settings.  To play apps, many require access to comparative profile data, and for self-presentation and meeting new people, one must expose ones profile.  Naturally, there is tension between how much a user chooses to reveal and what the other users want to see.  The results also show acceptance of the newsfeed and its "new role as a 'killer app'", despite the initial outcry.

This study contradicts the one above in that most users claimed to have increased their privacy settings:
* 'somewhat' more private: 25.6%
* 'much more' private: 21%
* 'as private as possible': 10.9%
On the one hand, it's just a claim.  But, on the other hand, this study was a few years later, after some publicity about Facebook privacy risks, a different demographic as subjects were recruited from all of Facebook (which I think included more than just university students by July 2007), and I would assume that Facebook had updated its user interface for privacy settings.

The method of this study reminded me of the Olson et al, "A Study of Preferences for Sharing and Privacy", in that it was done in two stages.  An exploratory stage elicited free text responses which were consolidated to 8 themes and finally 46 items.  The second stage, identifying uses and gratifications, used those 46 items with a 7-point Likert scale to produce data for the various analyses.  Unfortunately, I did not understand the statistical analyses.  It used "exploratory factor analysis" with "varimax rotation", "eigenvalues", "scree plot", and "unique loadings".  Then, those results were folded back in with demographic data for several MANOVA (multivariate analysis).  I cannot second-guess the numbers.

Sadly, I'm not sure if I can apply this study to my research question.  But, at least it seemed to be a well done and well written study, which may help me judge the quality of the other papers I read.


# Simpson (2008).  On the need for user-defined fine-grained access control policies for social networking applications

This paper refers to a significant amount of literature on e-health, asserting that the following principles should also be applied to SNS:
* "Who can see what is clearly the responsibility of the data owner."
* "As one cannot predict a priori what policies particular data owners might wish to impose, support for flexible and fine-grained models is essential."
* "Data owners should be able to know who has seen their data, i.e. tailored or transformed audits should be available."

It refers to "data grids" as a way for separate organizations to collaborate as a "virtual organization" "via the sharing and aggregation of data."  And, it holds up as an example of the technical part of a solution an implementation named "sif" (service-oriented interoperability framework), which the author himself was apparently involved with developing.  It also mentions XACML (eXtensible Access Control Markup Language) as part of the implementation.

Finally, it gives some examples of access control policies (rules) in "the mathematical language of Z", which looks like a cross between set notation and a simple programming language.  The examples are explained well enough for me to understand, and look like they would be easy to implement in a language like Groovy, or even a native Z compiler if one exists.  There is even an example of transitivity, friends of friends but not friends of v:  friends(| friends( u ) \ {v} |).  Unfortunately, these examples and language don't yield any insights, and a user could not read them.

A caveat mentioned as a side-effect of expressibility is complexity: "writing expressive policies is a complex task."  It "would have to be made as simple as possible."  This obvious dilemma is, in my mind, the primary issue with flexible and fine-grained access control, but this paper offers no solution for that.  Nevertheless, the main point of this paper, that SNS should avail itself of the research already done in areas such as e-health, is well taken.

Commenting on the writing itself, it read well and I enjoyed it, but it repeated its basic points, and a couple grammer errors stood out (e.g., "their" instead of "there").  It also had a lot of sizable quotes, although they were good.

Interesting references:

Anton, Bertino, Li, & Yu (2007).  A roadmap for comprehensive online privacy policy management.  Communications of the ACM, July 2007.

Becker, Fournet, & Gordon (2006).  SecPAL: Design and semantics of a decentralized authorization language.  Technical Report MSR-TR-2006-120, Microsoft Research.

Carminati, Ferrari, & Perego (2006).   Rule-based access control for social networks.  In "On the Move to Meaningful Internet Systems 2006: OTM 2006 Workshops."  Spring-Verlag Lecture Notes in Computer Science.

D'Agostino, Hinds, Jirotka, Meyer, Piper, Rahman, & Vaver (2008).  On the importance of intellectual property rights for e-science and the integrated health record.  Health Informatics Journal.

Hart, Johnson, & Stent (2007).  More contant - less control: Access control in the web 2.0.  In Proceedings of the IEEE Web 2.0 Privacy and Security Workshop.  IEEE Press.


# Strater & Lipford (2008).  Strategies and Struggles with Privacy in an Online Social Networking Community

This was a study of 18 undergraduate students who use Facebook at UNC.  Each was interviewed for about an hour in a usability lab, recording the computer screen, audio, and video.  Each completed a demographic survey and then logged into his/her own Facebook profile, showing the privacy settings and what information was disclosed.  They were interviewed about their motivations, opinions, and decisions, and then viewed four unfamiliar profiles and gave their impressions of each person and profile.

It noted two things about privacy strategies:

1.  They tend to be all or nothing.  There are two approaches: limiting the info given, and changing privacy settings:
    1.  For settings, 5 participants (28%) restricted all of their profile to only their friends, and 8 participants (44%) added no restrictions (leaving their whole profile open to their network).  Only 5 (28%) used settings between all and nothing.
    1.  For giving info, the participants chose to either leave all the fields blank, or fill in most of them (except what may be considered redundant or had been added later by Facebook).  There were few who did anything between all and nothing.
2.  The strategy decision tends to be a one time event.  "Participants reported forgetting what their privacy settings were, or whether they had even changed their default settings."  They make this decision as new users, and don't modify the settings based on ongoing use.

The participants judged disclosures based on two main factors:

1. "what they deemed safe and appropriate" (which is hard to judge for their friends or themselves, since it is appropriate between themselves when they need it, even while it's inappropriate for a stranger who also has access), and
2. "what seemed to be socially acceptable and normal within their networks."

The study found two main flaws with Facebook privacy:

1.  As users gain experience on Facebook interacting with their friends, they are lulled into the perception of a smaller audience who can access their profile, leading them to reveal more than they intend to the actually larger audience.
2.  Facebook's user interface for privacy settings is too complicated, comprising many different pages, misleading users into thinking that their settings are more restrictive than they actually are.

Participants reevaluated their privacy strategies after certain events:

1. unwanted contact from stranges,
2. Facebook introducing the newsfeed, and
3. participating in this study.

The study suggests several solutions:

1. "enforce, or at least default to, more restrictive settings, particularly for sensitive and risky information."
2. Make privacy controls highly visible and accessible while modifying the profile.
3. Promote a clearer understanding of the audience of the information.

However, it notes the balance between privacy and the functionality/utility of Facebook.  Partial restriction is hard to configure now, and off-putting to many browsers, who don't know what to make of it.  It suggests defaulting to allow access to info that browsers value more, such as photos and personal info, particularly shared interests (presumably not defaulting access to other info, such as the wall posts).  But, it admits the importance and difficulty of achieving a balance like that with good usability and customizability, without suggesting a specific solution.  I would like to read about the UI that author Lipford as well as Besmer & Watson designed and prototyped for this in "Understanding Privacy Settings in Facebook with an Audience View" (UPSEC 2008).

Although this paper did not address transitivity, I think that the usability issues for privacy settings are still relevant to my research topic, with respect to making it easy for users to confidently share their data with whomever they want and nobody else.  This is a significant and real concern.  Hopefully it doesn't make my topic too broad.


# Young & Quan-Haase (2009), Information Revelation and Internet Privacy Concerns on Social Network Sites: A Case Study of Facebook

They took a survey of 77 undergraduate university students, and interviewed 21 others (including a live Facebook profile analysis), much like Strater & Lipford's study above.  They focused on the strategies that students used to protect their privacy.  The interview format allowed them "to discuss what information is accurate, why certain types of information were posted and not others, and the social meaning of the information included on the profile."

An interesting discrepancy from Gross & Acquisti is that 64% of the respondents to this survey claimed to have limited their profile visibility to "only friends", while only 0.06% actually had their profile visibility limited to friends or friends of friends in the study done 4 years earlier at CMU.  I would like to see more research on this discrepancy.

The analysis of the survey found that students who revealed more information had more FB friends, students who were concerned about internet privacy revealed less information, and that there was no association between concern about unwanted audiences and information revelation.  (Users may have dealt with the latter concern by reducing the visibility of their profiles.   In this paper, "revelation" seems to mean the information input to FB, not the visibility settings, i.e., who can see that information.)

The interviews (with profile examination) revealed that students do take action to protect their privacy on FB.  Most do not include contact information:  "all 21 interviewees excluded their physical address and landline phone number, and 18 of 21 chose to exclude their cell phone number."  Some noted that this was to reduce their risk of "unwanted contact or physical harm from unknown others."  Other concerns noted were that "their information would be used, sold or appropriated without their knowledge or consent," and that "known others--that is, individuals known to the user in an offline context--would see information and/or images posted on Facebook that was not intended for them to view."  (I suppose this is obvious, though.)  "For the most part, students' information revelation was influenced by negative reports in the media rather than personal experience."

Some respondents use FB as a replacement of email and/or IM.  In this regard, FB functions as "an address book that is kept and updated by its users."  Another consideration mentioned for information revelation is "whether or not the information had been previously mentioned in an offline context."  Surprisingly, the more visible a user's profile, the more information he revealed.  This may just suggest that such users are not concerned about privacy.  The paper categorized two kinds of privacy concerns: expressive (i.e., image, making an impression on known others), and informational (i.e., unwanted audiences of potentially harmful purposes).  Interestingly, "students do not use fake or inaccurate information as a protective measure," primarily because their friends would question that information's validity, causing confusion.

Unfortunately, this paper didn't have anything specific to transitivity, although the users' concerns and strategies may have some relevance to my project.


# Hart, Johnson, & Stent (2007).  More Content - Less Control: Access Control in the Web 2.0

This 2-page paper advocates usable access control policy specification and automatic policy application, for blogs and social networks.  For automatic application, it suggests leveraging given tag folksonomies by infering appropriate tags for new documents via "several light-weight techniques from machine learning and natural-language processing."  This won't be perfect, so it also requires "a good, easy-to-use feedback mechanism for users to correct erroneous tags."  Usable policy specification can also include natural language input, or templates (such as, "allow group <name> to access blog posts on topic <tag>").

It mentions two ongoing projects in particular, PLOG (Privacy/Policy-aware bLOGging engine), and "a Wikipedia Integrity Project".  Hart, Castille, Johnson, & Stent published a paper apparently about PLOG for the 2009 International Conference on Computational Science and Engineering (Aug 29-31, Vancouver, Canada).

This paper is short, sweet, and to the point.  Unfortunately, these efforts don't look applicable to profile data fields, which lack natural language for processing.  Also, this paper mentions no details on implementations.  Whether the authors can actually do what they say is a significant question.


# Lipford, Besmer, & Watson (2008).  Understanding Privacy Settings in Facebook with an Audience View

They did a usability study with 16 people, comparing the accuracy and comfort of the (2008) Facebook privacy settings user interface with a static HTML prototype they made.  Their prototype was oriented around examples of the user's profile as viewed by different audiences: friends, network, search, or the profile owner himself.

The prototype yielded significantly higher accuracy and comfort than Facebook's actual interface, and it was 42% faster on average, too.  Moreover, some users were dangerously inaccurate with the actual interface.  However, their prototype has several limitations which may affect these findings:
* If the profile owner is a member of multiple networks (or groups, if Facebook allows), then there will be more view tabs than can fit across the web page.  The more views there are to check and configure, the less advantage to this design.
* The prototype does not include the controls for configuring the privacy settings.  That may make it simpler than the actual Facebook interface, improving accuracy and speed.  On the other hand, they noted a problem with this simplicity, in that participants spent extra time looking for information missing from a particular profile view.  For their next prototype, they plan to show the non-visible information, in a way that clearly distinguishes it from the visible information and minimizes the impact of the visible layout, while displaying hide/show controls next to each piece of information.

Interestingly, one or two papers I read earlier also referred to FB's global profile visibility setting, but that confused me, because I didn't recall any top-level setting like that, only more specific settings.  I even reconfigured my FB privacy settings last week, and didn't notice it.  But in figure 1 of this paper, I finally realized where the global setting is.  It's still the first drop-down select box on the Settings > Privacy -> Profile (Basic) page, but it's listed together on the same level as all the other settings below it (such as Basic Info, Personal Info, Status and Links, etc), which I now suspect are more specific settings.  But, when this study was done, the global setting was separated at the top of the page by two lines of text explaining that the settings below were more detailed alternatives.  The usability (accuracy) of that part of the interface is obviously much worse now, although Facebook may have done that intentionally (if I may be parinoid).

On the other hand, several participants in this study mentioned wanting to be able to view their own profile from the perspective of a particular person.  The study noted that Facebook lacked that feature, but it has been implemented now, although limited to friends.  Even though this paper was published just last year, significant parts seem to be out of date.


# Lipford, Hull, Latulipe, Besmer, & Watson (2009).  Visible Flows: Contextual Integrity and the Design of Privacy Mechanisms on Social Network Sites

This 5-page paper is something of a capstone to their previous papers.  It introduces the perspective of "contextual integrity as a framework for analyzing privacy with information technology."  It references Helen Nissenbaum (2004), Privacy as Contextual Integrity, in Washington Law Review.  She suggests two fundamental types of norms for information sharing:

1.  "appropriateness" deals with "the type or nature of information about various individuals that, within a given context, is allowable, expected, or even demanded to be revealed" (for example, sharing your mom's medical history with your doctor, but not your religeous views with your employer), and
2.  "distribution" covering the "movement, or transfer of information from one party to another or others" (for example, how it's inappropriate for a friend with a radio show to broadcast your personal details that you have shared with her).

The paper claims that Nissenbaum derives two main points from this:

1. "information is always tagged, as it were, with the context in which it is revealed: there is no such thing as context-free information."
2. The scope of privacy norms depends on the context.  "There is no such thing as a universal privacy norm."

The authors apply this theory to support their assertions from earlier papers that SNS need better privacy support.  They examine privacy issues for profiles, news feeds, photos, and applications (generally in terms of Facebook).  As a solution, they propose "to make these flows of information more visible", with a nice list of design guidelines:

> * Information flows should be transparent.  Users should always be able to determine what information is shared, and with whom.
> * Increase the awareness of information flows during regular activities, so that the ongoing decisions users make are informed by the context of their information.  This is needed to combat the "shrinking audience" phenomenon.
> * Increase awareness of how much information is archived, and still available.  This may influence users' current decisions about what to post, and may also influence users to remove old or outdated information.
> * Make information and context concrete.  Provide examples of the specific pieces of information when revealing information flows, and examples of specific people or organizations with whom it will be shared.
> * Provide more control over the information flows.  While many sites have some privacy settings, users are still not able to fully control the sharing of all of their information.
> * Do not abruptly modify the flow of information.  Give users a chance to modify their behavior before changes that could result in privacy problems.

Finally this paper shows a much-improved UI prototype for the profile privacy settings from the previous paper, including profile items with individual controls, displayed consistently instead of hidden.  It also references their other papers, noted above, on privacy settings for photos and applications.


# Gollu, Saroiu, & Wolman (2007).  A Social Networking-Based Access Control Scheme for Personal Content

I saw this cited in one or more papers so far, but it's just 1 page long.  Nevertheless, it outlines a need for orienting a content sharing social network authentication and access control scheme around the user who is sharing the content, instead of making the user try to recruit and redefine his social network on each SNS (MySpace, Flickr, YouTube, Google calendar, etc).  It suggests a public encryption scheme managed in the user's local address book, based on two concepts: "social attestations", and "social access control lists".  The social attestation is like a certificate of a social relationship, issued by an SNS or the user offering the content.  The social ACL is the content owner's list of users (i.e., public keys) or relationships that should be allowed to access the content.

This 1 page paper ends before it offers any usable details, but it prompted me to find the following related paper.


# Tootoonchian, Gollu, Saroiu, Ganjali, & Wolman (2008).  Lockr: Social Access Control for Web 2.0

This 6-page paper goes into more detail about the previous paper's access control scheme.  It lists two requirements and corresponding implementation proposals:

1.  "Provide a simple and flexiable way of defining access control rules." -> use social relationships to describe access control policies
2.  "Eliminate the management issues associated with using many content sharing sites." -> separate social networks from content delivery and sharing

It also adds a "relationship key" to protect the confidentiality of the social attestation, so only those holding the same kind of attestation (or the SNS making use of it for access control) can read it.  (This seems typical of cryptographic schemes:  they get paranoid and add more and more layers of cryptography.)

It mentions three methods of support for "revocation" of an attestation:
* Include an expiration date in the attestation.
* Add an exclusion list to the content's ACL, so even though someone has the required relationship, they are explicitly excluded.
* Reissue new attestations (to everyone else) with a different relationship key (updating the ACL to the new key).
I am concerned about revocation because of events like divorce.  I would note that the listed methods are not really revocation, because they change the accessability on the content server, but have no effect if the content has already been downloaded.

Lockr attestations are non-transferable: "access rights cannot be delegated (unlike with typical capabilities) - no one other than the issuer can grant access to the content."  I'm looking for transferability, or transitivity, but this limitation seems like just a result of Lockr's choice of rules, not an inherent characteristic of this type of scheme.  I also think this is not entirely true, as Lockr seems like just an authentication and authorization scheme.  This paper did not make it clear, but it seems to me that since this scheme has a host that must enforce the ACL, then that host is capable of accidentally or on purpose making the content available to anyone.

In the related work section, this paper contrasts Lockr with PGP and OpenID.  "PGP creates a 'Web of trust'", in "a single trust/no-trust relationship", while Lockr uses only direct certifications of various relationships.  "PGP's trust relationship is transitive.  However, since social relationships are diverse and complex in real-life, we have decided not to attempt to combine them to create transitive relationships."  Lockr's comparison to OpenID seems like a red herring, making me question the involvement of the Microsoft employees (Wolman at that time, and Saroiu within the following year for their next paper on Lockr), because it suggests that OpenID requires trusted third-party identity providers and makes users vulnerable to phishing attacks by using passwords to authenticate.


# Tootoonchian, Saroiu, Wolman, & Ganjali (2009).  Lockr: Better Privacy for Social Networks

This 12-page paper adds a few more details and scope to the previous one.  The main addition is to the references and the related work section.  It fleshes out its earlier mention of Reliable Email (which exploits Friend-of-Friend relationships) and Capabilities.  The important differences are that with capabilities, they encapsulate a unique object identifier and access rights, so a capability can't be leveraged elsewhere later, and they are inherently transferable, naturally supporting delgation.  This makes me interested in looking into Capabilities.  It also mentions Authenticatr, NOYB, and Persona.  That includes the Persona reference that Dr. Suthers found, which I will look at, and I may look at the NOYB reference too.

Also note that lockr.org provides an implementation as a demonstration.  A Facebook app provides a console for issuing and managing attestations to social contacts.  A BitTorrent (Vuze) plugin provides access to Lockr content in a distributed network.  And a Firefox add-on provides access to Lockr pictures in Flickr.  (The similarity in name suggests to me the original intent or metaphor.)

I can't find the "Chit-based access control" reference.  The referenced authors have lots of publications at U of Maryland, but the 3 Lockr papers are the only thing Google scholar has referencing this one, and the University of Maryland CS-TR-4878 is incorrect.  I found that ID is actually a different publication: http://www.lib.umd.edu/drum/handle/1903/6634  (on the evolution of the U Maryland CS department 1979-2006, and not containing the word "chit").  However, two of the referenced authors, Neil Spring and Bobby Bhattacharjee from U Maryland, are authors of the Persona paper I'm reading now.


# Sarvas, Viikari, Pesonen, & Nevanlinna (2004).  MobShare: Controlled and Immediate Sharing of Mobile Images

MobShare is a mobile client-side application for the Symbian Series 60 operating system (on some smartphones by Nokia and other manufacturers).  The app provides easy photo sharing, using phone numbers chosen from the phone's address book as an ACL, via a web server.  Centering access control around these kinds of mobile phones is convenient (for those who have these phones) because it solves the authentication and registration problems.  However, it is quite simple and limited, not suggesting anything that could be generalized beyond smartphones or to transitivity.  It also notes disadvantages with one person who has several phone numbers or who changes phone numbers.


# Shand, Dimmock, & Bacon (2003).  Trust for Ubiquitous, Transparent Collaboration

This paper is highly relevant to my topic!  It covers exactly my use case, except with PDAs instead of SNS.  It uses a public key framework to support transitive trust and data sharing, with fuzzy logic.  It is automated, but interactive when falling within the parameters suggesting that the owner's attention is waranted.

Recommendations advising data, its relevance, and level of trust are signed by the recommender's private key.  (I assume that the trust chain starts with public keys that the owner secures out-of-band, e.g., a face-to-face exchange via PDA.)  Trust is not binary; it comes with a confidence or belief rating that factors down the chain.  The cryptographic signatures do not protect the data, but merely validate the trust chain.  The recommendations are used to decide whether or which data to provide to a requester, and to decide the accuracy and relevance of the data to display to the PDA owner (or not).  This is access control, but once the requester has the data, it's in his hands (although the signatures prevent the requester from tampering with the recommendations that come with the data).

The key insight of this paper is "unifying trust assessments with access control."  Since the PDAs are managing distributed data, not centeralized on a web server, once the data is exchanged, control is lost.  The important thing is to not provide the initial access and exchange if the requester is untrustworthy of that data.  (However, this is also true for a centralized web server, because even if it revolks access, the requester could have already copied the data elsewhere.)

The PDA owner can define categories similar to roles, such as immediate family, business colleagues, business contacts, friends, and relatives.  Categories go into a hierarchy with four privilege bands: the owner, privileged, groups, and public.  For example, categories in the "groups" band "can conventionally recommend that members may write data to their own categories and those below them, and read data below them."  "The banding of categories allows user privileges to be easily and intuitively assigned.  However, if necessary the banding may be overridden, by explicitly associating extra permissions with categories or users."

"Recommendations associate one permission with another in our trust framework.  By treating the identities of actors, categories and data entries as permissions, we can use a homogeneous recommendation structure for privilege assignment and for restricting the flow of information."  "[R]ecommendations conveniently factorise and encapsulate trust policy."  For assessing risk and deciding access or interruption, "the position of a piece of data implicitly gives it a value that can be used to assess the risk of an operation involving it:  the higher in the hierarchy, the greater the value."

Dimmock published a 145-page thesis on this in 2005, "Using trust and risk for access control in Global Computing".  This was all part of a European project called SECURE, altho it didn't seem to produce any usable software.  Interesting references in this paper are Abdul-Rahman & Hailes (2000), Supporting trust in virtual communities, and Josang (2001), A logic for uncertain probabilities.

The recommendations that come with an initial piece of data, as well as the categories, remind me of Nissenbaum's contextual integrity. 


# Baden, Bender, Spring, Bhattacharjee, & Starin (2009)  Persona: An Online Social Network with User-Defined Privacy

Persona uses attribute-based encryption (ABE) to prevent social networking sites from reading a user's data which is stored on (or more likely just referenced by) that site.  Attributes are provided to other users by the data owner, similar to  roles or groups (or recommendations in Shand et al).  Users holding the right set of attributes can decrypt certain pieces of data.  ABE works like public-key cryptography, except that it enforces attribute intersections ("neighbor AND football fan"), while the latter is vulnerable to a colluding member from each group.

Furthermore, anyone who knows a user's ABE public key and the names and definitions of the desired attributes "can encrypt to any access structure (and thus create any group)".  "Using ABE allows friend-of-friend interactions without requiring enumerations of friend and attribute lists."  "As long as users share attribute names (and their meanings) with friends, ABE provides an elegant mechanism for users to target information for friends-of-friends."

"ABE operations are about 100-1000 times slower" than regular public-key encryptions.  However, ABE's slowness is not a big problem, because it "recycles" symetric keys to minimize ABE operations.  My larger slowness concern is Persona's latency from storing a hundred profile items on a separate server, which the browser plugin fetches individually.  They found the average load time for a Persona-fied Facebook profile to be over 2 seconds.

They demonstrated Persona with a Firefox "extension" (actually a plugin, I presume, because it uses native libraries for cryptography).  The trust must reside locally, I presume, because Persona's main purpose seems to be not to trust the SNS.  This is somewhat of a reorientation of the social network around the users, or at least around the Persona framework.

My main worry about Persona is that it defeats significant functionality and usability of an SNS.  If most of the profile is encrypted, then nobody can search on it, even if they have the necessary attributes (since downloading and decrypting all data one has access to, just to search through it locally, would be prohibitively expensive).  Persona advocates selective revelation, specifically for this "search application" example, so the SNS has only the data that the user wants it to have.  But the more than can be searched, the less use of Persona.  This paper starts by questioning the motives and security of SNS providers, but it doesn't go far enough to justify the reorientation and reduced functionality that Persona entails.  It mentions no usability studies, either.

This paper seems tangental to my research concern, although ABE's friend-of-friend support is interesting.


# Guha, Tang, Francis (2008).  NOYB: Privacy in Online Social Networks

This paper explains a clever method, and proof-of-concept on Facebook, for users to deny an SNS access to their true data, by substituting false data, without the cooperation or knowledge of the SNS.

The substitution is concealed by using a dictionary of data for the same fields by other SNS users, in such a way that the substituted data is statistically indistinguishable.  The substitution is made by encrypting an index into the relevant dictionary.  Related fields such as first name and gender are grouped together in atoms to avoid incompatible substitutions.  There are multiple dictionaries for atoms correlated to age or gender, such as favorite movies and TV shows, to preserve the joint distributions after encryption.  The proof-of-concept was a Firefox plugin for Facebook.

NOYB has four types of "channels".  The substituted atom in the SNS field is the primary channel.  The encrypted form of a dictionary index generates extra data that NOYB handles in a "residue channel", stenographically hidden in the profile photo for the Facebook proof-of-concept.  The dictionaries are public channels, anonymous web services separate from the SNS.  Finally, the cryptographic key for reversing the substitution is the fourth channel, distributed out-of-band to the user's social network (friends, friends-of-friends, etc).

This paper is not concerned with the distribution of the keys.  For the proof of concept, they used email.  Revocation is handled by negotiating a new key, but a whole profile cannot be re-encrypted immediately, because that would reveal the use of NOYB to the SNS.  Access is controlled first by the SNS, and then whether friends know of the use of NOYB and the key.  Keys can be redistributed or revealed, but NOYB does not address transitivity, so it does not seem related to my research topic.

It seems fun to use NOYB under the nose of the SNS, but just denying accurate data to the SNS does not seem worth the trade-offs.  First of all, it defeats search, since all searchers would need to use NOYB and the same key for a search field.  It's a lot of effort just to appear to be using an SNS, with misleading data that's indistinguishably randomized.  Is the SNS channel carrying a significant portion of the encrypted data versus the residue channel?

My main concern with NOYB, however, is that it would lead to much confusion, cause its users lots of hassles, and ultimately disclose its use to the SNS, which would ban its users entirely.  That's because there would always be some new friends, friends-of-friends, or network members who have access to some NOYB field without decrypting it properly (either because they're not aware of NOYB, haven't installed or used it properly, or don't have the necessary key for a given field of the given user).  Some users have difficulty even using Facebook the way it's intended, let alone succeeding in unsupported, unauthorized, stealth uses.  One of the earlier papers I read noted the low incidence of false profile data on Facebook, except as the rare absurd or ironic joke, because of the problems anticipated with friends raising questions about such information.  Such questions on Facebook could easily expose the use of NOYB, and if the profile owner includes an explanation of NOYB for uninformed friends then that would certainly alert Facebook as well.  I expect this would eventually give Facebook enough confidence in the identity of NOYB users to ban them, since they are breaking the terms of service.  If a user's social network is static enough to avoid these problem with new contacts, then there's not much point in using an SNS.


# Carminati, Ferrari, Heatherly, Kantarcioglu, & Thurainsingham (2009a).  A Semantic Web Based Framework for Social Network Access Control

This paper suggests an implementation of access control for a social network by leveraging a semantic web reasoning engine and queries.  Although this is an internal matter for the SNS, it enables elegant security policies.

The SNS data is modeled in the Web Ontology Language (OWL) to create a Social Network Knowledge Base (SNKB).  Standard schemas like Friend-of-a-Friend (FOAF), or extensions, can be used for modeling personal information, relationships between people, resources such as photos or walls, relationships between people and resources, and actions that users can do with the SNS.

Security policies are written in the Semantic Web Rule Language (SWRL).  These rules are run through a rule-based inference engine that can do both forward and backward chaining on the SNKB, to generate a Security Authorization Knowledge Base (SAKB), which enumerates which users can perform which actions on which objects.  There are two levels of rules:  admin (rules about who can make what kind of rules), and regular.  There are two kinds of regular rules: access control (positive), and filtering (negative "prohibitions").  Finally, there are two ways to filter:  preferences (one's own filters), and supervised (filtering what someone else can access, such as one's child).

That last type of rule is a 4-tuple (supervisor, target user, object, and privilege).  It's unlike the previous types, which are triples and so can be represented as a single property (i.e. relation connecting two nodes).  To model the 4-tuple, the paper chose to add an OWL class "Prohibition" to represent the privilege, with heirarchy "DeleteProhibition", "WriteProhibition", and "ReadProhibition", and properties for the other 3 parts (supervisor, targetUser, and targetObject).  This complicates the SWRL for this type of rule.

Although the rules depend on the ontology (i.e., the schema), the paper includes some nice examples.  The most impressive trick is how it manages the admin rules (i.e., meta-rules) uniformly with the regular rules by modifying the rule to add the necessary admin privilege.  For example, if user Bob submits the following SWRL to say that his friends can see the photos he owns:

    Owns(Bob, ?targetObject) & Photo(?targetObject) & Friend(Bob, ?targetSubject) => Read(?targetSubject, ?targetObject)

then the SNS can just prepend to the SWRL "AdminRead(Bob, ?targetObject) &", since this SWRL was submitted by Bob and it produces SAKB "Read(x, ?targetObject)", so the implementation is for Bob to have the AdminRead authorization on ?targetObject for his rule to be enforced.  That authorization can be inferred from a bootstrap rule such as "Owns(?grantor, ?target) => AdminAll(?grantor, ?target)", meaning that an owner of something can make rules about who is able to whatever with it.  AdminAll is a superclass of AdminDelete, AdminWrite, and AdminRead in the access control authorization heirarchy and of AdminPRead, AdminPWrite, and AdminPDelete of the prohibition authorization heirarchy.

The paper does not detail support for transitivity.   It does not mention what happens if a rule produces an Admin authorization.  Does the prepender require AdminAdminRead, or does AdminRead allow production of AdminRead as well as just Read?  Bootstrap rules could also provide for transitivity.  For example, "Read(?grantor, ?target) => AdminRead(?grantor, ?target)" would allow anyone with read authorization to the target to grant anyone else read authorization to that target.  I'm interested in how well this implementation could provide this kind of support.

The SWRL does support friend-of-friend access control, or more complex constraints, via explicit rules, such as:

    Photo(?targetObject) & Owns(?owner, ?targetObject) & Friend(?owner, ?targetSubject1) &
        Friend(?targetSubject1, ?targetSubject2) => Read(?targetSubject2, ?targetObject)

This access control by length of path does not take a simple number, such as 5 hops or less, so it would require 5 SWRL rules.  This does not seem like a significant performance problem, and few users would want to allow very large numbers of hops without just making the access public.  Also, the Admin authorization resides with the owner, unless there are some other bootstrap or admin production rules as I mentioned above.

I think that reifying the rules as SWRL and SAKB data instead of programming logic dynamically crawling the social network raises the interesting possibility of leveraging a journal of rule and authorization changes to make them visible to the user as a history, event notification, and/or explanation of how or by whom a particular object or user can be accessed.

The main limitation I see in this implementation is that it does not include support for trust levels.  The paper acknowledges the importance of including trust levels in access control, by referencing a paper from last year by some of the same authors (Carminati, Ferrari, & Perego.  2009.  Enforcing Access Control in Web-based Social Networks), which authorizes users based in terms of trust level as well as relationship type and depth.  But, the present paper puts trust outside the scope of this implementation, noting that "the TrustValue property of relationships is a value that is computed automatically outside the OWL/SWRL component of the social network. ...  We assume that there will be a more complicated formula used in calculating the TrustValue that may be beyond the bounds of the built-in mathematical operators of SWRL."

Another thing this paper doesn't cover is the user interface or other usability issues.


# Shehab, Squicciarini, & Ahn (2008).  Beyond User-to-User Access Control

This paper suggests an implementation for minimizing data provided to SNS apps.  It includes the nice idea of supporting not only the limitation but also the generalization of data.  This goes beyond partial disclosure of profile atoms, such as revealing only a birthdate's year or only an address's state, to revealing, for example, an address's region, such as central-Atlantic US, which is not a field in the address but can be automatically derived from the address.

The main idea is for an app using the SNS API to submit to the SNS an "application sheet" XML document specifying the data it needs from the API and a state diagram describing its process execution in, e.g., Business Process Execution Language for Web Services (WS-BPEL) XML.  The process diagram details which data it needs at which step, and what outcomes it can provide if given which data.  This allows the user to see and choose which outcome it wants from the app and the minimal set of data required for that outcome.  The app must be designed to tailor its functionality to the data that the user is willing to provide.

Unfortunately, this paper does not examine whether or how users would be willing and able to do this.  While this implementation seems possible and somewhat obvious to me, the real question is usability.  Fortunately, one of the authors, Shehab, examines the usability issue with Besmer, Lipford, & Cheek in a publication in the following year:  Social Applications: Exporing A More Secure Framework (2009).  But, this usability study found many users unconcerned or unwilling to configure privacy settings on an app-by-app basis.

Another thing I wonder about this implementation is whether app developers would be willing to design their apps around this API.  Unless the SNS is dominant, like Facebook, who would go to the trouble of dealing with this?  It greatly complicates the API and the app, raising the bar for getting developers to contribute apps to the SNS.  Even Facebook would need to be careful, because if it makes the API too difficult, then it gives an advantage to competing SNS with easier and more powerful APIs.  Users would need to value the extra security more than the easier to use and more powerful apps on the competing SNS.

This paper doesn't address transitivity, beyond that implied by an app's access to the user's friends' data.


# Anton, Bertino, Li, & Yu (2007).  A Roadmap For Comprehensive Online Privacy Policy Management

This paper looks at privacy policies from the perspective of enterprises and the users of their online web sites.  It assumes that those enterprises will attempt to adhere to the privacy policies that they publish and that their users will trust them to do so, and focuses on the problems still left even after those assumptions.

It notes problems with the W3C's Platform for Privacy Preferences Project (P3P), which lets web sites publish their privacy policy in XML format, but fails to define clear semantics for it.  The W3C's intent is for browsers to help users automatically enforce their privacy preferences by defining them once in the browser.  It cites CitiGroup's reluctance to use P3P because its unclear semantics may lead to legal and media risk because of misrepresentation.

It also mention's IBM's Enterprise Privacy Authorization Language (EPAL), an access control language with features devoted to privacy protection.  It raises 3 limitations of EPAL:

1.  It's not scalable because it must be enforced at the data level.
2.  P3P policies cannot or should not be generated from EPAL policies.
3.  EPAL doesn't handle data flowing to another application with a different privacy policy.  (It notes a "sticky policy paradigm" to associate relevant consents with users' data can help handle this, but that most interfaces don't support sticky policies.)

It goes on to describe its comprehensive framework, which is 3 tiers on the enterprise side: privacy policies, access control and audit policies, and fine-grained access control implementation.  It notes different concerns in each tier and issues with consistency between tiers.  Finally it notes on the user side the importance of usability.  The main point of proposing this framework seems to be to provide a context for the research issues that this paper details at the end:
* development of a formal language for specifying privacy policies
* automatic translation from natural language privacy policies to forman language policies
* development of policy languages for specifying access control and auditing policies
* theory and tools for comparing top-tier and middle-tier policies
* algorithms & tools to automate translation from middle-tier to bottom-tier policies
* theory for information flow control based on privacy policies
* development of a paradigm for the end-user to specify privacy preferences
* methods and tools to present privacy policies to end-users in a uniform and accessible way

This begs the question of whether the proposed framework or the assumptions behind it are ideal.  Nevertheless, it makes a nice roadmap, as the issues it raises seem useful, important, and not soon resolved.


# Dwoskin & Lee (2007).  Hardware-rooted Trust for Secure Key Management and Transient Trust

I only skimmed this paper, but the gist seems to be anchoring the trust model in the hardware so that the device owner (or the holder of the device, at least) is not trusted, enabling access to the data held in the device to be revolked remotely without the cooperation of the owner.  The key word here is "Transient", not transitive; i.e., the trust is temporary.

This reminds me of the digital rights management products that Phoenix Technologies tried to sell with the "trusted" BIOS.  It's interesting as the opposite of the user-oriented privacy schemes based on encryption, where the user doesn't trust the SNS, while this would enable the SNS to not trust the user with the data it provices (if the SNS could get the user to buy such hardware).

Such hardware would allow the SNS to manage transitive access control without trusting the user.  User trust cannot be clearly defined or predicted, so it's tempting to try to eliminate.  However, unless the SNS can produce and sell a dominant hardware platform, such as another iPod or Kindle, it will need to figure out how to trust the user.  Hardware that enforces this kind of DRM tends to put itself at a disadvantage by reducing the network effect, so I don't think it will be viable for an SNS.


# Zhao & Karamcheti (2000).  Expressing and Enforcing Distributed Resource Sharing Agreements

This paper suggests a technique of using tickets and currencies to express sharing agreements.  An absolute ticket gives the holder the right to an absolute amount of the granted resource, while a relative ticket is in terms of a "currency".  The currency is backed by some amount of resources, either locally and/or transitively, and either absolute and/or relative.  The percentage of the relative ticket to its total currency gives the ticket holder the right to that percentage of the resources backing the currency.

A currency is a level of indirection which provides two advantages:

1.  A currency can be inflated or deflated by increasing or decreasing the number of units in the currency, without changing the tickets.
2.  A participant can create additional, "virtual currencies", which "decouple the quantity of resources tranferred along some subset of its agreements from fluctuations in another subset."

The technique is transitive because the tickets that a participant holds are added to the resources backing his currency.  Resources can refer to logical entities such as access rights, although the examples given are for physical entities like disk space or CPU bandwidth.

The technique is "enforced" by a global resource allocation algorithm; I wouldn't call this enforcement, but simply evaluation of the tickets and currencies.  This paper does not address security concerns such as a malicious participant misusing a resource.  It seems global, not distributed, because the allocation algorithm needs to know all the tickets and absolute resources in the network.  The paper didn't mention any cryptographic signatures or certificates that would allow peers to accept tickets and currencies from neighbors and calculate the resource allocation locally.

I'm not sure if this paper could be applied to my research topic.  It makes me think of the "recommendations" in Shand et al (2003), although those used cryptographic signatures and were distributed (not global).  Those were for trust as well as access control.  Would Shand benefit from adding a "currency" level of abstraction, and would that preclude distributed usage?


# Hinds, Jirotka, Rahman, D'Agostino, Meyer, Piper, & Vaver (2005).  Ownership of Intellectual Property Rights in Medical Data in Collaborative Computing Environments

I couldn't find a free copy of the paper referenced by Simpson (2008), "On the importance of intellectual property rights for e-science and the integrated health record", because UH apparently doesn't have a subscription to the SAGE Journals Online for the Health Informatics Journal.  The closest I could find was this one, by many of the same authors, from 3 years earlier.  It's a summary of the start of the IMaGE project, a study of the Intellectual property rights of Medical data in Grid Environments.  (The paper I couldn't get seems to be from after that project had finished.)

The paper's abstract mentions "individual patient records" and the goal to "develop a UK-based intellectual property ownership model for the sharing of digitised medical data in a collaborative computing context."  Unfortunately, the paper was preliminary and broad, hardly concerned with individual patient control over their medical records.  It's concerned more with the use of agregate data for scientific research.  It investigates issues such as whether medical data becomes public domain once it's anonymized, whether the patient's implied or explicit consent is required, whether doctors who interpret data add enough value to gain some IP rights, and whether UK law regarding IP rights, privacy, etc will need to change for the sake of the related science project (eDiaMoND, www.ediamond.ox.ac.uk).

Unfortunately, I don't think I can use this paper in my literature review.


# Abdul-Rahman & Hailes (2000).  Supporting Trust in Virtual Communities

Google scholar says this paper is cited by 784.  It's where Shand et al (2003) got its recommendations, and explains how to evaluate them.  It sounds like how Netflix might implement its recommendation engine.  Agents who have a history in a given context of recommendations similar to the user's own experience are given greater weight for their recommendations on the user's future experiences.  Abdul-Rahman & Hailes claim not to suport trust transitivity, but it seems to me a kind of smart transitivity.  Although it's a kind of reputation system, it does not form chains of trust.  All agents are making evaluations and recommendations based on their direct experiences.  However, the user can leverage those recommendations based on his own direct experiences in that context and with those agents.  All experience is subjective, and all recommendations are interpreted subjectively.

The ratings are on a simple, 4-point scale, with some linearity, so the user can adjust how he interprets an agent's ratings.  For example, in the context of sci-fi movies, if agent A rates movie B as "good", but in A's history of sci-fi movie ratings, he has rated some movies as "good" that the user has rated as "very good", then the user may interpret A's rating of movie B as "very good".  Some agents may have a history of ratings that contradict the user's experience, but those are just as useful in this method.  If an agent tends to dislike movies that the user tends to like, then knowing that that agent dislikes a new movie suggests that the user may like it.

This helps me understand Shand et al, which I think will be important for my research topic.  This method and its contexts also tie in to Nissenbaum's contextual integrity. 


# Carminati, Ferrari, & Perego (2009b).  Enforcing Access Control in Web-Based Social Networks

This is an article in the ACM Trans. Info. Syst. Sec., noting it was received March 2007, revised April 2008, and finally published Oct 2009.  This access control for an SNS is based on the type, depth, and trust level of relationships between nodes.  It includes a review of some other research and trust systems.  It notes that trust is not necessarily transitive, but it uses a transitive algorithm anyway.  When it considers the type of the relationship (e.g., friendOf, colleagueOf, etc), this reminds me of the context in the above Abdul-Rahman, Shand, and Lipford papers.

The method is partly-decentralized.  The central part is a trusted server containing certificates that declare all relationships (including type and trust level).  The distributed part is that it's up to the client to provide the resource holder with a proof that the client has the necessary relationships to qualify under the holder's access control policy.  This method requires a central, trusted part because it uses the trust values of all shortest paths between the nodes in question, so the client that provides the proof cannot be trusted to include paths with negative impacts.

Performance testing on a prototype showed that certificate path discovery time increases exponentially, with 6000 nodes (of a given relationship type) taking about 1 second on a modern PC.  Because of this limitation, and the security hassle that normal users would not want to deal with, this system is suggested for mainly business or research purposes within an organization, not a global SNS.

The relationships are in cryptographic certificates, but I did not see any mention of encrypting the resources themselves.  I presume that all the relationships are public, since both nodes need to find all shortest paths between themselves.

The paper suggests that this kind of system could catch on, despite SNS users currently trusting the SNS, because some users are becoming concerned (e.g., protests of several recent Facebook changes), and users are the ones who provide the content for SNS, so it's ultimately up to them.  This paper doesn't address the loss of services, such as search, that require trust in the SNS.  It seems aimed at large-scale resources like photos, papers, or music, rather than at small-scale resources like profile fields (name, address, phone number) or even blog posts.

The introduction repeats a claim from the authors 2006 paper, Rule-Based Access Control for Social Networks, that current SNS access control paradigms do not allow for consideration of the type of relationship.  That's not really correct.  Facebook, for example, allows access control settings by networks, or by excluding friend lists such as "family" or "coworkers".


# Carminati, Ferrari, & Perego (2006).  Rule-Based Access Control for Social Networks

This is a shorter and more straight-forward description of the method elaborated on by the above paper.  It doesn't go into how to calculate the transitive trust level, just mentioning that it's averaged over relations of the same type.  It mentions an implementation with Berners-Lee's N3 for rules and Cwm for reasoning, because N3 allows a more elegant representation than SWRL or RuleML.  It also takes inspiration from W3C by using OpenID addresses for principals, URIs for resources, and an OWL vocabulary named REL-X for modeling the network.  However, when this paper mentions "enforcing access control in the Semantic Web", it does not mean using the Semantic Web in its method as two of the authors (Carminati & Ferrari) did with 3 others in "A Semantic Web Based Framework for Social Network Access Control" (2009).  It just means using a similar strategy by having the requesting party supply a proof that it satisfies the access requirements.

It includes a bad justification for the distributed architecture.  It says that hosting the reference monitor in a trusted SNS would be a naive solution because, since the number of participants may be quite big, "a centralized reference monitor would be a bottleneck."  However, these authors' "Enforcing" paper 3 years later has performance results from the prototype which suggest that this distributed architecture is a bottleneck.  Furthermore, since it's partly centralized, there is still a 3rd party (the central certificate/relationship server) that must be trusted with effective access to all resources.  And in addition, participants must provide their own servers, which calls for expenses like upload bandwidth and constant availability.

It mentions that users can decide to establish private relationships, but those can be used for access control "only by the users participating in them".  I presume that means they break transitivity.  It's also not clear whether these private relationships can avoid being exposed to the central certificate manager, although one of this paper's two main future research directions is the usage of access rules also for certificate protection, which reinforces my impression that the typical relationships in the current method needs to be public.

Another thing I'm not clear on in this paper is whether the central node's certificate manager and certificate retrieval module are finding the minimal paths in the network and calculating a trust score, "depth" (i.e., hops), and type for relationships between nodes (section 5), or if this paper means something else by certificate chain management.  If the former, then how much more work would it be to compare those relationships against the access rules?  What kind of proof is required if all relationships are put in direct terms?

The access rule examples in this paper at first glance look like the SWRL from these authors' "A Semantic Web Based Framework...", but on closer inspection they're just verbose versions of simple conditions that should be expressed more simply.  The main advantage of the current paper is that it includes trust levels, which their Semantic Web paper punts on.


# Dwyer & Suthers (2005).  A Study of the Foundations of Artifact-Mediated Collaboration

This paper from the class bibliography is shorter but contains less developed implications than the one I read but didn't reference for my last project, Dwyer & Suthers (2006) "Consistent practices in artifact-mediated collaboration".  Nevertheless, it has several interesting findings:

* Participants managed multiple topics with physical interaction contexts within their workspaces.  "Participants seemed to move the various topic threads between several states.  Participants used position and orientation to invite a response, to initiate collaboration, or to indicate ownership (and the corresponding limitation on their partner's contributions)."

* "The ability to easily and continuously express attitude is fundamental to conversation, but generally absent from current collaboration technologies."

* Participants developed and used only a small number of communicative methods and notational conventions.  "In the few cases where conventions were attempted, they either quickly became confusing, were immediately ignored or miscommunicated between the participants.  The effort of remembering and applying a convention outweighed its perceived value.  Collaborative technologies should be designed to reinforce the use of notations by allowing conventions to emerge from the interactions without them being explicitly defined."

* Actions such as pointing, underlining, and drawing an arrow take on meaning given the context in which they are used.  "Despite polymorphism, the intention of each action was almost never misconstrued.  Rather than create any formal definitions, participants were willing to expend the mental effort to perform continuous (re)interpretation of these actions and their context."

* "communicative and representational practices emerge from interaction."  "People make sense of the world through interactions based on their perception of how objects allow them to act, not necessarily a contemplation of the objects' purpose."  (These statements were not referenced, but they remind me of CHAT or even Krippendorff.)

However, this study was on short-term synchronous (live, interactive) collaboration for meaning-making of wicked problems.  My research topic involves long-term collaboration on the simple problem of maintaining contact information.


# Barth, Datta, Mitchell, & Nissenbaum (2006).  Privacy and Contextual Integrity: Framework and Applications

The authors team up with Nissenbaum, the author of the original 2004 "Privacy as contextual integrity", to apply the concept to a formal model in Linear Temporal Logic notation for privacy policy description and analysis.  "In our model, the subject of information in a message is as important as the sender and the recipient of the message."

It defines contextual integrity with four key constructs: informational norms, appropriateness, roles, and principles of transmission.  Informational norms apply to the transmission of personal information from one party to another.  Key to this is the information's type (i.e., category).  Appropriateness is whether the type conforms to the relevant norms.  Roles are certain capacities in which entities (agents, principals) are considered to be acting within the relevant contexts.  Transmission principles are the specific constraints (terms or conditions) regulating the flow of information.  Examples are confidentiality, reciprocity, whether an agent deserves to know, or awareness and consent.

Policies are applied to a history of "traces", which describe the state of knowledge in the world and the actions of the agents which exchange attributes (information about agents) in messages.  The Propositional Linear Temporal Logic formulas allow the expression of past and/or future conditions or constraints.  [LTL seems to be a mature and well-studied math or computer science technique, with a free tool from the 80's named SPIN, although I've never heard of either.]

Norms of transmission are expressed as temporal formulas, either positive (if) or negative (only if).  The paper notes a hierarchy in computation rules (attributes which can be inferred from other attributes) which create a natural downwards inheritence for allow rules and upwards inheritance for deny rules.  This reminds me of Carminati et al's SWRL class inheritence in the same order for permissions and prohibitions.

The paper asserts that because separate policies can be expressed in the same logic formulas, rather than depending on opaque functions, these fomulas can be combined to check for consistency (in terms of it being possible to achieve a given purpose) (with a LTL model-checker such as SPIN), for entailment (meaning that one policy implies or encompases another, such as a hospital's policy satisfying HIPAA), and for complience (meaning, given the history of communications, does the policy permit the current communication, what future requirement are incurred, and can they be satisfied).

Examples from three privacy laws are then presented: HIPAA (health information privacy), COPPA (Children's Online Privacy Protection Act), and GLBA (Gramm-Leach-Bliley Act, or the Financial Modernization Act of 1999).  The examples are quite eloquent, even terse to the point of me wondering how much meaning they have.  They note that their models side-step the issues of mapping reality to the model, taking as input the classifications and affiliations of the agents, roles, and attributes at issue.  Other noted limitations are numerical notations of time, and the expression that some information must be forgotten.  So, CI cannot express that GLBA requires the privacy notices to be delivered annually, and it cannot express that COPPA requires a child's information to be deleted when a parent revokes consent.

The paper also noted that CI assume that all the rules are followed, and cannot express what happens when they are not.  This seems like a serious limitation to me, which the paper does not explore.  How does the model know the history and knowledge state of reality?  What if an agent has some incorrect (or obsolete) information, or if the agent is malicious and sends messages containing lies?  There is no mention of trust or uncertainty.

Finally CI is compared to several other models:  Role-Based Access Control (RBAC), eXtensible Access Control Marckup Language (XACML), Enterprise Privacy Authorization Language (EPAL), and Platform for Privacy Preferences (P3P).  Anton et al (2007) also mentioned EPAL and P3P, but didn't suggest any concrete alternative.  I'm interested in comparing this to Carminati et al's application of SWRL, and to Shand et al's method with recommendations.
