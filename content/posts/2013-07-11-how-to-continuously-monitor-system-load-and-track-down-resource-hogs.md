---
title: 'How-To: Continuously Monitor System Load And Track Down Resource Hogs'
author: Tyler Longren
type: post
date: 2013-07-11T22:50:57+00:00
url: /how-to-continuously-monitor-system-load-and-track-down-resource-hogs/
featured_image: /wp-content/uploads/2013/07/tload.png
dsq_thread_id:
  - 1544476795
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - code
  - howto
  - Internet
  - Linux
  - Personal

---
 

I&#8217;ve been using Linux for 12+ years. In all that time I&#8217;d never used, or even heard of, [a program called _tload_][1]. tload is similar to the top program, in that is sits running in your terminal, showing you the current system load.

_tload_ gives you a basic text &#8220;graph&#8221; of the current system load average. It uses data from /proc/loadavg to operate. If you&#8217;re really into how _tload_ operates, check out [this post by Baron Schwartz][2].

I&#8217;ll usually open up a connection to a server via SSH and just let _tload_ run for a while. If the load gets to be too high, I&#8217;ll usually use _[top][3]_ to see which processes are sucking up all my resources, processor resources typically. I usually just run top like so:  
`top -H`

After that, there&#8217;s a couple commands that I use to find how many threads are running under a specific user or under a specific service. To find the users (5 in this case) with the largest number of threads running under them, run the following:  
`ps aux | awk '{print $1}' | sort | uniq -c | sort -nk1 | tail -n5`

To get the processes with the most threads running under them, run the code below. It&#8217;ll also show the top 5 processes. Change the `tail -n5` part to `tail -n10` to see the top 10 instead.  
`ps aux | awk '{print $11}' | sort | uniq -c | sort -nk1 | tail -n5`

That&#8217;s really all I use when I encounter extremely high loads, whatever the reason may be. They should work nicely for you too. _tload_ comes bundled with pretty much every linux distribution in existence. And from the info you gather with top and the awk commands above, you can easily narrow down what the issue is. Figuring out _why_ that issue is happening in the first place is an entirely different story though.

There&#8217;s one other really good method involving top that is [discussed at Joomlaperformance.com][4]. The code example they give is `top -b -i -n 20 >> ./top_procs`. It basically saves information from top into a file, top_procs, and runs the top command 20 times. [They describe it better than I do][4].

<blockquote class="wp-block-quote">
  <p>
    What that does is tell TOP to run in &#8220;batch&#8221; mode (not look for any user input), show only running processes, loop 20 times, and append the output to the file /top_procs. Run that command when you are experiencing a high server load. Then you can view the contents of that file to tell you some information.
  </p>
</blockquote>

So that&#8217;s that. Should be relatively easy for you to track down what&#8217;s causing high load on your vps, server, desktop, or whatever other linux system you use.

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="4580"
					data-ulike-nonce="b1f90e1eaa"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_4580"></button><span class="count-box"></span>
  </div>
</div>

[][5]{.later-button-el}

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

 [1]: http://man7.org/linux/man-pages/man1/tload.1.html
 [2]: http://www.xaprb.com/blog/2006/06/08/how-to-monitor-server-load-on-gnulinux/
 [3]: http://man7.org/linux/man-pages/man1/top.1.html
 [4]: http://www.joomlaperformance.com/articles/server_related/how_to_track_down_a_high_server_load_5_16.html
 [5]: #