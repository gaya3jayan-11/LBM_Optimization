# Multi-Objective Optimization of Laser Beam Machining (LBM)

## Project Overview

This project implements and analyzes intelligent optimization techniques (Evolutionary Algorithms and RSM models) to solve critical trade-off problems in Laser Beam Machining (LBM). The goal is to move beyond trial-and-error by providing process engineers with the mathematically optimal settings for balancing conflicting goals like maximizing productivity while minimizing quality defects.

**The core finding is the generation of the Pareto Front, which provides a full "menu" of optimal compromises for the LBM process.**

---

## 1. Project Components and Methodology

### 1.1 Predictive Modeling (The 'Machine Learning' Component)

We use empirical **Response Surface Methodology (RSM) models** derived from experimental data found in the literature. These polynomial equations serve as the project's **surrogate models** (or digital twins) that instantly predict the output quality characteristics based on input parameters.

### 1.2 Optimization Problems Analyzed

The project focuses on solving three key scenarios:

| Problem | Objectives | Decision | Key Insight |
| :--- | :--- | :--- | :--- |
| **P1: Pure Quality Trade-off** | Minimize **Heat Affected Zone (HAZ)** and Minimize **Taper**. | Multi-Objective | Compares a quality defect (HAZ) against a dimensional deviation (Taper). |
| **P2: Single-Objective Productivity** | **MAXIMIZE Material Removal Rate (MRR)**. | Single-Objective | Finds the absolute maximum achievable productivity (The teacher's specific request). |
| **P3: Final Engineering Trade-off** | **MAXIMIZE MRR** and **MINIMIZE HAZ**. | Multi-Objective | The most critical analysis, showing the **Productivity vs. Quality** trade-off curve. |

---

## 2. Key Results and Justification

### 2.1 The Value of Multi-Objective Optimization

Our project validates the supremacy of the multi-objective approach over traditional single-objective methods:

* **Traditional Methods (Weighted Sum/ABC):** Provide only one single point of best performance (e.g., the Green 'X' on the final plot). This forces a choice but doesn't show what is being sacrificed.
* **NSGA-II (Multi-Objective):** Produces the **Pareto Front** (the Purple/Blue curve). This curve shows every single possible *best* compromise.
    * **Justification:** By using the Pareto Front, a manager can choose a point that offers a slightly lower MRR but a drastically reduced HAZ, quantifying the exact cost of better quality.

### 2.2 Algorithms Used

| Algorithm | Type | Role in Project |
| :--- | :--- | :--- |
| **NSGA-II** | Evolutionary Multi-Objective (MOO) | Primary tool used to generate the **Pareto Front**. |
| **Weighted Sum Approach** | Traditional Single-Objective | Used as a benchmark to simulate the output of older techniques (like Genetic Algorithm or ABC). |

---

## 3. Setup and Execution Instructions

The project is built using Python within a Visual Studio Code (VS Code) Jupyter Notebook environment.

### 3.1 Setup

1.  **Clone the Repository:** Open your terminal/command prompt and clone the project:
    ```bash
    git clone https://github.com/gaya3jayan-11/LBM_Optimization.git
    cd LBM_Optimization
    ```

2.  **Create and Activate Virtual Environment:**
    * **macOS / Linux:**
        ```bash
        python3 -m venv venv
        source venv/bin/activate
        ```
    * **Windows (Command Prompt/PowerShell):**
        ```bash
        python -m venv venv
        .\venv\Scripts\activate
        ```

3.  **Install Dependencies:** Install all necessary libraries:
    ```bash
    pip install numpy pandas matplotlib tabula-py pymoo JPype1
    ```

4.  **Create Data Folder:** This folder is required for saving intermediate CSV files:
    ```bash
    mkdir data
    ```

### 3.2 Running the Project

1.  **Open VS Code** in the `LBM_Optimization` directory.
2.  Open the notebook: **`LBM_Optimization_Notebook.ipynb`**.
3.  **Select Kernel:** Ensure the VS Code kernel is set to the activated `venv` environment (check the top-right corner of the notebook).
4.  **Run Cells:** Run all cells sequentially. The notebook contains all steps, including data extraction, model definition, optimization, and final visualization.
