---
title: Add Schema.org Markup To Any WordPress Theme
author: Tyler Longren
type: post
date: 2014-02-23T12:29:11+00:00
url: /add-schema-org-markup-to-any-wordpress-theme/
featured_image: /wp-content/uploads/2014/02/schema_crushed.png
dsq_thread_id:
  - 2307497143
independent_publisher_primary_category:
  - Schema.org
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - code
  - GitHub
  - html
  - Internet
  - Open Source
  - Personal
  - poll
  - schema.org
  - WordPress

---
 

## Make Google, Yahoo, and Bing like you more!

The [last post I made on this topic][1] was a bit too specific to the Independent Publisher theme and was more editorial like, which made it really hard to follow. So, at the <a href="http://www.longren.org/adding-schema-org-markup-to-your-wordpress-themes/#comment-1256871206" target="_blank" rel="noreferrer noopener">request</a> of <a href="https://twitter.com/manishsuwal" target="_blank" rel="noreferrer noopener">Manish Suwal &#8216;Enwil&#8217;</a>, I&#8217;ve decided to write a more generic version that should apply to most, if not all, WordPress themes.

Please note that the class names used below could be different in the theme you&#8217;re using, so it&#8217;s mostly important to just pay attention to the HTML tags themselves, unless you&#8217;re doing something with a div, span, etc.

There&#8217;s 6 steps, although step 6 has a few different parts to it.

**1.** First, you&#8217;re going to want [this PHP function][2], a slightly modified version from [Paul Lund][3]. This function defines the schema type based on the type of content being displayed (article, author profile page, search results page, etc). Add this function to your themes **functions.php** file. The function is named `html_tag_schema()`. You can find it here:  


**2.** Find the `<html>` section of your theme and add our `html_tag_schema()` function. This will output the proper result from `html_tag_schema()`. It should look like the following:

<pre class="wp-block-preformatted">&lt;html class="no-js" &lt;?php schema_org_markup(); ?> &lt;?php language_attributes(); ?>></pre>

**3.** The page `title` tag is usually the same as the title of the page, so you can add this to your `titletag:<br/>
<title itemprop="name"><?php wp_title(''); ?></title>`

**4.** Now you&#8217;ll need to find the part of your theme that contains `the_content()` function. It could look something like this: 

<pre class="wp-block-preformatted">&lt;div class="entry-content" itemprop="mainContentOfPage">
  &lt;?php the_content(); ?>
&lt;/div></pre>

**5.** It&#8217;s generally a good idea to let Google (and other search engines) know when an article/post was published. You can also tell them if/when an article has been updated. Both of these can be taken care of with schema.org markup:  


<pre class="wp-block-preformatted">&lt;time class="entry-date" datetime="&lt;?php the_date('c'); ?>" itemprop="datePublished" pubdate>&lt;?php the_time( get_option( 'date_format' ) ); ?>&lt;/time></pre>

**6.** You can apply schema.org markup to any image, but it&#8217;s easiest when your theme supports featured images. I think most themes do support Featured Images now, and if your theme doesn&#8217;t, just [add Featured Image support yourself][4], or kindly ask the theme developer to add support. I could probably help you out, too.

