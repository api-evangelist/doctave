---
title: "What do you mean \"documentation\"?"
url: "https://www.doctave.com/blog/what-do-you-mean-documentation"
date: "Tue, 17 Oct 2023 10:00:00 +0300"
author: ""
feed_url: "https://www.doctave.com/feed.xml"
---
<p>There was a post submitted to the Orange Website™ the other week with the title
<a href="https://blog.orsinium.dev/posts/misc/docs/" target="_blank">“Delete half your documentation”</a>
(<a href="https://news.ycombinator.com/item?id=37868591" target="_blank">HN thread here</a>).</p>

<p>The author talks about how documentation inherently has a cost, and how we should
minimize the amount of documentation we need. It becomes outdated, requires
maintenance, and <em>“nobody reads it anyway”</em>.</p>

<p>Instead, they argue, we should use type annotations, tested examples, and other
methods to remove the requirement for manually maintaining documentation.</p>

<p>Some of these arguments have some merits in the right context.</p>

<p>But what really caught my eye in the post was this line:</p>

<div class="border-l pl-4 py-1 italic font-medium not-prose">
<blockquote>

“When I say 'documentation', I mean all forms of it, including README, Markdown
files, docstrings, and code comments.“

</blockquote>
</div>

<p><img alt="You keep using that word. I do not think it means what you think it means" src="/assets/img/2023-10-17/you-keep-using-that-word-i-do-not-think-it-means-what-you-think-it-means.jpeg" /></p>

<p>Hang on.</p>

<p><strong>This is not all forms of documentation!</strong> And we certainly cannot
apply these rules universally.</p>

<h2 id="documentation-is-in-the-eyes-of-the-reader">Documentation is in the eyes of the reader</h2>

<p>I recently Tweeted about the confusion that can happen when people use the word
“documentation” to refer to different things.</p>

<blockquote class="twitter-tweet"><p dir="ltr" lang="en">The word ”documentation” has so many meanings depending on who you’re talking to.<br /><br />To one person it’s a single README file. To another, it’s a full blown dev portal with guides and API references.<br /><br />Causes legitimate confusion sometimes</p>&mdash; Niklas Begley (@NiklasBegley) <a href="https://twitter.com/NiklasBegley/status/1699374945111818445?ref_src=twsrc%5Etfw">September 6, 2023</a></blockquote>


<p>The post mentioned above is a great example of this phenomenon.</p>

<p>The author clearly had the view that “documentation” means <em>code documentation</em>:
docstrings, and other supplementing information you can include in or generate
from raw source code.</p>

<p>This is quite natural for software developers, since it’s the kind of
documentation they are used to producing themselves. And for their case, perhaps
relying on automation over prose to ensure your documentation is in order is
a good idea.</p>

<p>But what about developer portals, manuals, or API references? Surely a technical
writer documenting a complex developer toolchain should not apply the same
thinking and “delete half their documentation”?</p>

<h2 id="an-overloaded-term">An overloaded term</h2>

<p>Technical documentation comes in many forms. Developer portals, docstrings,
walkthroughs, internal knowledge bases, marketing documentation, SDK
documentation, various kinds of manuals.</p>

<p>It’s hard to apply universal rules as best practices for all of these
categories.</p>

<p>The amount of effort you are willing to invest into your public developer
documentation compared to a small internal library is wildly different. The
former can have professional dedicated writing staff constantly improving the
content, while the latter may be written once and rarely updated after.</p>

<p>The context will determine what best practices, tools, workflows, and
expectations are valid for any given type of “documentation”.</p>

<h2 id="documentation-is-more-than-docstrings-and-readmes">Documentation is more than docstrings and READMEs</h2>

<p>When we talk about documentation, we shouldn’t limit ourselves to README.md
files on GitHub. It’s a much richer field.</p>

<p>There’s a whole world of professional technical writers that have advanced
tooling and workflows for producing documentation for some of the most beloved
developer tools out there. Documentation can make or break companies trying to
reach a developer audience.</p>

<p>You probably should not delete half your documentation.</p>
