---
author: Sat Naing
title: How to configure AstroPaper theme
slug: how-to-configure-astropaper-theme
featured: true
draft: false
tags:
  - configuration
  - docs
description: How you can make AstroPaper theme absolutely yours.
---
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "[http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd](http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd)">

<html xmlns="[http://www.w3.org/1999/xhtml](http://www.w3.org/1999/xhtml)">

<head>

<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />

<title>Untitled Document</title>

</head>

<body>

<p data-pm-slice="1 1 \[\]">AstroPaper is a highly customizable Astro blog theme. With AstroPaper, you can customize everything according to your personal taste. This article will explain how you can make some customizations easily in the config file.</p>

<h2>Table of contents</h2>

<h2>Configuring SITE</h2>

<p>The important configurations lies in src/config.ts file. Within that file, you'll see the SITE object where you can specify your website's main configurations.</p>

<p>During deveopment, it's okay to leave [SITE.website](http://SITE.website) empty. But in production mode, you should specify your deployed url in [SITE.website](http://SITE.website) option since this will be used for canonical URL, social card URL etc.. which are important for SEO.</p>

<pre>// file: src/config.ts export const SITE = { website: &quot;[https://astro-paper.pages.dev/&quot](https://astro-paper.pages.dev/&quot);, author: &quot;Sat Naing&quot;, desc: &quot;A minimal, responsive and SEO-friendly Astro blog theme.&quot;, title: &quot;AstroPaper&quot;, ogImage: &quot;astropaper-og.jpg&quot;, lightAndDarkMode: true, postPerPage: 3, scheduledPostMargin: 15 _60_ 1000, // 15 minutes }; </pre>

<p>Here are SITE configuration options</p>

<table>

<colgroup>

<col />

<col />

</colgroup>

<tbody>

<tr>

<th colspan="1" rowspan="1"><p>Options</p></th>

<th colspan="1" rowspan="1"><p>Description</p></th>

</tr>

<tr>

<td colspan="1" rowspan="1"><p>website</p></td>

<td colspan="1" rowspan="1"><p>Your deployed website url</p></td>

</tr>

<tr>

<td colspan="1" rowspan="1"><p>author</p></td>

<td colspan="1" rowspan="1"><p>Your name</p></td>

</tr>

<tr>

<td colspan="1" rowspan="1"><p>desc</p></td>

<td colspan="1" rowspan="1"><p>Your site description. Useful for SEO and social media sharing.</p></td>

</tr>

<tr>

<td colspan="1" rowspan="1"><p>title</p></td>

<td colspan="1" rowspan="1"><p>Your site name</p></td>

</tr>

<tr>

<td colspan="1" rowspan="1"><p>ogImage</p></td>

<td colspan="1" rowspan="1"><p>Your default OG image for the site. Useful for social media sharing. OG images can be an external image url or they can be placed under /public directory.</p></td>

</tr>

<tr>

<td colspan="1" rowspan="1"><p>lightAndDarkMode</p></td>

<td colspan="1" rowspan="1"><p>Enable or disable light &amp; dark mode for the website. If disabled, primary color scheme will be used. This option is enabled by default.</p></td>

</tr>

<tr>

<td colspan="1" rowspan="1"><p>postPerPage</p></td>

<td colspan="1" rowspan="1"><p>You can specify how many posts will be displayed in each posts page. (eg: if you set SITE.postPerPage to 3, each page will only show 3 posts per page)</p></td>

</tr>

<tr>

<td colspan="1" rowspan="1"><p>scheduledPostMargin</p></td>

<td colspan="1" rowspan="1"><p>In Production mode, posts with a future pubDatetime will not be visible. However, if a post's pubDatetime is within the next 15 minutes, it will be visible. You can set scheduledPostMargin if you don't like the default 15 minutes margin.</p></td>

</tr>

</tbody>

</table>

<h2>Configuring locale</h2>

<p>You can configure the default locale used for the build (e.g., date format in the post page), and for the rendering in browsers (e.g., date format in the search page)</p>

<pre>// file: src/config.ts export const LOCALE = { lang: &quot;en&quot;, // html lang code. Set this empty and default will be &quot;en&quot; langTag: \[&quot;en-EN&quot;\], // BCP 47 Language Tags. Set this empty \[\] to use the environment default } as const; </pre>

