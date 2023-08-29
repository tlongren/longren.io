---
title: Wrapping Text Inside Pre Tags
author: Tyler Longren
type: post
date: 2006-09-27T17:39:48+00:00
url: /wrapping-text-inside-pre-tags/
ratings_average:
  - 4.44
ratings_score:
  - 71
views:
  - 98684
wjt_diPostTopic:
  - design
ratings_users:
  - 16
DiggURL:
  - http://www.digg.com/design/Force_Text_Wrapping_Inside_Pre_Tags
dsq_thread_id:
  - 1385930385
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - browsers
  - code
  - coding
  - css
  - design
  - firefox
  - html
  - Internet
  - internet-explorer
  - Noteworthy
  - Personal
  - WordPress
  - wordpress-plugins

---
 

I sometimes display little snippets of code on this site. For example, [here][1], [here][2], and [here][3]. To do this, I use the [Code Markup wordpress plugin][4].

If you&#8217;re using Firefox, you may notice the long lines in [my Digg Integrator fix post][1]. It&#8217;s not really a problem for me having those really long lines in Firefox. Why? Because Firefox still displays my sidebar correctly. Internet Explorer is a totally different story though. When there&#8217;s long lines like that, my sidebar will appear at the very bottom of the page in IE.  
  
The long lines are caused by use of [the pre html tag][5]. The pre tag preserves spaces and line breaks in a chunk of text. Perfect for displaying snippets of code. However, some lines of code are quite long and will run off the page. This is exactly why my sidebar was getting pushed to the bottom of the page in IE.

So, I set out looking for a method to wrap text contained within pre tags. Google found [exactly what I was looking for][6]. Wrapping text inside pre tags is quite easy, all that&#8217;s required is a simple addition to your css:

<pre class="wp-block-preformatted">pre {
 white-space: pre-wrap;       /* css-3 */
 white-space: -moz-pre-wrap;  /* Mozilla, since 1999 */
 white-space: -pre-wrap;      /* Opera 4-6 */
 white-space: -o-pre-wrap;    /* Opera 7 */
 word-wrap: break-word;       /* Internet Explorer 5.5+ */
}</pre>

Quite simple. After adding that CSS, the text in pre tags still doesn&#8217;t wrap in Firefox, but I don&#8217;t care because Firefox displays the rest of my page as it should. Now, when you view a page in IE with a long line, the text is wrapped and my sidebar content appears at the top of the page instead of the bottom.

For consistency sake, let&#8217;s make these long lines wrap in Firefox too. This is extremely simple. It only requires adding a few characters to the CSS shown above. For text wrapping in Firefox, use this CSS:

<pre class="wp-block-preformatted">pre {
 white-space: pre-wrap;       /* css-3 */
 white-space: -moz-pre-wrap !important;  /* Mozilla, since 1999 */
 white-space: -pre-wrap;      /* Opera 4-6 */
 white-space: -o-pre-wrap;    /* Opera 7 */
 word-wrap: break-word;       /* Internet Explorer 5.5+ */
}
</pre>

  
Notice the only difference between the first and second examples is the addition of &#8220;!important&#8221; to the third line in example 2. After adding that little bit, your text between your pre tags should wrap well in basically every browser that&#8217;s currently in use.

#### UPDATE 3/10/2007

If you can&#8217;t seem to get the css above to work, give the css below a shot. I just set a width on the pre tag. When the width is set to 100%, you&#8217;ll get a horizontal scrollbar when viewing in IE7. That&#8217;s why I&#8217;ve set the width to 99%. The code will display just fine in IE6, IE6, and FireFox when width is set to 99%. I have not tested Opera. Try this updated CSS if you&#8217;re having issues with the original CSS from above.

<pre class="wp-block-preformatted">pre {
 white-space: pre-wrap;       /* css-3 */
 white-space: -moz-pre-wrap !important;  /* Mozilla, since 1999 */
 white-space: -pre-wrap;      /* Opera 4-6 */
 white-space: -o-pre-wrap;    /* Opera 7 */
 word-wrap: break-word;       /* Internet Explorer 5.5+ */
 width: 99%;
}
</pre>

#### UPDATE 6/4/2008

[Markku Laine][7] posted some css in [a comment][7] that seems to work better than the original css I posted. It works in IE, Safari, and FireFox. Try using Markku&#8217;s css below if the previous examples don&#8217;t work for you.

<pre class="wp-block-preformatted">pre {
 overflow-x: auto; /* Use horizontal scroller if needed; for Firefox 2, not needed in Firefox 3 */
 white-space: pre-wrap; /* css-3 */
 white-space: -moz-pre-wrap !important; /* Mozilla, since 1999 */
 white-space: -pre-wrap; /* Opera 4-6 */
 white-space: -o-pre-wrap; /* Opera 7 */
 /* width: 99%; */
 word-wrap: break-word; /* Internet Explorer 5.5+ */
}
</pre>

#### Update 1/20/2011

Some code Max [posted in a comment][8] also seems to be working well for many people. It may be worth trying as well:

<pre class="wp-block-preformatted">height: 120px;
overflow: auto;
font-family: “Consolas”,monospace;
font-size: 9pt;
text-align:left;
background-color: #FCF7EC;
overflow-x: auto; /* Use horizontal scroller if needed; for Firefox 2, not
white-space: pre-wrap; /* css-3 */
white-space: -moz-pre-wrap !important; /* Mozilla, since 1999 */
word-wrap: break-word; /* Internet Explorer 5.5+ */
margin: 0px 0px 0px 0px;
padding:5px 5px 3px 5px;
white-space : normal; /* crucial for IE 6, maybe 7? */</pre>

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="2247"
					data-ulike-nonce="1ba01d4c4e"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_2247"></button><span class="count-box">4+</span>
  </div>
</div>

[][9]{.later-button-el}

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

 [1]: http://www.longren.org/2006/09/23/digg-integrator-plugin-fix/
 [2]: http://www.longren.org/2006/08/19/improved-permalink-redirection/
 [3]: http://www.longren.org/2005/07/09/quick-and-easy-remote-backups/
 [4]: http://www.thunderguy.com/semicolon/wordpress/code-markup-wordpress-plugin/
 [5]: http://www.w3schools.com/tags/tag_pre.asp
 [6]: http://myy.helia.fi/~karte/pre-wrap-css3-mozilla-opera-ie.html
 [7]: http://www.longren.org/2006/09/27/wrapping-text-inside-pre-tags/#comment-198030
 [8]: http://www.longren.org/2006/09/27/wrapping-text-inside-pre-tags/#comment-242412
 [9]: #