# Self-hosting an open-source n8n alternative

Kortix is the open-source AI Operating System you self-host when the job is open-ended work an agent has to finish, and n8n is the fair-code workflow engine you keep for the same steps every time. Kortix runs on your laptop, a VPS, your VPC or on-premises, keeps your model keys on your account, and lands every change as a change request you review.

## What open source buys you here

For Kortix, open source is a practical property of the configuration. Agents and skills are markdown, memory is ordinary files, and the connectors, triggers and machine image are declared in one kortix.yaml, so you can grep the whole setup, diff any proposed change and roll any part of it back. Kortix is open source (Elastic License 2.0): self-host, read and modify the code, and the source is at [Kortix on GitHub](https://github.com/kortix-ai/suna). The install and deployment commands are in the [Kortix docs](https://kortix.com/docs/host). Managed cloud stays available if you would rather not run the stack, and the same repo moves between the two.

## Self-host Kortix

The commands run on macOS or Linux. Install the CLI, sign in, scaffold a project, then push it ([CLI reference](https://kortix.com/docs/cli)):

```
curl -fsSL https://kortix.com/install | bash
kortix login
kortix init my-app
kortix ship
```

kortix init scaffolds a project directory with a kortix.yaml and a starter agent, and kortix ship creates the cloud project on its first run, then pushes your code. To keep everything on your own box, take the self-host path instead:

```
kortix self-host init --domain kortix.example.com
kortix self-host start
kortix self-host status
kortix self-host configure
```

Point an A or AAAA record at the box for your domain and for api.your-domain, then open ports 80 and 443 so the bundled Caddy proxy can issue a TLS certificate. Kortix runs as one Docker Compose stack holding the frontend, the API, the LLM gateway and the Supabase distribution, while agent sessions run on a separate sandbox provider, with Daytona as the default ([Self-hosting docs](https://kortix.com/docs/host)). kortix self-host configure prompts for the sandbox provider key and an optional managed-git token, and a self-hosted instance uses your own LLM key by default.

## What you can build once it is running

From Slack or Microsoft Teams, you add the Kortix app, invite the bot to a channel and mention it with a task. The message starts a session, and the agent works on its own computer with your connected tools and replies in the same thread. For recurring work, a trigger in kortix.yaml starts a session on a cron schedule or a signed webhook with nobody present. For engineering, a session runs in its own sandbox on its own branch, and you review the result before merging. Governance is set per call: each tool is allow, ask or block, down to the arguments of a single command.

## Where n8n fits

n8n self-hosts with Docker for jobs whose steps are known in advance, and its docs recommend Docker for most self-hosting needs ([n8n docs](https://docs.n8n.io/deploy/host-n8n/install-options/install-with-docker)). n8n runs the same path every time on your infrastructure or n8n Cloud, and it stays the right tool when the process does not change ([n8n.io](https://n8n.io)). Kortix takes the open-ended work where the steps are not known up front, with the configuration in git and your own model keys. Many teams run both.

The full self-host walkthrough is on the campaign site at [the open-source n8n alternative you can self-host](https://n8n-alternative.com/open-source-n8n-alternative.html). [Get started with open-source Kortix](https://kortix.com).
