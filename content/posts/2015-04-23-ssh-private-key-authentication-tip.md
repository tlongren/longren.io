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

I don't allow password logins on any of my servers. Can only login via SSH key based authentication. No root login is allowed, and I specify every user that's allowed to login via SSH, _ie: me_.

If you're a regular here, you know I love [DigitalOcean][1]. They have a [very nice tutorial on setting up SSH private key login][2], even walking you through creating SSH keys if you don't already have one, and even adding that key to your [DigitalOcean][1] account.

None of that will be of interest to you if you already know how to generate SSH keys.

I'll SSH into my new Droplet, only to be rejected. I immediately know why, because it's happened so many times. It's due to incorrect permissions on your Droplet, VPS, server, whatever.

For SSH private key authentication to work, the `~/.ssh/authorized_keys` file and the `~/.ssh` folder need specific permissions: 

```shell
chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys
```

Run that, and then try logging in via SSH to your Droplet from your local machine. Should go this time.

If you still can't login to your remote system, something else is likely wrong. If that's the case, you'll want to start at the top of [the DigitalOcean post about setting up SSH private key authentication][2] and just follow the steps.

After you've followed those steps, change permissions on the `~/.ssh/authorized_keys` file again and on the `~/.ssh` folder again. Like so from your terminal: 

``` shell
chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys
```

## I'm curious&#8230;

<div id="polls-31" class="wp-polls">
</div>

<div id="polls-31-loading" class="wp-polls-loading">
  <img src="https://i2.wp.com/www.longren.io/wp-content/plugins/wp-polls/images/loading.gif?resize=16%2C16&#038;ssl=1" width="16" height="16" alt="Loading ..." title="Loading ..." class="wp-polls-image" data-recalc-dims="1" />&nbsp;Loading ...
</div>

If you do allow password logins, I'd love to hear what scenario causes you to need to allow password logins. Let me know in the comments if you don't mind.

 [1]: https://www.digitalocean.com/?refcode=cbf49d0481c8
 [2]: https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server
 [3]: #