---
title: "Documentation versioning best practices with docs-as-code"
url: "https://www.doctave.com/blog/documentation-versioning-best-practices"
date: "Fri, 20 Oct 2023 10:00:00 +0300"
author: ""
feed_url: "https://www.doctave.com/feed.xml"
---
<p>Many software products end up having multiple releases over their lifetimes.
When this happens, the documentation needs to be versioned along with the
product.</p>

<p>In this post we will look at documentation best practices when using a
Git-based <a href="/blog/2021/08/30/why-you-should-consider-docs-as-code.html">docs-as-code workflow</a>.</p>

<h2 id="software-versioning-basics">Software versioning basics</h2>

<p>Before going into how we should version documentation, let’s take a look at how
software projects generally handle versioning.</p>

<div class="p-4 rounded-lg border border-indigo-200 bg-indigo-50 shadow-md shadow-indigo-100">
<b>Disclaimer</b>: there is more than one way to version software. The method
outlined in this post works for many projects, but there are other valid
workflows too.
</div>

<h3 id="versioned-releases">Versioned releases</h3>

<p>Products like Windows, PostgreSQL, or React JS all have <em>versioned releases</em>.
Every once in a while, depending on their release cadence, a new version with
new features is released.</p>

<p><img alt="PingCap's TiDB's documentation versions" src="/assets/img/2023-10-20/pingcap-documentation-versions.png" /></p>

<div class="text-center -mt-6 mb-10 italic">
<small>A long list of versions for PingCap's TiDB documentation</small>
</div>

<p>Different projects will use different versioning schemes, but <a href="https://semver.org/" target="_blank">Semantic
Versioning</a> is a popular way of giving
structure to your version numbers. Another option is using a date-based scheme.</p>

<p>Usually, different versions are managed in separate <strong>Git branches</strong>.</p>

<p>A typical branching strategy is to have all work for the upcoming release
happening on a <code class="language-plaintext highlighter-rouge">main</code> or <code class="language-plaintext highlighter-rouge">development</code> branch. Then, when a new release is
ready, a new branch is created from the <code class="language-plaintext highlighter-rouge">main</code> branch and named after the
release (for example <code class="language-plaintext highlighter-rouge">v4.0</code>).</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
</pre></td><td class="rouge-code"><pre> main  <span class="c"># Development happens in this branch</span>
  <span class="k">*</span> 
  |   v4.0 <span class="c"># New branch for the release</span>
  <span class="k">*</span>     <span class="k">*</span>
  |    /
  <span class="k">*</span> ——
  |
</pre></td></tr></tbody></table></code></pre></div></div>

<p>There’s a few reasons for this. Firstly, it’s clear what code belongs in the
release, and what does not. But importantly, you can apply hotfixes to the
release branch:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
8
9
</pre></td><td class="rouge-code"><pre> main 
  <span class="k">*</span>
  |   v4.0 
  <span class="k">*</span>     <span class="k">*</span>  <span class="c"># &lt;- New hotfix commit</span>
  |     |
  <span class="k">*</span>     <span class="k">*</span>
  |    /
  <span class="k">*</span> ——
  |
</pre></td></tr></tbody></table></code></pre></div></div>

<p>This allows you to update and fix the <code class="language-plaintext highlighter-rouge">4.0</code> version, while you keep moving
forward in your <code class="language-plaintext highlighter-rouge">main</code> branch towards the next release. Perhaps you’ll even
release a patch release with bug fixes: a <code class="language-plaintext highlighter-rouge">4.0.1</code>.</p>

<p>This strategy also makes it clear which features and commits belong to which
version. You don’t have code for multiple versions mixed together. There is
clear separation between versions.</p>

<h3 id="when-is-versioning-not-needed">When is versioning <em><strong>not</strong></em> needed?</h3>

<p>There are some software products that do not have multiple versions. Take a
service like Slack. There is only one version of it: the currently live version.</p>

<p>In such cases, you typically have one set of documentation that lives with the
product. New features are built, documented, released, and ultimately deprecated
in unison.</p>

<p>What these kinds of products however may require is API versioning (see
<a href="#rest-api-documentation-versioning">below</a>).</p>

<h2 id="git-versioning-strategies-for-documentation">Git versioning strategies for documentation</h2>

<p>Ok now that we have an idea of how software versioning works, how do we apply
this to documentation?</p>

<p>One of the reasons you want to use docs-as-code is to mirror the release process
of the rest of your product. When you release a new version of your code, you
also release the corresponding documentation.</p>

<p>How is this managed in Git?</p>

<h3 id="versioning-documentation-in-multiple-branches">Versioning documentation in multiple branches</h3>

<p>With this method, you put the documentation for each version in its own branch:</p>

