---
title: 'WordPress Theme Devs: Add Schema.org Markup To Your Themes'
author: Tyler Longren
type: post
date: 2014-02-22T06:07:58+00:00
url: /adding-schema-org-markup-to-your-wordpress-themes/
featured_image: /wp-content/uploads/2014/02/structured_data_markup_helper1.png
dsq_thread_id:
  - 2301663007
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
dsq_needs_sync:
  - 1
tags:
  - code
  - GitHub
  - html
  - Open Source
  - Personal
  - poll
  - schema.org
  - structured data
  - WordPress

---
I&#8217;m using the [Independent Publisher theme][1]. I made a child theme to add [schema.org][2] markup a few days ago. Instead of hoarding it, I [sent a pull request on GitHub][3] with the [schema.org][2] markup for inclusion in Independent Publisher.

Not sure what schema.org is? It&#8217;s a widely adopted microdata format, similar to [microformats][4]. Schema.org, however, is [supported by all the major search engines][5], giving it a definite edge over other microdata. The [FAQ at schema.org][6] is definitely worth checking out.

[<img loading="lazy" src="https://i0.wp.com/longren.io/wp-content/uploads/2014/02/structured_data_markup_helper-150x150.png?resize=150%2C150&#038;ssl=1" alt="Structured Data Markup Helper" width="150" height="150" class="alignleft size-thumbnail wp-image-5253" srcset="https://i2.wp.com/www.longren.io/wp-content/uploads/2014/02/structured_data_markup_helper.png?resize=150%2C150&ssl=1 150w, https://i2.wp.com/www.longren.io/wp-content/uploads/2014/02/structured_data_markup_helper.png?zoom=2&resize=150%2C150&ssl=1 300w, https://i2.wp.com/www.longren.io/wp-content/uploads/2014/02/structured_data_markup_helper.png?zoom=3&resize=150%2C150&ssl=1 450w" sizes="(max-width: 150px) 100vw, 150px" data-recalc-dims="1" />][7]Google also has a [Structured Data Markup Helper][8] that helps you add structured-data markup to a sample page. Just give it a URL, select an element and choose which structured-data to apply.  
[<img loading="lazy" src="https://i2.wp.com/longren.io/wp-content/uploads/2014/02/structured_data_markup_helper1-1024x476.png?resize=700%2C325&#038;ssl=1" alt="Structured Data Markup Helper Interface" width="700" height="325" class="aligncenter size-large wp-image-5257" srcset="https://i0.wp.com/www.longren.io/wp-content/uploads/2014/02/structured_data_markup_helper1.png?resize=1024%2C476&ssl=1 1024w, https://i0.wp.com/www.longren.io/wp-content/uploads/2014/02/structured_data_markup_helper1.png?resize=300%2C139&ssl=1 300w, https://i0.wp.com/www.longren.io/wp-content/uploads/2014/02/structured_data_markup_helper1.png?w=1902&ssl=1 1902w" sizes="(max-width: 700px) 100vw, 700px" data-recalc-dims="1" />][9]  
It&#8217;s not like there&#8217;s no WordPress themes without schema.org markup built-in, but there&#8217;s certainly not many. I don&#8217;t even have this built into my WordPress themes, I should update [Rootdip][10] with schema.org markup. Unwakeable, however, hasn&#8217;t been maintained in forever, and schema.org didn&#8217;t even exist back then.

There&#8217;s plenty of plugins for adding schema.org markup to your WordPress site, but I think it makes sense to just integrate it right into the theme. The theme developers know exactly where their tags are, preventing the need to add additional info to the end of the post that&#8217;s wrapped in schema.org markup.

I tried out the [All In One Schema.org Rich Snippets plugin][11], but it would require me to enter duplicate content (title, description, etc). It would also display a box at the end of each individual post page containing that extra, unnecessary content.

Because of that, I decided to just add the schema.org markup myself. It&#8217;s really very simple and only took about 15 minutes to do. Google likes schema.org data, and making Google happy is important to the ranking of your site. 15 minutes is definitely worth the time to do it right.

[Paul Lund][12] has [an excellent write up][13] on adding schema.org to your WordPress theme. [This post by Isabel Castillo][14] basically spelled out how to add the proper attributes to images, which was one thing missing in Paul&#8217;s post.

