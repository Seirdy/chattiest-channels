chattiest-channels
==================

[![sourcehut]](https://git.sr.ht/~seirdy/chattiest-channels)
[![GitLab
mirror](https://img.shields.io/badge/mirror-GitLab-orange.svg?logo=gitlab)](https://gitlab.com/Seirdy/chattiest-channels)
[![GitHub
mirror](https://img.shields.io/badge/mirror-GitHub-black.svg?logo=github)](https://github.com/Seirdy/chattiest-channels)

`chattiest-channels` is a script that analyzes your WeeChat logs to determine which
channels have had the most active discussions lately. It does this by filtering out
known bots, join/leave messages, channel messages, away indicators, etc. and counts
the remaining lines across a given time interval.

By default, it analyzes the last 24-25 hours of logs; however, it can take an
optional parameter to specify a custom number of hours to search back.

Try it now, without installing anything:

``` sh
sh -c "$(curl -sSL 'https://git.sr.ht/~seirdy/chattiest-channels/blob/master/chattiest-channels')" - -n 20
```

Dependencies
------------

`chattiest-channels` is written in POSIX sh and uses only standard POSIX utilities,
with one exception: it requires an implementation of `date(1)` that supports the `-d`
flag to describe an arbitrary date. The versions of `date(1)` that come with GNU
coreutils, BusyBox, FreeBSD, and macOS satisfy this condition.

Usage
-----

``` sh
Usage: chattiest-channels [options]

analyze your WeeChat IRC logs to find the most active channels.

  -d, --duration <NUM>  Start counting messages from <NUM> hours ago, rounded down
                        to the earliest hour. Defaults to 24.
  -n, --lines    <NUM>  Show only the <NUM> most active channels. Defaults to showing
                        results from all available log files.
  -h, --help            Print this help and exit
```

Example
-------

Print the top 20 most active channels from the last 48-49 hours.

```
$ chattiest-channels -n 20 -d 48
chattiest channels from 2020-02-27 01:00 to 2020-02-29 01:42 PST
 1. snoonet.#gnulag 6415
 2. rizon.#chat 5429
 3. freenode.##linux 5058
 4. ircnet.#worldchat 3478
 5. freenode.#reddit 2756
 6. slashnet.#xkcd 2446
 7. snoonet.#portland 2419
 8. darkscience.#darkscience 2178
 9. 2600net.#2600 2153
10. efnet.#computers 2022
11. freenode.##chat 1761
12. snoonet.#redoxmasterrace 1693
13. rizon.#rice 1415
14. freenode.#podman 947
15. freenode.#lobsters-boil 932
16. freenode.#lobsters 911
17. freenode.#cat-v 887
18. freenode.#fsf 695
19. freenode.#fedora 684
20. cyberia.#cyberia 584
```

[sourcehut]: https://img.shields.io/badge/repository-sourcehut-lightgrey.svg?logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSINCiAgICB3aWR0aD0iMTI4IiBoZWlnaHQ9IjEyOCI+DQogIDxkZWZzPg0KICAgIDxmaWx0ZXIgaWQ9InNoYWRvdyIgeD0iLTEwJSIgeT0iLTEwJSIgd2lkdGg9IjEyNSUiIGhlaWdodD0iMTI1JSI+DQogICAgICA8ZmVEcm9wU2hhZG93IGR4PSIwIiBkeT0iMCIgc3RkRGV2aWF0aW9uPSIxLjUiDQogICAgICAgIGZsb29kLWNvbG9yPSJibGFjayIgLz4NCiAgICA8L2ZpbHRlcj4NCiAgICA8ZmlsdGVyIGlkPSJ0ZXh0LXNoYWRvdyIgeD0iLTEwJSIgeT0iLTEwJSIgd2lkdGg9IjEyNSUiIGhlaWdodD0iMTI1JSI+DQogICAgICA8ZmVEcm9wU2hhZG93IGR4PSIwIiBkeT0iMCIgc3RkRGV2aWF0aW9uPSIxLjUiDQogICAgICAgIGZsb29kLWNvbG9yPSIjQUFBIiAvPg0KICAgIDwvZmlsdGVyPg0KICA8L2RlZnM+DQogIDxjaXJjbGUgY3g9IjUwJSIgY3k9IjUwJSIgcj0iMzglIiBzdHJva2U9IndoaXRlIiBzdHJva2Utd2lkdGg9IjQlIg0KICAgIGZpbGw9Im5vbmUiIGZpbHRlcj0idXJsKCNzaGFkb3cpIiAvPg0KICA8Y2lyY2xlIGN4PSI1MCUiIGN5PSI1MCUiIHI9IjM4JSIgc3Ryb2tlPSJ3aGl0ZSIgc3Ryb2tlLXdpZHRoPSI0JSINCiAgICBmaWxsPSJub25lIiBmaWx0ZXI9InVybCgjc2hhZG93KSIgLz4NCjwvc3ZnPg0KCg==

<!--
vi:ft=markdown.pandoc.gfm
-->
