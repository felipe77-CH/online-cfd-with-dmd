# 🌊 Online CFD with DMD

Master’s Thesis – Reduced Order Modeling for Computational Fluid Dynamics

---

## 📌 Overview

This repository contains the implementation of a **Master’s thesis** focused on an **online reduced-order modeling (ROM) framework** for computational fluid dynamics (CFD). The main idea is to couple a **Dynamic Mode Decomposition (DMD)** model directly with a physics-based full-order solver (FOM), allowing the ROM to progressively replace high-fidelity simulations during runtime.

The DMD model is implemented using **PyDMD**, and the CFD solver is based on **FEniCSx**.

---

## 🧠 Abstract

In this study, a reduced-order model (ROM) was directly coupled with a physics-based solver to predict system evolution and progressively replace full-order model (FOM) solutions. Dynamic Mode Decomposition (DMD), implemented using the PyDMD library, was employed for ROM forecasting.

Two classical CFD problems were considered:
- 2D flow around a circular cylinder (Re = 100)
- Lid-driven cavity flow (Re = 400)

The FOM solver is implemented using **FEniCSx**.

The quality of the online DMD approximation was evaluated using:
- Residual norms from DMD-only predictions  
- Frobenius norm for velocity and pressure matrices  

Experiments analyzed the influence of the number of dynamic modes required to achieve the desired accuracy.

Results show that the proposed approach reduces computational cost by up to **20% (cylinder)** and approximately **30% (cavity flow)**, with minimal loss of accuracy.

---

## ⚙️ Methodology

### 🔹 Full Order Model (FOM)
- CFD solver implemented in **FEniCSx**
- Solves Navier–Stokes equations
- Provides high-fidelity velocity and pressure fields

### 🔹 Reduced Order Model (ROM)
- Based on **Dynamic Mode Decomposition (DMD)**
- Implemented using **PyDMD**
- Learns spatio-temporal evolution of the flow

### 🔹 Online Coupling Strategy
- ROM is updated during simulation
- Gradually replaces FOM solutions
- Monitored via error thresholds (residual-based switching)

---

## 📊 Benchmark Problems

### 🌀 Flow around a Cylinder (Re = 100)
- Laminar vortex shedding
- Benchmark for unsteady CFD validation

### 🧊 Lid-Driven Cavity (Re = 400)
- Classical benchmark for recirculating flow
- Strong shear-driven dynamics

---

## 📈 Performance Metrics

- Residual norm (DMD prediction stability)
- Frobenius norm (velocity & pressure accuracy)
- Computational time reduction:
  - Cylinder: ~20%
  - Cavity: ~30%

---

## 🖼️ Results

> Add your figures inside the `images/` folder and update the paths below

### Flow visualization

![Cylinder Flow](images/cylinder_flow.png)

![Cavity Flow](images/cavity_flow.png)

### Error analysis

![Error evolution](images/error_plot.png)

---

## 🧪 Requirements

- Python 3.10+
- PyDMD
- FEniCSx
- NumPy
- SciPy
- Matplotlib

---

## 🚀 How to run

```bash
git clone https://github.com/your-username/online-cfd-with-dmd.git
cd online-cfd-with-dmd

python main.py
