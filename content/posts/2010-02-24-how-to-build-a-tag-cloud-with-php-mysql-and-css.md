---
title: 'How To: Build a Tag Cloud with PHP, MySQL, and CSS'
author: Tyler Longren
type: post
date: 2010-02-25T04:23:43+00:00
url: /how-to-build-a-tag-cloud-with-php-mysql-and-css/
tt_auto_tweet:
  - 'false'
tt_auto_tweet_text:
  - 'New blog post: [TITLE] [URL]'
ratings_users:
  - 4
ratings_score:
  - 16
ratings_average:
  - 4
views:
  - 3609
dsq_thread_id:
  - 1385911440
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - code
  - css
  - howto
  - Internet
  - mysql
  - Noteworthy
  - Open Source
  - Personal
  - PHP

---
 

Tag clouds are everywhere. They are a popular way to show the weight (read: popularity) of tags, categories, or any words really. I needed to build a tag cloud for a project at work to display categories and show how many questions were contained inside each category. Categories with more questions would need a larger font, and categories with fewer questions would need smaller fonts. I came across [this post][1] from [Steve Thomas][2] titled [_How to make a tag cloud in PHP, MySQL and CSS_][1].

Steve&#8217;s code is exactly what I was looking for. I made a few modifications to his code and wrapped it all into a custom PHP function, which you can see below. 

[Download The Code][3]

The function returns an array that contains each category name, the CSS class that should be applied to the given category, and the category ID for linking to the page showing only questions in that category. 

<pre class="EnlighterJSRAW" data-enlighter-language="php" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;?php
function tagCloud($maximum=0) {
	$cats = array(); // create empty array
	
	$query = mysql_query("SELECT categories.catDesc, categories.catId, COUNT( questions.id ) AS totalQuestions FROM questions, categories WHERE questions.categoryId = categories.catId GROUP BY categories.catId;");
	while ($row = mysql_fetch_array($query)) {
		$cat = $row['catDesc'];
		$counter = $row['totalQuestions'];
		$catid = $row['catID'];

		// update $maximum if this term is more popular than the previous terms
		if ($counter&gt; $maximum) $maximum = $counter;
		
		$percent = floor(($counter / $maximum) * 100);
		if ($percent &lt;20) {
			$class = 'smallest';
		}
		elseif ($percent&gt;= 20 and $percent &lt;40) {
			$class = 'small';
		}
		elseif ($percent&gt;= 40 and $percent &lt;60) {
			$class = 'medium';
		}
		elseif ($percent&gt;= 60 and $percent &lt;80) {
			$class = 'large';
		}
		else {
			$class = 'largest';
		}
		$cats[] = array('term' =&gt; $cat, 'class' =&gt; $class, 'catid' =&gt; $catid);

	}
	return $cats;
}
?&gt;
</pre>

You&#8217;ll also need some CSS to style your tag cloud. This CSS is pretty much identical to what Steve published, I only made some minor changes to font sizes. 

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">#tagcloud {
    width: 300px;
    background:#FFFFCC;
    color:#0066FF;
    padding: 10px;
    border: 1px solid #FFE7B6;
    text-align:center;
}
 
#tagcloud a:link, #tagcloud a:visited {
    text-decoration:none;
}
 
#tagcloud a:hover, #tagcloud a:active {
    text-decoration: underline;
    color: #000;
}
 
#tagcloud span {
    padding: 4px;
}
 
.smallest {
    font-size: 10px;
}
 
.small {
    font-size: 12px;
}
 
.medium {
    font-size:14px;
}
 
.large {
    font-size:16px;
}
 
.largest {
    font-size:18px;
}
</pre>

To use the function, do something like this: 

<pre class="EnlighterJSRAW" data-enlighter-language="php" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;?php
$tagCloud = tagCloud();
foreach ($tagCloud as $t) {
	$cat = $t['term'];
	$class = $t['class'];
	$catid = $t['catid'];
	print "&lt;span class="$class"&gt;&lt;a href="category.php?id=$catid"&gt;$cat&lt;/a&gt;&lt;/span&gt;";
}
?&gt;

</pre>

I am still testing this code, but so far it seems to do exactly what I need it to do. It&#8217;s best to use tagclouds in a [virtual private server provider][4] that supports PHP, MySQL and CSS. If you experience trouble with the code or if it doesn&#8217;t act as expected, please let me know in the comments. If you&#8217;ve got ideas on how to improve the function, I&#8217;d love to hear your thoughts as well!

<div class="wpulike wpulike-default " >
  <div class="wp_ulike_general_class wp_ulike_is_not_liked">
    <button type="button"
					aria-label="Like Button"
					data-ulike-id="2526"
					data-ulike-nonce="40655d572d"
					data-ulike-type="likeThis"
					data-ulike-template="wpulike-default"
					data-ulike-display-likers="0"
					data-ulike-disable-pophover="0"
					class="wp_ulike_btn wp_ulike_put_image wp_likethis_2526"></button><span class="count-box">3+</span>
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

 [1]: http://stevethomas.com.au/php/how-to-make-a-tag-cloud-in-php-mysql-and-css.html
 [2]: http://stevethomas.com.au/
 [3]: http://www.longren.org/downloads/tagcloud.zip
 [4]: http://www.webhostingsearch.com/virtual-private-server.php
 [5]: #