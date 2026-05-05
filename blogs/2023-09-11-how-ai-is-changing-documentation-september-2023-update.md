---
title: "How AI is changing documentation (September 2023 update)"
url: "https://www.doctave.com/blog/how-ai-is-changing-documentation-update"
date: "Mon, 11 Sep 2023 10:00:00 +0300"
author: ""
feed_url: "https://www.doctave.com/feed.xml"
---
<p>In May this year, I wrote about <a href="/blog/how-ai-is-changing-documentation">how AI is changing documentation</a>,
a few months into the proliferations of LLMs. At the time, I argued LLMs had
not yet made much of a dent in the documentation landscape, due to a couple
points:</p>

<ul>
  <li>AIs <a href="https://en.wikipedia.org/wiki/Hallucination_(artificial_intelligence)">making things up</a>
is a big issue and especially problematic for documentation</li>
  <li>Without knowing how your product works, LLMs can’t write meaningful, quality
documentation by themselves</li>
</ul>

<p>I argued that AI would in the short term be most helpful in documentation as a
writing assistant, and that we are not yet replacing technical writers with AI.</p>

<p>But it’s now September 2023. Have things changed? Let’s do a quick review.</p>

<h2 id="ais-chatbots-for-documentation">AIs chatbots for documentation</h2>

<p>The first obvious use case for LLMs was being able to ask questions about your
documentation from an AI chat bot. This could be extremely useful. Readers
famously rarely read the documentation in detail, so maybe an LLM could help
surface relevant information. Or perhaps an AI could even generate customized
learning paths for the reader on the fly, based on the reader’s experince.</p>

<p>We’ve seen lots of companies add LLMs to their docs this year, Supabase being an
early example from the beginning of the year with their <a href="https://supabase.com/blog/chatgpt-supabase-docs">Clippy helper</a>.</p>

<p>Has anything changed? Are the responses better?</p>

<p>Not particularly.</p>

<p>Anecdotally, AI documentation chatbots have the same issues as in the
beginning of the year: not finding answers that are not explicitly mentioned
in the corpus, misunderstanding the docs, or making things up.</p>

<p>In the <a href="/blog/how-ai-is-changing-documentation#trust-issues">previous post</a>
I went through some of the technical details about why these issues exist, and
there haven’t been any AI research breakthroughs that have changed things.</p>

<h3 id="when-ai-assistants-backfire">When AI assistants backfire</h3>

<p>We now have a very public example of AI documentation chatbots failing in the
wild from Mozilla and their <a href="https://developer.mozilla.org/en-US/">MDN Web Docs</a>,
which describe open web technologies.</p>

<p>They <a href="https://developer.mozilla.org/en-US/blog/introducing-ai-help/">introduced an AI Help</a>
feature in late June, that lets you ask questions about the reference
documentation.</p>

<p>GitHub user <a href="https://github.com/eevee">eevee</a> opened <a href="https://github.com/mdn/yari/issues/9208">an issue</a>
just a few days later showing how the new AI helper is producing incorrect
answers. There are a number of examples listed in the long list of comments.</p>

<p><img alt="screenshot of the above mentioned GitHub issue with the title &quot;MDN can now automatically lie to people seeking technical information&quot;" src="/assets/img/2023-09-11/gh-eevee-issue.png" /></p>

<div class="text-center -mt-6 mb-10 italic">
<small>"MDN can now automatically lie to people seeking technical information"</small>
</div>

<p>What is interesting about this example is that <strong>MDN was like part of the OpenAI
training corpus that GPT-4 was trained on</strong>. Still, it was not able to produce
correct results enough of the time. <em>GPT-4 knows HTML, CSS, and JavaScript</em>, but
still ran into issues.</p>

<p>Your product was likely <em>not</em> part of the training set, so don’t expect better
results than this.</p>

<h3 id="non-expert-in-the-loop">Non-expert in the loop</h3>

<p>What makes documentation chatbots such a tough case for LLMs is that the user
is usually, by definition, a non-expert. They do not necessarily know when the
LLM is talking nonsense.</p>

<p>Imagine you had a support agent for your company that just made things up
5-10% of the time. That wouldn’t be acceptable.</p>

<p>Let’s look at an example of a similar use case that does work: LLMs helping
lawyers and other knowledge workers understand complex contracts. You can load
up large documents into LLMs and ask questions about the terms of a sales
agreement, for example.</p>

<p>One such vendor is <a href="https://www.box.com/en-gb/ai">Box</a>, which has introduced
these kinds of AI features to their suite of products.</p>

<p>Sounds very similar to documentation search, but with an important difference:
the user <em>is</em> an expert. They can recognise when the LLM is incorrect, while
still enjoying a productivity benefit from the tool most of the time.</p>

