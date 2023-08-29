---
title: 'How To: Cisco VPN Client On Ubuntu'
author: Tyler Longren
type: post
date: 2007-05-18T03:35:00+00:00
url: /how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/
views:
  - 428806
ratings_users:
  - 35
ratings_score:
  - 143
ratings_average:
  - 4.09
dsq_thread_id:
  - 1385935509
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - howto
  - Internet
  - Linux
  - networking
  - Noteworthy
  - Open Source
  - Security
  - ubuntu

---
<p class="alert">
  <a href="http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/#projectpage">IMPORTANT UPDATE, SEE BELOW</a>
</p>

So, I installed [Ubuntu 7.04][1] Feisty Fawn beta about 2 months ago. I installed it on my notebook and one of my workstations, both of which had Windows installed previously. I&#8217;m not dual booting on those machine, they&#8217;re 100% Ubuntu now.  
<!--adsense-->

  
After getting everything setup and running nicely, I realized I had no way of connecting to the Cisco PIX VPN we have at work. This is really important for me to be able to do, my job depends on it. I immediately went to Google and started searching. Turns out a nice fellow named [Alexander Griesser has created a patch][2] for the Cisco VPN client. The most recent CIsco VPN client for linux won&#8217;t compile with kernels 2.6.19 or newer. There&#8217;s really not much of a difference between his instructions and this how-to. However, I&#8217;m including more detailed instructions for those who may not be familiar with compiling software on Linux.

Here&#8217;s the steps I took to get the Cisco VPN Client to work under Unbutu 7.04 (Feisty Fawn). In all reality, this should work with any version of Ubuntu, not just 7.04. I used this same method to get the Cisco VPN Client working on Ubuntu 8.04. Note: A **$** at the beginning of a line signifies a command to be run from the terminal.

  1. Download [vpnclient-linux-4.8.00.0490-k9.tar.gz][3] ([mirror][4]) to your home directory.
  2. Open a terminal window and untar the vpnclient with the following command:  
    **$ tar xzf vpnclient-linux-4.8.00.0490-k9.tar.gz**  
    This will create a new folder called _**vpnclient**_ in your home directory. Leave the terminal window open, you&#8217;ll need it later.
  3. Download [the patch][5] ([mirror][6]) and save it to the _**vpnclient**_ folder that was created in step 2.
  4. Go back to your terminal window and move into the vpnclient folder:  
    **$ cd vpnclient/**
  5. Now patch the Cisco VPN source with this command:  
    **$ patch < vpnclient-linux-2.6.22.diff**
  6. Next we actually build the Cisco VPN client, issue this command:  
    **$ sudo ./vpn_install**  
    Just hit enter for everything it asks you, the defaults are all OK. You may see lots of warnings, but those are OK.
  7. The VPN client is installed, now we need to start it:  
    **$ sudo /etc/init.d/vpnclient_init start**
  8. Place your .pcf configuration files in **_/etc/opt/cisco-vpnclient/Profiles/_**
  9. If your .pcf file is called myVPN.pcf, you&#8217;ll connect to the VPN with the following command:  
    **$ sudo vpnclient connect myVPN**

<!--adsense-->

  
That&#8217;s it! You should now be able to connect to your Cisco VPN with the official Cisco VPN client on Linux. This will probably work on pretty much any linux setup, not just Ubuntu.  
**  
UPDATE (8/18/2007):** Alexander Griesser [released a new patch][7] that works with kernel versions 2.6.22 and greater. The new patch is backwards compatible, so it also works with older kernels as well, such as 2.6.10 and 2.6.21. All the download links above point to the newest release of the patch. I&#8217;ll continue to update this how-to as he releases new patches.<a id="newclient"></a>  
**  
UPDATE (10/04/2007):** Cisco has finally released a new version of their vpn client for Linux. This new version compiles on all the new 2.6.xx kernels without the need for patching! You can download it [from Alexander&#8217;s site][8] or you can [get it right here][9].  
<a id="projectpage"></a>  
**UPDATE (12/29/2007):** Alexander Griesser has a [new project page][10] for his Cisco VPN client patches. It contains basic usage information and will most likely always have the latest and greatest patch available for download. In addition to that, Alexander has a new patch to make version 4.8.01.0640-k9 of the Cisco VPN Client [compile on 64bit systems][11]. Again, you can download the latest Cisco VPN Client for linux from the following link:  
<http://www.longren.org/downloads/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz>  
**UPDATE (8/11/2011):** [Marius B commented][12] and mentioned [he has a post up on this same subject][13]. It&#8217;s worth checking [his post][13] out. He basically suggests enabling the option to only use the VPN connection for resources on the network you&#8217;re connected to. [See his post][13] for more. 

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="2318"
					data-ulike-nonce="1aed89228c"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_2318"></button><span class="count-box"></span>
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

 [1]: http://www.ubuntu.com/
 [2]: http://tuxx-home.at/archives/2007/04/10/T15_55_43/
 [3]: ftp://ftp.cs.cornell.edu/pub/rvr/upload/vpnclient-linux-4.8.00.0490-k9.tar.gz
 [4]: http://www.longren.org/files/vpnclient-linux-4.8.00.0490-k9.tar.gz
 [5]: http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff
 [6]: http://www.longren.org/files/vpnclient-linux-2.6.22.diff
 [7]: http://tuxx-home.at/archives/2007/05/29/T16_34_26/
 [8]: http://tuxx-home.at/archives/2007/09/24/T15_26_49/
 [9]: http://www.longren.org/files/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz
 [10]: http://projects.tuxx-home.at/?id=cisco_vpn_client
 [11]: http://tuxx-home.at/archives/2007/11/09/T18_06_10/
 [12]: http://www.longren.org/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/comment-page-5/#comment-573750
 [13]: http://www.unfoldingcode.com/2011/08/how-to-install-cisco-vpn-client-on.html
 [14]: #