---
title: Add Schema.org Markup to WooCommerce Products
author: Tyler Longren
type: post
date: 2014-11-26T16:03:09+00:00
url: /add-schema-org-markup-to-woocommerce-products/
featured_image: /wp-content/uploads/2014/11/woocommerce-schema-post.png
independent_publisher_primary_category:
  - Schema.org
dsq_thread_id:
  - 3265269843
pageViews:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
pageViews_cumul:
  - '{"hours":{"1":"","2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":"","25":"","26":"","27":"","28":"","29":"","30":"","31":"","32":"","33":"","34":"","35":"","36":"","37":"","38":"","39":"","40":"","41":"","42":"","43":"","44":"","45":"","46":"","47":""},"days":{"2":"","3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":""},"weeks":{"3":"","4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":""},"months":{"4":"","5":"","6":"","7":"","8":"","9":"","10":"","11":"","12":"","13":"","14":"","15":"","16":"","17":"","18":"","19":"","20":"","21":"","22":"","23":"","24":""}}'
tags:
  - cool
  - GitHub
  - Internet
  - Open Source
  - Personal
  - PHP
  - plugins
  - schema.org
  - themes
  - tutorials
  - WordPress
  - wordpress tutorials
  - wordpress-plugins
  - wordpress-themes

---
 

## WooCommerce & Schema.org Is Awesome

Adding [schema.org][1] markup to a well coded WordPress theme is relatively straight forward and doesn&#8217;t take very long to get setup.

I [covered how to add schema.org markup to your WordPress theme in a previous post][2], but I recently needed to apply schema.org markup to an e-commerce site using [WooCommerce][3].

It&#8217;s surprisingly easy to do. You&#8217;ll need to be using a child theme for the steps that follow.

### 1. Setup the necessary function in the functions.php file for your theme

Add the following to your _**functions.php**_ file. It creates a custom function, `schema_org_markup`.

<pre class="EnlighterJSRAW" data-enlighter-language="php" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">function schema_org_markup() {
    $schema = 'http://schema.org/';
    // Is single post
    if ( function_exists(is_woocommerce) && is_woocommerce() ) {
      $type = 'Product';
    }
    elseif ( is_single() ) {
        $type = "Article";
    } 
    else {
        if ( is_page( 644 ) ) { // Contact form page ID
            $type = 'ContactPage';
        } // Is author page
        elseif ( is_author() ) {
            $type = 'ProfilePage';
        } // Is search results page
        elseif ( is_search() ) {
            $type = 'SearchResultsPage';
        } // Is of movie post type
        elseif ( is_singular( 'movies' ) ) {
            $type = 'Movie';
        } // Is of book post type
        elseif ( is_singular( 'books' ) ) {
            $type = 'Book';
        }
        else {
            $type = 'WebPage';
        }
    }
    echo 'itemscope="itemscope" itemtype="' . $schema . $type . '"';
}</pre>

### 2. Call schema\_org\_markup() In Your Header

Open up the header.php file for your child theme and find the `html` tag, usually towards the top. You&#8217;ll want to call the `schema_org_markup` function inside that `html` tag, like so:

<pre class="EnlighterJSRAW" data-enlighter-language="php" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;html &lt;?php schema_org_markup(); ?> &lt;?php language_attributes(); ?>></pre>

### 3. Create a WooCommerce template file in your child theme

Create a directory in your child theme folder named **_woocommerce_**. Inside the **_woocommerce_** folder, create another new folder named **_single-product_**. Inside the **_single-product_** folder, create a file named **_price.php_**. The contents of your **_price.php_** file should look like this:

<pre class="EnlighterJSRAW" data-enlighter-language="php" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;?php
/**
 * Single Product Price, including microdata for SEO
 *
 * @author  WooThemes
 * @package     WooCommerce/Templates
 * @version     1.6.4
 */

if ( ! defined( 'ABSPATH' ) ) exit; // Exit if accessed directly

global $post, $product;
?>
&lt;div itemprop="offers" itemscope itemtype="http://schema.org/Offer">
 
    &lt;p class="price">&lt;?php echo $product->get_price_html(); ?>&lt;/p>
    &lt;meta itemprop="name" content="&lt;?php echo $product->get_name(); ?>" /> 
    &lt;meta itemprop="price" content="&lt;?php echo $product->get_price(); ?>" /> 
    &lt;meta itemprop="priceCurrency" content="&lt;?php echo get_woocommerce_currency(); ?>" />
    &lt;link itemprop="availability" href="http://schema.org/&lt;?php echo $product->is_in_stock() ? 'InStock' : 'OutOfStock'; ?>" />
 
&lt;/div></pre>

### 4. All Done

That&#8217;s all that&#8217;s required to add schema.org markup to individual WooCommerce product pages. Pretty simple.

If you run into any issues or it doesn&#8217;t seem to be working for you, let me know. I&#8217;ve only tested this with two themes, [Vantage][4] and [Virtue][5]. Remember, this only works with well-crafted WordPress themes. Doing this with purchased themes from ThemeForest or other paid theme marketplaces can be significantly more difficult.

Comments are open so let me know if you have any issues, additions, questions, or suggestions.

 [1]: http://schema.org
 [2]: https://longren.io/add-schema-org-markup-to-any-wordpress-theme/
 [3]: http://www.woothemes.com/woocommerce/
 [4]: https://wordpress.org/themes/vantage
 [5]: https://wordpress.org/themes/virtue
 [6]: #