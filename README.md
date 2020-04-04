chattiest-channels
==================

[![sourcehut](https://img.shields.io/badge/repository-sourcehut-lightgrey.svg?logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSINCiAgICB3aWR0aD0iMTI4IiBoZWlnaHQ9IjEyOCI+DQogIDxkZWZzPg0KICAgIDxmaWx0ZXIgaWQ9InNoYWRvdyIgeD0iLTEwJSIgeT0iLTEwJSIgd2lkdGg9IjEyNSUiIGhlaWdodD0iMTI1JSI+DQogICAgICA8ZmVEcm9wU2hhZG93IGR4PSIwIiBkeT0iMCIgc3RkRGV2aWF0aW9uPSIxLjUiDQogICAgICAgIGZsb29kLWNvbG9yPSJibGFjayIgLz4NCiAgICA8L2ZpbHRlcj4NCiAgICA8ZmlsdGVyIGlkPSJ0ZXh0LXNoYWRvdyIgeD0iLTEwJSIgeT0iLTEwJSIgd2lkdGg9IjEyNSUiIGhlaWdodD0iMTI1JSI+DQogICAgICA8ZmVEcm9wU2hhZG93IGR4PSIwIiBkeT0iMCIgc3RkRGV2aWF0aW9uPSIxLjUiDQogICAgICAgIGZsb29kLWNvbG9yPSIjQUFBIiAvPg0KICAgIDwvZmlsdGVyPg0KICA8L2RlZnM+DQogIDxjaXJjbGUgY3g9IjUwJSIgY3k9IjUwJSIgcj0iMzglIiBzdHJva2U9IndoaXRlIiBzdHJva2Utd2lkdGg9IjQlIg0KICAgIGZpbGw9Im5vbmUiIGZpbHRlcj0idXJsKCNzaGFkb3cpIiAvPg0KICA8Y2lyY2xlIGN4PSI1MCUiIGN5PSI1MCUiIHI9IjM4JSIgc3Ryb2tlPSJ3aGl0ZSIgc3Ryb2tlLXdpZHRoPSI0JSINCiAgICBmaWxsPSJub25lIiBmaWx0ZXI9InVybCgjc2hhZG93KSIgLz4NCjwvc3ZnPg0KCg==)](https://git.sr.ht/~seirdy/chattiest-channels)
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

Flood mitigation
----------------

Mitigating the effects of spam and flooding continues to be an ongoing challenge.
Current measures include:

- Merging consecutive messages from the same nick
- Filtering out known bots

Areas of improvement:

- Filtering out messages containing a lot of escape sequences (since these usually
  aren't part of a discussion)
- Filter out bots on a per-network or per-channel basis to avoid false positives

Dependencies
------------

`chattiest-channels` is written in POSIX sh and uses only standard POSIX utilities,
with one exception: it requires an implementation of `date(1)` that supports the `-d`
flag to describe an arbitrary date. The versions of `date(1)` that come with GNU
coreutils, BusyBox, FreeBSD, and macOS satisfy this condition.

Usage
-----

``` text
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

``` text
$ chattiest-channels -n 35 -d 24
channel stats from 2020-04-02 22:00 to 2020-04-03 22:24 PDT
total messages: 38527
chattiest channels:
1.   rizon.#chat                  4232
2.   efnet.#lrh                   3134
3.   snoonet.#gnulag              2989
4.   freenode.#python             2309
5.   ircnet.#worldchat            2206
6.   freenode.#anime              2119
7.   darwin.#darwin               2034
8.   freenode.##linux             1973
9.   freenode.##chat              1512
10.  tilde_chat.#meta             1455
11.  darkscience.#darkscience     1156
12.  quakenet.#quarantine         1154
13.  gotham.#funchat              987
14.  snoonet.#portland            812
15.  rizon.#rice                  777
16.  snoonet.#redoxmasterrace     772
17.  efnet.#computers             769
18.  slashnet.#xkcd               680
19.  2600net.#2600                672
20.  snoonet.##dataclonefreezone  604
21.  gotham.#gotham               542
22.  quakenet.#anime              472
23.  tilde_chat.#covid19          461
24.  gotham.#twilightzone         454
25.  freenode.#fsf                447
26.  freenode.#alacritty          426
27.  freenode.#reddit             381
28.  freenode.#lobsters           359
29.  slashnet.#compsci            292
30.  freenode.#fedora             255
31.  snoonet.#linuxmasterrace     203
32.  freenode.##anime             169
33.  grepnet.#chats               168
34.  freenode.#sway               140
35.  freenode.#tmux               139
```

<!--
vi:ft=markdown.pandoc.gfm
-->
