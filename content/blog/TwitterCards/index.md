---
title: Add Twitter Cards to Blog Tweets
hero_image: "powershellLogosmaller.png"
date: "2018-07-12"
---
<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@The_Scott_Hurst">
<meta name="twitter:creator" content="@The_Scott_Hurst">
<meta name="twitter:title" content="Twitter Cards - Making your blog post stand out.">
<meta name="twitter:description" content="Learning about Twitter Cards - How to make Twitter posts of your blog stand out">
<meta name="twitter:image" content="http://www.hurst.systems\assets\images\BlogPostImages\jekyll_github.png">
</head>
I'm really late to the blog game, and never really did much but lurk on Twitter. So when I started to blog, and then promoted the posts on Twitter, I noticed it was just an ugly URL link. It didn't stand out at all, in fact it was... boring... and this was BEFORE you got to my rambling. So how do all these Tweets end up with such pretty pictures attached to them??

I actually came across the answer to my question by accident.  I was reading about the whole "hosting your blog on GitHub.io" and Jekyll/Ruby thing that all the cool kids are doing these days (I'll write more about this in a later blog post)... (also... I LOVE Jekyll/Ruby/GitHub - so much lost sleep but in a good way) and I stumble across a Theme where the user had embedded a list of his Twitter posts within his blog. I was unable to find his code, but I was able to find more information about how this is accomplished on Twitter's site, on a page called this is from <a class="reference external" href="https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards">About Twitter Cards</a>

Once you've configured the HEAD of your post with the metadata you can test to make sure it works and get a preview of what the card looks like by using the <a class="reference external" href="https://cards-dev.twitter.com/validator">Card Validator</a>


So lets get into this, shall we?

Optimize Tweets with Cards


<h1>About Twitter Cards</h1>
With Twitter Cards, you can attach rich photos, videos and media experiences to Tweets, helping to drive traffic to your website. Simply add a few lines of markup to your webpage, and users who Tweet links to your content will have a “Card” added to the Tweet that’s visible to their followers.


<h3>Drive engagement from your Tweets<a name="drive-engagement-from-your-tweets"></a></h3>
<p>The different Card types each have a beautiful consumption experience built for Twitter’s web and mobile clients:</p>
<ul>
<li><a class="reference external" href="https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/summary-card-with-large-image">Summary Card</a>: Title, description, and thumbnail.</li>
<li><a class="reference external" href="/en/docs/tweets/optimize-with-cards/overview/summary-card-with-large-image.html">Summary Card with Large Image</a>: Similar to the Summary Card, but with a prominently-featured image.</li>
<li><a class="reference external" href="https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/app-card">App Card</a>: A Card with a direct download to a mobile app.</li>
<li><a class="reference external" href="https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/player-card">Player Card</a>: A Card that can display video/audio/media.</li>
</ul>
<p>To learn more about how the Card meta tags and web crawler work, check out the <a href="/cards/getting-started">Getting Started Guide</a>.</p>
<h3>Drive app downloads from your Tweets<a name="drive-app-downloads-from-your-tweets"></a></h3>
<p>In addition to displaying content in a more engaging way, Cards can also drive downloads of mobile apps, and even link directly into installed applications. For more information, see <a class="reference external" href="/cards/mobile">Cards for Mobile Developers</a>.</p>


this is from <a herf="https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards">About Twitter Cards</a> I am just testing the functionality.
