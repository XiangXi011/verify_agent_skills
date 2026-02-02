# agent-audit-skill

A gatekeeper/audit playbook for validating RAG + Agent systems across Stage0~Stage4 with evidence-first rules, hard blockers, and reproducible scoring.

## Contents

- `SKILL.md` — the full playbook (v1.2.0)
- `LICENSE` — MIT

## Identity

- Internal skill name: `verify-agent-rag-playbook`
- Trigger word: `agent-audit-skill`

## Quick Start (Codex skills)

1) Copy `SKILL.md` into your Codex skills directory.
2) In your `agent-audit-skill` system prompt, declare:
   - Follow Trigger / Input Contract / Interrogation Protocol / Output Contract
   - No evidence => UNKNOWN=FAIL
   - Use Scoring Spec (Appendix C) to compute `overall_result`
   - Output v1.2 JSON (with `system_fingerprint` and `evidence_refs`)
3) Run with a gate prompt, e.g.

```
agent-audit-skill，我们要做 Stage2 标准版验收。这里是指标与证据清单（…）。请按门禁输出 JSON 审计报告。
```

## Notes

- If a P0 blocker exists, the result must be `BLOCKER_FAIL`.
- If Target Stage or thresholds cannot be aligned, stop scoring and return `scoring_status=not_scored`.

## License

MIT
