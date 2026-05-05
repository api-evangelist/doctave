---
title: "The path to structured content with Markdown"
url: "https://www.doctave.com/blog/path-to-structured-markdown"
date: "Thu, 06 Jun 2024 10:00:00 +0300"
author: ""
feed_url: "https://www.doctave.com/feed.xml"
---
<p>This post was inspired by the <a href="https://www.brighttalk.com/webcast/9273/608016" target="_blank">Pros and Cons of Using Markdown for Technical Documentation Panel Discussion</a> with <a href="https://edmarsh.com/">Ed Marsh</a>, <a href="https://ericholscher.com/">Eric Holscher</a>, and <a href="https://passo.uno/">Fabrizio Ferri-Benedetti</a>. Around the ~40 minute mark the discussion moves onto how to maintain a consistent style with Markdown documentation, especially in larger teams.</p>

<p>The panel agrees that currently there are no clear ways to enforce a specific document structure when using Markdown.</p>

<p>Fabrizzio then on goes on to say (54:15):</p>

<blockquote>
  <p>Some day, someone is going to figure out a way to seamlessly grow Markdown into something that can mature into structured content</p>
</blockquote>

<p>I’ve been thinking about this a lot, and my claim is that Markdown and XML (which is traditionally used for structured authoring) are more similar than you would initially expect, and that the dream of adding validations and structure to Markdown is perhaps not too far away.</p>

<h2 id="the-structure-behind-markdown">The structure behind Markdown</h2>

<p>There’s a commonly held belief that Markdown is not structured. There is some truth to this, but I’d argue it’s more the case that the structure is <em>hidden</em>. While with most XML-based authoring tools you are manipulating the structure directly (or through a WYSIWYG editor), with Markdown we are one level removed from the actual underlying structure.</p>

<p>To demonstrate, let’s take a look at a quick example at how Markdown is actually almost equivalent to XML, if you squint a little.</p>

<p>Let’s take this Markdown content.</p>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
</pre></td><td class="rouge-code"><pre><span class="gh"># Hello, world</span>

This is a paragraph <span class="gs">**with some bold text**</span>

<span class="p">![</span><span class="nv">and this is an image</span><span class="p">](</span><span class="sx">cat.jpg</span><span class="p">)</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>When this Markdown is processed into HTML, it goes through a number of transformations. The first thing that happens is that the Markdown is converted into an <strong><a href="https://en.wikipedia.org/wiki/Abstract_syntax_tree">Abstract Syntax Tree</a></strong>. This means taking the raw text of the Markdown, and converting into something more <em>structured</em> that a program can manipulate.</p>

<p>Each Markdown parser does this a little bit differently, but we can see this in action with, for example, the <a href="https://astexplorer.net/">AST Explorer tool</a>. Let’s take Markdown above, and paste it into this tool to inspect the AST, and select the <em>JSON</em> output format.</p>