<ul>
  <li>Version 3.4 -&gt; branch <code class="language-plaintext highlighter-rouge">v3.4</code></li>
  <li>Version 4.0 -&gt; branch <code class="language-plaintext highlighter-rouge">v4.0</code></li>
  <li>New development -&gt; branch <code class="language-plaintext highlighter-rouge">main</code></li>
</ul>

<p>This is essentially the same strategy as described above with source code.</p>

<p>When you’re ready to create a new release, you create a new branch from the main
branch:</p>

<div class="language-shell highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
</pre></td><td class="rouge-code"><pre><span class="c"># Ensure you are on the main branch</span>
git checkout main

<span class="c"># Checkout a new branch with the name of the version</span>
git checkout <span class="nt">-b</span> v2.0
</pre></td></tr></tbody></table></code></pre></div></div>

<h4 id="pros-and-cons">Pros and cons</h4>

<p>The main benefit here is that you are able to match the workflow of the source
code itself. There is also no duplication of content: the content for each
version lives in its own branch.</p>

<p>The downside of this approach is that many docs-as-code tools do not support
this workflow. Static site generators like <a href="https://docusaurus.io/">Docusaurus</a>
cannot construct one site from multiple Git branches. Instead, you have to
deploy separate sites for each version, which can add a lot of complexity.</p>

<p><a href="https://www.doctave.com">Doctave</a> supports this form of versioning and can
build your documentation from separate branches into a single documentation
site. The user can then select which version of the documentation to view from
a dropdown menu.</p>

<p>On the open source side, the AsciiDoc documentation site generator
<a href="https://antora.org/">Antora</a> also supports this workflow.</p>

<p>So in short:</p>

<ul>
  <li>✅ Mirror how source code is versioned</li>
  <li>✅ Little duplication of content</li>
  <li>⚠️  Requires specialized support from your tools or managing multiple sites</li>
</ul>

<h3 id="versioning-documentation-in-one-branch">Versioning documentation in one branch</h3>

<p>You can also choose to version your documentation all in one branch. This is
arguably the simpler way to manage documentation.</p>

<p>The idea is to structure your documentation something like this in your Git
repository:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
6
7
</pre></td><td class="rouge-code"><pre>docs
├── v1
│   └── ...
├── v2
│   └── ...
└── v3
    └── ...
</pre></td></tr></tbody></table></code></pre></div></div>

<p>Each version lives in its own subdirectory, in a single branch. Docusaurus
supports <a href="https://docusaurus.io/docs/versioning">this method of versioning</a>,
and it is able to generate a dropdown that lets the user swap between versions.</p>

<p>You can also decide to build each version into a separate site that can be
deployed and hosted independently. But then the same issues regarding routing
come into play as in the multi-branch setup.</p>

<h4 id="pros-and-cons-1">Pros and cons</h4>

<p>The main benefit here is simplicity. If you are not an experienced Git-user,
having everything in one branch is easier than juggling multiple branches.</p>

<p>There are however some significant downsides to this workflow.</p>

<p>The main issue is around content duplication and build times. For example,
adding a new version in Docusaurus means <strong>copying</strong> all of the content you have
in your existing docs into a new subdirectory, which now becomes your new
version.</p>

<p>If you only change 20% of your docs between versions, 80% of your files will be
needlessly duplicated.</p>

<p>This can lead to very long build times. The Write The Docs Slack, popular among
technical writers, is full of anecdotes of Docusaurus builds even taking over 30
minutes.</p>

<p>Some other tools may be faster, but the fact is that the more content you have,
the slower your builds will be. Tools that cannot build versions independently
will always struggle when you add more versions.</p>

<p>So, to recap:</p>

<ul>
  <li>✅ Simple - no need to manage multiple branches</li>
  <li>⚠️  Duplicated content</li>
  <li>⚠️  Can be a big cause of long build times</li>
</ul>

<h3 id="versioning-documentation-using-git-tags">Versioning documentation using Git tags</h3>

<p>One final option that works in some cases is using Git tags.
<a href="https://git-scm.com/book/en/v2/Git-Basics-Tagging">Tags</a> are a feature in Git
that lets you effectively give a name to a specific commit.</p>

<p>In this workflow, when you are ready to publish the documentation for a given
version, you add a tag to that commit:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
</pre></td><td class="rouge-code"><pre>git tag <span class="nt">-a</span> v1.4 <span class="nt">-m</span> <span class="s2">"Version 1.4"</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>You can then go back to any tag you’ve created easily by checking out that tag:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
</pre></td><td class="rouge-code"><pre>git checkout v1.4
</pre></td></tr></tbody></table></code></pre></div></div>

