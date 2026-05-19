# Research Software in the Age of Gen AI Vulnerability Discovery and Exploit Creation

Draft 2026-04-08

Research software powers many Canadian research endeavors. What happens if there is a lack of high qualified people to maintain and/or sustain the software? Here within, a position is taken that Gen AI is altering the the level of urgency for discussions on maintaining and sustaining Canadian research software. CANARIE in the days before the Digital Research Alliance of Canada offered a funding stream that help maintain, sustain, and enhance in small ways Canadian research software. At present, there is no funding stream available for maintaining/sustaining research software. Why is this more of a concern in the age of Gen AI?

In the [“Evolution of LLM-based Offensive Capabilities 2025/6” (pg. 11/12)](https://labs.cloudsecurityalliance.org/wp-connt/uploads/2026/04/mythosreadyv95.pdf), one can see Gen AI has grown abilities to not just analyze and detect vulnerabilities in software but now in April 2026, early trials in also writing exploit code for the found vulnerabilities.

![“Evolution of LLM-based Offensive Capabilities 2025/6” (pg. 11/12)](./support/research_software_in_the_age_of_mythos/Screenshot%20from%202026-04-17%2012-47-47.png)

The growing Gen AI analysis and detection capabilities are associated with an increase in vulnerabilities [“AI Vulnerability Storm” (pg. 8)](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/04/mythosreadyv95.pdf). This means that the software and imported third-party libraries/modules requires an increased level of awareness and updating/patching as part of the stewardship of the research process and data.

With the growing ability of Gen AI to not only detect vulnerabilities but also write code to exploit the vulnerabilities, this means that the time between [vulnerability detection and exploit is decreasing (pg. 8)](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/04/mythosreadyv95.pdf). Awareness and response timeframes are decreasing due to the [Increased security patch cadence as indicated in the SANS Critical Advisory: BugBusters - AI Vulnerability Discovery Hype versus Reality](https://www.youtube.com/live/X0aik3eCTdU?t=2401s) and so-called "AI vulnerability storm".

![AI vulnerability storm, SANS Critical Advisory: BugBusters - AI Vulnerability Discovery Hype versus Reality, April 16, 2026 https://www.youtube.com/live/X0aik3eCTdU?t=2401s](./support/research_software_in_the_age_of_mythos/Screenshot%20from%202026-04-16%2016-43-54.png)

Given the stewardship requirement built into research grants, how can the limited resources be allocated to both properly steward the research software/data while continuing to move forward the research? Competing priorities.

What is CWRC trying? A combination of tools to increase awareness security updates, aid in merging security updates into the research software, creation of review environments, testing process to verify security updates don't break existing features, plus tooling that increases the effort needed by bots to access the site.

Summary:

* Drupal security alerts from the Drupal Security team
* Review environments to aid in testing
* Automated security detection testing with processes to create pull requests updating third party libraries
* Defense in depth (e.g., introduce hardship when bots access a site; disaster recovery)
