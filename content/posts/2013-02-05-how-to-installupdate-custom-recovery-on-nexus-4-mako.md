---
title: 'How-To: Install/Update Custom Recovery on Nexus 4 (Mako)'
author: Tyler Longren
type: post
date: 2013-02-05T21:30:11+00:00
url: /how-to-installupdate-custom-recovery-on-nexus-4-mako/
featured_image: /wp-content/uploads/2013/02/RAsb-240x270.jpg
dsq_thread_id:
  - 1541246562
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - android
  - howto
  - Internet
  - Open Source
  - Personal

---
I use [TWRP (Team-Win Recovery Project)][1] as a custom recovery. It&#8217;s easy to use and, as the name suggests, has a nice touch interface. TWRP [supports a bunch of devices][2], including the [Nexus 4 (Mako)][3].

Here&#8217;s the full description straight from the TWRP site:

> Team Win Recovery Project 2.4, or twrp2 for short, is a custom recovery built with ease of use and customization in mind. We started from the ground up by taking AOSP recovery and loading it with the standard recovery options, then added a lot of our own features. It’s a fully touch driven user interface – no more volume rocker or power buttons to mash. The GUI is also fully XML driven and completely theme-able. You can change just about every aspect of the look and feel.

<p class="clearfix">
  &nbsp;
</p>

Installing TWRP on your Google Nexus 4 is pretty simple. The TWRP site has good instructions, but I always forget how to update when a new version is released. And checking the actual TWRP site was something I didn&#8217;t think of doing, because I thought I had installed TWRP through a separate tool (which I did).

So, the suggested method for installing TWRP to your Google Nexus 4 (and the method I use) is really straight forward. You&#8217;ll need root.

  1. Install [GooManager from the Play Store][4] and open it up (grant it root permissions).
  2. Select the menu and then tap &#8220;Install OpenRecoveryScript&#8221;, then tap &#8220;Yes&#8221;.
  3. Make sure the filename says &#8220;mako&#8221; in it somewhere, this ensures you&#8217;ll get the Nexus 4 recovery.
  4. Tap &#8220;Yes&#8221; again.
  5. That&#8217;s it, TWRP will be downloaded and installed automatically.

Below are some TWRP2 screenshots, taken straight from the [TWRP website][1]. If you&#8217;re interested in contributing to TWRP, you can check out their [project on Github][5].  
<!-- see gallery_shortcode() in wp-includes/media.php -->

<div id='gallery-11' class='gallery galleryid-3474'>
  <dl class='gallery-item'>
    <dt class='gallery-icon'>
      <a href='https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/7zXg.jpg?ssl=1'><img width="150" height="150" src="https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/7zXg.jpg?resize=150%2C150&#038;ssl=1" class="attachment-thumbnail size-thumbnail" alt="" loading="lazy" srcset="https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/7zXg.jpg?resize=150%2C150&ssl=1 150w, https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/7zXg.jpg?zoom=2&resize=150%2C150&ssl=1 300w, https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/7zXg.jpg?zoom=3&resize=150%2C150&ssl=1 450w" sizes="(max-width: 150px) 100vw, 150px" data-recalc-dims="1" /></a>
    </dt>
  </dl>
  
  <dl class='gallery-item'>
    <dt class='gallery-icon'>
      <a href='https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/AO13.jpg?ssl=1'><img width="150" height="150" src="https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/AO13.jpg?resize=150%2C150&#038;ssl=1" class="attachment-thumbnail size-thumbnail" alt="" loading="lazy" data-recalc-dims="1" /></a>
    </dt>
  </dl>
  
  <dl class='gallery-item'>
    <dt class='gallery-icon'>
      <a href='https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/nkUM.jpg?ssl=1'><img width="150" height="150" src="https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/nkUM.jpg?resize=150%2C150&#038;ssl=1" class="attachment-thumbnail size-thumbnail" alt="" loading="lazy" srcset="https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/nkUM.jpg?resize=150%2C150&ssl=1 150w, https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/nkUM.jpg?zoom=2&resize=150%2C150&ssl=1 300w, https://i1.wp.com/www.longren.io/wp-content/uploads/2013/02/nkUM.jpg?zoom=3&resize=150%2C150&ssl=1 450w" sizes="(max-width: 150px) 100vw, 150px" data-recalc-dims="1" /></a>
    </dt>
  </dl>
  
  <br style="clear: both" />
  
  <dl class='gallery-item'>
    <dt class='gallery-icon'>
      <a href='https://i2.wp.com/www.longren.io/wp-content/uploads/2013/02/RAsb.jpg?ssl=1'><img width="150" height="150" src="https://i2.wp.com/www.longren.io/wp-content/uploads/2013/02/RAsb.jpg?resize=150%2C150&#038;ssl=1" class="attachment-thumbnail size-thumbnail" alt="" loading="lazy" data-recalc-dims="1" /></a>
    </dt>
  </dl>
  
  <br style='clear: both;' />
</div>

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="3474"
					data-ulike-nonce="9004ab277a"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_3474"></button><span class="count-box"></span>
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

 [1]: http://teamw.in/project/twrp2
 [2]: http://teamw.in/twrp_view_all_devices
 [3]: http://teamw.in/project/twrp2/129
 [4]: https://play.google.com/store/apps/details?id=com.s0up.goomanager
 [5]: https://github.com/TeamWin/Team-Win-Recovery-Project
 [6]: #