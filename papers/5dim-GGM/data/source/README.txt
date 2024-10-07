--- Script 'parallelotopes.py' ---

Usage: python3 parallelotopes.py inputFile outputFile

inputFile --- see FaceLatt_5_xx.txt
outputFile --- output file.

Example: python3 parallelotopes.py FaceLatt_5_13.txt out_5_13.txt

Output format:
For each parallelotope the following sequence of lines is repeated:

--
id
n_cells
TYPE|vertex|vertex|...|vertex
TYPE|vertex|vertex|...|vertex
...
TYPE|vertex|vertex|...|vertex
--

id --- lattice id, unique for a given input file
n_cells --- number of translationally different Delaunay 3-cells for the lattice
TYPE --- combinatorial type of a 3-dimensional Delaunay cell: SIMPLEX / PYRAMID / CROSSPOLYTOPE / PRISM / CUBE
vertex --- 5 space-separated coordinates of a vertex

Vertices are ordered according to the rules below:
SIMPLEX --- no rule applied;
PYRAMID --- apex first, then base in a cyclic order
CROSSPOLYTOPE: vertices 0 and 3, 1 and 4, 2 and 5 are opposite
PRISM: 012 and 345 are bases; 03, 14 and 25 are "vertical" edges
CUBE: 0123 and 4567 are opposite faces (each in a cyclic order); 04, 15, 26 and 37 are edges between them.


--- Script 'generate_complex.py' ---

Usage: python3 generate_complex.py inputFile outputFile GAP_destination

Generates a GAP program that computes the rank of H^1(Ven(P)).

inputFile --- see output format of 'parallelotopes.py'
outputFile --- output file
GAP_destination --- where the GAP program will write its output.

Example: python3 generate_complex.py out_5_13.txt gap_5_13.txt res.txt
