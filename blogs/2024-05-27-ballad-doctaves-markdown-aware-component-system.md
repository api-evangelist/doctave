---
title: "Ballad: Doctave's Markdown-aware component system"
url: "https://www.doctave.com/blog/ballad-components"
date: "Mon, 27 May 2024 10:00:00 +0300"
author: ""
feed_url: "https://www.doctave.com/feed.xml"
---
<p>Doctave 2.0 <a href="/blog/doctave-v2">is out</a>, and the biggest new feature in this release was our new <a href="https://docs.doctave.com/components" target="_blank">component system</a>, which we’re calling <strong>Ballad</strong>. In this post we want to talk about the path we took to get here, why we felt none of the existing solutions worked well for us, and what our component system enabled.</p>

<p><img alt="A Ballad tab component for showing code samples on different platforms" src="/assets/img/2024-05-27/tabs-v2.png" /></p>

<div class="text-center -mt-6 mb-16 italic leading-tight">
  <small>Ballad brings interactive components like tabs to your Doctave docs</small>
</div>

<h2 id="why-do-we-need-components">Why do we need components?</h2>

<p>Ballad lets you intersperse UI components in between your Markdown content. While Markdown is fantastic for simple prose, most documentation projects inevitably need widgets like buttons, cards, and callouts (or admonitions), or more complex layouts to keep the content clear and engaging.</p>

<p>This is what we’re solving with Ballad.</p>

<h2 id="how-it-works">How it works</h2>

<p>In short, you can add HTML-like tags into your Markdown, which Doctave will render into various components.</p>

<p>Let’s look at a basic example: adding a <code class="language-plaintext highlighter-rouge">Button</code> component into your documentation:</p>

<div class="language-html highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
</pre></td><td class="rouge-code"><pre>Click below to read more.

<span class="nt">&lt;Button</span> <span class="na">href=</span><span class="s">"/details"</span><span class="nt">&gt;</span>Read More<span class="nt">&lt;/Button&gt;</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>This gets rendered like so:</p>

<p><img alt="A Ballad button component" src="/assets/img/2024-05-27/button-v2.png" /></p>

<div class="text-center mb-16 italic leading-tight">
  <small>Sometimes a regular Markdown link just doesn't cut it</small>
</div>

<h3 id="components">Components</h3>

<p>Our components come in two flavors: <strong>UI components</strong> and <strong>layout components</strong>.</p>

<p>The former are components like <code class="language-plaintext highlighter-rouge">&lt;Button&gt;</code> or <code class="language-plaintext highlighter-rouge">&lt;Card&gt;</code>: visual elements that you’re adding to the page. Layout components instead (unsurprisingly) change the layout of your content. These are components like <code class="language-plaintext highlighter-rouge">&lt;Grid&gt;</code>, or <code class="language-plaintext highlighter-rouge">&lt;Flex&gt;</code> (a flexbox equivalent).</p>

<p>Combining these components lets you build interesting UIs and structure your content however you want on the page, without having to write any custom CSS.</p>

<h3 id="syntax">Syntax</h3>

<p>You can use an MDX-inspired syntax to add components into your documentation:</p>

<div class="language-html highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
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
</pre></td><td class="rouge-code"><pre>## Getting started

Learn how to get started with our SDK.

<span class="nt">&lt;Grid</span> <span class="na">cols=</span><span class="s">"2"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;Card&gt;</span>
    ...
  <span class="nt">&lt;/Card&gt;</span>
  <span class="nt">&lt;Card&gt;</span>
    ...
  <span class="nt">&lt;/Card&gt;</span>
<span class="nt">&lt;/Grid&gt;</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>In fact, the parser <em>is</em> an MDX parser. The component syntax rules are identical.</p>

<p>These HTML-style components work with your Markdown content, and you can nest and combine components and Markdown arbitrarily.</p>

<h3 id="expressions">Expressions</h3>

<p>Beyond just static components, ballad also has its own <strong>expression language</strong>. This is needed because Doctave supports <a href="https://docs.doctave.com/contents/user-preferences" target="_blank">user preferences</a>, which allows different readers to see different content based on, for example, what plan they’ve chosen.</p>

<p>If you for example would like to show a warning on a feature page when the user is not on an enterprise plan, you can do this:</p>