Anyway, here&#8217;s what I&#8217;ve put together as a basic starting point for integrating schema.org into your WordPress theme. Stuff is probably missing, some stuff may be incorrect. If so, please let me know in the comments.

<div id="polls-15" class="wp-polls">
</div>

<div id="polls-15-loading" class="wp-polls-loading">
  <img src="https://i2.wp.com/www.longren.io/wp-content/plugins/wp-polls/images/loading.gif?resize=16%2C16&#038;ssl=1" width="16" height="16" alt="Loading ..." title="Loading ..." class="wp-polls-image" data-recalc-dims="1" />&nbsp;Loading ...
</div>

## Before you begin

If your theme doesn&#8217;t include some of the tags mentioned below, like <span class="lang:default decode:true  crayon-inline " ><header></span>, <span class="lang:default decode:true  crayon-inline " ><footer></span> , <span class="lang:default decode:true  crayon-inline " ><article></span> , and <span class="lang:default decode:true  crayon-inline " ><time></span> , you can use regular <span class="lang:default decode:true  crayon-inline " ><span></span> tags instead. Just make sure you keep the `itemscope` attributes and their values.

### Modify single article file

This is usually single.php, content-single.php, or something similar. Find the <span class="lang:default decode:true  crayon-inline " ><article></span> tag and add the following to the end:  
<span class="lang:default decode:true  crayon-inline " >itemscope=&#8221;itemscope&#8221; itemtype=&#8221;http://schema.org/BlogPosting&#8221; itemprop=&#8221;blogPost&#8221;</span>

