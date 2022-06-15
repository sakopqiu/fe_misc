SEO in actionBackground

We tried to look back upon what we have done in the past and summarized all the best practices into an operationable manual here so that we can re-apply the same theory to future projects, e.g, TTCX.
Note that
- This doc is a practiceable manual rather than an abstract and theoretical one, comprehensive examples will be given along the way, which is different from any SEO tutorial you've read before. 
- What RDs need to do and what PMs need to cooperate with RD will be marked as red bold text.
- There are quite a few search engines in this world(Google, Bing, Baidu, Yandex), but we will focus on Google in this doc for the sake of simplicity. 
The same methodology applies to other web crawlers nonetheless.

This doc will be split into parts:
- SEO Basics refresher, so that we can be on the same page.
- Four pillars of optimization
- How to measure our efforts?

SEO Bascis
SEO in a nutshell
SEO stands for Search Engine Optimization. The goal of SEO is to create a strategy that will increase your ranking position in search engine results. The higher the ranking, the more organic traffic to your site, which ultimately leads to more business for you!

The four pillars of SEO optimization consist of 
- Crawling => how Google bot(spider) explores the whole world-wide-web and ultimately finds your web page
- Indexing => When you page is found, how Google bot associates keyword with your web page and then store that information in its database for future usage. 
- Rendering => This step is optional. 
This process is the hardest to understand even for engineers and the most unexplained one in normal tutorials and we will give concrete examples later. 
In short, most of the web pages are Client Side Rendering(CSR), which makes Google bot very hard to do the indexing the first time it opens up a web page. CSR needs rendering to happen.
Btw, the approach taken by CC is called Server Side Rendering(SSR). SSR does not necessarily need rendering to happen, which sometimes can be optional,  whether search engine crawlers will do rendering for SSR is implementation specific.
- Ranking => Ok, Google has found your webpage and has finished indexing it, but there are so many result pages associated with the keyword you want to target, how to make my web pages stand out? We will discuss it in the Ranking part.
We will go over the four concepts in the next section, before moving on, we will introduce the HTML fundamentals here to get yourself familiarized with the whole technical context.
HTML
In case you are new to HTML, here is a quick guide.
HTML is the acronym for Hypertext Markup Language . The name may sound mysterious but actually it is similar to writing a Lark document or Markdown document.
You write HTML code snippets by following some pre-defined rules and voila, the browser will generate a web page for you.
- Tags: e.g. <a>, <img>, <body>,<meta>, a specific tag has two forms
  - normal tag: <tag>content inside</tag>, content inside of it will be rendered on the web page in some way.  e.g, <h1>some content</h1>, <div>some content2</div>
  - self closing tag: <tag/>, most of which are descriptive tags used to express meta info of the web page. One of the exceptions is the <img/> tag, which we will see an example below.

Tags are organized in an hierarchical way, in the example below
```  
<a> is the parent of <b> and <c/>, <b> and </c> are the children of <a>.
<a> is the grandparent(ancestor) of <d/>.
<d> is the offspring of <a/>.
<a>
  <b>
    <d/>
  </b>
  <c/>
</a>
```
  
- Attributes:  any tag can contain multiple pre-defined attributes, for example
`<img src="some.jpg" alt="alt text if the image is not found" blahblah="aaa"/>`

In this example, src and alt are predefined attributes for the <img> tag while blahblah is not, so it will be simply ignored by the browser.

Let us take a quick look at a sample HTML code snippet to get some feelings.
Don't be overwhelmed by the mysterious code as we will discuss them one-by-one.
```
<html>
  <head>
     <title>Make cake/title>  // only this tag within <head> is visible to end user
     <link rel="canonical" href="https://somesite.com">
     <meta name="description" content="description about making cake"/> 
     <meta propety="og:title" content"make cake"/>
     <meta propety="og:url" content"https://somesite.com"/>
  </head>
  <body>
     <h1>Some site</h1>
     <img src="some-pic.jpg"/>
     <a href="www.google.com">Click me to go to google</a>
     <div>
       Here is the main text about how to make cakes
       blahblah....
       blahblah....
       blahblah....
       blahblah....
       <div>content can be nested</div>
     </div>
     <div>
       Here is the another part of the main text about how to 
       blahblah....
       blahblah....
       blahblah....
       blahblah....
       <div>content can be nested</div>
     </div>
  </body>
</html>
```

