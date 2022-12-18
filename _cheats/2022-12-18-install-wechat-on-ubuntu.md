---
layout: none
title: Install Wechat on Ubuntu
---

**Two options**:

+ [Dochat](https://github.com/huan/docker-wechat)
+ [Docker-wechat](https://github.com/top-bettercode/docker-wechat)

**Chinese input**:

Install [sogou pinyin](https://pinyin.sogou.com/linux/help.php)

**Install wechat**:

`2021-8-3`: Tested on Ubuntu 20.04.02 LTS with kernel 5.8.0-43-generic

Note: caution using `xhost +` as it also allows malicious access. Prefer `--network=host` when accessing your local x-server from docker. ([Reference](https://github.com/top-bettercode/docker-wechat))


```bash
docker run -d \
--name wechat \
--device /dev/snd \
--ipc="host" \
--network=host \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-v $HOME/Documents/wechat:/WeChatFiles \
-e DISPLAY=unix$DISPLAY \
-e XMODIFIERS=@im=fcitx \
-e QT_IM_MODULE=fcitx \
-e GTK_IM_MODULE=fcitx \
-e AUDIO_GID=`getent group audio | cut -d: -f3` \
-e GID=`id -g` \
-e UID=`id -u` \
bestwu/wechat
```

**Icon extension**

```bash
sudo apt install gnome-shell-extension-top-icons-plus
gnome-extensions-app
```

**Compatibility**

[WeChat compatibility list](https://github.com/countstarlight/deepin-wine-wechat-arch#%E5%85%BC%E5%AE%B9%E6%80%A7%E8%AE%B0%E5%BD%95)