If your theme supports post thumbnails, find `the_post_thumbnail();` function and replace it with something like this:  
<span class="lang:default decode:true  crayon-inline " >the_post_thumbnail( &#8216;thumbnail&#8217;, array(&#8216;itemprop&#8217;=>&#8217;image&#8217; ) );</span>

Now find where the post date/time is being displayed. You&#8217;ll want to wrap it in a <span class="lang:default decode:true  crayon-inline " ><time></span> tag like below. You can also use a regular <span class="lang:default decode:true  crayon-inline " ><span></span> tag as well, just be sure to add the <span class="lang:default decode:true  crayon-inline " >itemprop=&#8221;datePublished&#8221;</span> and `pubdate` attributes.  
<span class="lang:default decode:true  crayon-inline " ><time class=&#8221;entry-date&#8221; datetime=&#8221;<?php the_time(&#8216;Y-m-dTH:i:sO&#8217;); ?>&#8221; itemprop=&#8221;datePublished&#8221; pubdate><?php the_time( get_option( &#8216;date_format&#8217; ) ); ?></time></span> 

Next find where the title is printed, usually between h1 tags, add an `itemprop` attribute with a value of **name**, like so:  
<span class="lang:default decode:true  crayon-inline " ><h1 class=&#8221;entry-title&#8221; itemprop=&#8221;name&#8221;><?php the_title(); ?></h1></span> 

Now add another `itemprop` attribute wtih a value of **mainContentOfPage** to the div containing `the_content();` WordPress function:  
<span class="lang:default decode:true  crayon-inline " ><div class=&#8221;entry-content&#8221; itemprop=&#8221;mainContentOfPage&#8221;></span> 

### Modify header.php

Only a few easy changes in this file. First, change your <span class="lang:default decode:true  crayon-inline " ><html <?php language_attributes(); ?>></span> to look like this:  
<span class="lang:default decode:true  crayon-inline " ><html <?php html_tag_schema(); ?> <?php language_attributes(); ?>></span> 

Next, change your <span class="lang:default decode:true  crayon-inline " ><body></span> tag to this:  
<span class="lang:default decode:true  crayon-inline " ><body <?php body_class(); ?> itemscope=&#8221;itemscope&#8221; itemtype=&#8221;http://schema.org/WebPage&#8221;></span> 

If your theme has a <span class="lang:default decode:true  crayon-inline " ><header></span> element, change it so it&#8217;s similar to this:  
<span class="lang:default decode:true  crayon-inline " ><header id=&#8221;masthead&#8221; class=&#8221;site-header&#8221; role=&#8221;banner&#8221; itemscope itemtype=&#8221;http://schema.org/WPHeader&#8221;></span> 

### Modify footer.php

If you theme has a <span class="lang:default decode:true  crayon-inline " ><footer></span> element, modify so it resembles the code below:  
<span class="lang:default decode:true  crayon-inline " ><footer id=&#8221;colophon&#8221; class=&#8221;site-footer&#8221; itemscope=&#8221;itemscope&#8221; itemtype=&#8221;http://schema.org/WPFooter&#8221; role=&#8221;contentinfo&#8221;></span>

### functions.php addition

[Paul Lund][12] wrote this function to define the schema type automatically for the type of content being displayed (ie: article, contact page, etc). You can see the <span class="lang:default decode:true  crayon-inline " ><html <?php html_tag_schema(); ?> <?php language_attributes(); ?>></span> function in the [functions.php file in the demo repo][15].

### Ideal Implementation

Don&#8217;t modify the core files of the theme you&#8217;re using. It&#8217;s seriously wrong and makes upgrading your theme almost impossible. Instead, [create a child theme][16]. It&#8217;s really, really easy to do and will inherit all the functionality and styles of the parent theme. For your convenience, I&#8217;ve put an example child theme up on GitHub, [tlongren/wordpress-child-example][17].

Since it&#8217;s a child theme for Independent Publisher, you&#8217;ll want to fork it and modify it to fit your theme. If you&#8217;re already using Independent Publisher, you should be good to [download the repo][18], upload it to WordPress, and activate the new theme from the WP dashboard.

### Why Implement Schema.org?

Because [Google says so][19]:

> Historically, we’ve supported three different standards for structured data markup: microdata, microformats, and RDFa. Instead of having webmasters decide between competing formats, we’ve decided to focus on just one format for schema.org. In addition, a single format will improve consistency across search engines relying on the data. There are arguments to be made for preferring any of the existing standards, but we’ve found that microdata strikes a balance between the extensibility of RDFa and the simplicity of microformats, so this is the format that we’ve gone with.

It also helps you define the default image that&#8217;s pulled when sharing a link on Google+ or Facebook. Users will still have the option of choosing another image, but probably won&#8217;t when the featured image from your post is automatically there. And this is just one example of why you should at least consider implementing schema.org markup.

As usual, comments are open, so please let me know what I got wrong and what could be improved. I appreciate whatever feedback people offer.

### This post is a mess

[This one is much more concise and much easier to implement][20], you&#8217;re probably better off starting there. 

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="5218"
					data-ulike-nonce="8172208dd7"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_5218"></button><span class="count-box"></span>
  </div>
</div>

[][21]{.later-button-el}

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

 [1]: http://independentpublisher.me/
 [2]: http://schema.org/
 [3]: https://github.com/raamdev/independent-publisher/pull/60
 [4]: http://microformats.org/
 [5]: http://schema.org/docs/faq.html#1
 [6]: http://schema.org/docs/faq.html
 [7]: https://i0.wp.com/www.longren.org/wp-content/uploads/2014/02/structured_data_markup_helper.png
 [8]: https://www.google.com/webmasters/markup-helper/
 [9]: https://i1.wp.com/www.longren.org/wp-content/uploads/2014/02/structured_data_markup_helper1.png
 [10]: http://www.longren.org/wordpress/rootdip/
 [11]: http://wordpress.org/plugins/all-in-one-schemaorg-rich-snippets/
 [12]: http://www.paulund.co.uk/
 [13]: http://www.paulund.co.uk/add-schema-org-wordpress
 [14]: http://isabelcastillo.com/image-microdata-wordpress-thumbnail-images
 [15]: https://github.com/tlongren/wordpress-child-example/blob/master/functions.php
 [16]: https://codex.wordpress.org/Child_Themes
 [17]: https://github.com/tlongren/wordpress-child-example
 [18]: https://github.com/tlongren/wordpress-child-example/archive/master.zip
 [19]: https://support.google.com/webmasters/answer/1211158?hl=en
 [20]: http://www.longren.org/add-schema-org-markup-to-any-wordpress-theme/
 [21]: #