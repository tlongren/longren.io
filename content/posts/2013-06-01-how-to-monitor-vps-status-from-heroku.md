---
title: 'How-To: Monitor VPS Status From Heroku'
author: Tyler Longren
type: post
date: 2013-06-02T04:09:14+00:00
url: /how-to-monitor-vps-status-from-heroku/
featured_image: /wp-content/uploads/2013/05/heroku.jpg
dsq_thread_id:
  - 2306277465
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - fliphost
  - heroku
  - howto
  - Internet
  - Open Source
  - paas
  - PHP
  - php-code

---
 

I [built and released this tool][1] to monitor [the status][2] of your SolusVM client API-enabled VPS. It&#8217;s really easy to host it on Heroku, which is great since we don&#8217;t want to host the monitoring site on the VPS we want to monitor. You&#8217;ll need a [Heroku account][3] if you don&#8217;t already have one, the free account will do just fine.

Before we begin, you should probably install the [Heroku Toolbelt][4]. You&#8217;d also benefit from reading through some of the [Heroku Dev Center][5] articles. This [one about deploying to Heroku with git][6] is probably the most relevant for what we&#8217;re doing here.

You&#8217;ll need a terminal/command line for deploying to Heroku with git. A really great resource for new git users is [Git Immersion][7], just click the green &#8220;Start Git Immersion&#8221; arrow to get started with git. Anyway, the 5 steps that follow assume you&#8217;ve created a Heroku account and have git installed and working.

  1. Fork [tlongren/vps-status][8] on GitHub and make a local clone.
  2. Install the [Heroku Toolbelt][4] and login to Heroku with the command &#8220;_**heroku login**_&#8220;. Enter you username and password to login with the Heroku Toolbelt.
  3. Create a new app on Heroku either through the web interface, or with the command &#8220;_**heroku create**_&#8220;. If you do it with the command line the app name will be shown to you, [see here][6].
  4. Open a terminal and go into the folder that you cloned your fork into and run the command &#8220;_**heroku git:remote -a heroku-app-name**_&#8220;. That will add a remote named &#8220;heroku&#8221; to your local clone.
  5. Now, while still in your local clone folder, run &#8220;_**git push heroku master**_&#8221; to push your app to Heroku. If your app is named &#8220;heroku-app-name&#8221;, you can access your app at http://heroku-app-name.herokuapp.com.

That&#8217;s all there is to it. It might not seem simple at first glance, but it really is. To make changes, just edit the files in your local clone and commit those changes with git. Then run &#8220;_**git push heroku master**_&#8221; again to push the new code to Heroku.

**Make sure you don&#8217;t send your changes back to GitHub,** unless you&#8217;ve got private repositories. If you do a push to GitHub, your API key and hash will be accessible by the public, which isn&#8217;t something you want. Instead, you could either make a private repository at BitBucket or [create a private repo using Dropbox like I do][9]. The DropBox option is only reliable if you&#8217;re the only one editing the code, and if you&#8217;re only making changes from one machine at a time.

Let me know if you have any issues or think I&#8217;ve missed something.

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="4454"
					data-ulike-nonce="6e6a39366c"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_4454"></button><span class="count-box"></span>
  </div>
</div>

[][10]{.later-button-el}

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

 [1]: http://www.longren.org/vps-status-page-with-solusvm-and-fliphost/
 [2]: http://status.longren.org/
 [3]: http://www.heroku.com/
 [4]: https://toolbelt.heroku.com/
 [5]: https://devcenter.heroku.com/
 [6]: https://devcenter.heroku.com/articles/git
 [7]: http://gitimmersion.com/index.html
 [8]: https://www.github.com/tlongren/vps-status/
 [9]: http://mrdanadams.com/2011/github-free-private-git-repositories-dropbox/
 [10]: #