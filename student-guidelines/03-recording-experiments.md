# 3. Recording Experiments

**Every time** you work in the lab or analyze data, you should create or update an experiment entry. This section explains what to record and how to do it.

← **[Back to Student Guidelines](README.md)**

---

## Before You Start an Experiment

Open the lab notebook corresponding to that week’s experiment in VS Code. 

1. For every lab notebook, you will include your name, your lab partner(s), date, and isolate’s name.
<img width="612" height="281" alt="Screenshot 2026-08-14 at 2 36 31 PM" src="https://github.com/user-attachments/assets/3126c37a-4b93-49a1-a715-0d0b9f9916f4" />

2. You will also rename your lab notebook in VS Code. Right-click your lab entry and choose the “Rename” option. **Before submitting your work, rename your Lab notebook as: Lab-1-YourName-YYYY-MM-DD**
<img width="318" height="179" alt="Screenshot 2026-08-14 at 2 46 04 PM" src="https://github.com/user-attachments/assets/e3384eb4-bf68-405e-8a46-21076136e54f" />

3. Press (Command + S on Mac) or (Ctrl + S on Windows) to save the rename changes. To commit and push changes, follow the same steps as the “01-getting-started” instructions, Step 10. 


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