<div class="language-jsx highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
</pre></td><td class="rouge-code"><pre><span class="c1">// Only show this callout if the user is not on the enterprise plan</span>
<span class="p">&lt;</span><span class="nc">Callout</span> <span class="na">type</span><span class="p">=</span><span class="s">"warning"</span> <span class="na">if</span><span class="p">=</span><span class="si">{</span><span class="p">@</span><span class="nd">user_preferences</span><span class="p">.</span><span class="nx">plan</span> <span class="o">!=</span> <span class="dl">"</span><span class="s2">enterprise</span><span class="dl">"</span><span class="si">}</span><span class="p">&gt;</span>
  This feature is only available on the **enterprise** plan
<span class="p">&lt;/</span><span class="nc">Callout</span><span class="p">&gt;</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>You can also show the currently selected user preference in your content:</p>

<div class="language-jsx highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
</pre></td><td class="rouge-code"><pre><span class="nx">You</span> <span class="nx">are</span> <span class="nx">currently</span> <span class="nx">on</span> <span class="nx">the</span> <span class="p">{@</span><span class="nd">user_preferences</span><span class="p">.</span><span class="nx">plan</span> <span class="o">|</span> <span class="nx">capitalize</span><span class="p">}</span> <span class="nx">plan</span><span class="p">.</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<h3 id="custom-components">Custom components</h3>

<p>Not only does Ballad come with its own component library, you can build your own!</p>

<p>Let’s say I wanted to build a custom callout (admonition) component, because I want something more specialized. I can create a reusable component in my project under <code class="language-plaintext highlighter-rouge">_components/callout.md</code>:</p>

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
11
12
13
14
15
16
</pre></td><td class="rouge-code"><pre><span class="nn">---</span>
<span class="na">attributes</span><span class="pi">:</span>
  <span class="pi">-</span> <span class="na">title</span><span class="pi">:</span> <span class="s">type</span>
    <span class="na">required</span><span class="pi">:</span> <span class="no">false</span>
    <span class="na">default</span><span class="pi">:</span> <span class="s2">"</span><span class="s">info"</span>
    <span class="na">validation</span><span class="pi">:</span>
      <span class="na">is_one_of</span><span class="pi">:</span>
        <span class="pi">-</span> <span class="s2">"</span><span class="s">info"</span>
        <span class="pi">-</span> <span class="s2">"</span><span class="s">success"</span>
        <span class="pi">-</span> <span class="s2">"</span><span class="s">warning"</span>
        <span class="pi">-</span> <span class="s2">"</span><span class="s">error"</span>
<span class="nn">---</span>

<span class="nt">&lt;Box</span> <span class="na">class=</span><span class="s">"custom-callout-class"</span> <span class="na">data-type=</span><span class="s">{@type}</span> <span class="na">pad=</span><span class="s">"2"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;Slot</span> <span class="nt">/&gt;</span>
<span class="nt">&lt;/Box&gt;</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>This component can then be called with the following code anywhere in your project:</p>

<div class="language-jsx highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
</pre></td><td class="rouge-code"><pre><span class="p">&lt;</span><span class="nc">Component</span><span class="p">.</span><span class="nc">Callout</span> <span class="na">type</span><span class="p">=</span><span class="s">"warning"</span><span class="p">&gt;</span>
  Remember to back up your data before proceeding
<span class="p">&lt;/</span><span class="nc">Component</span><span class="p">.</span><span class="nc">Callout</span><span class="p">&gt;</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>Let’s see what’s going on in this file:</p>

<ul>
  <li>We’ve created a custom component in the <code class="language-plaintext highlighter-rouge">_components</code> directory</li>
  <li>We say that it takes a <code class="language-plaintext highlighter-rouge">type</code> attribute, and add some validation</li>
  <li>We use a <a href="https://docs.doctave.com/components/box" target="_blank"><code class="language-plaintext highlighter-rouge">Box</code> layout component</a> and set some padding, and add a custom CSS class for targeting styling</li>
  <li>Finally, we use the <code class="language-plaintext highlighter-rouge">&lt;Slot /&gt;</code> component which allows us to inject Markdown into the custom component when it is used</li>
</ul>

<h3 id="the-result">The result</h3>

<p>Ballad lets you combine components fairly complex layouts with very little code, and without any custom CSS:</p>

<p><img alt="A grid of card components created with Ballad" src="/assets/img/2024-05-27/cards-v2.png" /></p>

<div class="text-center -mt-6 mb-16 italic leading-tight">
  <small>No custom CSS needed</small>
</div>

<p>This is not a pre-built, hardcoded component in Doctave. It’s built by combining multiple components and regular Markdown into a complex layout.</p>

<p>This is really powerful, and we’re still discovering new ways to combine the components we’ve built!</p>