HTML provides a huge amount of Tags and Attributes out of the box but we will only pay attention to the following ones which are pertinent to SEO optimization.
```    
<html>
The root container of the whole web page.
<body>
The container tag which holds all elements that are visible to end users.
The tags below are all children under <body>
<a>
<a> creates a hyperlink. 
For example, the below code snippet will render a hyperlink whose text is "google" and the user will be taken to "www.google.com" when clicking it.
<a href="www.google.com">google</a>
</html>
  ```

`<h1>`
Search engine regard the contents inside <h1> as the theme or main topic of the web page, so normally we need to put the desired search text in this element.
For example, if the current web page discusses "Delicios cake" and your desired search key word is "how to use make Delicious cake" , then PM needs to provide copies which contain this information. 
However, the content inside the <h1> tag should be natural and non-contrived, so how to coin the right phrase or organize the appropriate sentence is an art to be deeply considered.
UI wise, <h1> is rendered as magnified text by default but we can use CSS to change its look-and-feel, so its appearance does not matter from Google's perspective.
Q: I have also seen <h2>,<h3> all the way to <h6> . Are they also important?
A: <h1> is the most important one for Google bot, while other <hx> tags are useful for it to understand the structure of your page, check this for more info.

`<img>`
This element  simply renders an image on the web page. src refers to the location where the image is located and the content in alt will be rendered only if the image is not found(AKA 404).
`<img src="some.jpg" alt="alternative text"/>`

From google's perspective, alt contains the semantic content of the image. For example, if the image's content is the Avatar of the famous cake shop "Super Cake", you can specify that information in alt for Google to know.
`<img src="avatar-4.jpg" alt="alt"/>`

PMs need to give alt for all images on SEO-related web pages. 

<div>
<div> element is the most ominipotent tag in the HTML world since it can contain any visible content.
That being said, <div> has no semantics since it can be used to show anything: the header, footer, sidbar, or even the main paragraph of the web page.
When HTML5 specification came into play, it is stipulated that <div> elements be replaced by semantics tags such as <header>, <footer>, <section>, <aside>, etc for search engines to understand your web page better. So RDs should pay more attention to this part when writing code.

`<head>`
It includes the meta info of that web page, all tags within <head/> are invisible to end users but include meta info of the page useful for Google to understand the page.
The tags below are all children tags under `<head>`
  
`<title>`
`<title>` is as important as <h1/> as it influences ranking significantly.
This tag includes the text which can be shown on the tab. 

 And it is also useful when displaying results in google's SERP.

`<link>`
This tag is a versatile one. 
It can be used to import CSS files in most cases but in SEO's realm, it can be used to de-duplicate repetitive pages.
// www.a.com/id=1 and www.a.com/name=shoes targets the same destination
// and we want to make id=1 as canonical
// insert the code snippet below in your web page.

`<link rel="canonical" href="www.a.com/id=1" />`

For example, if you have different urls for the same web page, Google regard the two links as distinct and thus the rating for each page is cut down by half.  On the end-users' end, they will see two search results showing the same title and same description, which is confusing and redundant.
This task is done by RD and is transparent to end users.
```
<meta>
It contains the meta info of the web page, we will only go over  SEO-related properties below.
- property = description
<meta property="description" content="something you will see in SERP" />
```

The description is actually what you see on google's SERP. Its content should be succint(50 to 60 characters) while appealing, since it determines whether the user will click the link to your site when seeing it on the SERP.
- property=keywords
`<meta property="keyword" content="how to make cake in shanghai" />`

This property is the most abused and wrongly-used one. 
The original purpose of the property, as the name suggests, is to correlate the keyword with the web pages. Nowadays, the search engine indexes web pages based on its own algorithm as described below, but declaring the keyword property seems to be more direct and intuitive.
However, many malicious websites took advantage of this property and tried to fool search engines by providing completely irrelevant content. 
For example, World Cup 2002 was the most searched keyword on Google at the moment and a candy store wanted to promote its candies. It could have gained traffic from google by making "keywords" property as "World Cup 2002" while the real content was the introduction of its lollipops.
As of 2009, Google opted out of using this property and many other search engines did the same thing. 
Yandex(The Russian Search Engine) still takes a look at this property as a reference but its priority is very low.
The usage of this property is discouraged.

