---
title: 'How-To: Show All Network Connections On Your DD-WRT Router'
author: Tyler Longren
type: post
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



<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="8145"
					data-ulike-nonce="bc7d1af716"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image image-unlike wp_ulike_btn_is_active wp_likethis_8145"></button><span class="count-box">9+</span>
  </div>
</div>

[][1]{.later-button-el}

<div class='what-next'>
  <h2>
    Well, now what?
  </h2>
  
  <div class='hire'>
    <h3>
      Work with Me
    </h3>
    
    <p>
      I'm available for hire and always taking new clients, big and small. Got a project or an idea you'd like to discuss? Startup plan but no developer to make it happen? Just <a href='https://www.longren.io/contact/'>get in touch</a>, I'd love to see if I can help you out!
    </p>
  </div>
  
  <div class='hire'>
    <h3>
      Leave some Feedback
    </h3>
    
    <p>
      Got a question or some updated information releavant to this post? Please, <a href='#respond' title='Leave a comment'>leave a comment</a>! The comments are a great way to get help, I read them all and reply to nearly every comment. Let's talk. 😀
    </p>
  </div>
  
  <div class='now-what-bottom-ad'>
    <h3>
      Longren.io is proudly hosted by <a href='https://www.digitalocean.com/?refcode=cbf49d0481c8'>DigitalOcean</a>
    </h3>
    
    <span class='do_link'><a href='https://www.digitalocean.com/?refcode=cbf49d0481c8' rel='nofollow' target='_blank'><img alt='DigitalOcean' border='0' src='https://i0.wp.com/longren.io/wp-content/uploads/2014/03/digitalocean.png?w=1100&#038;ssl=1' data-recalc-dims="1" /></a></span> <!--<h3>Need Cloud Monitoring? Try Mist.io!</h3><span class='do_link'><a href='http://mist.io/?ref=tyler' rel='nofollow' target='_blank'><img alt='Mist.io' border='0' src='https://i0.wp.com/longren.io/wp-content/uploads/2014/04/mistio.jpg?w=1100&#038;ssl=1' data-recalc-dims="1"></a></span>-->
  </div>
</div>

 [1]: #