
 # Software Requirements

Before starting this tutorial, please ensure that the following software is available on your computer.

## 📥 YASARA-BRIN

This tutorial uses **YASARA-BRIN**, a customized version of **YASARA Structure** developed for educational and research purposes.

Download the appropriate version for your operating system.

| Operating System | Download Link |
|------------------|---------------|
| 🪟 **Windows** | https://drive.google.com/file/d/1_eDUvY_VMGq61RyK_QhiGwoGYPmcR4tg/view?usp=sharing |
| 🍎 **macOS** | https://drive.google.com/file/d/1xWMJnFIC3PxMDwOoYyjsN8aBLwQlS9sp/view?usp=sharing |

> **Note**
> Install the version that matches your operating system before proceeding with this tutorial.

---

## 🧬 YASARA Structure

**YASARA Structure** is a comprehensive molecular modeling and simulation software used throughout this tutorial for:

- Protein preparation
- Molecular docking
- Molecular Dynamics (MD) simulations
- Trajectory analysis
- Molecular visualization

For workshop participants, the installation and licensing of **YASARA Structure** are managed by the organizing team. Therefore, **you do not need to install or activate YASARA separately** if you are using the provided YASARA-BRIN package.

For more information about YASARA Structure, visit:

https://www.yasara.org/products.htm

---

## 🔬 Discovery Studio Visualizer (DSV)

**BIOVIA Discovery Studio Visualizer (DSV)** is a free molecular visualization and analysis software used in this tutorial to:

- Visualize protein–ligand complexes
- Analyze molecular interactions
- Generate 2D interaction diagrams
- Prepare publication-quality figures

Download the latest version from:

https://drive.google.com/file/d/1FPHDcdrLsVAu87dwlm73z1pRkLePcMQ2/view

> **Note**
> Although docking and Molecular Dynamics simulations are performed in **YASARA Structure**, Discovery Studio Visualizer is highly recommended for interaction analysis and figure preparation.

---

# Input Files

Before starting this tutorial, download the required protein structure from the **RCSB Protein Data Bank (PDB)**.

### Protein Structure

| Item | Description |
|------|-------------|
| **Protein** | Epidermal Growth Factor Receptor (EGFR) |
| **PDB ID** | **4HJO** |
| **Database** | RCSB Protein Data Bank |
| **Download Page** | https://www.rcsb.org/structure/4HJO |

### Download Instructions

1. Open the **4HJO** page on the RCSB Protein Data Bank.
2. Click **Download Files**.
3. Select **PDB Format (Legacy)**.
4. Save the file as:

```text
4hjo.pdb
```

### Recommended Project Structure

```text
project/
│
├── protein/
│   └── 4hjo.pdb
│
├── ligand/
├── macros/
├── docs/
└── results/
```

> **Important**
>
> This tutorial uses the **Legacy PDB (.pdb)** file format. Do **not** download the **mmCIF (.cif)** version, as all examples and workflows in this guide are based on the classic PDB format.