<p>You can also list your tags easily:</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
2
3
4
5
</pre></td><td class="rouge-code"><pre>git tag
<span class="c"># v1.0</span>
<span class="c"># v1.1</span>
<span class="c"># v1.2</span>
<span class="c"># v1.4</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<div class="w-full not-prose my-12 flex items-start pt-4 p-6 rounded-xl bg-emerald-50 border border-emerald-300 relative shadow shadow-emerald-700/30">
  <span class="absolute block w-fit h-fit p-1 flex items-center justify-center bg-emerald-600 rounded-full text-emerald-100 -right-3 -top-3">
    <svg class="h-5 w-5" fill="currentColor" height="40" viewBox="0 0 24 24" width="40" xmlns="http://www.w3.org/2000/svg">
      <path d="M14.615 1.595a.75.75 0 01.359.852L12.982 9.75h7.268a.75.75 0 01.548 1.262l-10.5 11.25a.75.75 0 01-1.272-.71l1.992-7.302H3.75a.75.75 0 01-.548-1.262l10.5-11.25a.75.75 0 01.913-.143z" fill-rule="evenodd">
    </svg>
  </span>
  <div class="flex flex-col">
    <p class="text-base sm:text-lg font-display text-emerald-700 font-semibold tracking-tight">Tip: Use tags liberally</p>
    <div class="text-sm sm:text-base text-gray-700 pt-2"><p>Tags are a cheap and easy way to add details to your Git history. You can use them in conjunction with other versioning schemes too, and for other reasons than just versioning.</p>
</div>
    
    <div class="text-sm sm:text-base text-slate-300 font-light">
</div>
    
  </div>
</div>

<h4 id="pros-and-cons-2">Pros and cons</h4>

<p>This is a very lightweight way to add “checkpoints” in your Git history that
signify <em>“this was the state of the documentation at the time of release”</em>.</p>

<p>The main issue with this workflow is that you cannot backport fixes or make
changes to old versions. You can’t change the history of your main branch
(without some serious <a href="https://git-scm.com/docs/git-rebase">rebasing</a>).</p>

<p>The good news is that when you do, you can create a new branch!</p>

<div class="language-bash highlighter-rouge"><div class="highlight"><pre class="highlight not-prose"><code><table class="rouge-table"><tbody><tr><td class="rouge-gutter gl"><pre class="lineno">1
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
</pre></td><td class="rouge-code"><pre><span class="c"># Checkout the tag you want to update</span>
git checkout v1.4

<span class="c"># Create a branch from this point</span>
git checkout <span class="nt">-b</span> v1.4.1

<span class="c"># ...make your changes...</span>

<span class="c"># Commit your changes</span>
git add <span class="nb">.</span>
git commit <span class="nt">-m</span> <span class="s2">"Updated docs for version v.1.4.1"</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<p>You have now gone back to the branch-per-version workflow!</p>

<p>Finally, your tools will have to support the same workflow as with the
branch-based workflow: you have to be able to build your versions
separately.</p>

<p>So, to recap:</p>

<ul>
  <li>✅ Simple - no need to manage multiple branches</li>
  <li>✅ Works great if you know past versions will never be updated</li>
  <li>⚠️  Can’t make changes to old versions without moving to a branch-based model</li>
  <li>⚠️  Requires specialized support from your tools or managing multiple sites</li>
</ul>

<h2 id="rest-api-documentation-versioning">REST API documentation versioning</h2>

<p>API versioning is related to versioning in general, and warrants its own
section. This is a nuanced topic: there is no “one way” to version your APIs,
even if some best practices have emerged.</p>

<p>REST APIs will often be versioned <em>independently</em> from the rest of the product.
And because you generally cannot make breaking changes without giving your users
ample time to migrate, you can have <em>multiple versions of your API running at
the same time</em>.</p>

<p><a href="https://stripe.com/docs/api">Stripe</a> is a great example of an API that does
this. They write about their versioning strategy <a href="https://stripe.com/docs/api/versioning">here</a>.
The Stripe API expects a <code class="language-plaintext highlighter-rouge">Stripe-Version</code> HTTP header that specifies which
version of the API you want to be using. This way the user can decide which
version to use, and can update at their own pace.</p>

<p>When a breaking change is made, Stripe creates a new version:</p>

<blockquote>
  <p>When backwards-incompatible changes are made to the API, a new, dated version
is released. The current version is 2023-10-16.</p>
</blockquote>

<p>Now any client that wants to opt into these new features or breaking changes can
update their code and swap the HTTP header to the latest version.</p>

<h3 id="documenting-api-versions">Documenting API versions</h3>

<p>Stripe is of course famous for its documentation, and they customize their API
reference to match the API version of your account. When you update your API
version, the documentation changes to reflect that.</p>

<p>Another way to document differences between versions is to include notes in the
API reference itself. For example adding a note in an OpenAPI <code class="language-plaintext highlighter-rouge">description</code>
field saying <code class="language-plaintext highlighter-rouge">Deprecated since v2.4</code> or <code class="language-plaintext highlighter-rouge">Requires v4.1 or later</code> for any
operations or fields that have versioning requirements.</p>

