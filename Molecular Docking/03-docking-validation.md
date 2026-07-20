# Chapter 3
# Docking Validation

> **Estimated Reading Time:** 40–50 minutes
>
> **Difficulty:** ⭐⭐⭐ Intermediate

---

# Overview

Before docking a new ligand, the docking protocol must be validated. Protocol validation ensures that the selected docking parameters are capable of reproducing the experimentally observed binding mode of the native ligand.

The most common validation approach is **redocking**, in which the crystallographic ligand is removed from the protein and docked back into its original binding site. The predicted pose is then compared with the experimental crystal structure using the **Root Mean Square Deviation (RMSD)**.

A reliable docking protocol should reproduce the native binding orientation with minimal deviation.

---

# Learning Objectives

After completing this chapter, you will be able to:

- Understand the purpose of docking validation.
- Explain the concept of redocking.
- Perform 100 redocking simulations in YASARA.
- Interpret RMSD values.
- Determine whether a docking protocol is valid.
- Prepare a validated receptor for future docking studies.

---

# Why Validation Is Necessary

Docking software can generate many possible ligand orientations (poses). However, not every scoring function or search algorithm accurately predicts the experimentally observed binding mode.

Validation answers a simple question:

> **Can this docking protocol reproduce the experimentally known ligand position?**

If the answer is **yes**, the protocol can be confidently used to dock novel compounds.

---

# What Is RMSD?

Root Mean Square Deviation (RMSD) measures the average distance between the atoms of the experimental ligand and the docked ligand.

Mathematically,

\[
RMSD=\sqrt{\frac{\sum d_i^2}{N}}
\]

where

- \(d_i\) = distance between corresponding atoms
- \(N\) = number of atoms

Smaller RMSD values indicate better agreement.

---

# RMSD Interpretation

| RMSD | Interpretation |
|-------|---------------|
| < 2.0 Å | Excellent validation |
| 2.0–3.0 Å | Acceptable |
| > 3.0 Å | Poor validation |

Most molecular docking studies use **RMSD < 2 Å** as the acceptance criterion.

---

# Validation Workflow

```text
Prepared Protein

↓

Load Protein

↓

Delete Waters

↓

Set pH

↓

Clean Structure

↓

Save 4hjo.yob

↓

Run 100 Redocking

↓

Calculate RMSD

↓

Protocol Validation
```

---

# Required Files

Before starting, ensure that the following files are available:

```text
protein/

├── 4hjo.pdb

└── 4hjo.yob
```

---

# Step 1 — Open the Prepared Protein

Launch **YASARA Structure**.

Load the prepared receptor:

```text
File

↓

Load

↓

YASARA Object

↓

4hjo.yob
```

Verify that the structure loads correctly.

---

# Step 2 — Check the Protein Structure

Before performing validation, confirm that:

- Water molecules have been removed.
- pH has been adjusted.
- The structure has been cleaned.
- The native ligand is still present.

The native ligand is essential because it serves as the reference structure for RMSD calculations.

---

# Step 3 — Run Redocking

Navigate to:

```text
Options

↓

MolMod

↓

Redocking (100x)
```

YASARA will automatically perform:

- 100 independent docking runs
- Pose generation
- Pose clustering
- RMSD calculations

Depending on the computer specifications, this process may take several minutes.

---

# Step 4 — Monitor the Calculation

During execution, the console displays messages such as:

```text
Starting docking...

Pose 1 completed

Pose 2 completed

...

Pose 100 completed

Docking Finished
```

Do not interrupt the process.

---

# Step 5 — Locate the RMSD File

After completion, YASARA generates:

```text
rmsd_bestpose_all.txt
```

This file contains the RMSD value for each docking run.

Example:

```text
Run     RMSD (Å)

1       0.83

2       1.02

3       0.91

...

100     1.18
```

---

# Step 6 — Evaluate the Results

Open:

```text
rmsd_bestpose_all.txt
```

Review the RMSD distribution.

If all or most values are below:

```text
2 Å
```

the docking protocol is considered valid.

---

# Understanding RMSD

A low RMSD means that the docking algorithm successfully reproduced the experimentally observed binding orientation.

Conversely, a high RMSD suggests that the docking parameters, receptor preparation, or scoring function may need to be adjusted.

---

# Why Perform 100 Redocking Runs?

A single docking run may produce a good result by chance.

Running the protocol 100 times allows researchers to evaluate:

- Reproducibility
- Stability
- Robustness
- Consistency

This provides greater confidence in the docking protocol.

---

# Expected Output

After validation, the project directory should contain:

```text
validation/

├── rmsd_bestpose_all.txt

├── docking.log

└── generated poses
```

---

# Best Practices

- Always validate before docking new ligands.
- Save the RMSD report.
- Record docking parameters.
- Use the same protocol for all ligands.
- Keep the validated receptor unchanged.

---

# Common Problems

## RMSD > 2 Å

Possible causes:

- Incorrect receptor preparation
- Wrong binding pocket
- Native ligand removed
- Inappropriate docking parameters

---

## Redocking Stops Unexpectedly

Possible causes:

- Insufficient RAM
- Corrupted protein file
- Interrupted macro execution

---

## RMSD File Not Generated

Check that:

- The docking completed successfully.
- The output directory is writable.
- The macro finished without errors.

---

# Scientific Interpretation

Validation is not merely a software step—it is a quality assurance procedure.

A validated protocol demonstrates that the computational workflow can reproduce experimental observations, increasing confidence when predicting the binding modes of unknown ligands.

Without validation, docking scores and poses should be interpreted with caution.

---

# Summary

In this chapter, you learned how to:

- Perform docking validation.
- Conduct 100 redocking simulations.
- Interpret RMSD values.
- Evaluate protocol reliability.
- Decide whether the docking protocol is suitable for future studies.

Validation is a crucial prerequisite before screening or docking any new ligand.

---

# Next Chapter

➡ **Chapter 4 – Molecular Docking**

In the next chapter, you will learn how to prepare the receptor and ligand, define the binding pocket, execute docking using YASARA macros, and generate docking results for analysis.
