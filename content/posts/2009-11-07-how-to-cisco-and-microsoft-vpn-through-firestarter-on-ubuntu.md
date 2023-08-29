---
title: 'How To: Cisco and Microsoft VPN Through Firestarter on Ubuntu'
author: Tyler Longren
type: post
date: 2009-11-07T19:57:33+00:00
url: /how-to-cisco-and-microsoft-vpn-through-firestarter-on-ubuntu/
ratings_users:
  - 2
ratings_score:
  - 10
ratings_average:
  - 5
views:
  - 937
dsq_thread_id:
  - 1549400707
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - cisco
  - howto
  - Internet
  - Linux
  - microsoft
  - networking
  - Noteworthy
  - Open Source
  - Security
  - ubuntu
  - vpn

---
After doing a fresh install of Ubuntu 9.10 Karmic Koala on my router, I realized that I had lost the ability to connect to my employer&#8217;s VPN. I use [Firestarter][1] for managing my firewall on this particular router.  
[ad]  
As I usually do, I googled &#8220;[firestarter vpn][2]&#8220;. Much to my dismay, it appeared that the [Firestarter website][1] was no longer alive. Instead of the usual Firestarter page, a page filled with useless links about security and anti-virus loaded. Luckily I was able to access the cached version of the page from Google. Since then, it appears that the [Firestarter website][1] has come back to life.

I wanted to make a note of how to allow VPN connections in the event that the Firestarter website becomes inaccessible again, that&#8217;s basically the point of this post. The page on the Firestarter site that details VPN connections can be [found here][3]. This should apply to pretty much every Linux distribution, not just Ubuntu.

To allow VPN connections with the **Microsoft VPN client**, simply enter the following lines into **_/etc/firestarter/user-pre_**.

<pre># Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
</pre>

[ad]  
And to allow VPN connections with the **Cisco VPN client**, enter the following lines into **_/etc/firestarter/user-pre_**.

<pre># Forward Cisco VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p udp --dport 500 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 500 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 50 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 50 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT</pre>

Finally, if you&#8217;re running a **Microsoft VPN server** and want to allow incoming PPTP VPN connections, add the following lines to **_/etc/firestarter/user-pre_**.

<pre># Forward PPTP VPN connections to internal server
SERVER=192.168.0.100 # Internal VPN server

$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -t nat -A PREROUTING -i $IF -p tcp --dport 1723 -j DNAT --to $SERVER
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -t nat -A PREROUTING -i $IF -p 47 -j DNAT --to $SERVER 
</pre>

That should pretty much cover it. If you are using OpenVPN, head over to the [Firestarter VPN configuration][3] page for details. 

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="2476"
					data-ulike-nonce="610d5d9463"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_2476"></button><span class="count-box"></span>
  </div>
</div>

[][4]{.later-button-el}

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

 [1]: http://fs-security.com/
 [2]: http://www.google.com/search?q=firestarter+vpn
 [3]: http://fs-security.com/docs/vpn.php
 [4]: #