<p>Or, you may end up using one OpenAPI specification per API version. This may
happen if your API versions live under different path namespaces (for example
<code class="language-plaintext highlighter-rouge">/api/v1/</code> and <code class="language-plaintext highlighter-rouge">/api/v2/</code>. In this case, you will likely want to allow the user
to select which version of the API they are using in the documentation itself,
and show the appropriate API reference.</p>

<h2 id="hosting-considerations">Hosting considerations</h2>

<p>Good tools that create documentation websites will always have some kind of
versioning mechanism. You’ll want to make sure that it matches the workflow
you want to use for versioning.</p>

<p>Here are a few versioning-related details to consider when choosing your tools.</p>

<h3 id="switching-between-versions">Switching between versions</h3>

<p>Somewhere in your documentation, you will want to give your users the ability
to change the version they are viewing.</p>

<p><img alt="A version dropdown in Doctave" src="/assets/img/2023-10-20/version-dropdown.png" /></p>

<div class="text-center -mt-6 mb-10 italic">
<small>A version dropdown in a Doctave site</small>
</div>

<p>Commonly your URLs will map to specific versions too:</p>

<ul>
  <li>Content for the default version will be under <code class="language-plaintext highlighter-rouge">docs.mycompany.com/...</code></li>
  <li>Content for a v2 version would be under <code class="language-plaintext highlighter-rouge">docs.mycompany.com/v2/...</code></li>
  <li>Content for a v3 version would be under <code class="language-plaintext highlighter-rouge">docs.mycompany.com/v3/...</code></li>
</ul>

<h3 id="access-control">Access control</h3>

<p>In some cases it can be beneficial to only allow public access to certain
versions. Perhaps you only want to give preview access to a version to a
specific version?</p>

<p>In this case, you’ll have to make sure either your hosting provider or
documentation platform supports this, or you have to do some custom
engineering to achieve this.</p>

<p><a href="/">Doctave</a> is a solution that supports this out of the box. You can create
public, private, or password-protected versions and map them to any Git branch.</p>

<h3 id="releasing-new-versions">Releasing new versions</h3>

<p>Eventually new releases will show up, and old versions will be removed. Your
documentation has to reflect these changes.</p>

<p>Releasing new versions is the simpler case. Let’s say you are moving from <code class="language-plaintext highlighter-rouge">v3</code>
to <code class="language-plaintext highlighter-rouge">v4</code>. The process of updating your docs would likely be as follows:</p>

<ol>
  <li>You default docs (i.e <code class="language-plaintext highlighter-rouge">docs.mycompany.com</code>) now point to your <code class="language-plaintext highlighter-rouge">v4</code> docs</li>
  <li>You create a new space for your old <code class="language-plaintext highlighter-rouge">v3</code> docs under <code class="language-plaintext highlighter-rouge">docs.mycompany.com/v3</code></li>
</ol>

<p>One big benefit of this is SEO. Any content that did not change between
versions is still in the same URL path, and Google will keep sending traffic to
the latest version of your documentation.</p>

<h3 id="deprecating-old-versions">Deprecating old versions</h3>

<p>Deprecating versions is more involved, if you want your old URLs to still work.
This is done with <strong>redirects</strong>.</p>

<p>Let’s say you’re deprecating your legacy <code class="language-plaintext highlighter-rouge">v1</code> version and it lives under
<code class="language-plaintext highlighter-rouge">docs.mycompany.com/v1</code>. There will be content and links both on the internet
and in your own docs pointing to this old documentation. Ideally, you want those
links to continue to work. Both for SEO, but also to minimize confusion when
users are faced with a 404 page.</p>

<p>You’ll want to add redirect rules from your deprecated documentation that will
send readers to another version of your documentation.</p>

<p>The simple way is to redirect all links under the <code class="language-plaintext highlighter-rouge">/v1</code> path to e.g. your latest
version. This is easier, but can lead to confusion if your user was searching
for a specific topic, and then finds themselves on an unexpected page.</p>

<p>The more involved (but user friendlier) way is to try to map each piece of
content from your deprecated version into a corresponding page in your new
documentation. This will be simple for features that exist in both versions:
you can map a <code class="language-plaintext highlighter-rouge">/v1/account-creation</code> page to the latest version’s equivalent
page (likely, <code class="language-plaintext highlighter-rouge">/account-creation</code>). If an equivalent page does not exist, you
can fall back to sending people to the front page of your documentation.</p>

<h2 id="final-thoughts">Final thoughts</h2>

<p>In the end, your documentation versioning strategy should match your product’s
versioning strategy. The important thing is that your tools support the strategy
you choose and you are able to update past versions easily.</p>

<p>There are multiple right ways to do versioning, so you should discuss the
options with your team, and choose what is right for your situation.</p>
