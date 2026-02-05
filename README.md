# The Quadratic Bin Packing Problem – Benchmark Set

This repository contains the benchmark instances and the detailed computational results discussed in the paper *"The Quadratic Bin Packing Problem: Exact Formulations and Algorithm"* (forthcoming).

It contains :

- A folder `instances` containing the description of all instances;
- An excel file `results.xlsx` that reports the results obtained on each instance for each tested model.

---

## Instance Folder Structure

The folder `instances` contains one subfolder per instance. Each subfolder is named after the instance itself and contains a single `.in` input file:

```
instances
└───instance_name
│   │   instance_name.in
```

The instance name follows the format:

`QBPP_HJ[signal]_[items]_[density]_[μ]_[id]`

where:

| Field | Description | Possible values (meaning) |
|-------|-------------|---------------------------------|
| `signal` | Sign of the quadratic coefficients | `+` (positive), `-` (negative), `*` (unrestricted) |
| `items` | Number of items | `25`, `30`, `35`, `40`, `45` |
| `density` | Percentage of nonzero quadratic coefficients | `025` (25%), `050` (50%), `075` (75%) |
| `μ` | Parameter controlling the bin capacity `W` and the bin cost `α` | `06` (0.6), `10` (1.0), `20` (2.0) |
| `id` | Instance identifier | `1`, `2`, `3`, `4`, `5` |

See Section 4.2 of the article for the full details regarding the instance generation and parameter settings.

## Instance Format

Each instance input file follows the format described below:

- **1st line:** Instance name.
- **2nd line:** Three integers `n`, `W`, and `α`, corresponding respectively to the number of items, the bin capacity, and the bin cost.
- **3rd line:** `n` integers, where the *i*-th integer represents the weight of item *i*.
- **Next `n` lines:** Each line contains `n` integers representing the quadratic cost matrix.   The entry in the *j*-th column of the *i*-th row corresponds to *d<sub>ij</sub>*. The matrix is guaranteed to be symmetric, i.e., *d<sub>ij</sub> = d<sub>ji</sub>*.

## Results Table

The file `results.xlsx` reports the computational results obtained by each tested model on each instance.
The file contains one sheet per tested model.
In each sheet, every row corresponds to a single instance and reports the instance name, its parameters, and the metrics described below:

| Field | Description |
|-------|-------------|
| `OPT` | `1` if the instance was solved to proven optimality; `0` otherwise |
| `TLE` | `1` if the time limit (3600 seconds) was exceeded; `0` otherwise |
| `MLE` | `1` if the memory limit (32 GB) was exceeded; `0` otherwise |
| `root UB` | Upper bound at the root node of the search tree |
| `root LB` | Lower bound at the root node of the search tree |
| `best primal` | Best feasible (primal) solution value found |
| `best dual` | Best dual bound obtained |
| `gap` | Relative optimality gap |
| `runtime` | Total execution time in seconds |
