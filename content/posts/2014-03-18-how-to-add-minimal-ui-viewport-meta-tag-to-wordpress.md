---
title: 'How-To: Add Minimal-UI Viewport Meta Tag to WordPress'
author: Tyler Longren
type: post
date: 2014-03-18T12:28:23+00:00
url: /how-to-add-minimal-ui-viewport-meta-tag-to-wordpress/
featured_image: /wp-content/uploads/2014/03/minimal-ui-example.jpg
dsq_thread_id:
  - 2438706480
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - apple
  - Internet
  - ios
  - ipad
  - iphone
  - PHP
  - WordPress
  - wordpress-plugin
  - wordpress-plugins
  - wordpress-theme
  - wordpress-themes

---
 

## Introduced with iOS 7.1

I don&#8217;t have an iPhone, but my daughter does have an iPad Mini, which is running the latest iOS, 7.1. However, this only works for [those of you on iPhone&#8217;s][1], so I see no difference. 

[Martin Wolf][2] was kind enough to let me use the [image from his post about this subject][3] so that I could more easily illustrate the difference. So, even if you don&#8217;t have an iPhone, you can still see the changes this makes in the featured image above.

With the release of iOS 7.1 (and possibly late 7.0.x builds), [Safari introduced support for a new value][3] in the `viewport` meta tag. To me, it sounds like it adds effects similar to how Chrome hides its top bar when a page is loaded, but more. For example, the navigation buttons at the bottom are hidden.

I rarely use Safari, like never. Chrome is available on iOS, so that&#8217;s what I&#8217;ve always used. That&#8217;s not to say that you shouldn&#8217;t support Safari to it&#8217;s fullest, because I&#8217;d wager that a majority of iOS users stick with the default, which is Safari.

Chances are, your theme already has a `viewport` meta tag defined in it&#8217;s **header.php** file. If it does, add `minimal-ui` to it, so it should look something like this: 

<pre class="EnlighterJSRAW" data-enlighter-language="html" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimal-ui" /&gt;</pre>

If your theme doesn&#8217;t already have a viewport meta tag set, you can add one with [your functionality plugin][4] or theme&#8217;s **functions.php** file like so: 

<pre class="EnlighterJSRAW" data-enlighter-language="php" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;?php
function set_viewport() {
?>
&lt;meta name="viewport" content="width=device-width, minimal-ui">
&lt;?php
}
add_action('wp_head', 'set_viewport');
?></pre>

Adding the code above will add a brand new `viewport` meta tag for you, so only use that if your theme isn&#8217;t already using a `viewport` meta tag in it&#8217;s **header.php** file.

That&#8217;s it!

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="6132"
					data-ulike-nonce="4cf5cb5dc8"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_6132"></button><span class="count-box"></span>
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

 [1]: http://theamazingweb.net/2013/12/19/minimal-ui-viewport-meta-tag/
 [2]: http://visuellegedanken.de/
 [3]: http://visuellegedanken.de/2014-03-13/viewport-meta-tag-minimal-ui/
 [4]: http://longren.io/creating-a-wordpress-functionality-plugin/
 [5]: #