<p>We get something like this (I’ve removed some unimportant fields for brevity).</p>
<div class="language-json highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
</pre></td><td class="rouge-code"><pre><span class="p">{</span><span class="w">
  </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"root"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"children"</span><span class="p">:</span><span class="w"> </span><span class="p">[</span><span class="w">
    </span><span class="p">{</span><span class="w">
      </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"element"</span><span class="p">,</span><span class="w">
      </span><span class="nl">"tagName"</span><span class="p">:</span><span class="w"> </span><span class="s2">"h1"</span><span class="p">,</span><span class="w">
      </span><span class="nl">"children"</span><span class="p">:</span><span class="w"> </span><span class="p">[</span><span class="w">
        </span><span class="p">{</span><span class="w">
          </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"text"</span><span class="p">,</span><span class="w">
          </span><span class="nl">"value"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Hello, world"</span><span class="w">
        </span><span class="p">}</span><span class="w">
      </span><span class="p">]</span><span class="w">
    </span><span class="p">},</span><span class="w">
    </span><span class="p">{</span><span class="w">
      </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"element"</span><span class="p">,</span><span class="w">
      </span><span class="nl">"tagName"</span><span class="p">:</span><span class="w"> </span><span class="s2">"p"</span><span class="p">,</span><span class="w">
      </span><span class="nl">"children"</span><span class="p">:</span><span class="w"> </span><span class="p">[</span><span class="w">
        </span><span class="p">{</span><span class="w">
          </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"text"</span><span class="p">,</span><span class="w">
          </span><span class="nl">"value"</span><span class="p">:</span><span class="w"> </span><span class="s2">"This is a paragraph "</span><span class="w">
        </span><span class="p">},</span><span class="w">
        </span><span class="p">{</span><span class="w">
          </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"element"</span><span class="p">,</span><span class="w">
          </span><span class="nl">"tagName"</span><span class="p">:</span><span class="w"> </span><span class="s2">"strong"</span><span class="p">,</span><span class="w">
          </span><span class="nl">"children"</span><span class="p">:</span><span class="w"> </span><span class="p">[</span><span class="w">
            </span><span class="p">{</span><span class="w">
              </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"text"</span><span class="p">,</span><span class="w">
              </span><span class="nl">"value"</span><span class="p">:</span><span class="w"> </span><span class="s2">"with some bold text"</span><span class="w">
            </span><span class="p">}</span><span class="w">
          </span><span class="p">]</span><span class="w">
        </span><span class="p">}</span><span class="w">
      </span><span class="p">]</span><span class="w">
    </span><span class="p">},</span><span class="w">
    </span><span class="p">{</span><span class="w">
      </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"element"</span><span class="p">,</span><span class="w">
      </span><span class="nl">"tagName"</span><span class="p">:</span><span class="w"> </span><span class="s2">"p"</span><span class="p">,</span><span class="w">
      </span><span class="nl">"children"</span><span class="p">:</span><span class="w"> </span><span class="p">[</span><span class="w">
        </span><span class="p">{</span><span class="w">
          </span><span class="nl">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"element"</span><span class="p">,</span><span class="w">
          </span><span class="nl">"tagName"</span><span class="p">:</span><span class="w"> </span><span class="s2">"img"</span><span class="p">,</span><span class="w">
          </span><span class="nl">"properties"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span><span class="w">
            </span><span class="nl">"src"</span><span class="p">:</span><span class="w"> </span><span class="s2">"cat.jpg"</span><span class="p">,</span><span class="w">
            </span><span class="nl">"alt"</span><span class="p">:</span><span class="w"> </span><span class="s2">"and this is an image"</span><span class="w">
          </span><span class="p">}</span><span class="w">
        </span><span class="p">}</span><span class="w">
      </span><span class="p">]</span><span class="w">
    </span><span class="p">}</span><span class="w">
  </span><span class="p">]</span><span class="w">
</span><span class="p">}</span><span class="w">
</span></pre></td></tr></tbody></table></code></pre></div></div>

<p>The Markdown has been transformed into a tree structure. The top level object is of type <strong>root</strong>, which has a list of children. This object has three children, the first being the <strong>header</strong>, and the other two are <strong>paragraphs</strong>. The first contains some text, a part of which is bolded, and the latter an <strong>image</strong>.</p>

<p>Now, if we compare this to an equivalent DITA topic:</p>

<div class="language-xml highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
8
9
10
11
</pre></td><td class="rouge-code"><pre><span class="cp">&lt;?xml version="1.0" encoding="UTF-8"?&gt;</span>
<span class="cp">&lt;!DOCTYPE topic PUBLIC "-//OASIS//DTD DITA Topic//EN" "topic.dtd"&gt;</span>
<span class="nt">&lt;topic</span> <span class="na">id=</span><span class="s">"hello-world"</span><span class="nt">&gt;</span>
    <span class="nt">&lt;title&gt;</span>Hello, world<span class="nt">&lt;/title&gt;</span>
    <span class="nt">&lt;body&gt;</span>
        <span class="nt">&lt;p&gt;</span>This is a paragraph <span class="nt">&lt;b&gt;</span>with some bold text<span class="nt">&lt;/b&gt;&lt;/p&gt;</span>
        <span class="nt">&lt;p&gt;</span>
            <span class="nt">&lt;image</span> <span class="na">href=</span><span class="s">"../images/cat.jpg"</span> <span class="na">alt=</span><span class="s">"and this is an image"</span><span class="nt">/&gt;</span>
        <span class="nt">&lt;/p&gt;</span>
    <span class="nt">&lt;/body&gt;</span>
