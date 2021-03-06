# The Extended Syntax work is now moved to the [original repo](https://github.com/ubersl0th/markdown)   
# markdown

Deno Markdown module with Front-matter support forked from https://github.com/ubersl0th/markdown 

### Example usage

Simple md2html.ts script:

```typescript
import { Marked } from "./mod.ts";

const decoder = new TextDecoder("utf-8");
const filename = Deno.args[0];
const markdown = decoder.decode(await Deno.readFile(filename));
const marked = Marked.parse(markdown);
console.log(marked.content);
console.log(marked.metadata);
```

Now running:

```bash
deno run --allow-read md2html.ts example.md > example.html
```

```html
<h1 id="hello-world" href="#hello-world">Hello World</h1>
<h2 id="this-an-example-for-md2html-ts-" href="#this-an-example-for-md2html-ts-">This an example for <code>md2html.ts</code></h2>
<p>A small paragraph that will become a <code>&lt;p&gt;</code> tag</p>
<hr>
<p>Code Block (md2html.ts)</p>

<pre><code class="lang-typescript">import { Marked } from &quot;./mod.ts&quot;;

const decoder = new TextDecoder(&quot;utf-8&quot;);
const filename = Deno.args[0];
const markdown = decoder.decode(await Deno.readFile(filename));
const markup = Marked.parse(markdown);
</code></pre>
<p>
  This module is forked from
  <a
    href="https://github.com/ts-stack/markdown/tree/bb47aa8e625e89e6aa84f49a98536a3089dee831"
    >ts-stack/markdown</a
  >
</p>
<p>Made for Deno <img src="https://deno.land/logo.svg" alt="deno-logo" /></p>

{
  title: "Hello world!",
  subtitle: "Front-matter test",
  an-ordinary-list: [ "this", "is", { a: "list" } ]
}
```

---

### Notes

I had to do some changes to the source code to make the compiler happy, mostly fixes for things that were uninitialized and possibly null or undefined
