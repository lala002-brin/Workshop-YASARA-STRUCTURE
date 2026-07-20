## 📥 Download YASARA-BRIN

Download the appropriate version of **YASARA-BRIN** for your operating system.

| Operating System | Download Link |
|------------------|---------------|
| 🪟 **Windows** | https://drive.google.com/file/d/1_eDUvY_VMGq61RyK_QhiGwoGYPmcR4tg/view?usp=sharing |
| 🍎 **macOS** | https://drive.google.com/file/d/1xWMJnFIC3PxMDwOoYyjsN8aBLwQlS9sp/view?usp=sharing |

> **Note**
> Download and install the version that matches your operating system before proceeding with this tutorial.

---

# Input Files

Before starting this tutorial, download the required protein structure from the **RCSB Protein Data Bank (PDB)**.

### Protein Structure

- **Protein:** Epidermal Growth Factor Receptor (EGFR)
- **PDB ID:** **4HJO**
- **Database:** RCSB Protein Data Bank
- **Download Page:** https://www.rcsb.org/structure/4HJO

### Download Instructions

1. Open the **4HJO** page on the RCSB Protein Data Bank.
2. Click **Download Files**.
3. Select **PDB Format (Legacy)**.
4. Save the file as:

```text
4hjo.pdb
```

### Project Structure

Place the downloaded file in the following directory:

```text
project/
│
├── protein/
│   └── 4hjo.pdb
│
├── ligand/
├── macros/
└── docs/
```

> **Important**
>
> This tutorial uses the **Legacy PDB (.pdb)** format. Do **not** download the **mmCIF** version, as the workflow described in this guide is based on the classic PDB file format.
