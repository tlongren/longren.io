---
title: More SSH Brute Force Protection
author: Tyler Longren
type: post
date: 2006-08-24T01:17:54+00:00
url: /more-ssh-brute-force-protection/
featured_image: /wp-content/uploads/2006/08/Screenshot-06032013-014701-AM.png
DiggURL:
  - http://digg.com/linux_unix/More_SSH_Brute_Force_Protection
views:
  - 4803
ratings_users:
  - 2
ratings_score:
  - 10
ratings_average:
  - 5
wjt_diPostTopic:
  - linux_unix
DiggUrl:
  - http://digg.com/linux_unix/More_SSH_Brute_Force_Protection
dsq_thread_id:
  - 1385908846
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - breakinguard
  - code
  - coding
  - denyhosts
  - fail2ban
  - hacking
  - help
  - howto
  - Linux
  - Open Source
  - programming
  - Security
  - ssh

---
[Stopping SSH Brute Force Attacks][1] resulted in some really [great][2] [comments][3] [and][4] [suggestions][5] from readers.

So, this is a follow up to [the last SSH brute force post][6]. I didn&#8217;t realize there was such a wide selection of applications for dealing with this, but there is! The two best looking options in my opinion are [Fail2ban][7] and [DenyHosts][8].

I&#8217;ve actually started using DenyHosts on two machines now, and it&#8217;s working very well. I chose to go with DenyHosts for a very simple reason. [Community stats][9]. I love stats.

Anyway, if you&#8217;re looking for something to protect against ssh brute force attacks, go with [Fail2ban][7] or [DenyHosts][8], they&#8217;re still being actively developed. I can&#8217;t say the same for [Breakinguard][10], as it appears to have been abandoned about 1 year ago. And like I said, [DenyHosts][8] does it&#8217;s job extremely well, I couldn&#8217;t ask for anything more.

If you&#8217;re looking for another solution, try using cryptographic keys instead of passwords. [A tutorial on configuring SSH][11] to look for keys instead of passwords [can be found here][11]. This [was suggested by][12] commenter [pwyll][13].

Oh, and this is the 700th post. yay! 

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="2223"
					data-ulike-nonce="fb04ecf17f"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_2223"></button><span class="count-box"></span>
  </div>
</div>

[][14]{.later-button-el}

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

 [1]: https://longren.io/stopping-ssh-brute-force-attacks/
 [2]: http://www.longren.org/stopping-ssh-brute-force-attacks/#comment-30214
 [3]: http://www.longren.org/stopping-ssh-brute-force-attacks/#comment-30217
 [4]: http://www.longren.org/stopping-ssh-brute-force-attacks/#comment-30224
 [5]: http://www.longren.org/stopping-ssh-brute-force-attacks/#comment-30236
 [6]: http://www.longren.org/stopping-ssh-brute-force-attacks/
 [7]: http://fail2ban.sourceforge.net/wiki/index.php/Main_Page
 [8]: http://denyhosts.sourceforge.net/
 [9]: http://stats.denyhosts.net/stats.html
 [10]: http://breakinguard.sourceforge.net/
 [11]: http://kimmo.suominen.com/docs/ssh/
 [12]: http://www.longren.org/2006/08/21/stopping-ssh-brute-force-attacks/#comment-30224
 [13]: http://carnalreason.org/
 [14]: #