- `property="og:xxx"`
OpenGraph Tags(og for short)
The Open Graph protocol enables any web page to become a rich object in a social graph. For instance, this is used on Facebook to allow any web page to have the same functionality as any other object on Facebook.
The excerpt above seems a little bit abstract, see the self-descriptive picture below

I assume you've understood everything, and for each web page, PMs should provide rds with
```
- og:image
- og:url
- og:title
- og:url
```  
Note that Open Graph tags are not used to improve SEO, but rather a way to provide the user with a more user friendly look&feel when forwarding or retweeting on social media network.
CSS
As described above, all tags under <head/> are invisible and all tags under <body/> are visible, the visible tags have default UI style according to the HTML specification.
The default styles are only sufficient for prototyping, and when it comes to creating a fancier web page, we need to use CSS(Cascading style sheet).
For example, the default style for any content inside <div> is 16px+black+system default font, while applying the CSS rule below will make it look differently.
```
 <html>
  <style>
     div {
       color: blue;
       font-size: 24px;
       font-family: some-cool-font;
     }
  </style>
  <body>
    <div>Hello world</div>
  </body>
</html>
```
  
CSS can be declared in two ways
- Inserting code between the <style> tag, as shown above.
- Writing rules in a separate file and referencing it as shown below. 
RD prefers this form in most cases.
```  
// a.html
<html>
  <link rel="stylesheet" href="some.css"/>
  <body>
    <div>Hello world</div>
  </body>
</html>

// some.css
 div {
       color: blue;
       font-size: 24px;
       font-family: some-cool-font;
  }
```
That is all you need to know about CSS.

Javascript
HTML content is static and plain, CSS gives its more colorful and fancier look&feel.
Javascript is used to give it more dynamic behavior and enable user-interaction.
We can use Javascript to dynamically add new contents, edit existing content or even remove contents from the HTML page.
```  
<html>
  <body>
    <div>Hello world</div>
  </body>
  <script>
     const cc = document.createElement("div");
     cc.innerHTML = "make cake";
     document.body.appendChild(cc);
  </script>
</html>

The above code snippet will finally render the below HTML,  and the red part is added by Javascript.
<html>
  <body>
    <div>Hello world</div>
    <div>Make cake</div>
  </body>
  <script>
     const cc = document.createElement("div");
     cc.innerHTML = "make cake;
     document.body.appendChild(cc);
  </script>
</html>
```
Javascript can be declared in two ways
- Inserting code between the <script> tag, as shown above.
- Writing code in a separate file and referencing it as shown below.
RD prefers this form in most cases.
// this is the a.html
```  
<html>
  <body>
    <div>Hello world</div>
  </body>
  <script src="some.js"></script>
</html>

// this is some.js
const cc = document.createElement("div");
cc.innerHTML = "make cake";
document.body.appendChild(cc);
```
That is all you need to know about Javascript.

CSR
CSR refers to Client Side Rendering. 
This is the modern way of creating a dynamic web page and is adopted by many companies.
```  
<html>
  <head>
    ... contents are omiited for brevity
  </head>
  <body>
     <script src="dynamic.js"></script>
  </body>
</html>
```
  
You might have noticed that the HTML above is very concise and looks very differently from the full example where <body> contains a lot of HTML tags.
The sole dynamic.js actually does the heavy lifting under the hood
- Create tags dynamically to create the structure of the page.
- Apply CSS effect dynamically.
- Download external resources such as images and fonts.
You may have heard about the famous frontend framework like React, Vue or Angular.
No matter which framework your frontend team uses, the final product is one or multiple Javascript files that render the web page dynamically.

As an example, below is the project list page of TTCX.
You can see that the web page is really contentful while the initial HTML content returned by the server is surprisingly simple. The javascript files actually do the heavy lifting to render the ultimate page.


