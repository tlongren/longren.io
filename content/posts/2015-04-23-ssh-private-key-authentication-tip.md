---
title: SSH Private Key Authentication Tip
author: Tyler Longren
type: post
date: 2015-04-23T14:35:12+00:00
url: /ssh-private-key-authentication-tip/
featured_image: /wp-content/uploads/2015/04/key.jpg
independent_publisher_primary_category:
  - Security
dsq_thread_id:
  - 3706394005
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - digitalocean
  - hosting
  - Internet
  - Security
  - tips

---
## So easy to miss, but so important for SSH Private Key Authentication {.subtitle}

I don&#8217;t allow password logins on any of my servers. Can only login via SSH key based authentication. No root login is allowed, and I specify every user that&#8217;s allowed to login via SSH, _ie: me_.

If you&#8217;re a regular here, you know I love [DigitalOcean][1]. They have a [very nice tutorial on setting up SSH private key login][2], even walking you through creating SSH keys if you don&#8217;t already have one, and even adding that key to your [DigitalOcean][1] account.

None of that will be of interest to you if you already know how to generate SSH keys.

I&#8217;ll SSH into my new Droplet, only to be rejected. I immediately know why, because it&#8217;s happened so many times. It&#8217;s due to incorrect permissions on your Droplet, VPS, server, whatever.

For SSH private key authentication to work, the `~/.ssh/authorized_keys` file and the `~/.ssh` folder need specific permissions: 

```shell
chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys
```

Run that, and then try logging in via SSH to your Droplet from your local machine. Should go this time.

If you still can&#8217;t login to your remote system, something else is likely wrong. If that&#8217;s the case, you&#8217;ll want to start at the top of [the DigitalOcean post about setting up SSH private key authentication][2] and just follow the steps.

After you&#8217;ve followed those steps, change permissions on the `~/.ssh/authorized_keys` file again and on the `~/.ssh` folder again. Like so from your terminal: 

``` shell
chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys
```

## I&#8217;m curious&#8230;

<div id="polls-31" class="wp-polls">
</div>

<div id="polls-31-loading" class="wp-polls-loading">
  <img src="https://i2.wp.com/www.longren.io/wp-content/plugins/wp-polls/images/loading.gif?resize=16%2C16&#038;ssl=1" width="16" height="16" alt="Loading ..." title="Loading ..." class="wp-polls-image" data-recalc-dims="1" />&nbsp;Loading ...
</div>

If you do allow password logins, I&#8217;d love to hear what scenario causes you to need to allow password logins. Let me know in the comments if you don&#8217;t mind.

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="8003"
					data-ulike-nonce="3843792de5"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_8003"></button><span class="count-box"></span>
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

 [1]: https://www.digitalocean.com/?refcode=cbf49d0481c8
 [2]: https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server
 [3]: #