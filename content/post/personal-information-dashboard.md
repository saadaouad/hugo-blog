---
author: "Saad Aouad"
date: 2018-06-10
linktitle: Know your personal information dashboard for your terminal
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Know your personal information dashboard for your terminal
description: A personal terminal based dashboard utility, designed for displaying important and daily data.

weight: 10
---

[WTFutil](https://wtfutil.com/) is a personal terminal based dashboard utility, designed for displaying important and daily data.

### Quick start
> This tool is only compatible with Go versions 1.9.2 or later. It currently does not compile with gccgo.

```
➜  ~ go get -u github.com/senorprogrammer/wtf

➜  ~ cd go/src/github.com/senorprogrammer/wtf

➜  wtf make install

➜  wtf git:(master) make run
go build -o bin/wtf
bin/wtf

┌──────────── World Clocks ────────────┐┌─────────────── System ───────────────┐                                                               
│                                      ││   Built: parsing time "dev" as "2006-│                                                               
│ Avignon      19:41 CEST  Jun 10      ││    Vers: dev                         │                                                               
│ Barcelona    19:41 CEST  Jun 10      ││                                      │                                                               
│ Dubai        21:41 +04   Jun 10      ││      OS: 10.13.1                     │                                                               
│ Toronto      13:41 EDT   Jun 10      ││   Build: 17B1003                     │                                                               
│ Vancouver    10:41 PDT   Jun 10      ││                                      │                                                               
│                                      ││                                      │                                                               
│                                      ││                                      │                                                               
│                                      ││                                      │                                                               
│                                      ││                                      │                                                               
│                                      ││                                      │                                                               
└──────────────────────────────────────┘└──────────────────────────────────────┘                                                               
┌────────────── Security ──────────────┐┌──── Text File  ~/.wtf/config.yml─────┐                                                               
│ WiFi                                 ││wtf:                                  │                                                               
│  Network:                            ││  colors:                             │                                                               
│   Crypto:                            ││    border:                           │                                                               
│                                      ││      focusable: darkslateblue        │                                                               
│ Firewall        DNS                  ││      focused: orange                 │                                                               
│  Enabled: off   192.168.1.1          ││      normal: gray                    │                                                               
│  Stealth: off                        ││  grid:                               │                                                               
│                                      ││    columns: [40, 40]                 │                                                               
│ Users                                ││    rows: [13, 13, 4]                 │                                                               
│ macports, ...                        ││  refreshInterval: 1                  │                                                               
│                                      ││  mods:                               │                                                               
└──────────────────────────────────────┘└──────────────────────────────────────┘                                                               
┌─────────────────────────────────── Status ───────────────────────────────────┐                                                               
│                                                                              │                                                               
│👍                                                                            │                                                               
└──────────────────────────────────────────────────────────────────────────────┘ 
```

The important part of this tool is `Modules` functionality with this last you can extracts data from some source and packages like Git, Github, Jira and New Relic ref https://wtfutil.com/posts/modules/