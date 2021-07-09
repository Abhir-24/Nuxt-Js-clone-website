---
title: Writing content
description: 'Learn how to write your content/, supporting Markdown, YAML, CSV and JSON.'
position: 2
category: Getting started
multiselectOptions:
  - VuePress
  - Gridsome
  - Nuxt
---

First of all, create a `content/` directory in your project:

<br />

```bash
content/
  articles/
    article-1.md
    article-2.md
  home.md
```
<br />

This module will parse `.md`, `.yaml`, `.yml`, `.csv`, `.json`, `.json5`, `.xml` files and generate the following properties:

<br />

- `dir`
- `path`
- `slug`
- `extension` (ex: `.md`)
- `createdAt`
- `updatedAt`

<br />

The `createdAt` and `updatedAt` properties are based on the file's actual created & updated datetime, but you can override them by defining your own `createdAt` and `updatedAt` values. This is especially useful if you are migrating your past blog posts where the `createdAt` can be months or years ago.

<br /><br />

## Markdown

This module converts your `.md` files into a JSON AST tree structure, stored in a `body` variable.

Make sure to use the `<nuxt-content>` component to display the `body` of your markdown content, see [displaying content](/displaying).

<br />

> You can check the [basic syntax guide](https://www.markdownguide.org/basic-syntax) to help you master Markdown

<br /><br />

### Front Matter

<br />

You can add a YAML front matter block to your markdown files. The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines. Here is a basic example:

<br />

```md
---
title: Introduction
description: Learn how to use @nuxt/content.
---
```
<br />

These variables will be injected into the document:

<br />

```json
{
  body: Object
  excerpt: Object
  title: "Introduction"
  description: "Learn how to use @nuxt/content."
  dir: "/"
  extension: ".md"
  path: "/index"
  slug: "index"
  toc: Array
  createdAt: DateTime
  updatedAt: DateTime
}
```
<br /><br />

### Excerpt

<br />

Content excerpt or summary can be extracted from the content using `<!--more-->` as a divider.

<br />

```md
---
title: Introduction
---

Learn how to use @nuxt/content.
<!--more-->
Full amount of content beyond the more divider.
```
<br />

Description property will contain the excerpt content unless defined within the Front Matter props.

<br />

<alert type="info">

Be careful to enter <code>&lt;!--more--&gt;</code> exactly; i.e., all lowercase and with no whitespace.

</alert>

Example variables will be injected into the document:

<br />

```json
{
  body: Object
  title: "Introduction"
  description: "Learn how to use @nuxt/content."
  dir: "/"
  excerpt: Object
  extension: ".md"
  path: "/index"
  slug: "index"
  toc: Array
  createdAt: DateTime
  updatedAt: DateTime
}
```

<br /><br />

### Links

<br />

Links are transformed to add valid `target` and `rel` attributes using [remark-external-links](https://github.com/remarkjs/remark-external-links). You can check [here](/configuration#markdown) to learn how to configure this plugin.

<br />

Relative links are also automatically transformed to [nuxt-link](https://nuxtjs.org/api/components-nuxt-link/) to provide navigation between page components with enhanced performance through smart prefetching.

Here is an example using external, relative, markdown and html links:

<br />

```md
---
title: Home
---

## Links

<nuxt-link to="/articles">Nuxt Link to Blog</nuxt-link>

<a href="/articles">Html Link to Blog</a>

[Markdown Link to Blog](/articles)

<a href="https://nuxtjs.org">External link html</a>

[External Link markdown](https://nuxtjs.org)
```
<br />

### Footnotes

<br />

This module supports extended markdown syntax for footnotes using [remark-footnotes](https://github.com/remarkjs/remark-footnotes). You can check [here](/configuration#markdown) to learn how to configure this plugin.

<br />

Here is an example using footnotes:

<br />

```md
Here's a simple footnote,[^1] and here's a longer one.[^bignote]

[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.
```
<br />

> You can check the [extended syntax guide](https://www.markdownguide.org/extended-syntax/#footnotes) for more information about footnotes.

<br /><br />

### Codeblocks

<br />

This module automatically wraps codeblocks and applies [PrismJS](https://prismjs.com) classes (see [syntax highlighting](/writing#syntax-highlighting)).

Codeblocks in Markdown are wrapped inside 3 backticks. Optionally, you can define the language of the codeblock to enable specific syntax highlighting.

<br />

Orginally markdown does not support filenames or highlighting specific lines inside codeblocks. However, this module allows it with its own custom syntax:

<br />

- Highlighted line numbers inside curly braces
- Filename inside square brackets

<br />

<pre class="language-js">
```js{1,3-5}[server.js]
const http = require('http')
const bodyParser = require('body-parser')

http.createServer((req, res) => {
  bodyParser.parse(req, (error, body) => {
    res.end(body)
  })
}).listen(3000)
```
</pre>

<br />

After rendering with the `nuxt-content` component, it should look like this (without the filename yet):

<br />

```html[server.js]
<div class="nuxt-content-highlight">
  <span class="filename">server.js</span>
  <pre class="language-js" data-line="1,3-5">
    <code>
      ...
    </code>
  </pre>
</div>
```
<br />

Line numbers are added to the `pre` tag in `data-line` attribute.

<br />

> Check out [this comment](https://github.com/nuxt/content/issues/28#issuecomment-633246962) on how to render prism line numbers.

<br />

Filename will be converted to a span with a `filename` class, it's up to you to style it.

<br />

> Check out [the main.css file](https://github.com/nuxt/content/blob/dev/packages/theme-docs/src/assets/css/main.css#L56) of this documentation for an example on styling filenames.

<br /><br />

### Syntax highlighting

<br />

It supports by default code highlighting using [PrismJS](https://prismjs.com) and injects the theme defined in options into your Nuxt.js app, see [configuration](/configuration#markdownprismtheme).

<br /><br />

### HTML

<br />

You can write HTML in your Markdown:

<br />

```md[home.md]
---
title: Home
---

## HTML

<p><span class="note">A mix of <em>Markdown</em> and <em>HTML</em>.</span></p>
```
<br />

Beware that when placing Markdown inside a component, it must be preceded and followed by an empty line, otherwise the whole block is treated as custom HTML.

<br />

**This won't work:**

```html
<div class="note">
  *Markdown* and <em>HTML</em>.
</div>
```
<br />

**But this will:**

```html
<div class="note">

  *Markdown* and <em>HTML</em>.

</div>
```
<br />

**As will this**:

```html
<span class="note">*Markdown* and <em>HTML</em>.</span>
```
<br /><br />

### Vue components

<br />

You can use global Vue components or locally registered in the page you're displaying your markdown.

<br />

<alert type="warning">

An issue exists with locally registered components and live edit in development, since **v1.5.0** you can disable it by setting `liveEdit: false` (see [configuration](/configuration#liveedit)).

</alert>

<br />

Since `@nuxt/content` operates under the assumption all Markdown is provided by the author (and not via third-party user submission), sources are processed in full (tags included), with a couple of caveats from [rehype-raw](https://github.com/rehypejs/rehype-raw):

<br />

1. You need to refer to your components by kebab case naming:

```html
Use <my-component> instead of <MyComponent>
```
<br />

2. You cannot use self-closing tags, i.e., **this won't work**:

```html
<my-component/>
```
<br />

But **this will**:

```html
<my-component></my-component>
```

<br />

**Example**

<br />

Say we have a Vue component called [ExampleMultiselect.vue](https://github.com/nuxt/content/blob/master/docs/components/global/examples/ExampleMultiselect.vue):

<br />

```md[home.md]
Please choose a *framework*:

<example-multiselect :options="['Vue', 'React', 'Angular', 'Svelte']"></example-multiselect>
```
<br />

**Result**

<br />

<div class="border rounded-md p-2 mb-2 bg-gray-200 dark:bg-gray-800">
Please choose a <i>framework</i>:

<example-multiselect :options="['Vue', 'React', 'Angular', 'Svelte']"></example-multiselect>

</div>

<br />

You can also define the options for components in your front matter:

<br />

```md[home.md]
---
multiselectOptions:
  - VuePress
  - Gridsome
  - Nuxt
---

<example-multiselect :options="multiselectOptions"></example-multiselect>
```

<example-multiselect :options="multiselectOptions"></example-multiselect><br>

<alert type="info">

These components will be rendered using the `<nuxt-content>` component, see [displaying content](/displaying#component).

</alert>

<br /><br />

#### Templates
<br />

You can use `template` tags for content distribution inside your Vue.js components:

<br />

```html
<my-component>
  <template #named-slot>
    <p>Named slot content.</p>
  </template>
</my-component>
```
<br />

However, you cannot render
[dynamic content](https://vuejs.org/v2/guide/syntax.html) nor use
[slot props](https://vuejs.org/v2/guide/components-slots.html#Scoped-Slots). I.e.,
**this wont work**:

<br />

```html
<my-component>
  <template #named-slot="slotProps">
    <p>{{ slotProps.someProperty }}</p>
  </template>
</my-component>
```
<br /><br />

#### Global components

<br />

Since **v1.4.0** and Nuxt **v2.13.0**, you can now put your components in `components/global/` directory so you don't have to import them in your pages.

<br />

```bash
components/
  global/
    Hello.vue
content/
  home.md
```
<br />

Then in `content/home.md`, you can use `<hello></hello>` component without having to worry about importing it in your page.

<br /><br /><br />
