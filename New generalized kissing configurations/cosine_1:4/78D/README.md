## Recovering the Spherical Code

Here we provide the coordinate file for the 78-dimensional spherical code with 142,155 points.

The file `78D_142155_coordinates.npy` stores the coordinates in NumPy format. It can be loaded directly as follows:

```python
import numpy as np

coor = np.load("78D_142155_coordinates.npy")
coor = coor.astype(np.float64)
coor[:, 0] *= np.sqrt(3)
```

Here, `coor` is a NumPy array of shape `(142155, 78)`, where each row represents one point in the spherical code. The last line rescales the first coordinate by `sqrt(3)`, which restores the coordinates to the normalized Euclidean representation used in the construction.

After loading, one can verify the basic shape and norm normalization by running:

```python
print(coor.shape)
print(np.linalg.norm(coor, axis=1).min())
print(np.linalg.norm(coor, axis=1).max())
```

The pairwise inner products can be computed by:

```python
gram = coor @ coor.T
```

For memory efficiency, we recommend computing selected entries or blockwise Gram matrices instead of forming the full `142155 x 142155` Gram matrix at once.
