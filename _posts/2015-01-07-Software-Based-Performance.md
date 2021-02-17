---
layout: post
title:  "Software Based Performance"
date:   2015-01-07 20:33:36 -0600
categories: [Stupid_Bugs]
tags: [Optimization, SQL]
---

I like to read articles like this: [How we made editing Wikipedia twice as fast](https://blog.wikimedia.org/2014/12/29/how-we-made-editing-wikipedia-twice-as-fast/)

MediaWiki recently deployed the Facebook developed HHVM for their PHP code and their server capacity was increased and user experience improved. Overall cpu load on the application dropped from 50% to 10%. Page load time for the user dropped 30% as well (1.3s to 0.9s). Those are nice improvements.

I had a similar experience at my job. We had an application that was cpu intensive and grew to the point where the server couldn't keep up with the daily work load. We were exploring ideas to either ramp up the server size significantly or redesign the application. Now, I'm a Network Administrator by trade, but I've dabbled in enough areas to have a passing understanding of SQL Server and some programming skills, so I was tasked with find out what I could before the developers dove too far into pulling apart this application that a previous employee wrote. (He had since left for greener pastures.)

I captured some sql traces, and with a lot of luck, I narrowed down the culprits. The biggest offender was a stored procedure using a query that was doing a wildcard search with the wildcard in the first character in the search string. (e.g. it was doing something equivalent to  `*bar`). I found out that putting the wildcard as the first character means the database does an index scan instead of a seek, so every time this query ran the database went through the entire index which was 2GB in size. Sounds like the index wasn't acting like an index was it?

It took a while for the developers to fix it with all the necessary testing and QA, but they ended up removing the wildcard entirely and just searched on the filename. At first, they didn't add an index to that column either, so the database was still doing a table scan. After the second index was added, the time to run the entire stored procedure dropped from 10 seconds to 2.5 seconds. And the offending query became instantaneous.

Here were some simple timers of each stage:

* Pre-fix: wildcard searching.
* Post-fix Mon: no wildcard, but no index either.
* Post-fix Thurs: added index.

![sql_optimization](/assets/2015/01/sql_optimization.png)

For this application, this was a case of outgrowing the initial design. The application worked great in the beginning when there were only 100,000 records in the table, but with 7 million the logic needed a bit of reworking.

That's why I love reading stories like the one above. I can write simple programs, but I'm certainly no programmer, and I'm always impressed with the skills and talent that people use to find a way to do more, sometimes much more, with the same or even less.

And I'm quite proud I was able to find this issue and figure out how it needed to be fixed.
