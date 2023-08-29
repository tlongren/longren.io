---
title: Stopping SSH Brute Force Attacks
author: Tyler Longren
type: post
date: 2006-08-21T15:40:17+00:00
url: /stopping-ssh-brute-force-attacks/
DiggURL:
  - http://digg.com/linux_unix/Stopping_SSH_Brute_Force_Attacks
views:
  - 8550
ratings_users:
  - 3
ratings_score:
  - 15
ratings_average:
  - 5
wjt_diPostTopic:
  - linux_unix
DiggUrl:
  - http://digg.com/linux_unix/Stopping_SSH_Brute_Force_Attacks
dsq_thread_id:
  - 1385927286
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - breakinguard
  - code
  - coding
  - hacking
  - help
  - howto
  - Linux
  - Open Source
  - programming
  - Security
  - ssh

---
A few weeks ago at work, I noticed a bunch of failed login attempts to one of our Linux servers. After doing some investigation, I found that no intrusion had actually been made, which is excellent. Lines similar to this were filling my /var/log/messages log file:

> Aug 20 23:31:26 elixer sshd[22526]: Failed password for invalid user alias from 66.166.22.186 port 26217 ssh2

Notice they&#8217;re trying to login with the username &#8220;alias&#8221;, which doesn&#8217;t exist on that system. In fact, all the usernames attempted don&#8217;t exist, which makes me feel a little safer. Still, I don&#8217;t like seeing my boxes actively attacked. So, to stay on top of these breakin attempts, [I installed Breakinguard][1]. 

Breakinguard basically watches your log file for any failed login attempts. You can set a pre-defined number of attempts that can be executed before breakinguard will block the IP.

> The Package itself does a &#8216;tail -f&#8217; of your syslog, and when it identifies a matching line within your logs, it logs this &#8216;attempt&#8217;. If more than the pre-defined number of attempts from the same IP address are received it triggers the iptables (or any other block method defined) block and also emails you notification.

I&#8217;ve never been able to get the configure script to work for me, simply because the perl module installation always fails. So, to get around that I simply installed these perl modules manually and commented out these lines in the configure script:

<pre>$PERL -MCPAN -e "install File::Tail"
$PERL -MCPAN -e "install IO::Socket"</pre>

Those two lines execute perl and try to install the File::Tail module and the IO::Socket module. After manually installing the perl modules below and commenting out the lines above in the configure script, the configure script should run and do it&#8217;s thing without error.

> [File::Tail][2]  
> [IO::Socket][3] 

<!--adsense-->

  
After the configuration script has run, you should have a couple new files, /etc/breakinguard.conf and /etc/rc.d/breakinguard. Now, the /etc/breakinguard.conf file stores the breakinguard configuration. This is where you tell breakinguard which log file to monitor and how many incorrect login attempts are defined as a breakin.

I&#8217;m not going to bother going through all the options in breakinguard.conf, simply because they&#8217;re all explained pretty well within the conf file.

The other &#8220;new file&#8221;, /etc/rc.d/breakinguard is the script used to launch breakinguard. Run &#8220;/etc/rc.d/breakinguard start&#8221; to start breakinguard.

Once breakinguard is running, it will monitor whichever log file you specified in /etc/breakinguard.conf (/var/log/messages in my case). When it sees a failed login attempt, it will be noted. Now, when an IP fails a certain number of logins, iptables will be called to block all traffic from the IP.

Below is an example email that&#8217;s generated by Breakinguard when it blocks an IP:

> BreakinGuard has blocked an IP based on suspicious activity  
> Please review this server.
> 
> Detail:  
> Hostname: elixer.hostname  
> IP Blocked: 202.82.16.180  
> Last log entry that caused the block:  
> Aug 22 06:17:05 elixer sshd[25591]: Failed password for invalid user alias from 202.82.16.180 port 45340 ssh2

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="2219"
					data-ulike-nonce="fc3716cb1e"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_2219"></button><span class="count-box"></span>
  </div>
</div>

[][4]{.later-button-el}

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

 [1]: http://breakinguard.sourceforge.net/
 [2]: http://search.cpan.org/~mgrabnar/File-Tail-0.99.3/
 [3]: http://search.cpan.org/~gbarr/IO-1.2301/
 [4]: #