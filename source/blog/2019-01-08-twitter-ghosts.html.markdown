---
title: "The Haunted Twitter Account"
tweet: "Our twitter account is haunted by ghost followers 👻. We grabbed our mad computer skills and went on a ghost hunt. This is a story on how we got rid of our fake followers. @ThinkAboutConf #thinkabout19"
author_twitter: "@hldrbm"
author: Jakob

---

On Monday the 7th of January it happened: Over night we had more than 300
additional Twitter followers. Sounds cool, right? Well, unfortunately it is not. 

READMORE

We were not praised by sudden fame. All of those 300 new followers were ghost
followers: fake accounts that only exist to increase the reach of another
account. But where did they come from all of a sudden?

## The Short Version

Our account is haunted. Since the 7th of January we had 300 more followers and
since then we get a few new ghost followers every other minute. Just when I
checked this morning there were again over 300 more followers than last
evening. And it is not stopping. As of today (9th of January, we gain fake
accounts as ghost followers every minute).

Because we were annoyed to remove every new ghost follower manually I came up
with this tool that I would like to introduce to you in this article: Meet
[Ghostbuster](https://github.com/hrx-events/ghostbuster) - the friendly
commandline app to automatically delete all those nasty twitter ghost
followers. Running it looks kind of like this:

![A screenshot of a terminal running ghostbuster](/assets/images/blog/twitter-ghosts/terminal.png)

### The Issue

While reach through a lot of followers is usually a desireable thing on
Twitter, having a lot of ghost followers is not. This can have several severe
drawbacks:

1. Credibility: your account can be perceived as one of those shady twitter
citizens who pay money to gain extra followers
2. Ranking: Twitter may detect this behaviour and reduce your visibility
3. Ban: Twitter may even decide to ban your account because they suspect a fraud
scheme

To me personally, the weirdest thing about this situation is that we never
payed anyone to give us hundreds of fake followers. It just popped into
existence out of the blue. If anybody knows how such a thing can happen please
give us a tweet ([@thinkaboutconf](https://twitter.com/thinkaboutconf)) or a
mail ([kontakt@think-about.io](mailto:kontakt@think-about.io)).

### The Solution

I wrote a simple piece of code that utilizes the twitter API to detect ghost
followers and automatically bans them. If you ban a follower, they are removed
from your list of followers and may never follow or contact you again. Quite
drastic, but very efficient against automated fake accounts.

The detection is so far quite simple. It deletes all followers that are either:

1. With less than 10 followers
2. or have at most one post of their own

From the analysis of our ghost followers I could deduce this rule. All those
fake accounts have barely any followers and always just one "welcome" post or
no post at all.

Head over to Github and download
[Ghostbuster](https://github.com/hrx-events/ghostbuster). In order to use it,
you have to enable API access on twitter and create a twitter app. Both are
quite easy to do in a few steps which I will outline here.

## The longer Version

To be able to use the Twitter API, several steps have to be undertaken in order
to gain access.

### 1. Enable Access to Twitter API

Head over to the [Twitter API application
form](https://developer.twitter.com/en/apply) and request access as a
developer. You will have to provide your phone number and a reason why you want
access. I specifically typed there that I encountered many fake followers, and that
I want to use the API to detect and block them automatically.

Twitter will accept the request immediately by sending you an email.

### 2. Create a Twitter App

If you want to interact with the Twitter API you have to do this in the
context of a so called "Twitter App". An app does not have to be a big
application running on phones or in a browser. It is merely a context, in which
you can make calls to the API.

Open the [Twitter App Manager](https://developer.twitter.com/en/apps) and
create a new app by clicking on the **create** button. You can call it whatever
you want. You only have to fill in the field marked as **required**, especially
all those technical URLs can be omitted. As long as your app is not a user
facing one (which is the case here), this is totally fine. After doing so open
the App Settings by clicking on the **details** button beside the app as
outlined in this screenshot:

![A screenshot of the button to create a twitter app](/assets/images/blog/twitter-ghosts/twitter-app-details.png)

Now navigate to the tab "Keys and Tokens", there you will encounter two very
important secret keys. Both keys, the "API Key" and the "API Secret Key" should
be kept very secret. Here is a screenshot how it might look (the keys in the
screenshot are fake ones, for obvious reasons):

![A screenshot of the twitter app secret keys](/assets/images/blog/twitter-ghosts/twitter-app-keys.png)

Keep this tab open for the next step, since you will need both keys for
Ghostbuster. It will use them to create an API token. This API token will then
be used to query and block ghost followers.

### 3. Install Ghostbuster

Installing Ghostbuster is quite easy. Since it is a commandline application,
you will have to install and run it from the commandline. So open up the
terminal and type this

~~~
curl -sSL git.io/ghostbuster |bash
~~~

This will install ghostbuster and make it available for usage.

### 4. Start Ghostbuster

As with the installation, running Ghostbuster requires a terminal. But before
starting it, make sure you are logged into Twitter on your browser with the
account that is haunted by ghost followers. We need this later to verify your
app keys.

Now to start Ghostbuster, fire up your terminal and run:

~~~
ghostbuster
~~~

This will launch Ghostbuster and the first thing it will do is ask you for the
API Key and Secret which we have discovered above at step two.

Paste those keys into your terminal (usually with `[CTRL]+[SHIFT]+[V]` or
`[CMD]+[SHIFT]+[V]` or simply with right click and paste.

After supplying both information a twitter URL as displayed. Please open this
URL in the browser where you are logged into Twitter. After opening this URL, a
button labeled "Authorize App" is displayed. After clicking it the website will
display a PIN code consisting of several numbers. Copy this PIN code, go back
to the terminal and paste it into the waiting Ghostbuster. Now press enter.

Ghostbuster will now start busting ghost followers and blocking them
automatically. It will run indefinitely and look at your newest 100 followers
every five minutes. If it detects a ghost in those 100 followers, they will be
blocked automatically. You can abort it anytime using `[CTRL]+[C]`.

Whenever you are haunted by an army of ghosts that swarm into your account,
just fire up Ghostbuster in your terminal and watch them disappear.

To run it again, simply type `ghostbuster`. Since it stored your apps
credentials, on future runs it will just start hunting without the annoying
questions.

The five-minute break between runs is important, since the Twitter API has a
rate limiter. That means, if you ask too frequently for your own followers,
your API access will be temporarily disabled. Asking for 100 followers every
five minutes is exactly inside their maximum limits, so you should be fine.

## The End

Since the 7th of January, our Twitter Account is bombarded by ghost followers
and we have to run our Ghostbuster continuously to get rid of them. It is a
complete riddle to us where those fake accounts come from but we are happy that
it inspired us to write Ghostbuster and maybe help others to clean their
accounts.

And as mentioned earlier: If anybody knows how such a thing can happen please
give us a tweet ([@thinkaboutconf](https://twitter.com/thinkaboutconf)) or a
mail ([kontakt@think-about.io](mailto:kontakt@think-about.io)).
