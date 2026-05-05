---
title: "Markdown vs. DITA: Balancing Simplicity and Structure in Technical Documentation"
url: "https://www.doctave.com/blog/markdown-vs-dita"
date: "Thu, 06 Jun 2024 10:00:00 +0300"
author: ""
feed_url: "https://www.doctave.com/feed.xml"
---
<p>When embarking on a new documentation project, one of the first, and quite consequential choices you have to make is what tools and formats to pick. Do you go with <a href="https://www.markdownguide.org/">Markdown</a>, the ubiquitous and light-weight markup language with a low barrier to entry, or do you instead reach for an authoring system like <a href="https://en.wikipedia.org/wiki/Darwin_Information_Typing_Architecture">DITA</a> that lets you enforce structure and reuse content from day one?</p>

<p>In this post we’re going to look at both options and evaluate the pros and cons of both approaches, and when one might choose one over the other.</p>

<h2 id="what-is-markdown">What is Markdown?</h2>

<p>Markdown was originally developed by <a href="https://daringfireball.net/projects/markdown/">John Gruber</a> back in 2004. It was designed as an easy way to convert text into HTML easily. Here is John describing Markdown in the introduction:</p>

<blockquote>
  <p>Markdown is a text-to-HTML conversion tool for web writers. Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML).</p>
</blockquote>

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
</pre></td><td class="rouge-code"><pre><span class="gh"># Rocket Launch Sequence</span>
<span class="p">
1.</span> <span class="gs">**Pre-launch Jitters**</span>
<span class="p">   -</span> Double-check that the pointy end is facing up
<span class="p">   -</span> Ensure the rocket isn't just a giant firework
<span class="p">   -</span> Cross fingers and hope for the best
<span class="p">
2.</span> <span class="gs">**Blastoff!**</span>
<span class="p">   -</span> Light the candle and watch the show
<span class="p">   -</span> Try not to think about the astronomical fuel costs
<span class="p">   -</span> Wave goodbye to the rocket (and your paycheck)
<span class="p">
3.</span> <span class="gs">**Celebrate or Commiserate**</span>
<span class="p">   -</span> If the payload reaches orbit, break out the champagne
<span class="p">   -</span> If not, break out the tissues and start drafting the apology email
<span class="p">   -</span> Either way, start planning for the next launch (and budget)
</pre></td></tr></tbody></table></code></pre></div></div>

<div class="text-center -mt-6 mb-16 italic leading-tight">
  <small>Example Markdown snippet</small>
</div>

<p>Since then, Markdown has exploded in popularity. It has become the lingua franca for all kinds of technical content and blogs.</p>

<p>Developers have embraced the simplicity of Markdown. Most new programming languages support Markdown as part of their docstrings, OpenAPI supports Markdown in <a href="https://swagger.io/specification/#rich-text-formatting"><code class="language-plaintext highlighter-rouge">description</code> fields</a>, and most static site generators have built-in Markdown support. The ecosystem of Makdown tooling is vast.</p>

<p>This is why the <a href="/docs-as-code">docs-as-code</a> movement has mostly gravitated towards Markdown as the preferred authoring format. Developers and technical writers both being familiar with Markdown makes it a great choice for engineering teams collaborating on technical documentation.</p>

<h2 id="what-is-dita">What is DITA?</h2>

<p>DITA is an XML specification, <a href="http://dita-archive.xml.org/book/history-of-dita">first released in 2005</a>, for structured authoring.</p>

<blockquote>
  <p>The DITA OASIS Standard builds content reuse into the authoring process, defining an XML architecture for designing, writing, managing, and publishing many kinds of information in print and on the Web.<br />
<small><a href="http://dita-archive.xml.org/book/about-dita">«source»</a></small></p>
</blockquote>

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
</pre></td><td class="rouge-code"><pre><span class="cp">&lt;?xml version="1.0" encoding="UTF-8"?&gt;</span>
<span class="cp">&lt;!DOCTYPE task PUBLIC "-//OASIS//DTD DITA Task//EN" "http://docs.oasis-open.org/dita/v1.2/os/dtd/task.dtd"&gt;</span>
<span class="nt">&lt;task</span> <span class="na">id=</span><span class="s">"rocket-launch-sequence"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;title&gt;</span>Rocket Launch Sequence<span class="nt">&lt;/title&gt;</span>
  <span class="nt">&lt;taskbody&gt;</span>
    <span class="nt">&lt;steps&gt;</span>
      <span class="nt">&lt;step&gt;</span>
        <span class="nt">&lt;cmd&gt;</span>Pre-launch Jitters<span class="nt">&lt;/cmd&gt;</span>
        <span class="nt">&lt;substeps&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>Double-check that the pointy end is facing up<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>Ensure the rocket isn't just a giant firework<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>Cross fingers and hope for the best<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
        <span class="nt">&lt;/substeps&gt;</span>
      <span class="nt">&lt;/step&gt;</span>
      <span class="nt">&lt;step&gt;</span>
        <span class="nt">&lt;cmd&gt;</span>Blastoff!<span class="nt">&lt;/cmd&gt;</span>
        <span class="nt">&lt;substeps&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>Light the candle and watch the show<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>Try not to think about the astronomical fuel costs<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>Wave goodbye to the rocket (and your paycheck)<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
        <span class="nt">&lt;/substeps&gt;</span>
      <span class="nt">&lt;/step&gt;</span>
      <span class="nt">&lt;step&gt;</span>
        <span class="nt">&lt;cmd&gt;</span>Celebrate or Commiserate<span class="nt">&lt;/cmd&gt;</span>
        <span class="nt">&lt;substeps&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>If the payload reaches orbit, break out the champagne<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>If not, break out the tissues and start drafting the apology email<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
          <span class="nt">&lt;substep&gt;&lt;cmd&gt;</span>Either way, start planning for the next launch (and budget)<span class="nt">&lt;/cmd&gt;&lt;/substep&gt;</span>
        <span class="nt">&lt;/substeps&gt;</span>
      <span class="nt">&lt;/step&gt;</span>
    <span class="nt">&lt;/steps&gt;</span>
  <span class="nt">&lt;/taskbody&gt;</span>
