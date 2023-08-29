---
title: Remove SSH Login Message After DigitalOcean WordPress One-Click Install
author: Tyler Longren
type: post
date: 2014-04-29T12:41:49+00:00
url: /remove-ssh-login-message-after-digitalocean-wordpress-one-click-install/
featured_image: /wp-content/uploads/2014/04/do.png
dsq_thread_id:
  - 2646642322
independent_publisher_primary_category:
  - Linux
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - digitalocean
  - hosting
  - Internet
  - Linux
  - Open Source
  - opensource
  - Personal
  - services
  - tools
  - WordPress

---
After creating a new Droplet [using the pre-built WordPress image][1] provided by [DigitalOcean][2], you&#8217;re presented with a very helpful message after logging in via SSH:

> To finish installing WordPress, navigate to your droplet’s IP: http://xxx.xxx.xxx.xxx  
> Make sure to specify hostname from DO panel to your droplet before creating it (for example: ‘blog.mydomain.com’ or ‘myblog.com’)  
> This will create necessary Apache configs based on hostname and Apache will respond based on hostname.  
> Server will also respond to its IP address, so if you finish installation from http://IP then  
> you will need to change hostname from WordPress Settings later (from http://IP to http://hostname)

It&#8217;s a really helpful message, especially if you&#8217;re new to [DigitalOcean][2] and even more so if you&#8217;re new to hosting stuff on your own (ie: unmanaged hosting). However, the message isn&#8217;t really helpful after the first login, maybe two logins.

There&#8217;s [a great article][3] on how to get setup after using the One-Click WordPress install, but removing the message is never mentioned.

It&#8217;s just a [message of the day][4], the configuration for which can be found in `/etc/motd`. [Delete line 2][5], and you should be good to go.

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="6508"
					data-ulike-nonce="df4ba93560"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_6508"></button><span class="count-box"></span>
  </div>
</div>

[][6]{.later-button-el}

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

 [1]: http://longren.io/digitalocean-one-click-wordpress-install/
 [2]: https://www.digitalocean.com/?refcode=cbf49d0481c8
 [3]: https://www.digitalocean.com/community/articles/one-click-install-wordpress-on-ubuntu-13-10-with-digitalocean
 [4]: http://en.wikipedia.org/wiki/Motd_(Unix)
 [5]: http://amionrails.wordpress.com/2014/02/09/how-to-remove-annoying-message-on-digital-ocean-ssd-hosting-after-droplet-creation/
 [6]: #