Heroku Twitter Stream: Perl
======================

This is a Heroku Twitter Stream in Perl.

Usage
-----

Example usage:

    $ ls
    cpanfile
    Procfile
    stream.pl
    lib/

    $ cat cpanfile
    requires 'IO::Socket::SSL','0';
    requires 'Net::Twitter','0';
    requires 'Web::Scraper','0';
    requires 'LWP::UserAgent','0';
    requires 'HTTP::Request::Common','0';
    requires 'LWP::Protocol::https','0';
    requires 'URI::Escape','0';
    requires 'HTML::Entities','0';
    requires 'DateTime','0';
    requires 'Params::Validate','0';
    requires 'AnyEvent::Twitter::Stream','0';
    
    $ cat Procfile
    bot: perl -Mlib=/app/local/lib/perl5 /app/stream.pl
    
    $ heroku create --stack cedar --buildpack https://github.com/macminiosx/heroku-twitterstream-perl.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    -----> Twitter/Stream app detected
    -----> Installing dependencies
    
    $ heroku config:add MY_CONSUMER_KEY=... MY_CONSUMER_SECRET=... MY_OAUTH_TOKEN=... MY_OAUTH_TOKEN_SECRET=...

    $ heroku scale bot=1

    $ heroku ps

The buildpack will detect that your app has an `stream.pl` in the root.

Libraries
---------

Dependencies can be declared using `cpanfile` (recommended) or more traditional `Makefile.PL`, `Build.PL` and `META.json` (whichever you can install with `cpanm --installdeps`), and the buildpack will install these dependencies using [cpanm](http://cpanmin.us) into `./local` directory