<span class="nt">&lt;/task&gt;</span>
</pre></td></tr></tbody></table></code></pre></div></div>

<div class="text-center -mt-6 mb-16 italic leading-tight">
  <small>Example equivalent DITA snippet</small>
</div>

<p>Structured authoring was designed in order to manage large scale authoring projects. Imagine thousands of documents describing a matrix of products maintained by dozens of authors, and consider how you would enforce consistency in such a project. DITA allows you to reuse content, enforce document structure, and publish content in multiple formats. It does this by using concepts like topic-based authoring, where you write your content in reusable chunks that can be reused and combined on demand.</p>

<p>DITA is a fairly complicated standard and has a higher learning curve compared to Markdown. But in return you get an authoring system that can grow to manage very large projects.</p>

<h2 id="dita-and-markdown-are-not-the-same-thing">DITA and Markdown are not the same thing</h2>

<p>It should be noted that Markdown and DITA cannot be compared one to one. Markdown is only a markup language, while DITA is a full authoring standard. Markdown itself only describes a format for converting text into HTML and is not enough to create documentation alone. For this you need, for example, a static site generator, or an authoring platform like Doctave, that pulls multiple Markdown documents together and provides features on top of standard Markdown to create the actual published artifact.</p>

<p>So during this comparison, we are really comparing DITA with Markdown <em>as used as part of some other system for publishing documentation</em>.</p>

<h2 id="comparisons">Comparisons</h2>

<p>For the rest of this article we are going to talk about how Markdown and DITA compare on a few specific axis:</p>

<ul>
  <li>Ease of use</li>
  <li>Structure and semantics</li>
  <li>Content reuse and modularity</li>
  <li>Tooling and ecosystem</li>
</ul>

<p>Let’s dive in!</p>

<h3 id="ease-of-use">Ease of use</h3>

<p>This is where Markdown shines. Anyone can learn Markdown in a day and start contributing to your content immediately. There essentially is no learning curve. You bring your text editor of choice and start typing away.</p>

<p>And since Markdown is such a simple standard, it’s easy to also <em>programmatically generate Markdown</em>. This is incredibly useful when you for example have code samples that you want to sync with some source code. You can have your source code output the Markdown documentation itself, which can then be included or copied into your documentation.</p>

<p>But as mentioned, you have to use Markdown as part of some other publishing system, such as a static site generator or authoring platform like Doctave. This means your authors will have to become familiar with whatever tool you select. Markdown does also tend to be used in docs-as-code situations, which means your contributors need to be familiar with Git-based workflows (though DITA can also be used in a docs-as-code setting!).</p>

<p>DITA on the other hand does have a steeper learning curve. It takes time to understand the differences between DITA maps, topics, references, and getting familiar with the tools, especially if you are not familiar with XML.</p>

<p>If you are in a team where developers contribute to your documentation, it may be hard to get them to adopt your DITA toolchain and learn structured writing concepts. But if your team is mostly professional technical writers and content experts familiar with DITA, this will be less of an issue. There are also ways to include Markdown into DITA projects, such as the <a href="http://docs.oasis-open.org/dita/LwDITA/v1.0/cnprd02/LwDITA-v1.0-cnprd02.html">LwDITA project</a>, which can help bridge the gap between developers and professional writers. There are also lots of courses available to teach DITA (such as <a href="https://learningdita.com/">learningDITA</a>), which can help bring contributors up to speed.</p>

<h3 id="structure-and-semantics">Structure and semantics</h3>

<p>This one goes to DITA, and where structured authoring as a whole shines.</p>

