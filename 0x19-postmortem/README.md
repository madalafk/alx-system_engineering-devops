0x19. Postmortem
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

