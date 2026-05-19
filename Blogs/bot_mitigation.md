# An evolving commentary about blocking overly aggressive bots


## 2025

### May 20th

Last week we implemented an .htaccess rule. The rule blocks requests with a certain fingerprint from accessing a web route (search) that has a high load impact on the server. This addressed the immediate problem. The quantity of IPs and requests essentially acted as a likely unintentional DDOS. The .htaccess rule is simple but effective though very easy to circumvent by a slightly more sophisticated crawler tech which is why we've been asked not to publicly share.

At present, all is ok. However, I'm sure in the not too distant future, maybe 6 months, maybe a year CWRC will have a similar but different struggle once again.

Context: What I saw the first 6 days of May was about 800k unique IPs making 1-2 web scraping requests. Spot checks indicated world-wide residential IPs and the IPs were making requests that had knowledge of the site's structure. I suspect passive income seeking individuals selling their "clean" IP as a residential proxy as described in this article:

https://spur.us/the-market-for-clean-ip-addresses/. The load rendered the site useless acting like a DDOS attack against the site's search route, likely unintentional (due to buggy web scraping software that got lost in search facets). The following are our current thoughts for the immediate term, short term, and long term.

1. The immediate term

Upon analysis, we found the requests failed to include a HTTP referrer and based off others experience, we used a .htaccess rewrite rule to block.

# --------------------
<IfModule mod_rewrite.c>
  RewriteEngine on
  # Block requests that match the URL pattern and have no referrer
  # Block the high load URL patterns
  RewriteCond %{REQUEST_URI} ^/islandora/search [NC]
  # Skip this rule if the request already has a referrer
  RewriteCond %{HTTP_REFERER} !^.+$ [NC]
  # ALLOW access for legitimate search engine bots by skipping the blocking rule
  RewriteCond %{HTTP_USER_AGENT} !googlebot [NC]
  # Redirect to 403 Forbidden error page
  RewriteRule .* - [F,L]
</IfModule>

In my opinion, this solution likely will not last for long. For example, there are open source web crawler software the includes so called "stealth" features that add plausible but fake referrers such as https://github.com/D4Vinci/Scrapling/blob/561c8b0fcf647c069c8dbbe173c236c68d351d50/scrapling/fetchers.py#L129-L130.

2. The short term

We are looking to add a Javascript based challenge to the site, such as, https://github.com/libops/captcha-protect or Cloudflare turnstile to test if web requests are from humans or good bots that follow robots.txt rules and block unwanted bots without significantly impacting user experience. These seem to present a javascript challenge to the requestor and if the requestor responds, the proxy allows the request to the site. However, I don't anticipate this solution lasting for too long as there are open source web scrapers in the public that bypass these protections, such as: https://github.com/D4Vinci/Scrapling/blob/561c8b0fcf647c069c8dbbe173c236c68d351d50/scrapling/fetchers.py#L225-L270 - the deterrence in using this web scraping feature is the higher CPU load required to bypass the javascript challenge but time will likely erase the deterrence. I see some expensive tools that offer hope but for a small research project disseminating content via the web and experimenting with UX and different interfaces into the content, I've found nothing of use to protect against this type of future problem.

3. The longer term

We are looking toward making changes to the architecture of the CWRC platform with an aim toward improving sustainability and as a part, looking at an architecture that reduces maintenance needs and helps mitigate cybersecurity related site disruptions (like described earlier in this email). Another component is moving from a simple monitoring/alerting solution, currently Nagios, to a solution that provides more observability into the system (e.g., metric collection and centralized logging, both of which can help to alert and diagnos service disruptions. This long-term vision is not funded but was included in a research grant application earlier this year.

I'm not sure if what I'll mention next is within your purview or not but I'll mention in case.  I'm not sure if you have the ability to advocate for an increase in cybersecurity resources within DRAC, if you do and want want to bounce ideas off end-users or are looking for real-world use-cases from end-users of the DRAC Cloud or are looking for support for plan, feel free to email me and I'll try to help. One last point I'll mention, before DRAC, CANARIE used to administer a funding competition for research software/platforms that we used to help maintain (security updates, etc.) and enhance the CWRC platform. DRAC doesn't seem to have an equivalent funding stream for research software and there appears to be a gap during the transition.
