---
title: 'How-To: Make Animated Progress Circles Using Circliful'
author: Tyler Longren
type: post
date: 2014-09-02T12:38:23+00:00
url: /how-to-make-animated-progress-circles-using-circliful/
featured_image: /wp-content/uploads/2014/09/circliful.png
independent_publisher_primary_category:
  - jQuery
dsq_thread_id:
  - 2976124580
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - cool
  - css
  - git
  - GitHub
  - how-to
  - howto
  - Internet
  - JavaScript
  - Personal
  - tools

---
## A jQuery Plugin for Making Circles {.subtitle}

My [last post about the jQuery plugin Circliful][1] was pretty popular. So, here&#8217;s another, detailing how to actually _use_ [Circliful][2].

Circliful has a number of options that can be set as [data attributes][3]. Data attributes are the primary method for setting various options, such as the circle background color, fill color, and the percentage. All of the possible data attributes are available in the [README on GitHub][4].

Using Circliful is similar to every other jQuery plugin. Just make sure you&#8217;re loading up jQuery prior to loading the Circliful JavaScript.

### 1. Include Circliful JavaScript and CSS

Include the JavaScript and CSS files from Circliful just like you would any other JavaScript or CSS file.

<pre class="lang:xhtml decode:true " >&lt;link href="css/jquery.circlify.css" rel="stylesheet" type="text/css" /&gt;
&lt;script src="js/jquery.circliful.min.js"&gt;&lt;/script&gt;</pre>

### 2. Add an element with the necessary data attributes

This is where you can define all the data attributes that are [listed in the README][4]. I typically use an empty div with the following data attributes: **data-dimension**, **data-text**, **data-info**, **data-width**, **data-fontsize**, **data-percent**, **data-fgcolor**, **data-bgcolor**, **data-fill**, **data-total**, and **data-part**.

You&#8217;ll want to give your newly created element a unique ID to use as a selector in jQuery. I used **_circle-1_** as the element ID for this example.

<pre class="lang:xhtml decode:true " >&lt;div id="circle-1" class="circle" data-dimension="250" data-text="85%" data-info="Sweet" data-width="30" data-fontsize="38" data-percent="85" data-fgcolor="#61a9dc" data-bgcolor="#eee" data-fill="#ddd" data-total="100" data-part="85"&gt;&lt;/div&gt;</pre>

### 3. Add necessary JavaScript

This tells Circliful which element to build the circle from. We want to target the ID that we gave to our empty element/div above.

<pre class="lang:js decode:true " >&lt;script&gt;
$( document ).ready(function() {
        $('#circle-1').circliful();
    });
&lt;/script&gt;</pre>

**That&#8217;s it!** You should now have a circle similar to the first circle in the example below. If you have any questions, feel free to leave a comment or [get in touch with me directly][5].

You can find the necessary JavaScript and CSS on the [Circliful GitHub page][2]. You can see an example of Circliful in the embedded pen below.

<p data-height="600" data-theme-id="0" data-slug-hash="erojh" data-default-tab="result" class='codepen'>
  See the Pen <a href='http://codepen.io/tlongren/pen/erojh/'>erojh</a> by Tyler Longren (<a href='http://codepen.io/tlongren'>@tlongren</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="7351"
					data-ulike-nonce="b31976e935"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_7351"></button><span class="count-box">1+</span>
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

 [1]: http://longren.io/circliful-a-jquery-plugin-providing-animated-progress-circles/
 [2]: https://github.com/pguso/jquery-plugin-circliful
 [3]: https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_data_attributes
 [4]: https://github.com/pguso/jquery-plugin-circliful/blob/master/README.md
 [5]: http://longren.io/contact/
 [6]: #