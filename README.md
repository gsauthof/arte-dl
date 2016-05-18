## Historic Note ##

When I started arte-dl, there weren't usable alternatives for the command line
available. But fortunately, this situation has changed. In the meantime
[youtube-dl][youtubedl] support for sites besides youtube grew in astonishing
ways. Currently, it supports nearly every video website imaginable - including
[Arte][arte].

Thus, I decided to stop mainting my arte download script. I only keep it online
for historic purposes.

As of 2016, I highly recommend youtube-dl for all arte downloading needs.

2016-05-18, Georg Sauthoff <mail@georg.so>

## Introduction ##

arte-dl is a command line tool for downloading embedded videos
from [arte.tv][arte] to be able to view the stuff without having to use
[Adobe Flash][flash].

## Example ##

    $ ./arte-dl (URL)+

e.g.

    $ ./arte-dl http://videos.arte.tv/de/videos/leben_ohne_schadstoffe_-3334834.html
    Download leben_ohne_schadstoffe_-3334838.m4v (try: 0)
    Download leben_ohne_schadstoffe_-3334838.m4v (try: 1)

## Motivation ##

[Arte][arte] is this [public television][public] channel, payed by the people of
Germany/France. Some content is [available for 7 (sic!) days][7day] at
the website. But only viewable within a flash-application. There
are several reasons to avoid [Adobe Flash][flash].
For example uncountable security problems, the fact that it is
proprietary closed source software, non-availability for several
platforms and the mental-pain trying to imagine, why someone
would think that it is a good idea to use flash for distributing
videos.

## Background ##

The tool is written in [Python][python] (2.6.5 works). As dependency the
tool [flvstreamer][flvstreamer] (1.6 works) is needed, which is on current linux
distribution usually available (e.g. apt-get install
flvstreamer).

The license is GPL v3+.

The name is inspired by the nice tool [youtube-dl][youtubedl].

## Feedback ##

I appreciate feedback and comments:

    mail@georg.so
    gsauthof@sdf.lonestar.org

## Repositories ##

arte-dl is available via [GitHub][github]:

    https://github.com/gsauthof/arte-dl

Previously, it was also available via [Bitbucket][bitbucket]:

    https://bitbucket.org/gsauthof/arte-dl

Historically, I started with the Bitbucket repository first, but around 2012-11 I
created an 'official' mirror on GitHub as well. Rationale behind it was
making it easier for GitHub users (who don't have a Bitbucket account) to fork
and to contribute.

Since the code is only of intereset for historic reasons, it is sufficient
to keep it in one public repository. Thus, I've closed the Bitbucket one.

## Related Stuff ##

Nowadays (as of 2016) [youtube-dl][youtubedl] also supports downloading videos
from arte. It is widely available, easy to use and actively maintained. An example call:

    $ youtube-dl 'http://www.arte.tv/guide/de/047156-000/fukushima-chronik-eines-desasters'

It looks like the [Mediathek Java GUI](http://zdfmediathk.sourceforge.net/index.html)
supports arte.tv content (didn't try it).

Someone wrote an [example php-script](http://www.galipe.net/example/plussept.php)
how to extract useful data from the arte feeds.

Some [french][1] [threads][2] mention a python GTK interface for Arte and
some totem integration.

  [1]: http://forum.ubuntu-fr.org/viewtopic.php?id=395921&p=1
  [2]: http://forum.ubuntu-fr.org/viewtopic.php?id=369659

There is also [any-dl][anydl]. The scope of the [any-dl][anydl] is similar to
the one of `youtube-dl`. The difference is that it provides a Domain Specific
Language (DSL) for adding new sites. It comes with a configuration file that
include several example DSL snippets - including one for Arte. For Youtube and
Vimeo it externally calls `youtube-dl`.


## Troubleshooting ##

* In case that the automatically derived destination filename is already
  present in the destination directory the script tries to finish a previous
  started download. If the existing file is unrelated this does not work. Remove
  the existing file then.
* Arte streams some [rated videos only between 23h and 5h][jmstv]. The script tries to
  detect that. If this auto-detection fails the download does not work and the
  created file has to be removed before retrying.
* Arte-dl checks the [FLVStreamer][flvstreamer] version (currently at least v2.1 is needed)
  and prints a diagnostic if there is a problem.  Perhaps the content delivery
  network will introduce (new) incompatibilities in the future - thus when
  downloading stops working at all try a more recent flvstreamer version and
  report the issue to the arte-dl author.


[arte]: http://en.wikipedia.org/wiki/Arte
[flvstreamer]: http://savannah.nongnu.org/projects/flvstreamer
[python]: http://en.wikipedia.org/wiki/Python_(programming_language)
[flash]: http://en.wikipedia.org/wiki/Adobe_Flash
[7day]: http://de.wikipedia.org/wiki/Depublizieren
[public]: http://en.wikipedia.org/wiki/Public_broadcasting
[jmstv]: http://de.wikipedia.org/wiki/Jugendmedienschutz-Staatsvertrag
[bitbucket]: https://bitbucket.org/gsauthof/arte-dl
[github]: https://github.com/gsauthof/arte-dl
[youtubedl]: https://github.com/rg3/youtube-dl
[anydl]: https://github.com/klartext/any-dl