Q: Why do we call it Client Side Rendering?
A:  The rendering logic is contained in the Javascript files . Once the browser finishes downloading the Javascript file, it executes the code inside Javascript files on the clients' end to render the final page. 

Q: I don't see anything bad about it, why SSR?
A: The content returned by the server includes almost nothing renderable, the browser will make other network requests to 
- get the Javascript files in the initial content, which usually takes more than 1 second.
- After JS file is downloaded, execute code logic to render the web page(we call this rehyration), which usually takes 0.5 seconds for the first screen.
So most of the time the CSR solution will end up having users see a blank page for more than 1.5 seconds.
Another downside of it is that from Google bot's perspective, the initial content contains marginal information and there is little point in indexing this page. 
All these downsides can be perfectly solved by SSR.
SSR
As its name suggests, SSR renders the page on the server side and the initial content of the web page actually contains the whole HTML content.
The user will see the first screen in a flash(no white screen) and Google bot will index the web page happily.
Below is the initial content returned by the server for the home page of CC.


Q: SSR is so good, why not use it everywhere?
A: All good things come with a price, the maintenance cost of SSR pages is much higher than CSR ones. 
And SSR makes servers very stressful since all web pages should be pre-rendered by server while CSR disperses computational efforts to the users' browser.

Q: When do we use SSR over CSR and vice versa?
A: 
For SSR 
- If the specific page needs organic traffic from Google's SERP
- If the content of the page is mostly static.
- If you want to prevent users from seeing a blank page for a long time.
- If the website is content-oriented, e.g. CMS systems or Methodology platforms.
For CSR
- If the first-screen time is not the key metric
- If the content of the page is distinct for each user. 
- If the content behind the page needs authentication and authorization, Google Bot does not carry any user information.
- If the content is mostly dynamic, dispersing stresses on the clients' end will be more suitable.

Q: I see javascript files in SSR's server response, but I don't think they are necessary?
A: You might argue that since the full HTML content is returned by SSR's server, the Javascript files inside it seems redundant.
Actually, for SSR pages, most of the code logic happens on the server side while some code logic can only be executed on the client side.
Another reason is that Javascript files also registers event handlers on the fly, without which the users cannot interact with the web page.

Q: Well, what shall we do for TTCX?
A: The new home page as well as the partner profile related pages(Partner list page, Partner Detail page) will be SSR pages. In that sense, in the near future, those pages will be searchable on Google.
Other pages in TTCX will be using CSR and should not be searchable on Google. For example, you will not want the project list page or project detail page for a specific advertiser to show up on Google's SERP.

Q: Any recommended frameworks?
A: Next.js and Gatsby for React and Nuxt.js for Vue.
I have written a doc about Next.js and its evolution history here.

URL dissection
You may have heard about the jargon protocol, domain, path and parameters, they are self-explainable through an easy example.
Consider the urls:
```  
http://aa.com?a=123
https://www.bb.com/
https://cc.com/a/b/c?a=123&b=222
Protocol
1st: http
2nd: https
3rd: https
Note that all regular sites are https. 
Domain
1st: http://aa.com
2nd: https://www.bb.com
3rd: https://cc.com
Path
1st: / (browsers append the trailing backslash automatically for us)
2nd: /
3rd: /a/b/c
Parameters(or QueryString)
1st: ?a=123
2nd: empty string
3rd: ?a=123&b=222
 ```
  
