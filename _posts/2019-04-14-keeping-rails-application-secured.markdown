---
layout:       post
title:        "Keeping Rails Application Secured"
description:  >
    How to keep on top of security vulnerabilities of your Ruby on Rails
    application.
date:         2019-04-14 00:00:00
categories:   ruby rails security programming infosec
---
These are few steps that I usually take to make sure Ruby on Rails applications
are secured and all the gems that it uses have no known security
vulnerabilities. If you want learn about how to avoid common security problems,
[Securing Rails Applications][securing-rails] guide is a good start.

Just writing a secure application is not going to guarantee your application is
going to stay secured. New security vulnerabilities are discovered every day,
stale gems or new dependencies could introduce new vulnerabilities, also each
new bugfix or feature could potentially introduce a vulnerability. There are
a few steps that you could take to stay sane and have some assurance that your
application is secure. There are few steps that you could take to stay sane and
have a little bit of assurance that your application is secure.

## Add a gem trust policy
Adding a gem trust policy with `MediumSecurity` is a good way to stop malicious
gems getting installed on the server.

| Trust Policy     | Description                                     |
| ---------------- | ----------------------------------------------- |
| `HighSecurity`   | All dependent gems must be signed and verified. |
| `MediumSecurity` | All signed dependent gems must be verified.     |

    bundle --trust-policy MediumSecurity

Running the above command will create a `.bundle/config` file with
`MediumSecurity` trust policy and it will stop the bundler from installing any
gems that have signatures that cannot be verified. Make sure that you commit
this configuration file to your code repository.

`HighSecurity` is very desirable, if you can manage that.  But it might not be
very practical, because there are quite a few well know gems that not signed.

For more information read [RubyGems signing document][rubygems-security].
Keep in mind that just because a certain gem is cryptographically signed,
doesn't mean it's not a malicious gem and vice versa. Try to avoid installing
unnecessary gems and do your research before introducing new gems to your
application.

## Add bundler audit test
Easiest way to keeping up to date with new vulnerabilities is using
**[bundler-audit][bundler-audit]** gem and run it daily using a
[Jenkins][jenkins] job or similar.

[bundler-audit][bundler-audit] runs through your `Gemfile.lock` and reports 
with an error if any of the gems has a known vulnerability. This gem use
[ruby-advisory-db][ruby-advisory-db] which is kept up to date with known
vulnerabilities.

Run the following command as a daily security job and make sure you have
notifications set if this job fails.

    bundle audit check --update

Above command gets updates from `ruby-advisory-db` and checks your
`Gemfile.lock`. There is also a rails security [mailing list][mailing-list],
if you want to keep update with rails related vulnerabilities.

## Static analysis with Brakeman
**[Brakeman][brakeman]** is a static analysis security tool for Ruby on Rails.
You can configure your code repository server to run this before any pull
request and make the passing of this run as a merge requirement. Or you could
setup a daily job that runs this on your production or development branches.

    brakeman -A

Above command will run all the checks. You must run that on your project root.
It is possible that brakeman will complain about false positives. But it
provides nice way to ignore them. Read
[Brakemanscanner documentation][brakeman-docs] for more information.

## References
* [Securing Rails Applications][securing-rails]
* [RubyGems Security][rubygems-security]

## Edits
* Corrected some grammar mistakes. Thanks Dave. :)

[securing-rails]:    https://guides.rubyonrails.org/security.html
[rubygems-security]: https://guides.rubygems.org/security/
[ruby-advisory-db]:  https://github.com/rubysec/ruby-advisory-db/
[bundler-audit]:     https://github.com/rubysec/bundler-audit
[jenkins]:           https://jenkins.io/
[mailing-list]:      https://groups.google.com/forum/#!forum/rubyonrails-security
[brakeman]:          https://brakemanscanner.org/
[brakeman-docs]:     https://brakemanscanner.org/docs/
