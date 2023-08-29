---
title: Receive Alerts On SSH or SFTP Logins with Papertrail
author: Tyler Longren
type: post
date: 2014-06-26T11:42:35+00:00
url: /receive-alerts-on-ssh-or-sftp-logins-with-papertrail/
featured_image: /wp-content/uploads/2014/06/papertrail.png
dsq_thread_id:
  - 2785510562
primary_category:
  - Security
independent_publisher_primary_category:
  - Security
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - cool
  - digitalocean
  - GitHub
  - hosting
  - Internet
  - Linux
  - Open Source
  - opensource
  - papertrail
  - PHP
  - Security
  - services
  - ssh

---
## Frustration-free log management, plus a lot more {.subtitle}

I&#8217;ve been a huge fan of [Papertrail][1] ever since I discovered it, probably about a year ago or so. I use it mostly to monitor server logs. I currently have two servers setup to send syslog messages to [Papertrail][1].

The [Papertrail][1] Events dashboard can be a bit overwhelming at first, but the provided search is powerful and allows you to finely control which log messages you see and which you don&#8217;t.

You can even setup saved searches to fire when a specific event occurs. For example, I have a saved search that searches for the following:  
`Accepted publickey for tyler`

When that message shows up in [Papertrail][1], it means that I logged in, or that someone else has logged in using my SSH key. This can be quite handy, especially if you&#8217;re a one man shop like me and are usually the only person that has SSH or SFTP access to a server.

Getting a [DigitalOcean VPS][2] added to Papertrail, especially if it&#8217;s running Debian or Ubuntu, is super easy. It just requires that you modify `/etc/rsyslog.conf` and add a line to the end of the file that will send a copy of the system logs to [Papertrail][1].

[Papertrail][1] can monitor application logs, too, such as Apache httpd logs and MySQL server logs, although that takes a bit more configuration to get working properly.

If nothing else, it&#8217;s just nice having system logs aggregated in one central place, where everything is easy to search through, making it easy to find exactly what you&#8217;re looking for. If you&#8217;re an admin for one server or hundreds of servers, [Papertrail][1] could turn out to be one of your favorite tools. It&#8217;s definitely one of my favorites.

I suggest you [give Papertrail a try][1], can&#8217;t hurt, they even have a plan that&#8217;s free forever. It&#8217;s definitely a great service for monitoring server logs. 

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="7078"
					data-ulike-nonce="74013e5175"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_7078"></button><span class="count-box"></span>
  </div>
</div>

[][3]{.later-button-el}

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
    </p></p>
  </div>
  
  <div class='hire'>
    <h3>
      Leave some Feedback
    </h3>
    
    <p>
      Got a question or some updated information releavant to this post? Please, <a href='#respond' title='Leave a comment'>leave a comment</a>! The comments are a great way to get help, I read them all and reply to nearly every comment. Let's talk. 😀
    </p></p>
  </div>
  
  <div class='now-what-bottom-ad'>
    <h3>
      Longren.io is proudly hosted by <a href='https://www.digitalocean.com/?refcode=cbf49d0481c8'>DigitalOcean</a>
    </h3>
    
    <p>
      <span class='do_link'><a href='https://www.digitalocean.com/?refcode=cbf49d0481c8' rel='nofollow' target='_blank'><img alt='DigitalOcean' border='0' src='https://i0.wp.com/longren.io/wp-content/uploads/2014/03/digitalocean.png?w=1100&#038;ssl=1' data-recalc-dims="1" /></a></span><br /> <!--

<h3>Need Cloud Monitoring? Try Mist.io!</h3>

<span class='do_link'><a href='http://mist.io/?ref=tyler' rel='nofollow' target='_blank'><img alt='Mist.io' border='0' src='https://i0.wp.com/longren.io/wp-content/uploads/2014/04/mistio.jpg?w=1100&#038;ssl=1' data-recalc-dims="1"></a></span>--></div> </div>

 [1]: https://papertrailapp.com/?thank=33d541
 [2]: https://www.digitalocean.com/?refcode=cbf49d0481c8
 [3]: #