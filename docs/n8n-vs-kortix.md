# n8n vs Kortix: a workflow engine and an open-source AI Operating System

Kortix is the open-source AI Operating System for open-ended work an agent finishes on its own, and n8n is a fair-code workflow engine for automation whose steps are fixed. The choice comes down to the shape of the work: n8n runs the nodes you wired in the order you wired them, and Kortix runs a session that plans its own steps, uses tools on its own cloud computer, and lands the result as a change request a person reviews.

## What n8n is

n8n is a fair-code workflow automation platform with native AI capabilities. The n8n repository describes a visual canvas that you extend with JavaScript and Python, run self-hosted or in the cloud, with 1,500+ integrations and 9,000+ workflow templates ([n8n on GitHub](https://github.com/n8n-io/n8n)). n8n licenses the code under the Sustainable Use License and the n8n Enterprise License, which permit use for your own internal business purposes, and its own docs describe the model as fair-code ([n8n docs](https://docs.n8n.io/n8n-community-license)). n8n defines a workflow as a collection of nodes connected together to automate a process, and an execution as a single run of that workflow ([n8n docs](https://docs.n8n.io/build/understand-workflows)). n8n self-hosts with Docker, on-premises or air-gapped, or runs on n8n Cloud ([n8n.io](https://n8n.io)).

## What Kortix is

Kortix is the open-source AI Operating System. Your agents, their skills, your company memory and every connector live in one git repo you own, and each session runs an agent in an isolated Linux sandbox on its own branch ([Read the docs](https://kortix.com/docs)). The agent works on a real cloud computer, and finished work opens as a change request that a person reads as a diff before it merges. Kortix is model-agnostic, so you pick the model per agent, per session or per message across Anthropic, OpenAI, Google or your own OpenAI-compatible endpoint with your own keys, and you set each tool call to allow, ask or block ([Kortix on GitHub](https://github.com/kortix-ai/suna)). Kortix reaches 3,000+ apps plus any MCP, OpenAPI, GraphQL or HTTP API, and it self-hosts on a laptop, a VPS, your VPC or on-premises, or runs as managed cloud ([Kortix on GitHub](https://github.com/kortix-ai/suna)).

## How they compare

Both self-host and both work with your own models, so the differences sit in the unit of work and in how the configuration is stored.

| Platform | Open source | Unit of work | Configuration |
|---|---|---|---|
| Kortix | Yes, open source (Elastic License 2.0) | Agent session on its own cloud computer | One git repo you own |
| n8n | Fair-code (Sustainable Use License) | Fixed workflow of nodes | Visual canvas plus code nodes |

| Platform | Integrations | Model choice | Human gate |
|---|---|---|---|
| Kortix | 3,000+ apps, plus MCP, OpenAPI, GraphQL, HTTP | Any model, your keys, per agent | Change request before merge |
| n8n | 1,500+ integrations, 9,000+ templates | OpenAI, Anthropic, Google, open-source models | Human-in-the-loop steps in a workflow |

## When n8n is the right call

n8n suits automation where the steps are known in advance. A form submission syncs a record, an invoice triggers an approval, a nightly job posts a report. The canvas makes the path visible, the integrations connect the systems, and a human-in-the-loop step holds an action until someone signs off ([n8n.io](https://n8n.io)). n8n's pricing favors long flows: n8n states that an execution is a single run of the entire workflow no matter how many steps it contains, so a 40-step flow counts the same as a one-step flow ([n8n pricing](https://n8n.io/pricing/)). Only production executions count toward a paid plan's quota, while manual runs, sub-workflow runs and error-workflow runs do not ([n8n docs](https://docs.n8n.io/build/understand-workflows/understand-executions)). For a fixed flow that runs constantly, that model is predictable.

## When Kortix does the work

Kortix fits work with no fixed flowchart. Researching a list, reproducing a failing checkout and opening a fix, reading a support thread and drafting the reply, or chasing an invoice all require judgment about the next step, and the steps differ on every run. A Kortix agent plans, calls tools and finishes a multi-step run on its own machine, and you review the result instead of wiring every branch ([Read the docs](https://kortix.com/docs)). The configuration stays as files in one git repo, so you can grep the whole setup, diff any change and roll it back. An Ask holds a tool call until a person approves it, and merge stays a person's decision, so an agent cannot land its own work.

## Moving from n8n to Kortix

Most of a move is a rename: a workflow becomes an agent plus skills, a node becomes a connector, a trigger node becomes a trigger in kortix.yaml, and an execution becomes a session and a change request. The migration guide maps each n8n concept onto Kortix and walks the switch ([migrate from n8n](https://n8n-alternative.com/migrate-from-n8n.html)).

The point-by-point version of this comparison is on the campaign site at [n8n vs Kortix](https://n8n-alternative.com/n8n-vs-kortix.html). [Get started with open-source Kortix](https://kortix.com) and hand it one job your team already runs.
