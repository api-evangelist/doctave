---
title: "Continuous documentation: publishing docs early and often"
url: "https://www.doctave.com/blog/continuous-documentation"
date: "Tue, 23 Jan 2024 09:00:00 +0200"
author: ""
feed_url: "https://www.doctave.com/feed.xml"
---
<p>One of the key pillars of <a href="/docs-as-code">docs-as-code</a> is releasing changes via <a href="https://about.gitlab.com/topics/ci-cd/">CI/CD</a>. Just as how software is often released continuously, we can keep our documentation up to date as the product changes.</p>

<p>This lets us achieve <strong>continuous documentation</strong>: instead of large bulk releases, we can incrementally improve our documentation, as we make changes to our product.</p>

<p>Let’s dive into how continuous documentation is implemented in practice.</p>

<h2 id="making-it-easy-to-make-changes">Making it easy to make changes</h2>

<p>The key to continuous documentation is making it easy to contribute to documentation.</p>

<p>We want to lower the barrier to making changes, and empower contributors to make the docs better. Let’s see how!</p>

<h3 id="smaller-iterative-changes">Smaller, iterative changes</h3>

<p>The bigger the change, the harder it is to make. Everyone who has worked in the technology industry has seen large project spiral out of control, missing deadlines, and seemingly never ending.</p>

<p>Fast-moving teams get around this problem by splitting work into smaller chunks. Instead of a large monolithic release, preferring smaller, iterative changes that are easier to manage. Small changes are easier to review, have less risk, and can be shipped with fewer checks in place.</p>

<h3 id="releasing-docs-with-code">Releasing docs with code</h3>

<p>It makes sense to update your product and documentation at the same time. Documentation should be in your <a href="https://www.scrum.org/resources/what-definition-done">“definition of done”</a>: a hard requirement for a feature to be released.</p>

<p>A Git <a href="https://semaphoreci.com/blog/what-is-monorepo">monorepo</a>, it’s natural to even have code and documentation changes in the same branch or pull-request. Engineers and technical writers can work in the same branch, and eventually merge and deploy the code and documentation in tandem.</p>

<p>This is what we do at Doctave. We use a monorepo with a dedicated <code class="language-plaintext highlighter-rouge">/docs</code> folder. Every customer-facing feature will have documentation changes included, and get reviewed as part of the same pull-request on GitHub.</p>

<p>A multi-repository setup requires some more coordination. but the same principles apply. Every feature change should have a corresponding change in the documentation repository.</p>

<h3 id="empowering-contributors">Empowering contributors</h3>

<p>Documentation is the responsibility of the whole product team. We want to foster a culture where everyone is welcome to contribute by either writing or reviewing documentation.</p>

<p>Companies like <a href="/blog/2021/09/07/how-google-twitter-and-spotify-build-culture-of-documentation">Google, Twitter, and Spotify put a lot of effort into building a culture of documentation</a>. We also see this at many of our customers: reviews are done not just by technical writers, but engineers and product managers responsible for the implementation of a feature.</p>

<h3 id="automate-automate-automate">Automate, automate, automate</h3>

<p>Automation means your process is repeatable and, most importantly, transparent. You don’t want to be bottlenecked by that one person who knows how to copy your final artifacts to the production server.</p>

<p>Instead, when changes are merged, they should automatically be deployed without human intervention.</p>

<p>If you are worried about quality issues, you can catch lots of common issues with tools like linters like <a href="https://vale.sh/">Vale</a>. They will check your content for spelling issues or unwanted phrases. This lessens some of the burden on the manual reviewer.</p>

<h2 id="implementing-continuous-documentation">Implementing continuous documentation</h2>

<p>Let’s talk tactically: how do we implement continuous documentation in practice?</p>

<h3 id="cicd-integration">CI/CD integration</h3>

<p>CI/CD plays an important part in continuous documentation since it’s the engine automating everything.</p>

<p>The exact way you should implement CI/CD depends on your repository setup and choice of tools. At minimum, you need to be triggering automatic deployments whenever new changes are merged in your main branch.</p>

<p>To give a more complex example, we have an <a href="https://docs.doctave.com/docs/publishing/ci-cd">example in our documentation</a> about how to integrate Doctave to your CI/CD pipeline in <a href="https://github.com/features/actions">GitHub Actions</a>.</p>

<p>The way it works is:</p>

<ul>
  <li>Any time there is a pull request, or we’ve merged changes into the <code class="language-plaintext highlighter-rouge">main</code> branch,</li>
  <li>Check if there are changes to the <code class="language-plaintext highlighter-rouge">docs/</code> subfolder,</li>
  <li>If so, send the docs to Doctave</li>
</ul>

<p>We then have versioning rules set up in Doctave that update the public-facing documentation when the <code class="language-plaintext highlighter-rouge">main</code> branch is updated. Else, we just get an isolated preview environment that we can use in our review process.</p>

<p>It’s simple, and works great!</p>

<h3 id="building-a-culture-of-documentation">Building a culture of documentation</h3>

<p>We want to empower contributors by building a culture of documentation. Instead of technical writers being solely responsible for docs, developers should feel welcome to write documentation for the features they are working on, and product managers should be considering how documentation fits into the overall product.</p>

<p>We have found there are three key steps to doing this:</p>

<ul>
  <li><strong>Standardize your process and tools:</strong> Teach everyone in your team <em>how</em> your documentation is updated</li>
  <li><strong>Make documentation an expectation</strong>: No feature is done without great documentation</li>
  <li><strong>Remove as much friction as possible</strong>: Have a development environment that Just Works™ and use the same workflows you’re already using for reviewing code</li>
</ul>

<h3 id="versioning-and-branching">Versioning and branching</h3>

<p>It’s important your team has an agreed upon strategy for versioning and branching documentation. We’ve written a whole article on <a href="/blog/documentation-versioning-best-practices">versioning documentation</a>, so we’ll focus on branching strategies briefly in this section.</p>

<p>Choosing the right branching structure depends on your repository layout and team preferences. The goal is to ensure it’s clear which documentation changes are associated with a specific product change.</p>

<p>As mentioned above, in the multi-repo case the docs changes may be in the same pull-request. In the multi-repo case, there may be branches in different repositories with matching names.</p>

<p>Having your team is aligned on your branching strategy makes releasing changes much more fluid and removes confusion.</p>

<h2 id="conclusions">Conclusions</h2>

<p>Continuous documentation is not just a practice, but a mindset shift in how we approach documentation.</p>

<p>Here are the main takeaways:</p>

<ul>
  <li>
    <p><strong>Embrace small, iterative changes</strong></p>

    <p>Continuous documentation thrives on the principle of making small, manageable updates to documentation.</p>
  </li>
  <li>
    <p><strong>Foster a culture of documentation</strong></p>

    <p>By empowering all team members, from engineers to product managers, to contribute to documentation, we create a culture where documentation is everyone’s responsibility.</p>
  </li>
  <li>
    <p><strong>Leverage automation and CI/CD integration</strong></p>

    <p>Integrating documentation processes into CI/CD pipelines streamlines updates, making documentation an integral part of the development workflow.</p>
  </li>
</ul>