Other Jargons
Outbound links
<a/> links in a web page are called outbound links
Inbound links
If pageA has an <a/> link pointing to pageB, we would say pageA has an outbound link to pageB
and pageB has an inbound link from pageA.
Backlinks
Another way to express inbound links.
User agent
It is the software which is used to surf the internet.
Chrome, Safari, Firefox are all user agents.
Google bot is also a user agent.
However, Google bot is actually a background program rather than a browser with user interface . Such user agents always refer to "headless browsers" or "headless user agent"
Four Pillars of Optimization
As we discussed briefly above, the four pillars of SEO optimizations are crawling, indexing, rendering and ranking, details will be delved into in this section.
Note that the real mechanisms of each search engine are tremendously complex and distinct from each other, what we describe below is simply the general idea.
Crawling
Search engines have a list of initial web pages(the most notable web pages known to all internet surfers) as its base for crawling . Let us call it the crawling queue. 
The search engine iterates the crawling queue, takes the next task out of the queue, downloads its content and looks for <a/> tags within it. Since the href attribute of the <a/> tag refers to the url of the link, it adds the href attribute as a new task to the crawling queue. It will also index that page to its database, indexing will be discussed below.
Think of the whole process in an recursive way and it is not hard to imagine that at the end of the day almost the whole world-wide-web will be crawled by the search engine, and that is why we call it a spider. The spider starts from a very small web and finally manages to weave a giant web holding the whole www world.
Robots.txt
During the process of crawling, we may come across some pages that are not intended to be indexed. For example, the login/signup page, the pages that are only accessible after logging-in or require specific security permissions.
To that end, we can declare the restrictions in a robots.txt file to specify which paths under which circumstances should not be crawled.
Google stipulates that robots.txt be created on a per domain basis, which means:
https://some.com=>https://some.com/robots.txt.

Before google starts crawling a specific web page, it downloads the robots.txt file first and looks into it to make sure the path is crawlable.
Suppose below is the content of  https://some.com/robots.txt.
When the user-agent is Google bot, the web page https://some.com/signup is not crawlable.
When the user-agent is Baidu bot, the whole domain is not crawable.
User-agent: Googlebot
Disallow: /signup/

User-agent: Baidubot
Disallow: *

RDs are responsible for creating robots.txt.
noindex meta tag
<meta name="robots" content="noindex, nofollow" />

RDs should be responsible for creating the meta tag.
Sitemap
As its name suggests, sitemap contains the internal structure of a specific domain.
Instead of having google find the specific web page using its <a/> link recursive strategy, we are telling google explicitly what pages we have.
The syntax of the sitemap(XML file) is out of the scope of this doc and RDs should pay more attention to that.
The rough layout looks like
```  
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:news="http://www.google.com/schemas/sitemap-news/0.9"
        xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:image="http://www.google.com/schemas/sitemap-image/1.1"
        xmlns:video="http://www.google.com/schemas/sitemap-video/1.1">
    <url>
        <loc>https://some.com/page1</loc>
        <changefreq>daily</changefreq>
        <priority>0.9</priority>
    </url>
    <url>
        <loc>https://some.com/page12</loc>
        <changefreq>monthly</changefreq>
        <priority>0.9</priority>
    </url>
</urlset>
```

The sitemap file provides the search engine with information about all the crawable paths under that domain as well as the priority and frequency for that path.
Q: What is priority and frequency?
A: There are trillions and billions of web pages in this world, so web crawlers need to focus its relatively scarce computational resources onto the most important ones. 
In that sense, Google bot does not guarantee to crawl your page in a short time.
If you want to give more priority to some pages of a website over the others, giving the appropriate priority and update frequency is a good shot.

Q: How to let google know your sitemap configurations?
A: Well, I can think of 3 ways
- You can specify it in robots.txt
User-agent: Googlebot
Disallow: /nogooglebot/

User-agent: *
Allow: /

Sitemap: http://www.example.com/sitemap.xml

- You can configure it in Google Search Console, we will discuss Google search console in the later part.

- You can configure it in AHref, we will discuss AHref in the later part.


Q: It seems that sitemap is redundant?
A: According to the recursive strategy described above, you might argue that any web page can be finally found by Google bot so that sitemap is not necessary.
While we still need sitemap for two reasons
- Some of the newly created pages might not have any links pointing to them, which results in not being found by Google.
For example, suppose we have a partner list page(/partner-list) which only shows 20 partners containing the link to the partner detail page(/partner?id=1, /partner?id=2) by default. Apparently 20 links will be added to crawl queue by Google bot.
And if you want to view more partners, you have to click the "view more" button at the bottom of the page to view more partners. The key thing is that clicking the button is human interaction and Google bot will not bother to do this and thus the links of these partners are unknown to Google bot.
- Sitemap is a more explicit way to tell google what we have, which makes newly created pages discoverable more quickly.

