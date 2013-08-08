Title: CMS System History

I will provide a short history behind CMS system I am using to publish this web-site (I am saying “CMS” rather than “blog”, because the system is managing all content on this site, not just blog posts).

# Requirements

When it came to setting up this site, I had a few requirements that I needed to be met. These requirements include, in order of importance:

1. Easy writing of articles or blog entries on a tablet or, in a pinch, a smart phone.
2. The ability to write content offline and publish it easily and with minimal hassle when online.
3. The ability to write content on several different devices, depending on what makes the most sense in a given situation.
4. Provide a simple markup language (Markdown, reStructuredText, ASCIIDOC). _Not_ HTML!
5. Be secure, don’t require hand-holding and constant updates. There shouldn’t be a constant need to keep up on new security exploits in order to protect the site from being hacked.
6. Be dead simple and low in overhead when it comes to serving up content.
7. It should be able to deal with low-bandwith, high-latency Internet links fairly gracefully.

# The Options

## WordPress

The obvious choice for blog-centric web-site these days is, of course, WordPress. Almost everybody running a blog uses it. Almost anybody knows how to work with it. There are tons of themes and plugins ready to be installed. Ultimately, you can get your web-site to do anything under the sun using this platform. This _can_ be a good thing.

There’s just one problem – or rather seven. It doesn’t meet even a single one of my requirements.

1. The primary writing platform is clearly a computer. Yes, there are apps for tablets and phones, but they cost money, are buggy or a pain in the rear to use. Maybe even all of the above at once.
2. Writing is meant to be done online, using WordPress’ built-in editor. Trying to do anything else is a hack. Yes, you could write your content in OpenOffice, Word, or any other writing application. To get this content online, though, you still have to log into your WordPress dashboard and copy-paste your content. How do you preserve formatting doing this? You’d have to write in HTML. And how do you deal with off-line editing a blog post and then synching it with the online version?
3. To blog from different devices easily, you’ll have to use WordPress’ online editor. Otherwise, you’ll end up with several offline copies of the same post. Or you have to stick to the device you first created the content on. Also, if you write some posts from one device and some from another, each will have a different subset of your contents stored locally, and none will have it all.
4. In WordPress, you either post in HTML or you use their formatting editor. Neither of which pleases me. HTML tags are too cumbersome and verbose to type. Besides, you have to remember to escape HTML entities such as “&” and type “&amp;” instead. Using the formatting functions of the editor severely limits the flow of writing, as you end up reaching from the keyboard to the mouse to mark text and format it. Yes, there’s a Markdown plugin for WordPress, but that makes the system only more complex, more vulnerable (one more plugin whose potential security holes may affect the site) and slower.
5. WordPress in particular, but also PHP itself, have long been known for a spotty track record regarding security holes. The fact that there’s a database backend does nothing to help matters. It merely opens another attack vector: SQL query injection. Hard to find and fix. Easy to exploit once known.
6. WordPress is not “simple” when it comes to serving up contents. It creates HTML on the fly which requires memory and computing power on the server. The more hits a site receives, the more of a problem this becomes. Adding a Markdown plugin makes matters worse. Of course there are remedies for this (PHP caching and such), but that, again, makes the system only more complex.
7. The WordPress dashboard provides a convenient way of administering the site. That convenience comes with complexity (JavaScript, style sheets, etc.) that make the pages big and that can take a long time to load. I don’t want to be on the other end of a low-bandwidth connection, trying to log in, go to the blog-post creation page and start typing away. Saving your changes as you are typing would be slow, as well. And what if your connection drops right as it is trying to save a post? Will you lose everything you wrote up until that point?

## Other “Standard” Platforms

There are many similar systems one can use out there. There’s Moveable Type, Drupal, and a host of others. They more or less share the same advantages – and draw-backs – that WordPress does.

## Calepin and Scriptogr.am

These two platforms almost provide *exactly* what I am looking for – with one notable exception. Their publishing mechanism, while simple, is not what I would classify as “easy”. After storing your new content in Dropbox, you have to log into your dashboard and hit the “publish” button for your content to go online.

This may be easy enough if you write on your computer most of the time. You can have a browser window already open, compose your blog post in your favourite editor, and hit publish in the browser once you are done. This workflow is not very suited to a tablet or a smartphone. Applications are full screen, having multiple applications (“windows”) open is possible, but not as easy and intuitive as it is on a computer.

However, Scriptogr.am does provide one method of “direct publishing”. The editor Mou can directly trigger a “publish” event for one’s content, without the need to manually log into the web-site and publish from there. The drawbacks are clear:

* One is limited to using Mou if this feature is desired. (Not a severe draw-back. Mou is free and it is an excellent Markdown editor.)
* Much more severely, Mou only runs on OS X. That means you need a Mac to take advantage of this feature. Neither a tablet, nor a smartphone, nor a Windows machine will do.

I want the blog to update as soon as I “publish” content by saving into the corresponding Dropbox folder. I don’t want to have to do anything beyond that. The only exception would be a Mou-like option to trigger publishing of the content directly from the editor. Even then, I prefer not having to do that.

## The Home Grown Solution

So, I set out to slap together a system from pre-existing components. I didn’t want to write anything from scratch. There’s plenty of options to choose from out there already. This is how I ended up with the following concoction.

* Pelican serves as the Content Management System.
* Dropbox serves as the synchronization mechanism.
* Incron serves as the trigger that starts a publishing cycle whenever new content appears.

How all this works is described …

