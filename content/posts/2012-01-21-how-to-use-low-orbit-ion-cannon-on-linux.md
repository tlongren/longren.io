---
title: 'How-To: Use (LOIC) Low Orbit Ion Cannon On Linux'
author: Tyler Longren
type: post
date: 2012-01-21T18:01:14+00:00
url: /how-to-use-low-orbit-ion-cannon-on-linux/
featured_image: /wp-content/uploads/2012/01/loic-linux-604x270.png
views:
  - 1906
dsq_thread_id:
  - 1385920495
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
independent_publisher_primary_category:
  - Linux
tags:
  - how-to
  - howto
  - Internet
  - Linux
  - loic
  - Open Source
  - Security
  - tools

---
 

## Compiling and Using Low Orbit Ion Cannon on Linux

This will help you get Low Orbit Ion Cannon (LOIC) running on Linux. A lot of the how-to&#8217;s out there for this are outdated and aren&#8217;t entirely relevant any longer.

I know for a fact it works with Xubuntu 13.04, so it should work with other Ubuntu variants as well, probably even Debian.

First, you&#8217;ll need to install mono-gmcs, mono-mcs, monodevelop, and liblog4net-cil-dev. You can install them like so: 

<pre class="wp-block-preformatted">sudo apt-get install monodevelop mono-gmcs mono-mcs liblog4net-cil-dev</pre>

Running that will install all the packages you need to compile LOIC with Mono. Those 4 packages have other dependencies, so you&#8217;ll actually end up installing many more packages, but it&#8217;ll be done automatically.

After you&#8217;ve got that installed, download the [Low Orbit Ion Cannon from Github][1]. You can download it in .zip or .tar.gz format, whichever you&#8217;re most comfortable with.

Make a new folder on your desktop and extract the files from the .zip or .tar.gz to that new folder. Open a terminal and move into that folder (ie: `cd /home/tyler/Desktop/loic/)`.

Once you&#8217;re in the folder, type the following in your terminal: 

<pre class="wp-block-preformatted">mdtool build</pre>

That will compile LOIC, the executable will be in the **_debug_** folder that you extracted from the zip or tar.gz file you downloaded. After compiling is done, launch LOIC like so: 

<pre class="wp-block-preformatted">mono /path/to/loic/debug/LOIC.exe</pre>

That&#8217;s it, have fun! And don&#8217;t get in trouble.

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="3319"
					data-ulike-nonce="488f27a270"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_3319"></button><span class="count-box">4+</span>
  </div>
</div>

[][2]{.later-button-el}

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

 [1]: https://github.com/NewEraCracker/LOIC/downloads
 [2]: #