Q: How to create sitemap for your website?
A: Whenever you add a new path to your code base, you have to manually add the declaration in sitemap. However, this process is error-prone since you might forget to add configurations for some paths.
  
Indexing
When google bot finds your web page, the HTML content will be scanned, and the bot tries to extract useful information from that web page and tries to create an inverted index in its database.
This process is called indexing.
Let us take a quick look at the html files below, suppose a.html is on the left side and b.html on the right.

Google scans both files and creates something like this,
```  
Keyword
Found in
Latest Iphone
a.html
b.html
Iphone 10000
b.html
Apple
b.html
How much latest iphone
a.html
```
  
Just imagine how big this table can become after google bot crawls most of the web pages in this world.
The keyword "Iphone 10000" might point to millions of web pages, and that is why SEO optimization is so important to make your webpage not inundated by your peers.

Here are a few noteworthy points when Google scans your page :
- Stopwords(a, the, etc) are ignored.
- Variant of a specific word is normalized, e.g, plurals, conjugations might be treated as the normal form of the word. 
- How google separates English words or phrases is out of the scope of this doc, so the table above might not be accurate, but you get the idea.
- Synonymous expressions are normalized in some way so that "How much" and "What is the price of" can be converted into a consistent expression in Google and, in a result, they are somewhat equivalent internally.
- The keyword Iphone appears in many places in the HTML above and Google gives a different weight to each area. <title> and <h1> has higher priorities. 

Rendering
First thing first, Rendering is optional.  It is only needed for CSR pages.
If you still recall CSR and SSR, the initial content of the CSR is merely Javascript files declarations and the content is almost empty while SSR returns everything.
For the dumb search engines, since the CSR pages are almost empty and non-exploitable, there is little point in indexing that page.
When it comes to Google bot, a smart one, it will try to 
- spawn a headless browser in the background
- download Javascript files
- execute js files' code logic to rehydrate
- Wait for some time for the web page to settle down
- Index the web page based on the current html content
The above process is called "Rendering".
Apparently, rendering for CSR pages needs way more effort than SSR pages, and Google bot does not guarantee to do rendering in time, resulting in bad indexing effect.
If you put your feet in Google bots' shoes, you will also love the SSR pages since it saves you a lot of energy.
Ranking
Ranking is the most difficult and mysterious part of SEO.
If you are doing SEO seriously, what will be your ultimate goal?
Needless to say, you want to see your website rank #1 after inputting all desired keywords in Google search bar.
We can make our rank get higher position from several aspects.
The below aspects are ordered by importance(Descending).
- PageRank
- Contentful web page.
- Bid for long-tail keywords
- Don't fool Google
- Better Web vital metrics.
- Mobile friendly

PageRank
How does Google rank pages that are associated with a specific keyword, say, "How to make delicious cake"?
It uses Page Ranking. 
Simply put, if there are 4 web pages in this world, A,B,C,D, all pages are given an initial rank as 1/4.
Page B has 3 outbound links and one of which points to PageA.
Page C has 2 outbound links and one of which points to PageA.
Page D has 1 outbound link and one of which points to PageA.
PR(A) can be deduced as: (Damping factor is omitted for brevity)

PR(A) = 0.25 / 3 + 0.25 / 2 + 0.25 after the first iteration.
The same formula is also applied to the rest of the pages for each iteration.
The iteration will be executed many times until(or relationship)
- The PageRank for all pages does not fluctuate over a pre-defined threshold
- The iterations have been executed for N(predefined) times.