**6a.**If your theme supports Featured Images, it should make use of the `the_post_thumbnail()` function. **Find that function in your theme** and replace it with this:  
the\_post\_thumbnail( &#8216;thumbnail&#8217;, array(&#8216;itemprop&#8217;=>&#8217;image&#8217; ) );

**6b.**If the &#8216;thumbnail&#8217; parameter value in your existing `the_post_thumbnail()` function is something other than &#8216;thumbnail&#8217;, make sure to keep that original paramater value. For example, if your `the_post_thumbnail()` call looked like the\_post\_thumbnail( array( 700, 700 ) );, adjust your `the_post_thumbnail()` function call to the following:  
the\_post\_thumbnail( array( 700, 700 ), array(&#8216;itemprop&#8217;=>&#8217;image&#8217; ) );

**6c.**The `array( 700, 700 )` piece can be replaced by whatever size you want. The first array value is the width, and the second is the height. There&#8217;s a variety of image sizes pre-defined by WordPress:

<blockquote class="wp-block-quote">
  <p>
    The default image sizes of WordPress are &#8220;thumbnail&#8221;, &#8220;medium&#8221;, &#8220;large&#8221; and &#8220;full&#8221; (the size of the image you uploaded). These image sizes can be configured in the WordPress Administration Media panel under Settings > Media. This is how you can use these default sizes with <code>the_post_thumbnail()</code> and schema.org markup:<br /> <code>the_post_thumbnail();                  // without parameter -> 'post-thumbnail'</code>
  </p>
  
  <p>
    the_post_thumbnail(&#8216;thumbnail&#8217;,array(&#8216;itemprop&#8217;=>&#8217;image&#8217; )); // Thumbnail (default 150px x 150px max)<br /> the_post_thumbnail(&#8216;medium&#8217;,array(&#8216;itemprop&#8217;=>&#8217;image&#8217; )); // Medium resolution (default 300px x 300px max)<br /> the_post_thumbnail(&#8216;large&#8217;,array(&#8216;itemprop&#8217;=>&#8217;image&#8217; )); // Large resolution (default 640px x 640px max)<br /> the_post_thumbnail(&#8216;full&#8217;,array(&#8216;itemprop&#8217;=>&#8217;image&#8217; )); // Full resolution (original size uploaded)
  </p>
  
  <p>
    <code>the_post_thumbnail( array(100,100), array('itemprop'=>'image' ) );  // Other resolutions (100x100)</code>
  </p>
</blockquote>

### That&#8217;s it!

If you want to know more about schema.org, have a look at [my original post][1]. [Schema.org][5] is also a wonderful resource, their [documentation][6] is excellent and would advise that you read through the [Getting Started Guide][7], it provides a great overview of the concepts behind structured data and schema.org.

### Other Resources

Google has this little post about [adding schema.org markup for organization logos][8]. If you&#8217;re an organization, you should probably [see what that&#8217;s all about][8].

[Craig Bradford at Moz.com][9] says [you&#8217;re behind if you&#8217;re not using schema.org][10] yet. That post from Craig also has a lot of really good information for those new to schema.org and structured data.

Google also has a post about [adding schema.org markup to videos][11], which could be really useful if you run a site with a lot of video content.

Searching the [Google Webmaster Central Blog][12] for &#8220;schema&#8221; [yields some pretty useful results][13], too.

### End

That&#8217;s all there is to adding basic schema.org structured data to your WordPress theme. You could obviously extend it to support [more schema.org &#8220;things&#8221;][14], but I&#8217;ll leave that for you. If you did every step in this post, you&#8217;ll have schema.org markup for featured images, article publish and update time, main content declaration and structured data enabled `title` and `head` HTML tags.

<div id="polls-15" class="wp-polls">
</div>

<div id="polls-15-loading" class="wp-polls-loading">
  <img src="https://i2.wp.com/www.longren.io/wp-content/plugins/wp-polls/images/loading.gif?resize=16%2C16&#038;ssl=1" width="16" height="16" alt="Loading ..." title="Loading ..." class="wp-polls-image" data-recalc-dims="1" />&nbsp;Loading ...
</div>

<div class="wp-block-image">
  <figure class="aligncenter"><a href="https://i2.wp.com/longren.io/wp-content/uploads/2014/02/mike-arnesen-structured-data-seo.png"><img loading="lazy" width="585" height="300" src="https://i2.wp.com/longren.io/wp-content/uploads/2014/02/mike-arnesen-structured-data-seo.png?resize=585%2C300" alt="No structured data? You suck." class="wp-image-5323" srcset="https://i0.wp.com/www.longren.io/wp-content/uploads/2014/02/mike-arnesen-structured-data-seo.png?w=585&ssl=1 585w, https://i0.wp.com/www.longren.io/wp-content/uploads/2014/02/mike-arnesen-structured-data-seo.png?resize=300%2C153&ssl=1 300w" sizes="(max-width: 585px) 100vw, 585px" data-recalc-dims="1" /></a></figure>
</div>

Have any questions, comments, or maybe even praise? Comments are open, as usual.  


<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="5283"
					data-ulike-nonce="30f3cf2086"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_5283"></button><span class="count-box"></span>
  </div>
</div>

[][15]{.later-button-el}

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

 [1]: http://www.longren.org/adding-schema-org-markup-to-your-wordpress-themes/
 [2]: https://gist.github.com/tlongren/9148513
 [3]: http://www.paulund.co.uk/
 [4]: http://codex.wordpress.org/Post_Thumbnails
 [5]: http://schema.org
 [6]: http://schema.org/docs/documents.html
 [7]: http://schema.org/docs/gs.html
 [8]: http://googlewebmastercentral.blogspot.com/2013/05/using-schemaorg-markup-for-organization.html
 [9]: http://moz.com/community/users/296192
 [10]: http://moz.com/blog/schema-examples
 [11]: http://googlewebmastercentral.blogspot.com/2012/02/using-schemaorg-markup-for-videos.html
 [12]: http://googlewebmastercentral.blogspot.com/
 [13]: http://googlewebmastercentral.blogspot.com/search/label/crawling%20and%20indexing
 [14]: http://schema.org/Event
 [15]: #