<h3 id="surely-its-not-all-bad">Surely it’s not all bad?</h3>

<p>One issue I pointed out in May was that AI search was sloooooow. Especially the
larger GPT-4 based models took a long time to generate tokens.</p>

<p>Well, that has (predictably) changed!</p>

<p>GPT-4 is significantly faster than it was just a few months ago, and this is a
great usability improvement. I tried looking for data on this but OpenAI does
not seem to publish speed benchmarks (at least that are easy to find). So
you’ll have to take my word for it: GPT-4 is (anecdotally) much faster.</p>

<p>But is this enough to make AI-powered documentation search 10x better than
traditional search? Given the other issues we’ve mentioned, my verdict is still
a “no”. We haven’t seen foundational changes to LLMs that would solve the issues
I discussed in May.</p>

<h2 id="ai-for-writing-docs">AI for writing docs</h2>

<p>The promise of AI writing all your documentation for you has not materialized.</p>

<p>This is especially true for larger product documentation and tutorials. While it
is possible on a function or module level for source code, writing accurate,
helpful, and consistent documentation for a complex technical product is still
outside the capabilities of LLMs.</p>

<p>But assisting professional writers do exactly this is something that LLMs are
well suited for!</p>

<p>This is where the recent advancements in AI are much more useful. If you are a
technical writer, developer advocate, or product owner writing documentation,
LLMs can be fantastic assistants. They help you rephrase content, produce
outlines, keep a consistent voice across your docs. They’re a great cure for
blank page syndrome.</p>

<p>Depending on what tools you are currently using, you may have an AI integration
already in your writing environment, but personally I tend to spend time in
the ChatGPT interface when writing all sorts of content - not just documentation.</p>

<p>There will likely be more innovation in this space aimed at technical writing
specifically in the future.</p>

<h2 id="are-your-docs-ai-ready">Are your docs AI-ready?</h2>

<p>OpenAI announced <a href="https://openai.com/blog/chatgpt-plugins">ChatGPT Plugins</a> in
March 2023, which let ChatGPT fetch information from external live data sources.</p>

<p>The question I posed in May was, are we going to need to ensure our docs are
easily accessible for LLMs, and if so, what does that mean in practice?</p>

<p>This was speculative then, and still remains so today. There certainly has not
been a proliferation of autonomous AI agents collecting information or
performing tasks for their users, and which would need to query your docs in
order to complete said tasks.</p>

<p>If this does come to pass, an API references and <a href="/blog/2023/02/21/what-is-openapi.html">OpenAPI</a>
may end up playing an important role. (Yes, OpenAPI vs OpenAI is confusing…)</p>

<div class="not-prose flex justify-center">
<blockquote class="twitter-tweet"><p dir="ltr" lang="en">Hear me out: a standard “documentation” endpoint for every API that returns clear and concise API documentation for the purpose of feeding into an LLM to generate API queries.</p>&mdash; Yohei (@yoheinakajima) <a href="https://twitter.com/yoheinakajima/status/1698364131336941991?ref_src=twsrc%5Etfw">September 3, 2023</a></blockquote> 
</div>

<p>I believe this tweet (or is it an “x” now?) misses the fact that we already
have such a tool: OpenAPI.</p>

<p>OpenAPI is a great way to describe how your API works to an LLM. In fact, <a href="https://platform.openai.com/docs/plugins/introduction">OpenAI
plugin manifest files require an OpenAPI spec</a>
that ChatGPT then uses to call the service behind the plugin. It kind of sounds
like magic: you just provide a JSON blob describing the endpoint and the AI
figures out the rest.</p>

<p>Here’s a key point from the docs:</p>

<blockquote>
  <p>The model will see the OpenAPI description fields, which can be used to
provide a natural language description for the different fields.</p>
</blockquote>

<p>It may be important for your API references to include well written usage
instructions, so that LLMs can use them properly. For example, what order do we
invoke the operations in?</p>

<h2 id="conclusions">Conclusions</h2>

<p>I think my overall opinions have not changed since my first post in May:</p>

<ul>
  <li>AI docs chatbots are not particularly helpful and are occasionally borderline
problematic</li>
  <li>AIs are great tools for helping writers produce content</li>
</ul>

<p>What I hadn’t considered before is the possible importance of OpenAPI references
for describing APIs to LLMs. We will have to see how this develops.</p>

<p>GPT-5 is expected to be released at the end of this year, bringing with it at
least another order of magnitude in computational power to the bleeding edge of
LLM development. We will have to see what new capabilities it brings, or if we
will see signs of hitting the limits of current <a href="https://en.wikipedia.org/wiki/Transformer_(machine_learning_model)">transformer-based
architectures</a>.</p>

<p>It still remains to be seen how AI is going to change knowledge work in the
coming years.</p>