It can be easily deduced that
- The more inbound links a specific page receives, the more PageRank it gains
- The quality of the inbound link is important since "PageRank" is transitive.
If a web page has a lot of inbound links but all of them are from web pages which have very low PageRank, the final PageRank for this web page will still not be satisfactory.
- The average outbound weight of a specific page is divided by the number of its outbound links.
For example, if pageA's PageRank is super high.
If it only has 1 outbound link, its sole downstream web page will receive the full weight of it, which is very good for its own PageRank.
If it has 100 outbound links,  then its downstream web pages will only receive 1/100 of its weight, offsetting the effect brought by the super high PageRank from pageA.
As a result, 
- PMs need to talk to the PSO team and also GBM team to add high quality inbound links to CC and TTCX. High quality here means we need inbound links from websites which already receive high traffic or have a good reputation in the industry such as BBC, Facebook, Twitter, etc. 
- We can also have social media influencer help us promote our website in his/her tweets.
- We can also try to add a new entry in Wikipedia since its weight is very high.
- Internal links are also important, RDs should make sure internal connectivity is good for their own website. For example, make sure all internal links are connected in some way so that there is no "isolated island".
In addition, Google will also give higher page ranks according to the following metrics
  - CTR on the SERP, the more click a link gets, the higher ranking it will have in the future
  - If a link is visited by the same user repeatedly
  - Brand effect, inbound links from mass media such as Twitter and Facebook.
  - Paid ads, which is out of the scope of this doc.

Contentful Web Page
We have talked about this topic a lot in the prior paragraphs.
We will simply give summrization here.
- Be sure to declare all the useful meta info in the <header/> tag, we created a React Component in our Next.js project, just for your reference. Need RD's attention.
```  
import Head from 'next/head';
import React from 'react';

export interface CommonSeoHeadProps {
  keywords: string;
  title: string;
  desc: string;
  canonicalUrl;
  ogUrl: string;
  ogImage?: string;
}

export default function CommonSeoHead(props: CommonSeoHeadProps) {
  const { keywords, title, desc, canonicalUrl, ogUrl, ogImage } = props;
  return (
    <Head>
      <title>{title}</title>
      <link rel="canonical" href={canonicalUrl} />
      <meta property="title" content={title} />
      <meta property="description" content={desc} />
      <meta property="keywords" content={keywords} />
      {ogImage && <meta property="og:image" content={ogImage} />}
      <meta property="og:type" content="website" />
      <meta property="og:title" content={title} />
      <meta property="og:description" content={desc} />
      <meta property="og:url" content={ogUrl} />
      <meta name="twitter:title" content={title} />
      <meta name="twitter:description" content={desc} />
      <meta name="twitter:url" content={ogUrl} />
    </Head>
  );
}

- For any pages that do not want to be crawled by Google bot, use this one. Need RD's attention.
import Head from 'next/head';
import React from 'react';

export interface CommonSeoNoIndexHeadProps {
  title: string;
}

export default function CommonSeoNoIndexHead(props: CommonSeoNoIndexHeadProps) {
  const { title } = props;
  return (
    <Head>
      <title>{title}</title>
      <meta name="robots" content="noindex, nofollow" />
    </Head>
  );
}
```
  
- Be sure to have 1 <h1/> for each web page. Need RD's attention but PM should give the copy.
- Try your best to give each <img/> an alt property. Need RD's attention but PM should give the copy.
- <hx> tags help Google bot understand the structure of your web page. Need RD's attention.
- Try your best to use semantic tags like <header>, <footer/>, <article> instead of <div/>. Need RD's attention.
- Try to only talk about one topic for each web page and be sure to provide high quality content.
Need PMs to talk to the PSO team or GBM team to provide and supervise the content.
- Although the latest algorithm of Google Bot supports Passage Ranking, which is more friendly to articles containing several topics, it is out of the scope of our discussion since most of our articles only deal with one topic. 

Bid for long-tail keywords
If you set the desired keyword to be "declicous cake", the concept is way too vague and there are too many competitors out there.
Be more specific about your keywords.
In practice, specify as concrete as possible in your <title/> and <h1/>
For example, "Delicious cake in Changning District".

Don't Fool Google
Never ever try to fool Google otherwise your web page might get eradicated from Google's index!
Avoid the following techniques:
- Automatically generated content
- Participating in link schemes
- Creating pages with little or no original content
- Cloaking
- Sneaky redirects
- Hidden text or links
- Doorway pages
- Scraped content
- Participating in affiliate programs without adding sufficient value
- Loading pages with irrelevant keywords
- Creating pages with malicious behavior, such as phishing or installing viruses, trojans, or other badware
- Abusing structured data markup
- Sending automated queries to Google 
Simply put, write yourq copies and css code honestly. The end user should see what you intend to show them.

