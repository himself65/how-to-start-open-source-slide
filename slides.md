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

---
layout: intro-image
image: profile.png
---

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

---
layout: intro-image
image: road-trip.jpg
---

--- 
---
# Google

<img style="height: 400px;" src="/google.jpeg?raw=true">

---
layout: two-cols
---

# Book

<img border="rounded" style="height: 350px" src="/c-primer-plus.png?raw=true">

C Primer Plus 5th

::right::

<img border="rounded" style="height: 400px" src="/book.png?raw=true">

https://gpp.tkchu.me/

---
class: px-20
---

# Minecraft Server

<div grid="~ cols-2 gap-2" m="-t-2">
  <img border="rounded" src="/minecraft.jpeg?raw=true"/>
  <img border="rounded" src="/server.png?raw=true">
</div>

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

---
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

---
---
# Node.js

- https://github.com/nodejs/node/pull/25818/commits/bea7431f42de5323eadd0a879c1777093aea3d88#diff-330bdd22a188135540523f69deb4f9563e03b00a913cd369e1ee84d899f178a9
- https://github.com/nodejs/node/commits?author=himself65

---
---
# AFFiNE

<img border="rounded" style="height: 400px" src="/affine.png?raw=true">

---
---
# 开源

- jotai
- yjs
- swr
- next.js
- pnpm
- node.js
- slidev

---
layout: end
---
