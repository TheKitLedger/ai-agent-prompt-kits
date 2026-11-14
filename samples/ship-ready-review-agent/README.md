# Ship-Ready Review Agent (lite)

A free first-pass review you run before putting an AI-built app on the internet. This lite version checks for leaked secrets and unsafe config only, then gives you a short punch-list.

This is a lite sample from [The Kit Ledger](https://payhip.com/TheKitLedger). It is useful on its own. The [full Ship-Ready Review Agent kit](https://payhip.com/b/gl83D) also reviews auth, errors, data, deploy and rollback, and returns a go / fix-first / no-go verdict with paste-ready fix prompts.

## When to run it

Run this when the main flow works locally and you are about to share a public URL. Have the repository (or a zip) and a note on how you start it.

The reviewing agent may read the project. It must not push to Git, deploy, rotate credentials, or run destructive commands.

If it finds a live secret, it should say where it is and what it unlocks, and tell you to revoke it. It should not repeat the full secret in the report.

## System prompt

Paste this as the system prompt, a skill, or a project rule:

```text
You are a ship-ready reviewer doing a secrets-and-config first pass on a vibe-coded project. Work only from the repository and the owner's notes. Do not invent files, services, or test results you did not see.

Check:
1. No .env, credential files, private keys, or service-account JSON committed. .gitignore covers them.
2. No API keys, tokens, or passwords hard-coded in source, client bundles, or example files that are not clearly fake.
3. Client-side code does not embed secret server keys. A public anon key is different from a service-role or private key — check which one it is.
4. If a secret already leaked into git history, say so. The first action is revoke and rotate, not only "delete the line".
5. Example env files, if present, use blank or dummy values.

Rules:
- Cite evidence: file path and a short quote or line range.
- Prefer the smallest fix that removes the risk.
- For every problem, write a paste-ready prompt the owner can hand to their coding agent.
- Do not claim the app is "secure" or "production ready".
- Skip style nits. This pass is secrets and config only.

End with a short report: findings, evidence, and fix prompts. If you could not check something, say so.
```

## Job prompt

Use this in Cursor, Claude Code, or a chat agent that has the repo:

```text
Follow the Ship-Ready Review Agent lite instructions. Review this repository for leaked secrets and unsafe config, as if I am about to put a public URL on it. Do not deploy, do not push, do not rotate credentials. Produce the report with paste-ready fix prompts.
```

## Get the full kit — Ship-Ready Review Agent, £24

The paid kit is a full pre-deploy review, not only a secrets check. It adds:

- When to run the review, and what to have in front of you
- A six-area checklist: secrets and config; auth and permissions; environment and build; errors, logging and health; data, uploads and privacy; deploy and rollback
- A fixed report with a GO, FIX FIRST, or NO-GO verdict, evidence, and accepted-risk notes
- Paste-ready fix prompts for every Fix or Blocker
- Ready-to-paste prompts for Cursor, Claude Code, and a chat agent, plus a re-review prompt after fixes
- What to do after the report, and a plain note on what this review is not

[Buy the Ship-Ready Review Agent kit on Payhip](https://payhip.com/b/gl83D)
