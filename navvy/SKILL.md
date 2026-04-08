---
name: navvy
description: >
  Diagnose a codebase through its git history before reading any code. Surfaces churn hotspots,
  bus factor risks, bug clusters, velocity trends, and firefighting patterns. Only invoked directly
  via /navvy — does not auto-trigger.
---

# Navvy

Five git commands, run in under a minute, that tell you more about a codebase than an hour of reading code. Commit history is diagnostic data — it reveals team dynamics, risk concentration, and maintenance patterns that the code itself cannot.

Run all five commands, then synthesize the results into a diagnostic report.

## The Commands

Run these in parallel where possible. Adjust `--since` to match the project's age — use `1 year ago` for active projects, extend for slower-moving ones.

### 1. Churn hotspots

```bash
git log --format=format: --name-only --since="1 year ago" | sort | uniq -c | sort -nr | head -20
```

The 20 most-modified files in the past year. High churn on a file that nobody wants to own is the clearest signal of codebase drag — these files have unpredictable blast radius and inflate estimates.

### 2. Contributor map

```bash
git shortlog -sn --no-merges
```

Ranks contributors by commit count. Look for bus factor risk: if one person accounts for 60%+ of commits, knowledge is dangerously concentrated. Also check whether core contributors are still active.

### 3. Bug clusters

```bash
git log -i -E --grep="fix|bug|broken" --name-only --format='' | sort | uniq -c | sort -nr | head -20
```

Files most frequently touched in bug-related commits. Files appearing in both this list and the churn hotspots are highest-risk code — they keep breaking and keep getting patched.

### 4. Velocity trend

```bash
git log --format='%ad' --date=format:'%Y-%m' | sort | uniq -c
```

Commit counts by month across the full history. A steady rhythm is healthy. Sharp declines suggest departures or loss of momentum. Sporadic spikes suggest batched releases rather than continuous delivery.

### 5. Firefighting signals

```bash
git log --oneline --since="1 year ago" | grep -iE 'revert|hotfix|emergency|rollback'
```

Reverts and hotfixes. Frequent occurrences signal the team doesn't trust its deploy process — a symptom of deeper issues with testing or deployment reliability.

## Synthesizing the Report

After running all five commands, write a short diagnostic report. Structure it around what the data reveals, not around the commands themselves.

### What to look for

- **Overlap between churn and bugs.** Files appearing in both lists are the highest-leverage targets for refactoring or better test coverage.
- **Bus factor.** A single dominant contributor who's gone inactive is a risk. A well-distributed contributor map is healthy.
- **Velocity shifts.** Correlate drops or spikes with what you know about the project — team changes, rewrites, launches.
- **Firefighting frequency.** A few reverts a year is normal. Monthly hotfixes suggest systemic issues.

### Report format

```
# Codebase Diagnostic: [repo name]

## Key Findings
[2-4 bullet points: the most important things to know before touching this code]

## Churn Hotspots
[Top files, what they are, whether they overlap with bug clusters]

## Team & Ownership
[Bus factor assessment, active vs inactive contributors]

## Health Signals
[Velocity trend interpretation, firefighting frequency]

## Recommendations
[Where to focus attention, what to investigate further]
```

Keep it concise. The point is orientation, not exhaustive analysis. A reader should finish the report knowing where the bodies are buried and where to tread carefully.
