---
title: Secure SSH By Disabling Password Logins
author: Tyler Longren
type: post
date: 2014-04-05T16:00:13+00:00
url: /secure-ssh-by-disabling-password-logins/
featured_image: /wp-content/uploads/2014/04/key.png
dsq_thread_id:
  - 2587114273
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - digital ocean
  - digitalocean
  - hosting
  - Internet
  - Personal
  - Security
  - ssh

---
## Make bruteforce attempts almost impossible {.subtitle}

I always disable SSH password logins when setting up a new server, allowing authentication via private key only. It&#8217;s a good way to secure SSH all-around.

Disabling password logins in Ubuntu is extremely easy.

Open _/etc/ssh/sshd_config_ with nano or vi. You&#8217;ll want to change options for 3 different directives, `ChallengeResponseAuthentication`, `PasswordAuthentication`, and `UsePAM`.

Find those directives in /etc/ssh/sshd_config and set them to the following:

<pre class="lang:default highlight:0 decode:true " >ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no</pre>

Save `sshd_config`, and reload ssh:

<pre class="lang:sh decode:true " >sudo service ssh reload</pre>

That&#8217;s it, now you won&#8217;t be able to SSH to your server and login with a password, and neither will anyone else.

Of course, you&#8217;ll want to enable private key authentication, first. If you don&#8217;t, you&#8217;ll lock yourself out of your server.

DigitalOcean has a [good article on how to do this][1].

<div id="polls-23" class="wp-polls">
</div>

<div id="polls-23-loading" class="wp-polls-loading">
  <img src="https://i2.wp.com/www.longren.io/wp-content/plugins/wp-polls/images/loading.gif?resize=16%2C16&#038;ssl=1" width="16" height="16" alt="Loading ..." title="Loading ..." class="wp-polls-image" data-recalc-dims="1" />&nbsp;Loading ...
</div>

Let&#8217;s go a bit farther and only allow specific users to login via SSH. We can do so with by adding a line like the one below to _/etc/ssh/sshd_config_:

<pre class="lang:default highlight:0 decode:true " >AllowUsers firstuser seconduser thirduser</pre>

This will allow only three users to login: _firstuser_, _seconduser_, or _thirduser_. I usually add my _AllowUsers_ directive towards the top of sshd_config.

After modifying _/etc/ssh/sshd_config_, reload ssh again like so:

<pre class="lang:sh decode:true " >sudo service ssh reload</pre>

 [1]: https://www.digitalocean.com/community/articles/how-to-use-ssh-keys-with-digitalocean-droplets
 [2]: #