<span class="nt">&lt;/topic&gt;</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>Because it’s JSON, it’s a bit more verbose, but fundamentally <strong>the same structure and information is there</strong>. In fact, you could convert the JSON into XML to get to something very close to DITA.</p>

<p>This becomes even more clear when this AST finally gets converted to HTML as part of the Markdown to HTML pipeline:</p>

<div class="language-html highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
</pre></td><td class="rouge-code"><pre><span class="nt">&lt;h1&gt;</span>Hello, world<span class="nt">&lt;/h1&gt;</span>
<span class="nt">&lt;p&gt;</span>This is a paragraph <span class="nt">&lt;strong&gt;</span>with some bold text<span class="nt">&lt;/strong&gt;&lt;/p&gt;</span>
<span class="nt">&lt;p&gt;&lt;img</span> <span class="na">src=</span><span class="s">"cat.jpg"</span> <span class="na">alt=</span><span class="s">"and this is an image"</span><span class="nt">&gt;&lt;/p&gt;</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>Markdown is just a level “above” XML, but it is representing very similar information.</p>

<h2 id="the-horror-of-markdown-templating">The horror of Markdown templating</h2>

<p>With bigger projects you eventually want to enable some kind of content reuse.</p>

<p>The issue is that <strong>all tools incorrectly tend to assume Markdown can be processed as just text</strong>. This causes surprising breakage and prevents robust templating and content reuse.</p>

<p>Let me demonstrate.</p>

<p>Let’s say you have a warning snippet that you want to reuse across your pages:</p>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
</pre></td><td class="rouge-code"><pre><span class="gs">**Warning**</span>

Do not attempt without expert supervision
</pre></td></tr></tbody></table></code></pre></div></div>

<p>Next, let’s say I’m creating a list of steps in Markdown, and I want to include this snippet (I’m assuming Liquid syntax here).</p>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
</pre></td><td class="rouge-code"><pre><span class="p">1.</span> Press the big red button

   {% include "snippets/warning.md" %}
<span class="p">
2.</span> Perform questionable science
<span class="p">
3.</span> Profit??
</pre></td></tr></tbody></table></code></pre></div></div>

<p>This will, slightly surprisingly, not work, and your list will be broken:</p>

<ol>
  <li>
    <p>Press the big red button</p>

    <p><strong>Warning</strong></p>
  </li>
</ol>

<p>Do not attempt without expert supervision</p>

<ol>
  <li>
    <p>Perform questionable science</p>
  </li>
  <li>
    <p>Profit??</p>
  </li>
</ol>

<p>Note how the list is not ordered correctly, and the second line of the snippet is not rendered inside the list.</p>

<p>The reason for this is that unlike XML, Markdown is <strong>whitespace-sensitive</strong>. When Liquid does the string template replacement, what you actually are doing is this:</p>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
8
9
10
</pre></td><td class="rouge-code"><pre><span class="p">1.</span> Press the big red button

   <span class="c">&lt;!-- snippet is injected here --&gt;</span>
   <span class="gs">**Warning**</span>

Do not attempt without expert supervision   <span class="c">&lt;!-- Incorrectly indented --&gt;</span>
<span class="p">
2.</span> Perform questionable science
<span class="p">
3.</span> Profit??
</pre></td></tr></tbody></table></code></pre></div></div>

<p>The <code class="language-plaintext highlighter-rouge">include</code> snippet was just replaced verbatim with the content of the snippet file.</p>

<p>But because the indentation did not exist in the snippet, the second line is not indented correctly in the list, breaking the flow of the ordered list.</p>

<p><strong>Any robust template system used for Markdown needs to be aware of the Markdown syntax itself</strong>.</p>