Better Web Vitals
Web vitals is a broad topic and I've covered this topic comprehensively from RD's perspective in another article. RD should pay more attention to this part.
Briefly speaking,  Web Vitals is an initiative created by Google to provide unified guidance and metrics to measure end-user page experience on the web.
Core Web Vitals is a subset of Web Vitals, and currently consists of three metrics that measure loading, interactivity, and visual stability. These metrics are Largest Contentful Paint (LCP), First Input Delay (FID), and Cumulative Layout Shift (CLS).
Achieving a great score in these three metrics will create a smoother website experience for your user and also will impact its search engine ranking as Google starts to use Core Web Vitals as a ranking factor for their search algorithm. Poor vitals can have an impact on your web traffic and business.
In order to achieve better web vital metrics, RDs should optimize code logic to
- Make first-screen as fast as possible by generating smaller js bundles by using treeshaking, on-demand dynamic import and minification.
- SSR always comes with a naturally faster LCP and lower CLS.
- Serve resource files(js, img, font, css) on the CDN.
- Adopt the usage of 
  - DNS prefetch
  - TCP preconnect
  - Resource preload
  These optimizations are naturally provided by Next.js.

- Optimize images
  - Compress images appropriately
  - Serve different images for different devices, for example, show images with low definitions for mobile devices while high definitions for PC devices.
  - Only show images when they are about to come into the viewport. (IntersectionObserver can be used).
  - Next.js's image component could be a good try.
- Arrange the order of the resource files
  - CSS links should always be at top of the page, followed by Font files declaration so that LCP can be faster and CLS can be alleviated.
  - Javascript files should be at the bottom of the page so that DOM parsing is not blocked.
  - Make Javascript files async/defer if they are not related to rendering.
- Refrain from using window.onunload and window.beforeunload since it will disable BFC.

Mobile friendly
Google bot spawns two user agents for a specific web page, one for PC and one for mobile.
In that sense, your web page will get a higher page rank if responsive design is applied.
Most of the pages in CC are mobile friendly.
The home page of TTCX is not mobile friendly.
RDs and PMs should foresee the tradeoff of mobile-first development for longer and harder development experience.
Nice to have
Google provides the "search appearance" feature so that the user can be presented with a fancier search result. 
This feature is nice to have and we plan to apply these techniques across the span of next year as p2 tasks.


How to measure our efforts
This part is WIP.
Google search console(GSC)
GSC a tool provided by Google to help us know
SERP results
- Total impressions, higher impressions we are doing a good job in SEO.
- Total clicks,, higher clicks means that the description is enticing and users are willing to click on it.
- CTR = Total clicks / Total impressions, higher CTR means that the description is enticing and users are willing to click on it.
- Average position: Average position refers to the average position of your website in search results (calculated by the system using the highest position whenever your website appears in search results). 

One thing to notice is that the average position is not very ideal, this is a little bit counter-intuitive.
The reason for that is we are feeding Google a very large sitemap recently, so the number of keywords associated with Creatice Center has also exploded. 
Some of the keywords are not so that important but did significantly affect the average position metric. We will look into this issue later to see how we can filter out the less relevant ones.

Below are the most exhibited pages(ordered by desc).

Coverage
GSC tell us 
- how many pages are indexed by it 
- how many pages are provided by sitemap but not indexed and the reason for that
- How many pages are deemed error pages and why.


Note that the data above is collected on Dec 14th, which is outdated.
We have fixed some of the issues already but are still waiting for Google to do a re-indexing.

Web site experience
How well our web page is performing from Google's perspective.
Web vital is a core metrics here . We are not doing a very good job for CC and we will fix issues one by one according to its suggestions.


AHref
AHref is a super cool tool where you can see more metrics and even run audits for your web site.
We are using it along with GSC to track down potential issues and tackle them one by one.
Actually, there are so many useful tools that you need to figure out the usage by playing with it on your own.

The auditing feature of it provides a score and suggestions every time we run it.
We are fixing our code logic according to the suggestions and we are seeing steady improvements in the past few months.

Only care about the most desired Keywords
Since there are so many keywords that can be associated with our website, we have to define the most desired ones and make sure the search result position ranks #1~#3.
AHref has a feature listing all the keywords and their position in SERP


