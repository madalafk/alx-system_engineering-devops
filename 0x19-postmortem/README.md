0x19. Postmortem

0. My first postmortem

This postmortem describes an assumption issue and its resolution for the 0x19. Postmortem project, created for ALX SWE students practice

Issue Summary:
Duration: 
-	The server outage occurred on October 15, 2023, from 8:00 AM to 4:30 PM (GMT +2).

Impact: 
-	During the this outage, our primary web application experienced a major slowdown, resulting in a degraded user experience. Approximately 90% of our users were affected, leading to performance being affected and delayed access to critical services which included all reports.

Timeline:

Issue Detected: 
-	The issue was initially detected at 8:03 AM (GMT +2) through automated reporting system which indicate that critical management reports were not being generated. A PID (Process ID) associated with the application server showed abnormal resource consumption.

Actions Taken:
-	The IT manager , upon receiving the alert, initiated an investigation into the performance degradation. Initially, we assumed it might be due to a sudden increase in user traffic or server overload, and we used `curl` to perform quick diagnostic tests.

Misleading Investigation:
-	As a first step, we examined our server load and network traffic but found no significant anomalies. This led us to explore the application code and configuration, as we suspected a code issue, or a misconfiguration might be the root cause. We also ran `strace` on the application server processes to trace system calls, but this did not reveal the root cause.

Escalation: 
-	When the investigation didn't reveal any obvious issues within the application code, the issue was escalated the to the development team, suspecting a potential software bug. The developers began examining the codebase and ran `puppet apply` to check if the server configuration was consistent.

Issue Resolution: 
-	After in-depth code analysis, it was identified that the root cause of the system failure, was a database query optimization problem. An inefficient database query was causing excessive load on our database server, leading to system overloading hence system failure.

Root Cause and Resolution:

Root Cause:
-	The issue was traced back to a specific database query in our application code that had been performing well previously with a smaller dataset. However, due to increased sales and customer reviews, dataset grew, this query became a performance bottleneck. The database query was not optimized to handle the larger dataset efficiently.

Resolution:
-	To resolve the issue, the development team restructured the database query, optimizing it for the larger dataset. Additionally, we applied an index to speed up the retrieval of the required data. These changes significantly improved database query performance.

Corrective and Preventative Measures:
Improvements/Fixes
-	Database Query Optimization:
-	We will Regularly review and optimize database queries to ensure they perform efficiently, especially as the dataset grows.
  Automated Monitoring:
-	We will enhance our monitoring system to provide more specific and early warnings about potential performance issues. Monitor PIDs for resource usage anomalies.

 Load Testing: 
-	We will implement periodic load testing to simulate high user traffic scenarios and identify potential bottlenecks.

 Documentation: 
-	We will ensure that code and query optimization best practices are well-documented for all team members.

Tasks which will help to Address Issues like these one :

 Database Query Review: 
-	We will periodically review and optimize database queries in the application codebase.

Automated Alerts:
-	We will fine-tune automated monitoring alerts to detect performance issues more proactively. Monitor PIDs for unusual resource consumption.

 Load Testing Schedule: 
-	We will implement a schedule for regular load testing to identify and address performance bottlenecks in advance.

Knowledge Sharing: 
-	We will share the lessons learned with the entire development and operations teams to improve collective knowledge about performance optimization. Run `puppet apply` for consistent server configuration checks.






1. Make people want to read your postmortem



When the Database tries to be the boss for the day


Dramatic Data Dilemma
Like In the world of web operations, even the Great Christopher Columbus, sometimes had to be hit by turbulent waters

Issue Summary
Duration
The outage played hide and seek from 8:00 AM to 4:30 PM (GMT +2), When It clearly needed some "no shared-time."
Impact
On a Very_hot clear sky – day, Our primary web application decided to take a very hot  coffee break, causing a stir among users. Approximately 90% of our users were affected, making our hearts beating with a thunder sound

Root Cause
It turns out that a database was day-dreaming , leading to a performance nosedive. 

Timeline
Issue Detected: The Grand Auto, outage made its grand entrance at 8:05 AM through automated monitoring alerts, setting the stage for an unforgettable performance. A PID (Process ID) with an appetite for trouble signaled the start of the show.
Actions Taken
Our fearless IT support, team, equipped with a 'curl' of determination, initiated an investigation. But no matter how much 'curl' was involved, it wasn't enough to untangle this web.
Misleading Investigation
 Our commandos, explored the server load and network traffic, believing that they'd find a server party in full swing. To our surprise, the servers were on their best behavior. We even 'strace'd the situation, but it was like watching a mime on mute - fascinating but uninformative.
Escalation:
When the script ran out of jokes, that’s when our snipers prepared for a head shot . They dug deep into the code, suspecting a software bug, while our server config did a 'puppet apply' to check its makeup.
Issue Resolution
Like a USA special force commando, the developers uncovered the real joker of the story: an inefficient database query stealing the spotlight. The query was swiftly given a rewrite, and an index was placed to speed up its performance. A standing ovation from our users ensued.

Root Cause and Resolution
Root Cause
 The database query, failing to land any laughs, had grown inefficient as our dataset expanded, it was like a Bluetooth device which was connected to so many devices in which all the devises wanted to function at the same time, leaving the Bluetooth device in dilemma on which operation was to be priotised 

Resolution
The developers restructured the query and added an index, transforming the query from a comedy flop disk into a high performance gaming SSD.

Corrective and Preventative Measures
By employing Improvements/Fixes ,Database Query Reviews and Regular reviews and optimizations to keep queries in fit 
Automated Alerts by a Monitoring that's more sensitive to Vodka like James Bond.
Load Testing , made us all aware that servers should always practice their lines more often.

Tasks to Address the Issue:
 Database Query Review
As IT marines, we should Make sure our queries aren't writing bad jokes.
 Automated Alerts in such a way that all things are safely set like nuclear bombs with no room for  errors














