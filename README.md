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
$ date +"%Y-%m-%dT%H:%M:%S%:z"
2020-02-28T07:23:17-08:00

$ chattiest-channels -n 20 -d 48
chattiest channels since 2020-02-26 07:00
 1. snoonet.#gnulag 6386
 2. freenode.##linux 5036
 3. rizon.#chat 4538
 4. freenode.#reddit 2612
 5. slashnet.#xkcd 2506
 6. 2600net.#2600 2386
 7. ircnet.#worldchat 2253
 8. snoonet.#portland 2144
 9. darkscience.#darkscience 1935
10. freenode.##chat 1934
11. darwin.#darwin 1890
12. rizon.#rice 1329
13. efnet.#computers 1274
14. snoonet.#redoxmasterrace 988
15. freenode.#lobsters-boil 966
16. freenode.#fedora 811
17. freenode.#alacritty 791
18. freenode.#lobsters 756
19. cyberia.#cyberia 749
20. freenode.#cat-v 715
```

[sourcehut]: https://img.shields.io/badge/repository-sourcehut-lightgrey.svg?logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSINCiAgICB3aWR0aD0iMTI4IiBoZWlnaHQ9IjEyOCI+DQogIDxkZWZzPg0KICAgIDxmaWx0ZXIgaWQ9InNoYWRvdyIgeD0iLTEwJSIgeT0iLTEwJSIgd2lkdGg9IjEyNSUiIGhlaWdodD0iMTI1JSI+DQogICAgICA8ZmVEcm9wU2hhZG93IGR4PSIwIiBkeT0iMCIgc3RkRGV2aWF0aW9uPSIxLjUiDQogICAgICAgIGZsb29kLWNvbG9yPSJibGFjayIgLz4NCiAgICA8L2ZpbHRlcj4NCiAgICA8ZmlsdGVyIGlkPSJ0ZXh0LXNoYWRvdyIgeD0iLTEwJSIgeT0iLTEwJSIgd2lkdGg9IjEyNSUiIGhlaWdodD0iMTI1JSI+DQogICAgICA8ZmVEcm9wU2hhZG93IGR4PSIwIiBkeT0iMCIgc3RkRGV2aWF0aW9uPSIxLjUiDQogICAgICAgIGZsb29kLWNvbG9yPSIjQUFBIiAvPg0KICAgIDwvZmlsdGVyPg0KICA8L2RlZnM+DQogIDxjaXJjbGUgY3g9IjUwJSIgY3k9IjUwJSIgcj0iMzglIiBzdHJva2U9IndoaXRlIiBzdHJva2Utd2lkdGg9IjQlIg0KICAgIGZpbGw9Im5vbmUiIGZpbHRlcj0idXJsKCNzaGFkb3cpIiAvPg0KICA8Y2lyY2xlIGN4PSI1MCUiIGN5PSI1MCUiIHI9IjM4JSIgc3Ryb2tlPSJ3aGl0ZSIgc3Ryb2tlLXdpZHRoPSI0JSINCiAgICBmaWxsPSJub25lIiBmaWx0ZXI9InVybCgjc2hhZG93KSIgLz4NCjwvc3ZnPg0KCg==

<!--
vi:ft=markdown.pandoc.gfm
-->
