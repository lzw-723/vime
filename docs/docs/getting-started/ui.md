---
title: User Interface
sidebar_label: UI
---

import Tabs from '@theme/Tabs'
import TabItem from '@theme/TabItem'

UI components are visually displayed elements inside the media player that _may_ be interactable
such as a playback control or slider, or they _may_ be simple visual feedback such as the length
of the media (duration). It can be quite time consuming and challenging to setup an entire interface for a
video player, so let's start by using the [default UI](../components/ui/default-ui) given to us out
of the box...

<Tabs
groupId="framework"
defaultValue="html"
values={[
{ label: 'HTML', value: 'html' },
{ label: 'React', value: 'react' },
{ label: 'Vue', value: 'vue' },
{ label: 'Svelte', value: 'svelte' },
{ label: 'Stencil', value: 'stencil' },
{ label: 'Angular', value: 'angular' }
]}>

<TabItem value="html">

```html {16-18} title="player.html"
<!-- Notice we turned off controls? We're supplying our own, so we hide the native ones. -->
<vm-player>
  <vm-video cross-origin="true" poster="https://media.vimejs.com/poster.png">
    <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
    <track
      default
      kind="subtitles"
      src="https://media.vimejs.com/subs/english.vtt"
      srclang="en"
      label="English"
    />
  </vm-video>

  <!-- We've replaced the `<vm-ui>` element. -->
  <!-- We can also turn off any features we don't want via properties. -->
  <vm-default-ui no-click-to-play>
    <!-- We can place our own UI components here to extend the default UI. -->
  </vm-default-ui>
</vm-player>
```

</TabItem>

<TabItem value="react">

```tsx {24-26} title="Player.tsx"
import React from 'react';
import { Player, Video, DefaultUi } from '@vime/react';

function Player() {
  return (
    {/* Notice we turned off controls? We're supplying our own, so we hide the native ones. */}
    <Player>
      <Video crossOrigin="" poster="https://media.vimejs.com/poster.png">
        <source
          data-src="https://media.vimejs.com/720p.mp4"
          type="video/mp4"
        />
        <track
          default
          kind="subtitles"
          src="https://media.vimejs.com/subs/english.vtt"
          srcLang="en"
          label="English"
        />
      </Video>

      {/* We've replaced the `<Ui />` component. */}
      {/* We can turn off any features we don't want via properties. */}
      <DefaultUi noClickToPlay>
        {/* We can place our own UI components here to extend the default UI. */}
      </DefaultUi>
    </Player>
  );
}
```

</TabItem>

<TabItem value="vue">

```html {17-19} title="Player.vue"
<template>
  <!-- Notice we turned off controls? We're supplying our own, so we hide the native ones. -->
  <Player>
    <video crossorigin="" poster="https://media.vimejs.com/poster.png">
      <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
      <track
        default
        kind="subtitles"
        src="https://media.vimejs.com/subs/english.vtt"
        srclang="en"
        label="English"
      />
    </video>

    <!-- We've replaced the `<Ui />` component. -->
    <!-- We can turn off any features we don't want via properties. -->
    <DefaultUi noClickToPlay>
      <!-- We can place our own UI components here to extend the default UI. -->
    </DefaultUi>
  </Player>
</template>

<script>
  import { Player, Video, DefaultUi } from '@vime/vue';

  export default {
    components: {
      Player,
      Video,
      DefaultUi,
    },
  };
</script>
```

</TabItem>

<TabItem value="svelte">

```html {16-18} title="Player.svelte"
<!-- Notice we turned off controls? We're supplying our own, so we hide the native ones. -->
<Player>
  <video crossorigin="" poster="https://media.vimejs.com/poster.png">
    <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
    <track
      default
      kind="subtitles"
      src="https://media.vimejs.com/subs/english.vtt"
      srclang="en"
      label="English"
    />
  </video>

  <!-- We've replaced the `<Ui />` component. -->
  <!-- We can turn off any features we don't want via properties. -->
  <DefaultUi noClickToPlay>
    <!-- We can place our own UI components here to extend the default UI. -->
  </DefaultUi>
</Player>

<script lang="ts">
  import { Player, Video, DefaultUi } from '@vime/svelte';
</script>
```

</TabItem>

<TabItem value="stencil">

```tsx {24-26} title="player.tsx"
class Player {
  // ...

  render() {
    return (
      {/* Notice we turned off controls? We're supplying our own, so we hide the native ones. */}
      <vm-player>
        <vm-video crossOrigin="" poster="https://media.vimejs.com/poster.png">
          <source
            data-src="https://media.vimejs.com/720p.mp4"
            type="video/mp4"
          />
          <track
            default
            kind="subtitles"
            src="https://media.vimejs.com/subs/english.vtt"
            srclang="en"
            label="English"
          />
        </vm-video>

        {/* We've replaced the `<vm-ui>` component. */}
        {/* We can turn off any features we don't want via properties. */}
        <vm-default-ui noClickToPlay>
          {/* We can place our own UI components here to extend the default UI. */}
        </vm-default-ui>
      </vm-player>
    );
  }
}
```