<p>LOCALE.lang will be used as HTML ISO Language code in &lt;html lang=&quot;en&quot;&gt;. If you don't specify this, default fallback will be set to en. LOCALE.langTag is used as <a href="[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Date/toLocaleDateString#locales">datetime](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleDateString#locales">datetime) locale</a>. For this, you can specify an array of locales for fallback languages. Leave LOCALE.langTag empty \[\] to use the environment default at <em>build-</em> and <em>run-time</em>.</p>

<h2>Configuring logo or title</h2>

<p>You can specify site's title or logo image in src/config.ts file.</p>

<p><img src="[https://res.cloudinary.com/noezectz/v1663911318/astro-paper/AstroPaper-logo-config\_goff5l.png](https://res.cloudinary.com/noezectz/v1663911318/astro-paper/AstroPaper-logo-config_goff5l.png)" alt="An arrow pointing at the website logo" /></p>

<pre>// file: src/config.ts export const LOGO\_IMAGE = { enable: false, svg: true, width: 216, height: 46, }; </pre>

<p>If you specify LOGO\_IMAGE.enable =&gt; false, AstroPaper will automatically convert SITE.title to the main site text logo.</p>

<p>If you specify LOGO\_IMAGE.enable =&gt; true, AstroPaper will use the logo image as the site's main logo.</p>

<p>You have to specify logo.png or logo.svg under /public/assets directory. Currently, only svg and png image file formats are supported. (<strong><em>Important!</em></strong> <em>logo name has to be logo.png or logo.svg)</em></p>

<p>If your logo image is png file format, you have to set LOGO\_IMAGE.svg =&gt; false.</p>

<p>It is recommended that you specify width and height of your logo image. You can do that by setting LOGO\_IMAGE.width <em>and</em> LOGO\_IMAGE.height</p>

<h2>Configuring social links</h2>

<p>You can configure your own social links along with its icons.</p>

<p><img src="[https://res.cloudinary.com/noezectz/v1663914759/astro-paper/astro-paper-socials\_tkcjgq.png](https://res.cloudinary.com/noezectz/v1663914759/astro-paper/astro-paper-socials_tkcjgq.png)" alt="An arrow pointing at social link icons" /></p>

<p>Currently 20 social icons are supported. (Github, LinkedIn, Facebook etc.)</p>

<p>You can specify and enable certain social links in hero section and footer. To do this, go to /src/config.ts and then you'll find SOCIALS array of object.</p>

<pre>// file: src/config.ts export const SOCIALS: SocialObjects = \[ { name: &quot;Github&quot;, href: &quot;[https://github.com/satnaing/astro-paper&quot](https://github.com/satnaing/astro-paper&quot);, linkTitle: `${SITE.title} on Github`, active: true, }, { name: &quot;Facebook&quot;, href: &quot;[https://github.com/satnaing/astro-paper&quot](https://github.com/satnaing/astro-paper&quot);, linkTitle: `${SITE.title} on Facebook`, active: true, }, { name: &quot;Instagram&quot;, href: &quot;[https://github.com/satnaing/astro-paper&quot](https://github.com/satnaing/astro-paper&quot);, linkTitle: `${SITE.title} on Instagram`, active: true, }, ... \] </pre>

<p>You have to set specific social link to active: true in order to appear your social links in hero and footer section. Then, you also have to specify your social link in href property.</p>

<p>For instance, if I want to make my Github appear, I'll make it like this.</p>

<pre>export const SOCIALS: SocialObjects = \[ { name: &quot;Github&quot;, href: &quot;[https://github.com/satnaing&quot](https://github.com/satnaing&quot);, // update account link linkTitle: `${SITE.title} on Github`, // this text will appear on hover and VoiceOver active: true, // makre sure to set active to true } ... \] </pre>

<p>Another thing to note is that you can specify the linkTitle in the object. This text will display when hovering on the social icon link. Besides, this will improve accessibility and SEO. AstroPaper provides default link title values; but you can replace them with your own texts.</p>

<p>For example,</p>

<pre>linkTitle: `${SITE.title} on Twitter`, </pre>

<p>to</p>

<pre>linkTitle: `Follow ${SITE.title} on Twitter`; </pre>

<h2>Conclusion</h2>

<p>This is the brief specification of how you can customize this theme. You can customize more if you know some coding. For customizing styles, please read <a href="[https://astro-paper.pages.dev/posts/customizing-astropaper-theme-color-schemes/">this](https://astro-paper.pages.dev/posts/customizing-astropaper-theme-color-schemes/">this) article</a>. Thanks for reading.&#9996;&#55356;&#57339;</p>

</body>

</html>