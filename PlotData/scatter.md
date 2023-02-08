# Scatter

Author: Zhaojiacheng Zhou

This file introduces some common options of the function `scatter`

---

## Menu

1. Grammar
2. "MarkerFaceAlpha"

---

### Grammar

The common syntax of the function `scatter` is:

```matlab
scatter(x,y,sz,"col",option)
```

size refer to the size of the marker, while the col stand for the color of the marker.

The sz input can be a vector of positive integers that specifies a different size for each marker.

- Sample Code

    ```matlab
    % The cat variable contains the category of the hurricane for each reading. 
    % When the hurricane was classified as a tropical storm or depression, it was coded as a 0.
    szCat = (cat+1)*10;
    scatter(ws,pr,szCat)
    ```

Similarly, the col input can be a vector to use color to relay information.

- Sample Code

    ```matlab
    % The variable elapsedTime contains the time (in days) since the first reading.
    scatter(ws,pr,szCat,elapsedTime,"filled")
    ```

It's highly recommended to add a colorbar to the plot using the function `colorbar`

---

### "MarkerFace Alpha"

When markers are overlapping, you may be able to see them better by setting the transparency with the `"MarkerFaceAlpha"` property.

The value a can be from 0 (fully transparent) to 1 (opaque).
