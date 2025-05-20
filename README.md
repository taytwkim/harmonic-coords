# Harmonic Coordinates

A simple 2D demonstration of [Harmonic Coordinates for Character Articulation](https://graphics.pixar.com/library/HarmonicCoordinatesB/paper.pdf).

Repo set up instructions are provided below.

## Harmonic Coordinates

In cage-based deformation, a *cage* is defined around a target shape. The deformation of the shape is driven by manipulating the control points (vertices) of the cage. As the cage is deformed, we want the enclosed shape to follow smoothly.

To achieve this, we assign a set of weights to each interior point `p` relative to the cage control points `(c₁, ..., cₙ)`, such that: `p​ = ∑​ wi​(p) * c​i` and `∑ ci = 1`. These weights determine how much influence each control point has on the interior point. If `p` is closer to `c₁` than to `c₂`, then ideally `w₁ > w₂`.

After computing the weights once, we can deform the cage and compute the new position `p'` as: `p' = ∑​ wi​(p) * c'​i`.


In this project, we use **harmonic coordinates** — a type of weight function computed by minimizing the **Dirichlet energy** subject to boundary conditions. This leads to solving the Laplace equation, ensuring that the weights vary smoothly and produce natural-looking deformations.

Harmonic weights are especially useful for complex or non-convex cages, offering smooth and stable results.

## Set Up Instructions

* Set up a venv
```bash
mkdir gp25
python3.10 -m venv gp25 # use python 3.10
source gp25/bin/activate
```

* Install packages
```bash
pip install libigl==2.5.0
pip install git+https://github.com/skoch9/meshplot/
pip install pythreejs
pip install notebook
pip install matplotlib
```

* Launch jupyter notebook
```bash
gp25/bin/jupyter notebook
```