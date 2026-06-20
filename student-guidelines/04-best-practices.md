# 4. Best Practices

Following these practices will make your lab notebook more useful to you and easier for your instructor to review.

← **[Back to Student Guidelines](README.md)**

---

## Commit Early and Often

Think of `git commit` as saving your work with a description. You should commit:

- **Before** you start an experiment (planned entry with objective/hypothesis).
- **During** a long experiment when you hit a natural pause.
- **After** you finish writing up results and discussion.
- **Whenever** you add, revise, or correct anything — even fixing a typo is worth a commit.

A good rule of thumb: **at least one commit per lab session**.

---

## Write for Your Future Self

Assume that you will re-read this notebook six months from now with no memory of what you did. Always include:

- The full name and lot number of reagents and equipment.
- The exact instrument settings (not just "standard settings").
- Environmental conditions if they matter (temperature, humidity, time of day).
- Why you made decisions, not just what you decided.

---

## Never Delete or Overwrite Raw Data

Raw data files in `data/` should be treated as read-only once committed. If you need to process or clean data, create a new file (e.g., `2025-03-14_dataset-cleaned.csv`) and keep the original.

Git retains the history of all changes, so previous versions are always recoverable — but only if you have not overwritten the file without committing first.

---

## Use Issues for Questions and Corrections

If you realize you made an error in a past entry, **do not silently edit it**. Instead:

1. Open a GitHub Issue in your notebook repository describing the error.
2. Make the correction in a new commit that references the issue number (e.g., `Fix concentration value, closes #3`).

This creates a transparent audit trail.

---

## Keep Your README Up to Date

Your `README.md` is the first thing your instructor sees. Update it at least once a week to reflect:

- Current project status.
- A brief summary of recent work.
- Any major findings or open questions.

---

## Use Branches for Parallel Experiments

If you are running two unrelated experiments simultaneously, consider using Git branches to keep entries organized:

```bash
git checkout -b experiment/drug-titration
# work on this experiment, commit as usual
git push -u origin experiment/drug-titration
```

Merge into `main` once the experiment is complete and reviewed.

---

## Sync Regularly

Push to GitHub at the end of every lab session:

```bash
git push
```

This ensures your work is backed up and visible to your instructor, and protects against losing data if your local machine has a problem.

---

## Summary Checklist

Use this checklist at the end of each lab session:

- [ ] All observations recorded in the entry file
- [ ] Raw data files added to `data/`
- [ ] Entry updated with results and initial discussion
- [ ] All changes committed with descriptive messages
- [ ] Changes pushed to GitHub (`git push`)
- [ ] README updated if significant progress was made