<p>This is something we learnt the hard way at Doctave, and fixed in our <a href="/blog/doctave-v2">2.0 release</a>. Our template and component system is fully Markdown-aware, which removes pitfalls like the one above. Stripe also solved this with <a href="https://markdoc.dev/">Markdoc</a>. Both options can handle the case described above - they can see <em>“ah, I’m inside a list, so I know that the paragraph must be made a child of the list item”</em> instead of doing naive string replacements.</p>

<p>This should be considered table stakes for any authoring system using Markdown.</p>

<h2 id="enforcing-structure">Enforcing structure</h2>

<p>Now we get to the part that does not exist today: how can you ensure and validate a consistent structure in your Markdown-based documentation project? There’s a great section in the <a href="https://www.brighttalk.com/webcast/9273/608016">panel discussion above</a> at around 45 minutes on this topic.</p>

<p>DITA and other structured authoring tools were designed for this: using schemas and other structures to ensure that your content conforms to a specific standard. Be it for maintaining consistency and/or ensuring legal or regulatory compliance, this is what lets you scale large authoring teams and projects.</p>

<p>Markdown, on the other hand, doesn’t support this. While we can use tools like <a href="https://vale.sh/">Vale</a> to help us enforce a style guide, constraining the actual structure of the Markdown isn’t something that we can do.</p>

<p>Think about how in Markdown you would ensure that <em>“all our how-to guides must have an h1 title, followed by one or more paragraphs, followed by one or more steps to achieve the guide’s goal”</em>, and then consider how <a href="https://www.oxygenxml.com/dita/1.3/specs/archSpec/technicalContent/dita-task-topic.html">easy it is</a> in DITA.</p>

<p>This is just not really possible today, at least in any popular Markdown-based framework.</p>

<h2 id="there-is-a-path">There is a path</h2>

<p>Bridging the gap between Markdown and structured authoring will require building new tooling and standards. It’s unlikely that CommonMark or any other popular Markdown flavor would consider going in this direction, so we’ll have to create tools <em>around</em> Markdown.</p>

<p>We at Doctave have some ideas about how to achieve this, and have a roadmap on how to get there. At a high level there are a few things we would need:</p>

<ul>
  <li><strong>✅ A parser and template system that is Markdown-aware</strong></li>
  <li><strong>❌ A language for describing constraints and rules for your Markdown content</strong></li>
  <li><strong>❌ An engine that enforces those rules on your content</strong></li>
</ul>

<p>We’re already part of the way there!</p>

<p>Let’s imagine a world for a moment where you could add a little annotation to your Markdown file and have a format enforced:</p>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
</pre></td><td class="rouge-code"><pre><span class="p">---</span>
<span class="gh">schema: ../schemas/task.schema
--
</span>
<span class="gh"># Uploading files</span>

...
</pre></td></tr></tbody></table></code></pre></div></div>

<p>Or perhaps MDX-inspired format where Markdown is embedded inside HTML-like tags:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
8
9
</pre></td><td class="rouge-code"><pre>&lt;Task&gt;
  &lt;Task.Title&gt;
    Uploading Files
  &lt;/Task.Title&gt;

  &lt;Task.Description&gt;
    To upload files using our [portal](https://www.example.com)...
  &lt;/Task.Description&gt;
&lt;/Task&gt;
</pre></td></tr></tbody></table></code></pre></div></div>

<p>And your format would be validated automatically:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
</pre></td><td class="rouge-code"><pre>Document validation error

  &lt;Task&gt;
  ▲▲▲▲▲▲
    └─ Missing `Title` field
</pre></td></tr></tbody></table></code></pre></div></div>

<p>This would let you enjoy the low barrier to entry of Markdown, but scale up to a more robust authoring system, layering on rules and schemas as required.</p>

<p>Fundamentally, this is possible. We just need to go out and build it.</p>

<p>I find this really exciting, and something we are exploring at Doctave. If you have ideas or opinions about this area, or just want to nerd out about Markdown toolchains, reach out! You can email me at nik@doctave.com.</p>
