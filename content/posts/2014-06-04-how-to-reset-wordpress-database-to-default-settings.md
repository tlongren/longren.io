---
title: 'How-To: Reset WordPress Database to Default Settings'
author: Tyler Longren
type: post
date: 2014-06-04T12:45:49+00:00
url: /how-to-reset-wordpress-database-to-default-settings/
featured_image: /wp-content/uploads/2014/06/wpdb-reset.png
dsq_thread_id:
  - 2734117058
primary_category:
  - WordPress
independent_publisher_primary_category:
  - WordPress
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
switch_like_status:
  - 1
tags:
  - cool
  - git
  - GitHub
  - how-to
  - howto
  - Internet
  - Open Source
  - opensource
  - Personal
  - plugin
  - tools. tool
  - WordPress
  - wordpress-plugin
  - wordpress-plugins

---
## Easily Reset WordPress Database {.subtitle}

[WordPress Database Reset][1] is a WordPress plugin I recently came across that will at some point prove very, very useful to me.

It&#8217;s not often that I need to reset a production WordPress database to it&#8217;s default settings, but this plugin will make the task a whole lot easier. [Chris Berthe][2], the author, describes the plugin like this:

> WordPress Database Reset is a secure and easy way to reinitialize your WordPress database back to its default settings without actually having to reinstall WordPress yourself. 

I can see this being crazy useful for WordPress plugin and theme developers. We frequently need a fresh database to work with, so I&#8217;ll be adopting this plugin in my WordPress plugin and theme development workflow from here on.

WordPress Database Reset requires WordPress 3.0+ and can be installed just like any other WordPress plugin. It&#8217;s in the [WordPress Plugin directory][3], and can [also be found on GitHub][1].

It even integrates with [WP-CLI][4], a command line tool for interacting with WordPress. This allows you to do things like select which tables you want to reset:

<pre class="lang:sh decode:true " >wp reset database --tables='users, posts, comments, options'</pre>

Here&#8217;s a list of features:

  * Extremely fast one click process to reset the WordPress database
  * Choose to reset the entire database or specific database tables
  * Secure and super simple to use
  * Prefer the command line? Reset the database in one command
  * Excellent for theme and plugin developers who need to clean the database of any unnecessary content quickly

If you&#8217;re a WordPress theme or plugin developer, you should [definitely check it out][1]. 

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="7030"
					data-ulike-nonce="a98f81176f"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_7030"></button><span class="count-box"></span>
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

 [1]: https://github.com/chrisberthe/wordpress-database-reset
 [2]: https://twitter.com/chrisberthe
 [3]: http://wordpress.org/plugins/wordpress-database-reset/
 [4]: http://wp-cli.org/
 [5]: #