[[ReadItLater]] [[Article]]

# [Using GPT-3 to explain how code works](https://simonwillison.net/2022/Jul/9/gpt-3-explain-code/)

One of my favourite uses for the GPT-3 AI language model is generating explanations of how code works. It’s shockingly effective at this: its training set clearly include a vast amount of source code.

(I initially thought this was related to GitHub Copilot being built on GPT-3, but actually that’s built on a GPT-3 descendent called [OpenAI Codex](https://openai.com/blog/openai-codex/).)

Here are a few recent examples.

#### Explaining some Python

Ned Batchelder [shared](https://gist.github.com/nedbat/3676fdc9b3135b8f6a6c44447af906e1) this brilliant Python code snippet [on Twitter](https://twitter.com/nedbat/status/1545772259402338304) this morning:

import re

TOKEN\_RX \= r"""(?xm)
    (?P<string> ".\*?"|'.\*?'             )| 
    (?P<float>  \\d\*(\\d\\.|\\.\\d)\\d\*       )|
    (?P<int>    \\d+                     )|
    (?P<id>     \[\_a-zA-Z\]\[\_a-zA-Z0-9\]\*  )|
    (?P<punct>  \[(){}:\\\[\\\]=.,+\*/-\]      )|
    (           \\#.\*$                   )|
    (           \\s+                     )
    """

def tokens(text):
    for match in re.finditer(TOKEN\_RX, text):
        if match.lastgroup:
            yield (match.lastgroup, match\[0\])

TEXT \= """
    x = 123 + "hello #99"  # ignore me!
    print(hello.bye\[0\] + 3.14, 'single')
    """

for kind, text in tokens(TEXT):
    print(f"{kind:7}: {text\=}")

I pasted it into GPT-3 (here’s [how to use the playground interface](https://simonwillison.net/2022/Jun/5/play-with-gpt3/)) and started asking questions.

This uses the feature of GPT-3 where you can get a response, then add more text and run it again to get further details.

Anything in bold is text that GPT-3 responded with. The rest are my prompts.

> Explain this code:
> 
> ```
> import re
> 
> TOKEN_RX = r"""(?xm)
>     (?P<string> ".*?"|'.*?'             )| 
>     (?P<float>  \d*(\d\.|\.\d)\d*       )|
>     (?P<int>    \d+                     )|
>     (?P<id>     [_a-zA-Z][_a-zA-Z0-9]*  )|
>     (?P<punct>  [(){}:\[\]=.,+*/-]      )|
>     (           \#.*$                   )|
>     (           \s+                     )
>     """
> 
> def tokens(text):
>     for match in re.finditer(TOKEN_RX, text):
>         if match.lastgroup:
>             yield (match.lastgroup, match[0])
> 
> TEXT = """
>     x = 123 + "hello #99"  # ignore me!
>     print(hello.bye[0] + 3.14, 'single')
>     """
> 
> for kind, text in tokens(TEXT):
>     print(f"{kind:7}: {text=}")
> ```
> 
> **The code is defining a regular expression that will match different types of tokens in a string of text. The different groups defined in the regular expression will match different types of tokens, such as strings, floats, ints, ids, punctuation, and comments. The code will then iterate over the matches and yield the type of token and the text that was matched.**
> 
> Explain the regular expression:
> 
> **The regular expression is made up of a number of different groups, each of which match a different type of token. The first group, “string”, matches any text enclosed in double or single quotes. The second group, “float”, matches any text that looks like a floating point number. The third group, “int”, matches any text that looks like an integer. The fourth group, “id”, matches any text that looks like a variable name. The fifth group, “punct”, matches any text that looks like punctuation. The sixth group, “#.\*$”, matches any text that looks like a comment. The seventh group, “\\s+”, matches any text that looks like whitespace.**
> 
> What does (?xm) do?
> 
> **The (?xm) notation is a modifier that allows the regular expression to span multiple lines and to use comments.**
> 
> Why does it use match.lastgroup?
> 
> **The match.lastgroup variable contains the name of the last group that was matched by the regular expression. This is used to determine the type of token that was matched.**

This is a really good, really clear explanation of what’s going on.

I already knew how that code works though. Let’s try something that I genuinely didn’t understand.

#### Explaining some JavaScript

Chris Haynes [tweeted](https://twitter.com/wcbytes/status/1541546418539732997) an ingenious demo showing how the new Web Component Declarative Shadow DOM `<slot>` mechanism ([described here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/slot)) can be used to create a page that streams content from a server, filling in different regions of the page as the content arrives—without using any JavaScript!

His demo is at [enamel.pages.dev](https://enamel.pages.dev/) but only works for me in Chrome. For other browsers, he provides [enamel.pages.dev/?js](https://enamel.pages.dev/?js) which loads a tiny polyfill.

The polyfill code lives in [enamel-lite.js](https://enamel.pages.dev/enamel-lite.js) and I could not figure out how it works. So I asked GPT-3.

> Explain this code:
> 
> ```
> class Enamel extends HTMLElement {
>   attemptPolyfillDSD() {
>     const dsd = this.querySelector('template[shadowroot]');
> 
>     if (dsd?.content) {
>       const mode = dsd.getAttribute('shadowroot');
>       this.attachShadow({ mode });
>       this.shadowRoot.appendChild(dsd.content);
> 
>       dsd.remove();
> 
>       return true;
>     }
> 
>     return false;
>   }
> 
>   connectedCallback() {
>     if (
>       !HTMLTemplateElement.prototype.hasOwnProperty('shadowRoot') &&
>       !this.attemptPolyfillDSD()
>     ) {
>       const _observer = new MutationObserver(() => {
>         if (this.attemptPolyfillDSD()) {
>           _observer.disconnect();
>         }
>       });
> 
>       _observer.observe(this, {
>         childList: true,
>       });
>     }
>   }
> }
> 
> export default Enamel;
> ```
> 
> **This code polyfills the Shadow DOM API for older browsers that do not support it.**

OK, that sounds convincing, but it’s not enough information for me. So I added another prompt:

> How does it do that?
> 
> **The code uses a MutationObserver to watch for changes to the element’s children. When a new child is added, the code checks to see if that child is a `<template>` element with a ’shadowroot’ attribute. If so, the code creates a Shadow Root for the element and appends the template’s content to it. Finally, the code removes the template element from the DOM.**

That is a *really* good explanation. After reading that, I went back to look at the code again and I now completely understand how it works.

#### Building some SQL

I wanted to build a SQL query that would return all of the rows in one table that were not represented in another table... but where the rows used a compound primary key covering two columns. I didn’t know the right syntax for this off the top of my head.

First, I needed to create a table with a compound primary key. Rather than look that up I asked GPT-3 directly:

> SQLite create a pages table that has a compound primary key of type, id and a content column.
> 
> **CREATE TABLE pages ( type TEXT, id TEXT, content TEXT, PRIMARY KEY (type, id) );**

It seems to know about SQLite SQL syntax, which is handy. Turns out you create a compound primary key using `PRIMARY KEY (col1, col2)` at the end of the table definition.

I added a second line with my own CREATE TABLE, then asked it to build me a query:

> CREATE TABLE pages\_done ( type TEXT, id TEXT, PRIMARY KEY (type, id) );
> 
> SQL query returning rows in the pages table that do not have corresponding records in the pages\_done table:
> 
> **SELECT type, id, content FROM pages WHERE (type, id) NOT IN (SELECT type, id FROM pages\_done)**

This is useful! I thought that a `WHERE ... NOT IN (SELECT` pattern would be good here, but I wasn’t sure of the syntax for looking up two columns at once.

I’m pretty sure this could instead be solved with a join... so I asked that too:

> That query but using a join:
> 
> **SELECT p.type, p.id, p.content FROM pages p LEFT JOIN pages\_done pd ON p.type = pd.type AND p.id = pd.id WHERE pd.type IS NULL;**

But which is better? I posed two more questions:

> Which of those two queries is more efficient and why?
> 
> **The first query is more efficient because it uses a WHERE clause with a subquery. The second query is less efficient because it uses a LEFT JOIN.**
> 
> Why is a subquery more efficient?
> 
> **A subquery is more efficient because it only returns the rows that meet the conditions specified in the WHERE clause. A LEFT JOIN returns all rows from the left table, even if there is no match in the right table.**

As with everything GPT-3, this answer sounds very convincing! But is this actually true? I would expect the SQL query optimizer to be smart enough to optimize the `LEFT JOIN` to the point where it would run efficiently. I think GPT-3’s answer to that question is actually very misleading.

And that’s not surprising, because GPT-3 doesn’t actually know anything about anything at all. It’s a huge pattern generator. You can’t trust anything it says, because all it does is group words together into convincing looking shapes based on text that it’s seen before.

Once again, I’m reminded that tools like GPT-3 should be classified in the “bicycles for the mind” category. You still have to know how to pedal!

They’re fantastic tools for thinking, but to actually use their output effectively requires VERY deep knowledge—both of the subject matter in question, and of the way that the AI tools themselves work.

#### Leading questions

Got this great tip [from Riley Goodside](https://twitter.com/goodside/status/1545791351991795713):

> When prompting like this, it’s important (and difficult) to avoid leading questions. If you ask which of two queries are more efficient and why, it’s extremely unlikely to to say “It doesn’t matter,” no matter how true that is.

I hadn’t considered this at all. I’ll be keeping that in mind in my future experiments.

#### Bonus: how about mathematics?

I decided to try one more thing: could it explain mathematical equations?

GitHub [recently added](https://github.blog/2022-05-19-math-support-in-markdown/) LaTeX rendering to their Markdown implementation. I grabbed a formula at random from [this page of documentation](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions):

> Explain this:
> 
> `$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$`
> 
> **This is the Cauchy-Schwarz inequality.**

OK, so you know what it’s called. But how does it work?

I added “Explain the formula syntax step by step, using $ wrapped around the formula steps:” (the `$` bit is explained in a moment):

> ```
> $\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$
> 
> This is the Cauchy-Schwarz inequality.
> 
> $\left( \sum_{k=1}^n a_k b_k \right)^2$
> 
> This is the sum of all products of corresponding elements in the vectors a and b, squared.
> 
> $\leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$
> 
> This is saying that this sum is less than or equal to the product of the sums of the squares of each vector.
> ```

Here’s why I added that bit about `$` to the prompt: doing so caused it to produce its answer in valid GitHub Markdown syntax. I [pasted that into a Gist](https://gist.github.com/simonw/5741ffa7e21dd8c2f1b845f6a0c48d5a) and rendered it, and it came out like this:

![That same thing but with rendered mathematical equations for the different step explanations](ReadItLater%20Inbox/assets/That%20same%20thing%20but%20with%20rendered%20mathematical%20equations%20for%20the%20different%20step%20explanations.png)

#### Explaining configuration files

Here’s another prompt pattern I stumbled across that seems to work really well: “Explain every line of this config file:”. I tried it against the [Lit example](https://github.com/vitejs/vite/blob/24f4f62c5807f40ec45ec5834328d4b5cec47753/packages/create-vite/template-lit/vite.config.js) from the [Vite 3.0 starter templates](https://vitejs.dev/blog/announcing-vite3.html#create-vite-starter-templates):

> Explain every line of this config file:
> 
> ```
> import { defineConfig } from 'vite'
> 
> // https://vitejs.dev/config/
> export default defineConfig({
>   build: {
>     lib: {
>       entry: 'src/my-element.js',
>       formats: ['es']
>     },
>     rollupOptions: {
>       external: /^lit/
>     }
>   }
> })
> ```
> 
> **This config file is written in JavaScript, using the ViteJS library. The first line imports the “defineConfig” function from the ViteJS library. This function allows the user to define a configuration object for the build process.**
> 
> **The next line exports the “defineConfig” function as the default export. This means that when this file is imported, the “defineConfig” function will be the only thing that is imported.**
> 
> **The “defineConfig” function takes one argument, which is an object. This object contains the configuration for the build process. The “build” property contains the configuration for the build tool. The “lib” property contains the configuration for the library that will be built. The “entry” property contains the path to the entry file for the library. The “formats” property contains the formats that the library will be built in. In this case, the library will only be built in the “es” format.**
> 
> **The “rollupOptions” property contains the configuration for the Rollup tool. The “external” property contains a regular expression that matches the names of the dependencies that should be excluded from the build. In this case, all dependencies whose names start with “lit” will be excluded from the build.**