---
title: "Introducing Skills Registry"
url: "https://portkey.ai/blog/skills-registry/"
date: "Thu, 23 Apr 2026 13:07:50 GMT"
author: "Siddharth Sambharia"
feed_url: "https://portkey.ai/blog/rss/"
---
<img alt="Introducing Skills Registry" src="https://storage.ghost.io/c/04/80/04808bfa-0485-4139-98cc-e3f82ab7f009/content/images/2026/04/Facebook-Post-7.png" /><p>Coding agents are only as good as the context you give them. <a href="https://code.claude.com/?ref=portkey.ai">Claude Code</a>, <a href="https://cursor.com/?ref=portkey.ai">Cursor</a>, and <a href="https://openai.com/index/introducing-codex/?ref=portkey.ai">Codex</a> all support <a href="https://agentskills.io/?ref=portkey.ai">Agent Skills</a> &#x2013; markdown files that tell your agent how your team actually works. Code review standards, security checklists, PR requirements, service conventions. Write a skill once, put it in the right directory, and the agent picks it up automatically.</p><p>The problem is what happens after that. The skills your best engineer has on their laptop aren&apos;t on anyone else&apos;s. Different agents need them in different directories. There&apos;s no versioning, no review process, no way to push an update to the whole team.</p><p><strong>Skills Registry fixes this</strong>. Author skills in one place, review and version them, sync to every agent with one command.</p><hr /><h2 id="how-it-works">How it works</h2><h3 id="1-create-skills-in-portkey">1. Create skills in Portkey</h3><p>In <a href="https://portkey.ai/docs/product/prompt-library?ref=portkey.ai">Prompt Engineering Studio</a>, create a <a href="https://portkey.ai/docs/product/prompt-library/prompt-partials?ref=portkey.ai">Prompt Partial</a> for each skill. Write the <code>SKILL.md</code> content directly in the editor:</p><figure class="kg-card kg-image-card kg-card-hascaption"><img alt="Introducing Skills Registry" class="kg-image" height="697" src="https://storage.ghost.io/c/04/80/04808bfa-0485-4139-98cc-e3f82ab7f009/content/images/2026/04/image-33.png" width="2000" /><figcaption><span style="white-space: pre-wrap;">Portkey&apos;s Skill Template</span></figcaption></figure><pre><code class="language-yaml">---
name: code-reviewer
description: Use when reviewing code or PRs. Apply company review standards.
---

# Code Review Standards

Lead with the most important issue.
Explain why it&apos;s a problem, not just what it is.
Suggest a specific fix with code, not just a description.
Group by severity: critical &#x2192; warning &#x2192; suggestion.
</code></pre><p>Each skill gets a stable ID, full version history, and a draft/publish workflow. Start with a few high-value ones &#x2014; code review, security patterns, what makes a PR mergeable at your org.</p><h3 id="2-review-and-publish">2. Review and publish</h3><p>Portkey&apos;s draft/publish model maps to any review process your team already has:</p><ol><li>Engineer authors a skill &#x2192; saved as draft</li><li>Tech lead or senior engineer reviews</li><li>Approved &#x2192; published</li></ol><p>Published skills are what syncs. Drafts stay invisible to the CLI. Every change is tracked in version history. If a published skill causes problems, roll back to any previous version with one click &#x2014; the next sync propagates the fix.</p><h3 id="3-sync-to-every-agent">3. Sync to every agent</h3><p><a href="https://github.com/Portkey-AI/cli?ref=portkey.ai">Portkey&apos;s CLI</a> pulls published skills from your Portkey workspace and writes them to the correct directory for each agent &#x2014; Claude Code, Cursor, Codex, OpenCode, GitHub Copilot, and more.</p><p>To sync just skills:</p><pre><code class="language-bash">npx portkey skills sync
</code></pre><pre><code>Fetching skills from Portkey...

  Found 3 skill(s) in your workspace:

   1.  code-reviewer       Code review standards
   2.  security-patterns   Security checklist for all code
   3.  pr-checklist        PR merge requirements

  Sync all 3? [Y]: Y

&#x2713; Synced 3/3 skills to 3 agents
</code></pre><p>If your team also uses Portkey for model routing and <a href="https://portkey.ai/docs/product/mcp-gateway/mcp-registry?ref=portkey.ai">MCP management</a>, the CLI configures the full stack at once &#x2014; gateway routing for <a href="https://portkey.ai/docs/product/observability?ref=portkey.ai">observability</a> and cost tracking, MCP servers from your workspace, and published skills from your registry:</p><pre><code class="language-bash">npm install -g portkey</code></pre><pre><code>&#x2713;  Gateway configured  &#x2192; ANTHROPIC_BASE_URL=https://api.portkey.ai/v1
&#x2713;  MCP servers (3)     &#x2192; .claude/mcp.json
&#x2713;  Skills synced (12)  &#x2192; .claude/skills/
</code></pre><p>A new engineer joins, runs the command, and they&apos;re working with the same context as someone who&apos;s been on the team for three years.</p><hr /><h2 id="get-started">Get started</h2><p>The Skills Registry is available on all Portkey <a href="https://portkey.ai/pricing?ref=portkey.ai">plans</a>.</p><ul><li><a href="https://portkey.ai/docs/guides/coding-agents/skills?ref=portkey.ai" rel="noreferrer">Skills Registry docs </a></li><li><a href="https://portkey.ai/docs/guides/coding-agents/agent-cli?ref=portkey.ai" rel="noreferrer">CLI docs </a></li></ul><p><a href="https://app.portkey.ai/?ref=portkey.ai"><strong>Set up your skills registry &#x2192;</strong></a></p>
