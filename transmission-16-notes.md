Notes from [Transmission #16](https://www.youtube.com/watch?v=668vPl7q3xg). Please take these notes as general gist, and if you want to know what they actually said just watch the video.


### Vue.js as basis of Blaze 2.0
(1:46)

* Sashko suggests people try out Vue.js with Meteor first, in order to work out any kinks in integration.
    * MDG would be willing to make Vue a recommended view layer alongside React, Angular, and Blaze with accompanying documentation once more people test out the compatibility with Meteor
    * After this point would be the time to look at building on top of Vue.js for Blaze 2.0
* Sashko is also interested in following the development of Svelte, a new UI framework with a syntax similar to Blaze/Handlebars, but it only handles the conversion of template to JS, and not the runtime library that runs it.

### Redis Oplog 
(7:43)

* Sashko first impressions of Redis Oplog
    * Distinction from Mongo Oplog: Mongo oplog knows about db changes regardless of source of change (such as from external services). Redis oplog only knows changes made through the Meteor app.
    * Benefits: 
        * A new set of tradeoffs available. Mongo Oplog may be more intuitive, Redis more scalable especially since it could allow you to specify db changes that trigger updates or not.
        * Potentially can integrate with systems outside Meteor        
    * Ben and others are excited about enabling the package to be succesful. If succesful it could be a great integration point between GraphQL and Meteor.
    * Meteor has always been designed at the lower level to be able to plug in to systems other than Mongo on the server
* From Galaxy customer survey, scalability is only an issue for a small percentage of Meteor users, so community development is the right way to solve for it.

### Electrode / Code splitting 
(15:15)

* Forum thread: Electrode "JS build tool server thing” from Walmart
    * Client side only with focus on SSR
    * Next.js another example focused on optimizing initial load time
    * This focus comes with its own set of compromises
* Meteor does not specifically target this optimization
    * Targets things that are more app-like, users load app once and then have a lot of interaction
    * Load time is important but not the primary consideration as it is in these tools
* Forum thread: community member implementing experimental code-splitting
    * Ben is excited about this and will try to work together with this person to align the implementation with TC39 proposal for asynchronous imports
    * In keeping with Meteor philosophy, the goal is to “avoid ceremony” — minimize amount of config needed to turn this on.
* Sashko talks technical challenges of code splitting implementations
    * Current implementations address limited use cases where code is clearly separated
    * A common solution discussed in Meteor community has been splitting apps into smaller apps.
* MDG is committed to improving the Meteor build system
    * Build system is one of Meteor’s core advantages
    * They’ve had reports of people switching to Webpack with longer build times
    * Next release is all about reducing run time of JS at startup
    * They’ve found that the biggest cost of app startup time was execution of many files
    * Enabling asynchronous imports will enable reducing that execution time

### Meteor+Apollo integration
(23:39)

* MDG is currently using Meteor and Apollo together in Galaxy and Optics
* There is a community-maintained Meteor+Apollo integration package
* MDG has prioritized Meteor-specific pain points (like build tool performance) over Apollo integration, for a number of reasons:
    * Meteor-specific improvements impact a wider percentage of Meteor users — people interested in Apollo integration are in the minority
    * Apollo integration is already possible and a number of people are using it successfully with Meteor
    * What’s missing to enable Meteor developers to start using Apollo: 
        * Educational materials, blog posts
        * Addressing edge cases: using GraphQL subscriptions together with DDP subscriptions, communication between DDP and Apollo
        * Ultimate dream: For users who don’t want to use Mongo, have a version of Meteor that runs entirely without Mongo, that uses another DB via GraphQL
* Paul vouches for the feasibility of using Apollo with Meteor
    * OKGrow is using Meteor + Apollo in a GraphQL training course
    * There is some setup to do but it’s very doable
* Accounts with Meteor + Apollo
    * Accounts works fine with Apollo but is still tied to MongoDB
    * Decoupling Accounts from MongoDB is probably a longer term goal
* Producing content about how to use Apollo in Meteor is a current priority

### 1.5
(31:05)

* Paul: Is there a 1.5 in the plans and what would it be?
* Sashko: We’re not sure right now
    * Goes on to discuss the meaning of version numbers. Sounds like 1.4.2 performance improvements took the place of a 1.5 Apollo integration in terms of a major release.

### Community Health
(33:53)

* Arunoda/Kadira leaving, various forum threads
    * Kadira’s packages can now be adopted by new maintainers
    * Arunoda is now working on stuff that is not limited to Meteor, but now that Meteor is more open, it still benefits from Arunoda’s work such as with GraphQL and React
    * Meteor community is not necessarily shrinking but has diversified in terms of choices of tech stack, and this is a good thing
* Updating roadmap
    * MDG is setting a monthly meeting to update roadmap
    * Community members can submit a design document for something to be added to roadmap. See contributing guidelines on github.
* MDG looking for a better communication channel
    * Responding to every forum thread has not been effective
    * Having the same conversation repeatedly on many diff threads
    * Unclear how representative individual forum threads are of community as a whole
    * For actionable issues, best way to improve meteor is to submit issue requests and submit designs on github 
* Paul invites feedback about the podcast
* MDG surveyed customers and will be sharing the results
* As always, MDG is hiring. Email Sashko or submit an application on meteor.com

