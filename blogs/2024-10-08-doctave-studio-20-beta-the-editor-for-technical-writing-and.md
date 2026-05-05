---
title: "Doctave Studio 2.0 Beta: The editor for technical writing and docs-as-code"
url: "https://www.doctave.com/blog/doctave-studio-2-beta"
date: "Tue, 08 Oct 2024 08:00:00 +0300"
author: ""
feed_url: "https://www.doctave.com/feed.xml"
---
<p>We’re excited to announce that Doctave Studio 2.0 is now available in public beta! Doctave Studio is a new editor for technical writing and docs-as-code, and we’re excited to share it with you.</p>

<p>Want to see it in action? Here’s a quick introductory video of Doctave Studio 2.0:</p>

<div class="aspect-video rounded-md overflow-hidden md:-mx-8">
  
</div>

<div class="mt-12 bg-indigo-50 text-indigo-800 not-prose px-6 py-4 rounded-2xl border border-indigo-400 flex gap-4 items-start">
  <svg class="mt-1 size-6" fill="currentColor" height="200px" stroke="currentColor" stroke-width="0" viewBox="0 0 512 512" width="200px" xmlns="http://www.w3.org/2000/svg"><path d="M256 48C141.1 48 48 141.1 48 256s93.1 208 208 208 208-93.1 208-208S370.9 48 256 48zm19 304h-38.2V207.9H275V352zm-19.1-159.8c-11.3 0-20.5-8.6-20.5-20s9.3-19.9 20.5-19.9c11.4 0 20.7 8.5 20.7 19.9s-9.3 20-20.7 20z"></path></svg>
  <p class="leading-6">
  If you just want to see how to participate in the beta, you can <a class="text-indigo-950 underline" href="#how-to-get-involved-in-the-beta">jump straight to the end of this post</a></p>
</div>

<h2 id="why-build-a-new-editor">Why build a new editor?</h2>

<p>One of the biggest issues with docs-as-code is inconsistent tooling. While there are great tools out there (like <a href="https://github.com/errata-ai/vale" target="_blank">Vale</a>), it’s really hard to create a great authoring environment for docs-as-code. Getting spell check, broken links checking, auto-complete, and more configured is often too complex or time consuming, that lots of authors live without these tools.</p>

<p>This problem is compounded when you have multiple authors collaborating on the same documentation. One will have a spell checker configured, one will have auto-complete configured, another doesn’t have a broken links checker. The lack of a common authoring system causes friction, confusion, and ultimately raises the barrier for contributions.</p>

<p>And after all that, you still need to set up these same checks in your CI/CD pipeline!</p>

<p>This is what we set out to solve with Doctave Studio 2.0.</p>

<p>We’ve already made it easy to host, version, and review docs-as-code projects with our <a href="https://doctave.com" target="_blank">existing product</a>. Now we’re taking the next logical step and improving the docs-as-code <em>authoring experience</em>.</p>

<h2 id="whats-in-the-doctave-studio-20-beta">What’s in the Doctave Studio 2.0 beta?</h2>

<p>Today we’re launching Doctave Studio 2.0 into beta with a few key features:</p>

<ul>
  <li>A new, modern editor with a focus on the authoring experience</li>
  <li>Real-time previews of your content as you type (Markdown and OpenAPI!)</li>
  <li>Powerful auto-complete for your links, assets, and components</li>
  <li>Great error-reporting inline in your Markdown</li>
</ul>

<p>Let’s see some of these in action!</p>

<h3 id="real-time-previews">Real-time previews</h3>

<p>The right-side panel in Doctave Studio is dedicated to a real-time preview window. It shows you what your content will look like once published, and it’s updated in real-time as you make changes.</p>

<div class="rounded-2xl shadow px-6 pt-6 bg-radix-gray-2 h-fit md:-mx-8 mt-8 mb-4 not-prose border-radix-gray-4 border">
  <video class="rounded-lg border border-radix-gray-4" controls="" loop="" src="/assets/img/2024-10-08/real-time-previews.mp4">
  <p class="text-sm pt-4 pb-4 mb-0 text-radix-gray-11 font-medium text-center mx-auto">See your updates to Markdown and OpenAPI documentation in real-time</p>
</div>

<h3 id="auto-complete">Auto-complete</h3>

<p>Auto-complete helps you move fast as an author! It also prevents you from making mistakes when linking between different parts of your documentation.</p>

<p>Doctave Studio 2.0 supports auto-complete for all your internal links and assets.</p>

<div class="rounded-2xl shadow px-6 pt-6 bg-radix-gray-2 h-fit md:-mx-8 mt-8 mb-4 not-prose border-radix-gray-4 border">
  <video class="rounded-lg border border-radix-gray-4" controls="" loop="" src="/assets/img/2024-10-08/autocomplete-link.mp4">
  <p class="text-sm pt-4 pb-4 mb-0 text-radix-gray-11 font-medium text-center mx-auto">Auto-complete links and assets in your project</p>
</div>

<p>This also works Doctave’s built in components, as well as your own components. Not only do we auto-complete the names of your components, but we also auto-complete the attributes and their possible values.</p>

