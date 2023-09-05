---
title: 'How-To: Show All Network Connections On Your DD-WRT Router'
author: Tyler Longren
type: blog
date: 2018-10-13T04:00:36+00:00
url: /how-to-show-all-network-connections-on-your-dd-wrt-router/
featured_image: /wp-content/uploads/2015/09/screencapture-192-168-1-1-apply-cgi-14420106888013.png
independent_publisher_primary_category:
  - Internet
tags:
  - cool
  - Internet
  - Linux
  - Open Source
  - Personal
  - Security
  - tools
  - tutorials

---
## Find the bandwidth hog by viewing all network connections passing through your DD-WRT router

Something was using all of my upstream bandwidth, wasn&#8217;t sure what device or who it was (had friends over). To get to the bottom of it quickly, a simple command can be run from the DD-WRT web-based gui that will show all network connections on your DD-WRT router.

Just follow these 5 easy steps below:

#### 1. Login to your router&#8217;s web interface.

#### 2. Click the _&#8220;Administration&#8221;_ tab, and then click the _&#8220;Commands&#8221;_ tab.

#### 3. In the text area to enter commands, enter this:

<pre class="EnlighterJSRAW" data-enlighter-language="shell" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">cat /proc/net/ip_conntrack</pre>

#### 4. Click the _&#8220;Run Commands&#8221;_ button below where you entered the command above.

Once you&#8217;ve clicked the _&#8220;Run Commands&#8221;_ button, wait a few seconds, and you&#8217;ll eventually see some output similar to what you see in the image above, below is the raw text from the image:  


Now the key to tracking down the offending user/device is to look for a source IP (almost always a non-routable IP, like 192.168.1.x, 10.10.10.x or whatever) that shows up a LOT more often than other non-routable IP&#8217;s.

Once you&#8217;ve found that IP, go to the _&#8220;Status&#8221;_ tab in the DD-WRT web interface, click _&#8220;LAN&#8221;_, find the IP that you suspected was the culprit from above and make a note of the MAC address associated with that IP.

 [1]: #