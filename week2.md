# Planning for optimizing a program
1. Analyze: What parts should be parallelized.
+ Times measurement of parts to decide.
+ When optimizing, can measure times of GPU activities quickly.
2. Design: Diagram, Plan.
3. Implement.
+ It has to run correctly (lmao).
+ Avoid randomization (use same seeding).
4. Evaluate.
+ Does the idea work? If not, do you know why?

# General optimization guidelines

# Sequential version

# Colab Notebook / Kaggle Notebook
Kaggle often provides better GPU than Colab.

# Python vs C/C++ speed

# NumPy vs og Python speed
+ NumPy only runs sequentially on GPU.
+ There are cases of preprocessing data which are difficult to express using Numpy operations; using loops is easier bu t...
+ Not everything is optimizable.
+ %timeit