</TabItem>

<TabItem value="angular">

```html {16-18} title="player.html"
<!-- Notice we turned off controls? We're supplying our own, so we hide the native ones. -->
<vm-player>
  <vm-video cross-origin="true" poster="https://media.vimejs.com/poster.png">
    <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
    <track
      default
      kind="subtitles"
      src="https://media.vimejs.com/subs/english.vtt"
      srclang="en"
      label="English"
    />
  </vm-video>

  <!-- We've replaced the `<vm-ui>` element. -->
  <!-- We can also turn off any features we don't want via properties. -->
  <vm-default-ui no-click-to-play>
    <!-- We can place our own UI components here to extend the default UI. -->
  </vm-default-ui>
</vm-player>
```

</TabItem>
    
</Tabs>

Glorious! Here's the result so far 🥁 ...

import BasicPlayer from '../../src/components/players/LoadableBasicPlayer'

<BasicPlayer
showDefaultUi
defaultUiProps={{ noClickToPlay: true }}
/>
<br />

:::tip
Remember to load the default player theme or you might see something you regret 😱

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@vime/core@^5/themes/default.css"
/>
```

:::

Just like that we've setup an interface for audio/video/live media that looks good on both
mobile/desktop and is ARIA friendly... not bad 😎 &nbsp;

What if we want to put together our own UI? We can easily achieve this by mixing together predefined
components by Vime and creating our own. Let's say we only wanted to be able to click the player to toggle
playback, and to able to tap the sides to seek forward/backward. If we look through the components
in the `Components > UI` section in the sidebar (on your left), we see there is a
[`ClickToPlay`](../components/ui/click-to-play) component which solves our first requirement, but
nothing seems to match our second requirement. This calls for a custom component, so let's see
how we can go about putting this together...

<Tabs
groupId="framework"
defaultValue="html"
values={[
{ label: 'HTML', value: 'html' },
{ label: 'React', value: 'react' },
{ label: 'Vue', value: 'vue' },
{ label: 'Svelte', value: 'svelte' },
{ label: 'Stencil', value: 'stencil' },
{ label: 'Angular', value: 'angular' }
]}>

<TabItem value="html">

:::caution

The following HTML example is not complete, feel free to contribute by helping us complete it 🙂

Here's some links for you to learn about web components:

- [Google Developers - Web Components](https://developers.google.com/web/fundamentals/web-components/customelements)
- [MDN - Web Components](https://developer.mozilla.org/en-US/docs/Web/Web_Components)
- [CSS Tricks - Introduction to Web Components](https://css-tricks.com/an-introduction-to-web-components/)
- [Robinwieruch - Web Component Tutorial for Beginners](https://www.robinwieruch.de/web-components-tutorial)

:::

```html {13-20} title="player.html"
<vm-player>
  <vm-video cross-origin="true" poster="https://media.vimejs.com/poster.png">
    <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
    <track
      default
      kind="subtitles"
      src="https://media.vimejs.com/subs/english.vtt"
      srclang="en"
      label="English"
    />
  </vm-video>

  <vm-ui>
    <!-- Vime components. -->
    <vm-click-to-play></vm-click-to-play>
    <vm-spinner></vm-spinner>
    <vm-poster></vm-poster>
    <!-- Custom web component. -->
    <tap-sides-to-seek></tap-sides-to-seek>
  </vm-ui>
</vm-player>
```

</TabItem>

<TabItem value="react">

:::info
You can view the custom `TapSidesToSeek` component [here](https://github.com/vime-js/vime/blob/master/examples/react/src/TapSidesToSeek.tsx).
:::

```tsx {19-26} title="Player.tsx"
import React from 'react';
import { Player, Video, Ui, ClickToPlay, Spinner, Poster } from '@vime/react';
import TapSidesToSeek from './TapSidesToSeek';

