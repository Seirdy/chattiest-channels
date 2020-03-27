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

```
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
$ chattiest-channels -n 25 -d 48
channel stats from 2020-03-24 13:00 to 2020-03-26 13:09 PDT
total messages: 81092
chattiest channels:
 1. snoonet.#gnulag 8976
 2. efnet.#lrh 7066
 3. rizon.#chat 6597
 4. ircnet.#worldchat 6331
 5. freenode.##linux 5878
 6. freenode.#python 5705
 7. 2600net.#2600 4302
 8. darwin.#darwin 3996
 9. darkscience.#darkscience 3159
10. snoonet.#portland 3058
11. slashnet.#xkcd 2272
12. snoonet.#redoxmasterrace 2146
13. gotham.#gotham 2047
14. rizon.#rice 1797
15. freenode.#cat-v 1637
16. freenode.##chat 1500
17. snoonet.##dataclonefreezone 1402
18. efnet.#computers 1330
19. freenode.#lobsters 1061
20. slashnet.#compsci 1046
21. freenode.#reddit 971
22. gotham.#twilightzone 964
23. freenode.#lobsters-boil 821
24. freenode.#alacritty 790
25. cyberia.#cyberia 763
```

[sourcehut]: https://img.shields.io/badge/repository-sourcehut-lightgrey.svg?logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSINCiAgICB3aWR0aD0iMTI4IiBoZWlnaHQ9IjEyOCI+DQogIDxkZWZzPg0KICAgIDxmaWx0ZXIgaWQ9InNoYWRvdyIgeD0iLTEwJSIgeT0iLTEwJSIgd2lkdGg9IjEyNSUiIGhlaWdodD0iMTI1JSI+DQogICAgICA8ZmVEcm9wU2hhZG93IGR4PSIwIiBkeT0iMCIgc3RkRGV2aWF0aW9uPSIxLjUiDQogICAgICAgIGZsb29kLWNvbG9yPSJibGFjayIgLz4NCiAgICA8L2ZpbHRlcj4NCiAgICA8ZmlsdGVyIGlkPSJ0ZXh0LXNoYWRvdyIgeD0iLTEwJSIgeT0iLTEwJSIgd2lkdGg9IjEyNSUiIGhlaWdodD0iMTI1JSI+DQogICAgICA8ZmVEcm9wU2hhZG93IGR4PSIwIiBkeT0iMCIgc3RkRGV2aWF0aW9uPSIxLjUiDQogICAgICAgIGZsb29kLWNvbG9yPSIjQUFBIiAvPg0KICAgIDwvZmlsdGVyPg0KICA8L2RlZnM+DQogIDxjaXJjbGUgY3g9IjUwJSIgY3k9IjUwJSIgcj0iMzglIiBzdHJva2U9IndoaXRlIiBzdHJva2Utd2lkdGg9IjQlIg0KICAgIGZpbGw9Im5vbmUiIGZpbHRlcj0idXJsKCNzaGFkb3cpIiAvPg0KICA8Y2lyY2xlIGN4PSI1MCUiIGN5PSI1MCUiIHI9IjM4JSIgc3Ryb2tlPSJ3aGl0ZSIgc3Ryb2tlLXdpZHRoPSI0JSINCiAgICBmaWxsPSJub25lIiBmaWx0ZXI9InVybCgjc2hhZG93KSIgLz4NCjwvc3ZnPg0KCg==

<!--
vi:ft=markdown.pandoc.gfm
-->
