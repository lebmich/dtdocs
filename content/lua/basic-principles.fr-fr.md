---
author: people
draft: 'false'
id: basic-principles
title: 'basic principles: luarc files'
weight: 20
---

At startup, darktable will automatically run the Lua scripts `$DARKTABLE/share/darktable/luarc` and `$HOME/.config/darktable/luarc` (where `$DARKTABLE` represents the darktable installation directory and `$HOME` represents your home directory).

This is the only time darktable will run Lua scripts by itself. These scripts can register callbacks to perform actions on various darktable events. This callback mechanism is the primary method of triggering lua actions.