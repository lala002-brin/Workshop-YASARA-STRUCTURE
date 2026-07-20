# Chapter 4
# Molecular Docking Using YASARA Structure

> **Estimated Reading Time:** 45–60 minutes
>
> **Difficulty:** ⭐⭐⭐ Intermediate

---

# Overview

Once the docking protocol has been successfully validated, the next step is to perform **molecular docking**.

Molecular docking predicts how a ligand binds inside the active site of a target protein and estimates the binding affinity between both molecules.

In this tutorial we will perform docking using:

| Component | Value |
|-----------|-------|
| Protein | EGFR |
| PDB ID | 4HJO |
| Docking Engine | YASARA Structure |
| Ligand | Native Ligand (first) |

After completing this chapter you will be able to dock any ligand using the same protocol.

---

# Learning Objectives

After completing this chapter you should be able to

- Prepare the receptor
- Prepare the ligand
- Define the binding pocket
- Configure the simulation cell
- Fix receptor atoms
- Execute docking using a macro
- Interpret docking output
- Save docking results

---

# What is Molecular Docking?

Molecular docking is a computational technique used to predict how a small molecule (ligand) binds to a biological macromolecule (protein).

The docking algorithm searches many possible ligand orientations inside the binding pocket and evaluates each pose using a scoring function.

The best pose generally has

- Lowest binding energy
- Correct orientation
- Favorable interactions
- Minimal steric clashes

---

# Docking Workflow

```text
Prepared Protein

↓

Energy Minimization

↓

Define Binding Pocket

↓

Create Simulation Cell

↓

Fix Receptor

↓

Prepare Ligand

↓

Run Docking Macro

↓

Generate Docking Results

↓

Analyze Binding Energy
```

---

# Required Files

Before continuing, your project should contain

```text
project/

protein/

4hjo.yob

macros/

dock_run.mcr
```

---

# Step 1
## Load the Prepared Protein

Open

```text
File

↓

Load

↓

YASARA Object
```

Load

```text
4hjo.yob
```

---

# Step 2
## Perform Energy Minimization

Before docking, minimize the energy of the receptor.

Navigate to

```text
Options

↓

Choose Experiment

↓

Energy Minimization
```

YASARA automatically optimizes

- bond lengths
- bond angles
- atomic positions
- steric clashes

Typical output

```text
Energy minimization completed

Final Energy

-9974 kJ/mol
```

A successful minimization indicates that the receptor is in a more stable conformation before docking.

---

# Why Energy Minimization?

Experimental crystal structures may contain

- steric strain
- unfavorable contacts
- crystallographic artifacts

Energy minimization reduces these effects without significantly altering the overall protein structure.

Skipping this step may produce unrealistic docking poses.

---

# Step 3
## Define the Binding Pocket

The docking search must be restricted to the biologically relevant active site.

Select the native ligand region.

Right-click

```text
Select

↓

Newly
```

The selected atoms define the binding region.

---

# Step 4
## Create the Simulation Cell

Navigate to

```text
Simulation

↓

Define Simulation Cell
```

Choose

```text
Set Size Automatically
```

Shape

```text
Cube
```

Then select

```text
Around Selected Atoms
```

The simulation box now encloses the active site.

---

# Why Define a Simulation Cell?

Without defining the docking region, the ligand could search the entire protein surface.

Restricting the search space

- reduces computational cost
- increases docking accuracy
- focuses on the active site

---

# Step 5
## Fix the Receptor

Navigate to

```text
Simulation

↓

Fix

↓

All
```

All receptor atoms become fixed.

Only the ligand will move during docking.

---

# Why Fix the Protein?

Classical docking assumes

- rigid receptor
- flexible ligand

Protein flexibility is later investigated during Molecular Dynamics simulations.

---

# Step 6
## Save the Receptor

Save the prepared receptor as

```text
4hjo_receptor.sce
```

Navigate to

```text
File

↓

Save As

↓

YASARA Scene
```

---

# Step 7
## Prepare the Native Ligand

Reload

```text
4hjo.yob
```

Delete the protein

Only the native ligand should remain.

Save

```text
4hjo_ligand.yob
```

---

# Why Separate Protein and Ligand?

Docking requires

- receptor
- ligand

as independent objects.

This separation allows YASARA to manipulate the ligand while keeping the receptor fixed.

---

# Step 8
## Set Docking Target

Navigate to

```text
Options

↓

Macro & Movie

↓

Set Target
```

Select

```text
4hjo_receptor.sce
```

Choose

```text
Remove from underscore

↓

OK
```

---

# Step 9
## Run Docking Macro

Navigate to

```text
Options

↓

Macro & Movie

↓

Play Macro
```

Select

```text
dock_run.mcr
```

Click

```text
OK
```

Docking begins automatically.

---

# Docking Process

During docking YASARA

- loads receptor
- loads ligand
- generates poses
- evaluates poses
- clusters solutions
- calculates binding energy
- saves results

Console example

```text
Loading receptor...

Loading ligand...

Searching conformations...

Evaluating poses...

Docking Finished.
```

---

# Generated Files

After docking finishes, the folder should contain

```text
4hjo.log

4hjo_001.pdb

4hjo_002.pdb

4hjo_003.pdb
```

Each file represents one predicted binding pose.

---

# Understanding the Output

## Docking Log

Contains

- binding energy
- docking score
- cluster information
- docking parameters

---

## Docking Pose

Each

```text
4hjo_001.pdb
```

contains

- receptor
- ligand
- predicted coordinates

---

## Cluster Information

Docking often generates many similar poses.

YASARA groups similar conformations into clusters.

Large clusters generally indicate

- stable solutions
- reproducible binding modes

---

# Selecting the Best Pose

The best docking pose usually has

- lowest binding energy
- correct orientation
- hydrogen bonding
- active-site interactions
- large cluster size

Binding energy alone should never be the only criterion.

---

# Best Practices

✔ Use the validated protocol.

✔ Keep the receptor unchanged.

✔ Save every docking result.

✔ Record software version.

✔ Document docking parameters.

✔ Repeat docking when necessary.

---

# Common Mistakes

| Problem | Cause |
|----------|-------|
| Docking fails | Wrong macro |
| Ligand disappears | Wrong target |
| Empty output folder | Macro interrupted |
| Wrong binding site | Incorrect selection |
| Unrealistic pose | Poor receptor preparation |

---

# Troubleshooting

## Macro does not start

Check

```text
dock_run.mcr
```

exists.

---

## Docking stops unexpectedly

Possible reasons

- insufficient RAM
- corrupted receptor
- missing ligand

---

## Output files not generated

Verify

- target receptor
- macro path
- write permission

---

# Scientific Interpretation

Docking predicts the most favorable orientation of a ligand inside the protein binding pocket.

However,

Docking **does not** prove biological activity.

Experimental validation remains essential.

Docking should therefore be viewed as

> a hypothesis-generation tool.

---

# Summary

In this chapter you learned

- receptor preparation
- ligand preparation
- binding pocket definition
- simulation cell generation
- receptor fixing
- docking execution
- docking output interpretation

The generated docking poses will be analyzed in the next chapter.

---

# Next Chapter

➡ **Chapter 5 — Docking Analysis Using Discovery Studio Visualizer**

You will learn how to

- interpret docking scores
- analyze hydrogen bonds
- identify hydrophobic interactions
- generate 2D interaction diagrams
- select the best docking pose for Molecular Dynamics simulation
