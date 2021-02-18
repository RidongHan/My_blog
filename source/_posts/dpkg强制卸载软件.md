---
title: dpkg强制卸载软件
date: 2021-02-06 15:34:09
tags: dpkg
categories: dpkg
abbrlink: '20210206'
---

# dpkg强制卸载软件，忽略依赖warning

```
sudo dpkg --purge --force-depends 软件名
```
例如：
```
sudo dpkg --purge --force-depends "libglvnd-dev"
```
