---
theme: apple-basic
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## How to start open source?
drawings:
  persist: false
transition: slide-left
css: unocss
title: Welcome to Slidev
layout: intro
---

# 学生时代如何参与开源项目

<div class="absolute bottom-10">
  <span class="font-700">
    by Himself65
  </span>
</div>

<!--
介绍自己Alex，面包。
推特
-->

---
layout: intro-image
image: profile.png
---



<!--
GitHub主页，自己之前和现在在做的项目
-->

---
layout: two-cols
---

# Podcast

https://podcasters.spotify.com/middlecat/episodes/ep-e24ga5e

https://podcasts.apple.com/us/podcast/%E5%AE%87%E5%AE%99%E4%B8%AD%E7%8C%AB/id1659350101?i=1000614022758

::right::
<div style="padding-left: 50px"> 
  <Tweet id="1660806978116153346" scale="0.65" />
</div>

<!--
宣传中猫的podcast，从里面大致的内容引出自己今天的话题
-->

---
layout: intro-image
image: road-trip.jpg
---



<!--
介绍湾区
-->

---

# Google

<img style="height: 400px;" src="/google.jpeg?raw=true">

<!--
谷歌朋友
-->

---
layout: two-cols
---

# Book

<img border="rounded" style="height: 350px" src="/c-primer-plus.png?raw=true">

C Primer Plus 5th

::right::

<img border="rounded" style="height: 400px" src="/book.png?raw=true">

https://gpp.tkchu.me/

<!--
高中时候开始读书
-->

---
class: px-20
---

# Minecraft Server

<div grid="~ cols-2 gap-2" m="-t-2">
  <img border="rounded" src="/minecraft.jpeg?raw=true"/>
  <img border="rounded" src="/server.png?raw=true">
</div>

<!--
兴趣是最好的老师
-->

---
layout: two-cols
---

# Minecraft

```js{all|11,14-16|all}
const { EventEmitter } = require('events')

const server = new EventEmitter()

server.on('user:join', function setup(user) {
  user.on('move', function handleMove() {
    // ...
    if (/* x */) {
      user.once('jump', function handleJump() {
        // ...
        return 1;
      })
    } else if (/* y */) {
      user.rawListeners('jump').forEach(fn => {
        const result = fn()
        console.log("result:", result)
        // ...
      })
    }
  })
})
```

<arrow v-click="1" x1="400" y1="420" x2="320" y2="350" color="#564" width="3" arrowSize="1" />

::right::

<div style="height: 50px"/>

```shell
> node ./server.ts
...
result: undefiend
...
```

<!--
小小的问题
-->

---

```js
// https://github.com/nodejs/node/blob/b1ef279d5726905d7941f4a58978b379daa3cdc4/lib/events.js#L282-L303
function onceWrapper(...args) {
  if (!this.fired) {
    this.target.removeListener(this.type, this.wrapFn);
    this.fired = true;
    Reflect.apply(this.listener, this.target, args);
  }
}

function _onceWrap(target, type, listener) {
  var state = { fired: false, wrapFn: undefined, target, type, listener };
  var wrapped = onceWrapper.bind(state);
  wrapped.listener = listener;
  state.wrapFn = wrapped;
  return wrapped;
}

EventEmitter.prototype.once = function once(type, listener) {
  checkListener(listener);

  this.on(type, _onceWrap(this, type, listener));
  return this;
};
```

<!--
Node.js 的 bug
-->

---
---
# Node.js

- https://github.com/nodejs/node/pull/25818/commits/bea7431f42de5323eadd0a879c1777093aea3d88#diff-330bdd22a188135540523f69deb4f9563e03b00a913cd369e1ee84d899f178a9
- https://github.com/nodejs/node/commits?author=himself65

---

# BlockSuite

<img border="rounded" style="height: 400px" src="/blocksuite.png?raw=true">

<!--
BlockSuite 编辑器，是AFFiNE的底层
-->

---

# AFFiNE

<img border="rounded" style="height: 400px" src="/affine.png?raw=true">

<!--
AFFiNE是我目前主导的项目，整个Web端架构设计都是我一个人来完成的。

稍微讲一下创业。
-->

---

# 开源

- jotai
- yjs
- swr
- next.js
- pnpm
- node.js
- slidev

<!--
开源不仅仅是只将代码放在网上，而是一种与人合作的一种方式
-->

---

# 最后

- 不断学习
- 与他人合作
- 提出自己的看法

<!--
- WebGPU，shader
- 参与社区（哪怕是issue）
- 与人沟通
-->

---
layout: end
---

END
