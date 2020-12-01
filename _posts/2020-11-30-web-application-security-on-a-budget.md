---
layout:       post
title:        Web Application Security on a Budget
description:  Tips for running secured web application for a small business.
date:         2020-11-30 23:54:23
image:        /images/2020-11-30-img_0006_20130131_the_news_bangkok.png
categories:   information security infosec web applications
---
[![The News - Suvarnabhumi Airport, Bangkok](/images/2020-11-30-img_0006_20130131_the_news_bangkok.png)](https://www.flickr.com/photos/kesara_rathnayake/8515398094/)

For a small business, information security mishap can be fatal blow to the
business. When you don't have budget do annual penetration tests and keep a
dedicated set of engineers to maintain and look after your systems it might be
tough task to provide a secure online service to your customers.

In this blog post, I'm providing some tips on keeping your online services
secured with on a very low budget.

## Passwords
First things first use a [password manager](https://www.cert.govt.nz/individuals/guides/getting-started-with-cyber-security/keep-your-data-safe-with-a-password-manager/) to keep your passwords for different services like emails,
domain name, accounting software etc.

Make sure that you use [good password](https://www.cert.govt.nz/individuals/guides/getting-started-with-cyber-security/how-to-create-a-good-password/)
for each service and it's different from service to service. Never use the
same password for two different services.

Other must do thing is to enable [Two Factor Authentication (2FA)](https://www.cert.govt.nz/individuals/guides/getting-started-with-cyber-security/two-factor-authentication/)
on all the services that provide it. These days most of major online services
provide 2FA, if the service that you use doesn't provide 2FA, it might be a
good idea to move to a different provider that provide a better security.
[twofactorauth.org](https://twofactorauth.org/) has a list of major online
services that provide 2FA.

Subscribe for [Have I been pwned? Notify Me](https://haveibeenpwned.com/NotifyMe)
service with all of your email addresses. This will provide you an alert if
any of your email addresses are linked in existing data breaches or newly
identified data breaches. Make sure to update your password if you got an
alert.

## Static Website
Ask your self whether you need a dynamic web application or a just a static
website is enough. If you don't update your content that often and your website
is just place to provide information to visitors, then small static website
will be enough.

In that case consider using a service that provide small
static service or get a static website developed by credible developer or an
agency. If you are tech savvy you could make use of services like
[GitHub Pages](https://pages.github.com/) or [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/).

Not having dynamic content, and sections such as user comments etc. greatly
minimizes some of the major attacks.

## Dynamic Web Applications
If you provide a dynamic web application such as web shop, consider using a
reputable web shop provider. Similarly if you are after blog, use a reputable
blog service provider.

Some of the security advantages that you get by going with an online web
application platform rather than getting a developer or agency to build you a
bespoke web application are:
* Ongoing maintenance and security upgrades.
* Better monitoring (from platform provider side).
* Low chance of existing vulnerabilities. (Usually these services get frequent
penetration testing and has good bug bounty programs).

When using a web platform, make sure to be familiar with the security controls
provided by those services and use a good password and enable 2FA.

Don't install any "add-ons" / "plugins" unless your really have to. If you are
installing them make sure to do proper research on them and update them
promptly. Things to look out for in third party "add-ons" / "plugins" are:
* Online reviews
* Popularity
* Plugin update frequency

Avoid using any plugins that hasn't been updated in a while.

## Domain Names
Having a good domain name is important to your business but it is very
important that you keep your domain name with you without letting it expired.
As discussed above, using a good password and 2FA with your domain name
registrar or reseller is important. It is advisable to keep the domain name on
auto renew. Put a annual event in your calendar to check that auto renewal is
successful. Sometimes, a bad credit card, incorrect/old email address or
failure at the provider might end up your domain not getting renewed.

Allowing your domain to expire and if a malicious party get hang of your
domain name, that will open a plethora of attacks on you, your customers and
providers.

---
Photograph: ["The News - Suvarnabhumi Airport, Bangkok" by Kesara Rathnayake](https://www.flickr.com/photos/kesara_rathnayake/8515398094/)
