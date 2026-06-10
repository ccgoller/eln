# 3. Recording Experiments

Every time you work in the lab or analyze data, you should create or update an experiment entry. This section explains what to record and how to do it.

← **[Back to Student Guidelines](README.md)**

---

## Before You Start an Experiment

1. Create a new entry file from the template:

```bash
cp path/to/templates/experiment-entry.md \
   experiments/YYYY-MM-DD_short-title.md
```

2. Fill in the **Objective**, **Hypothesis**, and **Materials/Reagents** sections *before* you begin.
3. Commit and push this initial entry so there is a timestamped record that you planned the experiment:

```bash
git add experiments/YYYY-MM-DD_short-title.md
git commit -m "Add planned entry: short-title"
git push
```

---

## During the Experiment

Record observations in real time whenever possible. Write:

- Exact quantities, concentrations, lot numbers, and instrument settings.
- Any deviations from the written protocol.
- Unexpected observations, even if they seem unimportant now.
- The time at key steps (especially for time-sensitive procedures).

---

## After the Experiment

1. Complete the **Results** and **Discussion** sections of your entry.
2. Add any raw data files to the `data/` folder and link to them from the entry.
3. Commit all changes:

```bash
git add experiments/YYYY-MM-DD_short-title.md data/YYYY-MM-DD_dataset.csv
git commit -m "Complete entry: short-title — results and data"
git push
```

---

## Adding Images and Data Files

Large binary files (images, videos, large datasets) should be placed in `data/` and referenced by relative path in your Markdown entry:

```markdown
![Gel electrophoresis result](../data/2025-03-14_gel-image.png)
```

For very large files (> 50 MB), ask your instructor about using [Git LFS](https://git-lfs.com/).

---

## Commit Messages

Good commit messages make it easy to find what changed and when.

| ✅ Good | ❌ Bad |
|---------|-------|
| `Add entry: pcr-optimization — initial setup` | `update` |
| `Complete entry: western-blot — band quantification added` | `changes` |
| `Fix typo in protocol-western-blot.md` | `fix` |
| `Add raw data: flow-cytometry 2025-03-20` | `data` |

**Format:** `<verb> <what>: <short-title> — <detail if needed>`

---

## Referencing Protocols

If you followed a standard lab protocol, write the protocol name in the entry and store the full protocol in `protocols/`:

```markdown
## Protocol

See [Protocol: Western Blot](../protocols/protocol-western-blot.md).
Deviations: used 10% SDS-PAGE gel instead of 12%.
```

---

## Linking Between Entries

You can cross-reference experiments by linking to other files:

```markdown
Follows up on [2025-03-10 initial PCR](2025-03-10_pcr-initial.md).
```

---

## Next Step

→ [Best Practices](04-best-practices.md)
