---
title: Displaying content
description: 'You can use `<nuxt-content>` component directly in your template to display your Markdown.'
position: 1
category: Getting started

---

<alert type="info">This section is only for Markdown files.</alert>
<br />
<br />

## Component

<br />

### Page Body

<br />

You can use `<nuxt-content>` component directly in your template to display the page body:

<br />

```vue
<template>
  <article>
    <h1>{{ page.title }}</h1>
    <nuxt-content :document="page" />
  </article>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const page = await $content('home').fetch()

    return {
      page
    }
  }
}
</script>
```
<br />

**Props:**
<br />
<br />

- document:

<br />

  - Type: `Object`
  - `required`

  <br />

Learn more about what you can write in your markdown file in the [writing content](/writing#markdown) section.

<br /><br />

### Excerpt

<br />


If you are utilizing the [excerpt](/writing#excerpt) feature, you can display the content of your excerpt using the following model:

<br />

```vue
<template>
  <article>
    <h1>{{ page.title }}</h1>
    <nuxt-content :document="{ body: page.excerpt }" />
  </article>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const page = await $content('home').fetch()

    return {
      page
    }
  }
}
</script>
```
<br />

## Style

<br />

Depending on what you're using to design your app, you may need to write some style to properly display the markdown.

`<nuxt-content>` component will automatically add a `.nuxt-content` class, you can use it to customize your styles:

<br />

```css
.nuxt-content h1 {
  /* my custom h1 style */
}
```
<br />

> You can find an example in the theme-docs [main.css](https://github.com/nuxt/content/blob/master/packages/theme-docs/src/assets/css/main.css) file. You can also take a look at the [TailwindCSS Typography plugin](https://tailwindcss.com/docs/typography-plugin) to style your markdown content like we do in the `@nuxt/content-theme-docs`.

<br /><br />

## Live Editing

<br />

> Available in version **>= v1.4.0**

<br />

**In development**, you can edit your content by **double-clicking** on the `<nuxt-content>` component. A textarea will allow you to edit the content of the current file and will save it on the file-system.

<br /><br /><br />