<p><em>(Oh, and we also support dark-mode!)</em></p>

<div class="rounded-2xl shadow px-6 pt-6 bg-radix-gray-2 h-fit md:-mx-8 mt-8 mb-4 not-prose border-radix-gray-4 border">
  <video class="rounded-lg border border-radix-gray-4" controls="" loop="" src="/assets/img/2024-10-08/autocomplete-component.mp4">
  <p class="text-sm pt-4 pb-4 mb-0 text-radix-gray-11 font-medium text-center mx-auto">Both Doctave's built in components and your own components are auto-completable</p>
</div>

<h3 id="error-reporting">Error reporting</h3>

<p>Doctave Studio 2.0 is built with a focus on error reporting and catching issues early.</p>

<p>You get a global view of all the errors in your project is our “Issues” tab:</p>

<p><img alt="Issues tab" src="/assets/img/2024-10-08/issues-tab.png" /></p>

<p>And as you’re typing we’ll also highlight issues inline in the editor itself:</p>

<p><img alt="Inline error inside the editor" src="/assets/img/2024-10-08/inline-error.png" /></p>

<p>We’re adding more and more error reporting features in the coming weeks, so stay tuned!</p>

<h2 id="what-were-focusing-on-next">What we’re focusing on next</h2>

<p>We’re only just getting started.</p>

<p>There’s a long list of improvements and features that we’ll be adding in the coming weeks and months. That being said, here’s non-exhaustive list of features we’re working on:</p>

<ul>
  <li>
    <p><strong>Refactoring support</strong></p>

    <p>Making it easy to move content around and not have all your links break, or extracting content into reusable components.</p>
  </li>
  <li>
    <p><strong>1-click publishing</strong></p>

    <p>We’re integrating Doctave’s hosting platform seamlessly with Doctave Studio. You’ll be able to publish your docs-as-code project in a single click.
(Or from CI/CD pipelines, naturally!)</p>
  </li>
  <li>
    <p><strong>Spell-check and Vale integration</strong></p>

    <p>We want you to be able to define your own style guides in your project, and they’ll automatically be enforced in Doctave Studio. No plugins to install.</p>
  </li>
  <li>
    <p><strong>Git-integration</strong></p>

    <p>Git is at the heart of docs-as-code, and Doctave Studio will assist with common Git workflows out of the box.</p>
  </li>
</ul>

<h2 id="how-to-get-involved-in-the-beta">How to get involved in the beta</h2>

<p>We’d love for you to try out Doctave Studio and share your feedback with us!</p>

<p>If you’re interested in participating in the beta, join our <a href="https://join.slack.com/t/doctavestudio20beta/shared_invite/zt-2rr6xyyn7-sS7zGsi372JdzMNCewNTnQ" target="_blank">Slack community</a>. Once you’ve joined, you’ll get instructions on how to install and get started with Doctave Studio 2.0.</p>

<div class="not-prose">
  <a class="bg-indigo-600 hover:bg-indigo-700 text-white rounded-md px-3 py-2 text-sm font-medium inline-flex items-center gap-x-2" href="https://join.slack.com/t/doctavestudio20beta/shared_invite/zt-2rr6xyyn7-sS7zGsi372JdzMNCewNTnQ" target="_blank">
    <svg class="size-4" fill="none" height="200px" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" width="200px" xmlns="http://www.w3.org/2000/svg"><path d="M14.5 10c-.83 0-1.5-.67-1.5-1.5v-5c0-.83.67-1.5 1.5-1.5s1.5.67 1.5 1.5v5c0 .83-.67 1.5-1.5 1.5z"></path><path d="M20.5 10H19V8.5c0-.83.67-1.5 1.5-1.5s1.5.67 1.5 1.5-.67 1.5-1.5 1.5z"></path><path d="M9.5 14c.83 0 1.5.67 1.5 1.5v5c0 .83-.67 1.5-1.5 1.5S8 21.33 8 20.5v-5c0-.83.67-1.5 1.5-1.5z"></path><path d="M3.5 14H5v1.5c0 .83-.67 1.5-1.5 1.5S2 16.33 2 15.5 2.67 14 3.5 14z"></path><path d="M14 14.5c0-.83.67-1.5 1.5-1.5h5c.83 0 1.5.67 1.5 1.5s-.67 1.5-1.5 1.5h-5c-.83 0-1.5-.67-1.5-1.5z"></path><path d="M15.5 19H14v1.5c0 .83.67 1.5 1.5 1.5s1.5-.67 1.5-1.5-.67-1.5-1.5-1.5z"></path><path d="M10 9.5C10 8.67 9.33 8 8.5 8h-5C2.67 8 2 8.67 2 9.5S2.67 11 3.5 11h5c.83 0 1.5-.67 1.5-1.5z"></path><path d="M8.5 5H10V3.5C10 2.67 9.33 2 8.5 2S7 2.67 7 3.5 7.67 5 8.5 5z"></path></svg>
    Join us on Slack
  </a>
</div>

<p>Happy documenting!</p>

<p><em>- Nik &amp; Anton, Doctave Founders</em></p>
