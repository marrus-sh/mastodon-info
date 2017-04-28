---
layout   : "post"
title    : "Everything You Need to Know About Mastodon's New Privacy Settings"
lede     : "In version 1.3 of the Mastodon software, the Mastodon development team made changes to how post privacy settings work&mdash;particularly, with respect to the `private` post setting. In this post, we'll take an in-depth look at Mastodon's privacy features, and answer a few common questions about the change."
date     : "2015-04-27 18:50:00 -0800"
author   : "ALLIE \u2764 HART"
tags     : "privacy"
---

In [version 1.3](https://github.com/tootsuite/mastodon/releases/tag/v1.3) of the Mastodon software, the Mastodon development team [made changes](https://github.com/tootsuite/mastodon/pull/2111) to how post privacy settings work&mdash;particularly, with respect to the `private` post setting.
<b>In this post, we'll take an in-depth look at Mastodon's privacy features, and answer a few common questions about the change.</b>

###  Okay, so, give me a recap. How do Mastodon's privacy settings work?

Mastodon has four privacy settings.
These are:

<dl>
<dt><code>public</code></dt>
<dd>Your post can be seen or reblogged by anybody, and <em>will</em> display on the public timelines</dd>
<dt><code>unlisted</code></dt>
<dd>Your post can be seen or reblogged by anybody, but <em>won't</em> display on the public timelines</dd>
<dt><code>private</code></dt>
<dd>Your post can only be seen by people who follow you (or anyone mentioned in the post), and can't be reblogged</dd>
<dt><code>direct</code></dt>
<dd>Your post can only be seen by people who are mentioned directly in the post</dd>
</dl>

Something you may not know about Mastodon's privacy settings is that they are __recommendations, not demands.__
This means that it is up to each individual server whether or not it chooses to enforce them.
For example, you may mark your post with `unlisted`, which indicates that servers *shouldn't* display the post on their global timelines, but servers which don't implement the `unlisted` privacy setting still can (and do).

It is important to note that regardless of your post's privacy settings, server administrators can read every post you send out.
You should only ever post personal or confidential information on instances whose administrators you trust.

###  Wait, so you're telling me that my “private posts” weren't really all that private??

Sort of.
Mastodon can't force a server to respect its privacy settings, but it *can* control which servers have access to its posts.
Before the 1.3 update, Mastodon servers avoided the problem of other servers not respecting their privacy settings by simply *not sharing their private posts*.

An exception to this is that Mastodon servers would always share their posts with any users mentioned in the body of the post.
You may have seen this warning pop up when you were about to make a private post mentioning someone else:

<figure>
<img alt="Your private status will be delivered to mentioned users on icosahedron.website. Do you trust that server? Post privacy only works on Mastodon instances. If icosahedron.website is not a Mastodon instance, there will be no indiciation that your post is private, and it may be boosted or otherwise made visible to unintended recipients." src="/media/2015-04-27-are-you-sure.png">
</figure>

This lengthy explanation is Mastodon's complicated way of saying <q>We have no control what happens to this post once it leaves our servers.</q>

###  So what changed?

Not sharing private posts with other servers worked back when most Mastodon users were all on [`mastodon.social`](https://mastodon.social), but now that there are [over 1000 Mastodon instances,](https://instances.mastodon.xyz/) most users have followers on other servers that they may want to see their private posts.
In the 1.3 update, Mastodon now will share your private posts __with every server that follows you__, regardless of whether or not that server supports privacy settings.

The name of “private posts” has also changed to “followers-only” in the user interface to indicate that these posts are no longer truly private.

###  This sounds like a bad idea.

It might be.
But the 1.3 update also introduces new features to allow you more control over who follows you and has access to your posts.
The new “Authorized Followers” section in your user settings can be used to automatically block users from following you for servers that you're not sure that you can trust.
There are a few important things to note about this feature:

1.  This will remove any followers from the instances you select, but it will also make you unfollow anyone on those same instances.
    This is because this feature actually works by blocking and then unblocking all of the users on the instances you provide.

2.  If your account isn't locked, there is nothing to stop the users removed by this feature from immediately re-following you and regaining access to your posts.

###  This still sounds like a bad idea.

If you're really not comfortable with this change, you should __petition your instance's administrator__ to hold off on the update until better features are in place.
(Of course, this means you will also miss out on any other features which Mastodon 1.3 provides.)

There are a number of proposed changes which will make this feature function better in the future:

<dl>
<dt><a href="https://github.com/tootsuite/mastodon/issues/712">Letting users opt out of the new behavior</a></dt>
<dd>It was proposed that users should be allowed to opt in or out of this new behavior through user settings, although at the moment this hasn't been implemented.</dd>
<dt><a href="https://github.com/tootsuite/mastodon/issues/423">Instance whitelisting</a></dt>
<dd>If Mastodon allowed users to whitelist only select instances into seeing their posts, they could limit followers to only those instances that they knew supported Mastodon's privacy settings <em>without</em> locking their account. However, users from other instances still wouldn't be able to see their posts.</dd>
<dt><a href="https://github.com/tootsuite/mastodon/issues/422">Supporting lists</a></dt>
<dd>Instead of making private posts that are sent to all of your followers, Mastodon lists would allow you to send posts only to the subset that you knew would respect your privacy.</dd>
<dt><a href="https://github.com/tootsuite/mastodon/issues/669">Asking instances before sharing private posts</a></dt>
<dd><p>Right now, Mastodon has no way of knowing if an instance supports its privacy settings beforehand or not. If instances communicated this information, then Mastodon could choose to only share private posts with those instances that promised to respect them. (Of course, there would be no way of ensuring that an instance fulfilled this promise, but instances which didn't would quickly find themselves being blocked.)</p></dd>
</dl>

Communicating to the development staff that these features are important to you is the best way to ensure they are made priorities and quickly implemented.
The current project manager for Mastodon is [`@maloki@mastodon.social`](https://mastodon.social/@maloki), and you can (respectfully!) contact her with any questions you have about these new features.
