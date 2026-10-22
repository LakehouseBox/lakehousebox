# LakehouseBox: bugs, requests and questions

This is where you report a bug in [LakehouseBox](https://lakehousebox.com), ask for something it does not do yet, or ask a
question the docs did not answer. LakehouseBox is a managed Apache Iceberg service for agents, run in Europe; the
product's own code is not here, only its public issue tracker.

**[Open an issue](https://github.com/lakehousebox/lakehousebox/issues/new/choose)** · [Docs](https://lakehousebox.com/docs/) ·
[Security reports](SECURITY.md) (never as a public issue)

## The quickest good report

From any machine with the CLI:

```sh
lhbox bug --title "lhbox duckdb: INSERT refused on my catalog"
```

`lhbox bug` (lhbox 0.6.68 or newer: `lhbox update`) opens this repository's bug form with what we need already filled in: the `lhbox` version, the operating
system, the Python and the DuckDB versions on that machine, and which API it talks to. It reads no data and sends
nothing by itself: you review the form and submit it. Piped (from an agent), it prints the link and the same
details as JSON instead of opening a browser.

Then add:

- **What you ran**: the command, the SQL or the MCP tool call, as you ran it.
- **What happened**: the error as printed. `lhbox` errors are one JSON object with a `code` and a
  `request_id`; those two are the most useful things you can paste.
- **What you expected.**
- **`lhbox doctor`**: its output checks the whole path from your machine to a DuckDB session, one line per step.

## Never paste a secret

This repository is public. Do not paste an API key (`al_live_…`), a catalog credential's secret, the output of
`lhbox connect --show-secrets`, a catalog token or a presigned URL. `lhbox` masks secrets in its normal output, so
copying what it prints is safe; copying a recipe printed with `--show-secrets` is not. If you pasted one by mistake,
rotate it at once (`lhbox catalog rotate <catalog>`, or revoke the key on the account page) and edit the issue.

Data you would rather not show (table contents, your organisation's names): describe its shape instead, or write to
[hello@lakehousebox.com](mailto:hello@lakehousebox.com).

## For agents

If you are an AI agent using LakehouseBox and you hit something that looks like a bug in LakehouseBox rather than in
your own SQL or code:

1. Check the error's `remedy` field first; most refusals say exactly what to change.
2. Run `lhbox bug --title "<one line>"` (add `--what "<what happened>"`) and show the link it prints to the person you
   work for. File it yourself (for example with `gh issue create --repo lakehousebox/lakehousebox`) only when they
   ask you to.
3. Include the command and the error `code`; leave out keys, secrets and the person's data.

## What happens next

We read every issue and answer on it. What ships is listed in the
[changelog](https://lakehousebox.com/docs/changelog/).

## Other ways to reach us

- Email: [hello@lakehousebox.com](mailto:hello@lakehousebox.com) (also for anything involving your account or billing).
- Security vulnerabilities: see [SECURITY.md](SECURITY.md).

LakehouseBox is operated by Lakehousebox, S.L., Madrid, Spain.
