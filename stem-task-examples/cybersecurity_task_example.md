# SkillsBench Task Example — Cybersecurity Domain

## Task: Identify Access Control Violations in a System Log

### Instruction
You are given a system access log (`access_log.json`). Analyze the log and produce a report (`violations_report.md`) that:
1. Lists all access attempts that violate the principle of least privilege
2. Classifies each violation by severity: Critical, High, Medium, or Low
3. Provides a one-sentence remediation recommendation for each violation
4. Saves the final report to `/output/violations_report.md`

Rules:
- Do not flag failed login attempts as violations unless they exceed 5 in a 10-minute window
- Cross-reference user roles against the provided `roles_matrix.json`
- Output must be valid Markdown with a table structure

---

### Reference Solution Approach
1. Parse `access_log.json` — extract user_id, resource_accessed, timestamp, role
2. Load `roles_matrix.json` — build allowed resource map per role
3. Compare each access event against allowed resources
4. Flag mismatches, classify severity by resource sensitivity
5. Write structured Markdown report

---

### Verifier Checklist
- [ ] Output file exists at `/output/violations_report.md`
- [ ] File is valid Markdown
- [ ] Contains a table with columns: User, Resource, Timestamp, Severity, Remediation
- [ ] All Critical severity items involve admin-level resource access
- [ ] No false positives on legitimate accesses per roles_matrix

---

### Skill File (what the AI agent learns from)
- In this system, `admin` resources are prefixed with `/sys/`
- Severity classification: `/sys/` access by non-admin = Critical; data exfil patterns = High; misconfigured read access = Medium
- Least privilege principle: users should only access resources explicitly listed in their role
- Common edge case: service accounts (prefix `svc_`) have elevated permissions by design — do not flag
