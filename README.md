arte-dl is a command line tool for downloading embedded videos
from [arte.tv][arte] to be able to view the stuff without having to use
[Adobe Flash][flash].

## Example ##

    $ ./arte-dl (URL)+

e.g.

    $ ./arte http://videos.arte.tv/de/videos/leben_ohne_schadstoffe_-3334834.html
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

The name is inspired by the nice tool [youtube-dl](https://github.com/rg3/youtube-dl).

## Feedback ##

I appreciate feedback and comments:

    mail@georg.so
    gsauthof@sdf.lonestar.org

## Repositories ##

arte-dl is available via [Bitbucket][bitbucket] and [GitHub][github]:

    https://bitbucket.org/gsauthof/arte-dl
    https://github.com/gsauthof/arte-dl

Historically, I started with the Bitbucket repository first, but now (2012-11) I
have created an 'official' mirror on GitHub as well. Rationale behind it is
making it easier for GitHub users (who don't have a Bitbucket account) to fork
and to contribute.

Until further notice I'll keep both repositories in sync.

## Related Stuff ##

It looks like the [Mediathek Java GUI](http://zdfmediathk.sourceforge.net/index.html)
supports arte.tv content (didn't try it).

Someone wrote an [example php-script](http://www.galipe.net/example/plussept.php)
how to extract useful data from the arte feeds.

Some [french][1] [threads][2] mention a python GTK interface for Arte and
some totem integration.

  [1]: http://forum.ubuntu-fr.org/viewtopic.php?id=395921&p=1
  [2]: http://forum.ubuntu-fr.org/viewtopic.php?id=369659

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

