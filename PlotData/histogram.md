# Histogram

Author: Zhaojiacheng Zhou

This file includes the some useful information about the `histogram`

## Menu

1. Intro
2. Grammar
3. `"Normalization"`
4. `"FaceAlpha"`

---

### Intro

histogram is usually used to decrible the data on a continuous x axis

---

### Grammar

```matlab
histogram(data)
```

- Control Bin Width

  ```maltab
  histogram(data,"BinWidth",width);
  ```

- Control the number of bins

  ```matlab
  histogram(data,num);
  ```

---

### `"Normalization"`

- Intro

  This flag is used to set the way of normalization

- Grammar

  ```matlab
  histogram(seaWS,15,"Normalization","probability");
  ```

---

### `"FaceAlpha"`

- Intro

  This flag is used to set the face transparency of the histogram

- Grammar

  ```matlab
  histogram(landWS,15,"Normalization","probability","FaceAlpha",.3)
  ```