function Player() {
  return (
    <Player>
      <Video crossOrigin="" poster="https://media.vimejs.com/poster.png">
        <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
        <track
          default
          kind="subtitles"
          src="https://media.vimejs.com/subs/english.vtt"
          srcLang="en"
          label="English"
        />
      </Video>

      <Ui>
        {/* Vime components. */}
        <ClickToPlay />
        <Spinner />
        <Poster />
        {/* Custom component. */}
        <TapSidesToSeek />
      </Ui>
    </Player>
  );
}
```

</TabItem>

<TabItem value="vue">

:::info
You can view the custom `TapSidesToSeek` component [here](https://github.com/vime-js/vime/blob/master/examples/vue/src/TapSidesToSeek.vue).
:::

```html {15-22} title="Player.vue"
<template>
  <!-- Notice we turned off controls? We're supplying our own, so we hide the native ones. -->
  <Player>
    <video crossorigin="" poster="https://media.vimejs.com/poster.png">
      <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
      <track
        default
        kind="subtitles"
        src="https://media.vimejs.com/subs/english.vtt"
        srclang="en"
        label="English"
      />
    </video>

    <Ui>
      <!-- Vime components. -->
      <ClickToPlay />
      <Spinner />
      <Poster />
      <!-- Custom component. -->
      <TapSidesToSeek />
    </Ui>
  </Player>
</template>

<script>
  import { Player, Video, Ui, ClickToPlay, Spinner, Poster } from '@vime/vue';
  import TapSidesToSeek from './TapSidesToSeek.vue';

  export default {
    components: {
      Player,
      Video,
      Ui,
      ClickToPlay,
      Spinner,
      Poster,
      TapSidesToSeek,
    },
  };
</script>
```

</TabItem>

<TabItem value="svelte">

:::info
You can view the custom `TapSidesToSeek` component [here](https://github.com/vime-js/vime/blob/master/examples/svelte/src/TapSidesToSeek.svelte).
:::

```html {13-20} title="Player.svelte"
<Player>
  <Video crossorigin="" poster="https://media.vimejs.com/poster.png">
    <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
    <track
      default
      kind="subtitles"
      src="https://media.vimejs.com/subs/english.vtt"
      srclang="en"
      label="English"
    />
  </Video>

  <Ui>
    <!-- Vime components. -->
    <ClickToPlay />
    <Spinner />
    <Poster />
    <!-- Custom component. -->
    <TapSidesToSeek />
  </Ui>
</Player>

<script lang="ts">
  import {
    Player,
    Video,
    Ui,
    ClickToPlay,
    Spinner,
    Poster,
  } from '@vime/svelte';
  import TapSidesToSeek from './TapSidesToSeek.svelte';
</script>
```

</TabItem>

<TabItem value="stencil">

:::info
You can view the custom `<tap-sides-to-seek>` component [here](https://github.com/vime-js/vime/tree/master/examples/stencil/src/components/tap-sides-to-seek).
:::

```tsx {21-28} title="player.tsx"
class Player {
  // ...

  render() {
    return (
      <vm-player>
        <vm-video crossOrigin="" poster="https://media.vimejs.com/poster.png">
          <source
            data-src="https://media.vimejs.com/720p.mp4"
            type="video/mp4"
          />
          <track
            default
            kind="subtitles"
            src="https://media.vimejs.com/subs/english.vtt"
            srclang="en"
            label="English"
          />
        </vm-video>

        <vm-ui>
          {/* Vime components. */}
          <vm-click-to-play />
          <vm-spinner />
          <vm-poster />
          {/* Custom component. */}
          <tap-sides-to-seek />
        </vm-ui>
      </vm-player>
    );
  }
}
```

</TabItem>

<TabItem value="angular">

:::info
You can view the custom `<tap-sides-to-seek>` component [here](https://github.com/vime-js/vime/tree/master/examples/angular/src/app/tap-sides-to-seek).
:::

```html {13-20} title="player.html"
<vm-player>
  <vm-video cross-origin="true" poster="https://media.vimejs.com/poster.png">
    <source data-src="https://media.vimejs.com/720p.mp4" type="video/mp4" />
    <track
      default
      kind="subtitles"
      src="https://media.vimejs.com/subs/english.vtt"
      srclang="en"
      label="English"
    />
  </vm-video>

  <vm-ui>
    <!-- Vime components. -->
    <vm-click-to-play></vm-click-to-play>
    <vm-spinner></vm-spinner>
    <vm-poster></vm-poster>
    <!-- Custom component. -->
    <tap-sides-to-seek></tap-sides-to-seek>
  </vm-ui>
</vm-player>
```

</TabItem>
    
</Tabs>

Glorious! Here's the result 🥁 ...

import ClickPlayer from '../../src/components/players/LoadableClickPlayer';

:::tip
Click the player anywhere in the center region to toggle playback, and click to the sides to
seek forwards and backwards.
:::

<ClickPlayer />
<br />

So far we've seen how to setup our player and provider, load the default Vime interface and
how to put together our own. It's important to keep in mind, that the examples so far have been
kept simple on purpose, as they are focused mainly on getting you up and running... what you
create and how far you take it is up to you.

🚂 &nbsp;Let's move onto [controls!](./controls)
