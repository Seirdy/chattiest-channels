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
channel stats from 2020-04-17 22:00 to 2020-04-18 22:08 PDT
total messages: 29460
chattiest channels:
1.   snoonet.#gnulag           3533
2.   ircnet.#worldchat         3497
3.   freenode.#python          2441
4.   freenode.##linux          2362
5.   rizon.#chat               1959
6.   tilde_chat.#meta          1447
7.   freenode.#anime           1422
8.   2600net.#2600             1150
9.   freenode.##chat           1093
10.  gotham.#funchat           921
11.  quakenet.#anime           914
12.  rizon.#rice               866
13.  snoonet.#linuxmasterrace  826
14.  slashnet.#xkcd            746
15.  rizon.#8_a_               688
16.  freenode.#cat-v           643
17.  darkscience.#darkscience  613
18.  quakenet.#quarantine      572
19.  efnet.#computers          497
20.  gotham.#gotham            274
21.  freenode.#tmux            221
22.  freenode.#sway            219
23.  gotham.#twilightzone      201
24.  freenode.#minetest        158
25.  freenode.#lobsters        149
26.  freenode.##anime          140
27.  freenode.#fedora          135
28.  snoonet.#portland         128
29.  freenode.#reddit          118
30.  freenode.#firefox         78
31.  ircnet.#ircnet            77
32.  supernets.#superbowl      60
33.  rizon.#rizon              50
```

<!--
vi:ft=markdown.pandoc.gfm
-->