<p>DITA has built in elements such as <code class="language-plaintext highlighter-rouge">&lt;step&gt;</code> and <code class="language-plaintext highlighter-rouge">&lt;task&gt;</code> that add semantic meaning to your content. You can also define your own schemas. This means using the <a href="https://learn.microsoft.com/en-us/previous-versions/windows/desktop/ms765537(v=vs.85)">XSD</a> language to create rules that verify that your content conforms to specific shapes. Essentially any structure you can imagine can be modelled in DITA.</p>

<p>Markdown on the other hand, has essentially none of these features. This can be both a blessing and a curse. With small projects, defining lots of rules for your content can introduce a lot of overhead that can get in your way when trying to publish content. Markdown gives you a simple vocabulary to just write your content without additional fanfare. But as your project matures, it can be useful to start adding guard rails, especially as the number of contributors grows.</p>

<p>We’ve written about <a href="/blog/path-to-structured-markdown">how structured authoring concepts could be brought into Markdown</a>, but at the moment, DITA reigns supreme in this category, if these features are important to you.</p>

<h3 id="content-reuse-and-modularity">Content reuse and modularity</h3>

<p>Content reuse means taking a piece of content, like a product description or error message, and including it in multiple parts of your published artifact. It’s a powerful strategy for maintaining consistency, reducing maintenance efforts, and streamlining the authoring process.</p>

<p>DITA has built-in support for content reuse, with mechanisms like conrefs and keyrefs that enable the creation of modular, reusable content components. This makes DITA an excellent choice for large-scale projects with significant amounts of reusable content.</p>

<p>While Markdown doesn’t have native content reuse capabilities, many static site generators and documentation platforms have extended Markdown to support this functionality. However, the implementation and syntax can vary between tools, and maintaining the structure and formatting of reused content can be challenging.</p>

<p>To address this issue, we at Doctave have developed a <a href="/blog/ballad-components">Markdown-aware component system</a> that handles the structure and formatting of reused content, ensuring seamless integration with the surrounding Markdown. This approach combines the modularity and reusability of DITA with the simplicity and flexibility of Markdown.</p>

<h3 id="tooling-and-ecosystem">Tooling and ecosystem</h3>

<p>When it comes to tooling and ecosystem, both Markdown and DITA offer a wide range of options to suit different needs and preferences.</p>

<p>For Markdown, the ecosystem is vast. Countless open-source and commercial tools are available, ranging from simple text editors to sophisticated documentation platforms. To transform Markdown into publishable output, you’ll typically use a static site generator or a Markdown-compatible documentation platform. These tools often provide additional features like templating, content reuse, and version control integration, allowing you to create professional-grade documentation. The choice of tool depends on factors such as your project’s complexity, desired level of customization, and team’s technical expertise.</p>

<p>DITA, on the other hand, benefits from being a well-established standard. This standardization promotes interoperability between different tools and systems, giving you the freedom to choose the best tools for your needs. Many DITA tools are designed to work seamlessly together, enabling smooth content creation, management, and publishing workflows. The DITA ecosystem includes authoring tools, content management systems, and publishing engines, catering to different aspects of the documentation process. While some tools may offer unique features or vendor-specific extensions, the core functionality remains consistent across the ecosystem.</p>

<p>Ultimately, the choice of tooling in both Markdown and DITA ecosystems depends on your specific requirements, budget, and team preferences. Assess your project’s needs, evaluate the available options, and select the tools that best align with your goals and workflows. Keep in mind that as your project evolves, you may need to adapt your tooling to accommodate changing requirements and scale effectively.</p>

<h2 id="choosing-markdown-or-dita">Choosing Markdown or DITA</h2>

<p>When choosing between Markdown and DITA, consider your team’s composition, project size, and specific requirements. Markdown’s simplicity makes it a great fit for teams with developers and a docs-as-code workflow. Its low barrier to entry enables quick start-up and collaboration. DITA’s structured authoring and content reuse shine in large, complex projects managed by experienced technical writers.</p>

<p>However, Markdown’s simplicity doesn’t mean it can’t scale. With the right tools and platform, Markdown can support larger projects while maintaining its ease of use. Doctave, for example, brings many structured authoring concepts to Markdown, offering the best of both worlds.</p>

<h2 id="the-future-of-markdown-and-dita">The future of Markdown and DITA</h2>

<p>As technical documentation evolves, both Markdown and DITA will play important roles. Markdown’s popularity among developers and its growing ecosystem of tools and platforms position it well for the future. We expect to see Markdown-based solutions continue to evolve, incorporating structured authoring concepts to handle more complex projects.</p>

<p>DITA will remain a strong choice for large-scale, complex documentation projects requiring advanced content reuse and strict document structure. However, the rise of Markdown is likely to influence DITA’s future, with more DITA-based tools embracing Markdown as an authoring format.</p>

<p>At Doctave, we believe in the power of Markdown and its potential to transform the world of technical documentation. By investing in tools and platforms that enhance Markdown’s capabilities while preserving its simplicity, we aim to make high-quality, well-structured documentation accessible to teams of all sizes and compositions.</p>
