---
layout: post
title:  "Chat with us on Matrix"
slug: group-chat
categories: group chat 
---

In addition to Discord and sshchat, we have bridged a Matrix room for our group to chat in:

[https://matrix.to/#/#central-utah-lug:matrix.org](https://matrix.to/#/#central-utah-lug:matrix.org)

Discord, sshchat and Matrix are all bridged to the same `#general` channel in our Discord instance. We are using [Matterbridge] to facilitate the bridging of the separate services.

## Matterbridge config

For anyone curious, at the time of writing this is how Matterbridge is configured to bridge these separate services (with sensitive values scrubbed):

```
[sshchat.culug]
Server="<snip>:22"
Nick="matterbridge"
RemoteNickFormat="[{PROTOCOL}] <{NICK}> "

[discord.culug]
Token="<snip>"
Server="<snip>"
AutoWebhooks=true
RemoteNickFormat="[{PROTOCOL}] <{NICK}> "
PreserveThreading=true

[matrix.matrix-org]
Server="https://matrix.org"
Login="<snip>"
Password="<snip>"
RemoteNickFormat="[{PROTOCOL}] <{NICK}> "
NoHomeServerSuffix=false

[[gateway]]
name="ssh-chat-discord-matrix-gateway"
enable=true

  [[gateway.inout]]
  account="discord.culug"
  channel="general"

  [[gateway.inout]]
  account="sshchat.culug"
  channel="sshchat"

  [[gateway.inout]]
  account="matrix.matrix-org"
  channel="#central-utah-lug:matrix.org"
```

## Bonus: SSHchat

This is the snippet with how we're running `sshchat`:

```
docker run -v ./motd.txt:/opt/motd.txt -v ./ssh:/root/.ssh -p 22:2022 -d --name=sshchat --restart=unless-stopped docker.io/heywoodlh/ssh-chat:daf4677 /usr/local/bin/ssh-chat --identity=/root/.ssh/id_rsa --admin=/root/.ssh/admin_authorized_keys --motd=/opt/motd.txt
```