<h2 id="why-not-choose-an-existing-technology">Why not choose an existing technology?</h2>

<p>Choosing an existing technology would have been preferable, but after looking around, we did not see a viable existing alternative that we could incorporate into Doctave.</p>

<p>The main blockers we ran into were:</p>

<ul>
  <li>Security issues</li>
  <li>Usage complexity</li>
</ul>

<h3 id="security">Security</h3>

<p>Two options we looked at carefully were <a href="https://mdxjs.com/">MDX</a> and <a href="https://markdoc.dev/">Markdoc</a>. The former is a way to include arbitrary React components in Markdown documents, while the latter is a Markdown-aware templating/authoring system. Both are written in JavaScript and expect users to write JavaScript to define components.</p>

<p>We unfortunately had to dismiss both options because of security concerns.</p>

<p>Doctave builds and hosts your documentation for you, which means we would have to execute the JavaScript required to render the user’s MDX/Markdoc components. This opens a huge can of worms from a security perspective. Ask any security expert, and they will say executing arbitrary user submitted code is a security nightmare.</p>

<p><a href="https://github.com/orgs/mdx-js/discussions/1371">Here is a thread</a> where one of MDX’s creators responds to a question asking if it’s ok to let their users write MDX. His response is pretty straightforward: <a href="https://github.com/orgs/mdx-js/discussions/1371#discussioncomment-198897"><em>“no, it’s not safe, it’s dangerous”</em></a>.</p>

<p>Ballad on the other hand is fully isolated, has a limited API, does not support looping or unbounded recursion, and does not require a full JavaScript runtime to execute. It’s smaller, faster, and safer.</p>

<h3 id="usage-complexity">Usage complexity</h3>

<p>Another issue we wanted to prevent was making your templates too complex. Content reuse is a known double edged sword by tech writers, and sometimes it can be hard to understand where some content is coming from.</p>

<p>This problem is amplified when you can put too much business login into your templates.</p>

<p>Markdoc has an excellent section in their FAQ under <a href="https://markdoc.dev/docs/faq#why-not-mdx">“why not MDX?”</a> where they discuss why you should keep your templates simple:</p>

<blockquote>
  <p>Content can quickly become as complex as regular code, which can lead to maintainability complications or a more difficult authoring environment.</p>
</blockquote>

<p>Stripe famously used Ruby’s <a href="https://docs.ruby-lang.org/en/2.3.0/ERB.html">ERB templates</a> prior to Markdoc for their documentation, and Markdoc was created at least partly to address the complexity caused by having a full programming language available in your template engine.</p>

<p>We did not want to repeat the same mistakes, and have kept Ballad’s API deliberately limited. It is always possible to add features later, but removing capabilities is impossible once users are relying on them.</p>

<h2 id="what-ballad-enabled-for-us">What Ballad enabled for us</h2>

<p>We naturally <a href="https://en.wikipedia.org/wiki/Eating_your_own_dog_food" target="_blank">eat our own dog food</a>, and use Doctave for our own documentation.</p>

<p>Here are some things we realised once we started using Ballad:</p>

<ul>
  <li>
    <p><strong>Landing pages become easy</strong><br />
Previously we spent a lot of time using custom CSS to make compelling landing pages. Now, we just use components to create call-to-actions and guide users to important articles.</p>
  </li>
  <li>
    <p><strong>More compelling tutorials</strong><br />
Components <a href="https://docs.doctave.com/components/steps"><code class="language-plaintext highlighter-rouge">Steps</code></a> and <a href="https://docs.doctave.com/components/code-select"><code class="language-plaintext highlighter-rouge">CodeSelect</code></a> to make it easy to create interesting multi-language tutorials and walkthroughs.</p>
  </li>
  <li>
    <p><strong>Quick one-off custom components are easy</strong><br />
You can create small components inline in your articles by combining a few components. A clickable card with some text and an icon can be done in a couple lines.</p>
  </li>
</ul>

<p>But the overall feeling was a feeling of empowerment. These components add a very important and powerful tool into our docs toolbelt. And as we said, we’re still learning new ways to use Ballad and our component library!</p>

<h2 id="whats-next">What’s next?</h2>

<p>You can expect a few things going forward:</p>

<ul>
  <li>More UI and layout components</li>
  <li>Tutorials on how to effectively combine components</li>
  <li>When we release more themes, all components will conform to the new theme</li>
</ul>

<p>If you’re interested in staying up to date, sign up to the newsletter below!</p>
