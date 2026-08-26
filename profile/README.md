<p align="center">
  <img src="https://www.dawnlit.com/favicon.svg" width="76" alt="DawnLit AI" />
</p>


<h1 align="center">DawnLit AI</h1>

<p align="center"><strong>We build AI products — not just models.</strong></p>

---

## What we work on

A language model on its own does very little. Nearly everything that makes one useful sits
around it: the software that lets it reach into the tools people already use, the serving layer
that keeps it answering, and the interface that puts it in front of someone who is not an
engineer.

So that is the work — AI products end to end, rather than a model and a demo. Research tooling,
agent infrastructure, and the applications built on top of both. Some of it is open source, and
that part lives here.

## Open source

### [`outlook-bridge`](https://github.com/dawnlit-ai/outlook-bridge)

Drive a real, locally installed Outlook client from Node — read the inbox, send and reply,
manage drafts and signatures, work with template mail, file and delete messages. No Graph API,
no app registration, no tenant admin sign-off: it automates the desktop client itself, the same
way a person would.

- **Windows** through PowerShell and Outlook's COM object model, **macOS** through AppleScript —
  one contract, fully implemented on both, so nothing returns a per-platform union you have to
  narrow.
- `capabilities()` is derived from the type, so a function added to the contract fails both
  platform maps at compile time rather than quietly reporting itself as supported.
- Every deliberate failure is an `OutlookError` carrying a stable `code`. The codes are the API;
  the messages are not.
- Per-call timeouts, output ceilings and `AbortSignal` cancellation, on an instance no other
  caller in the process can disturb.

<sub>TypeScript · Node 24+ · Apache-2.0</sub>

### [`outlook-mcp`](https://github.com/dawnlit-ai/outlook-mcp)

The same surface as [MCP](https://modelcontextprotocol.io) tools. One call registers a full set
of Outlook read / send / reply / draft / template / cleanup tools on any MCP server, and a model
can work a real mailbox.

- Thin, generic wrappers over the bridge — no application's business rules baked in, so it reads
  the same whether the host is a logistics assistant, a sales CRM, or anything else.
- Attachment handling comes along: PDF, Excel and plain-text extraction, images passed through.
- Registers alongside whatever app-specific tools you already have; reach past it into the bridge
  for anything it deliberately leaves out.

<sub>TypeScript · Apache-2.0</sub>

---

<p align="center">
  <a href="https://dawnlit.com">dawnlit.com</a>
</p>
