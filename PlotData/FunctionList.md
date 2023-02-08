# Function List

Author: Zhaojiacheng Zhou

This file includes useful plot functions and brief introductions for them

---

## Menu

1. scatter
2. colorbar
3. grid on
4. bar
5. histogram
6. geoscatter
7. legend
8. xtick
9. ytick
10. yline

---

### Scatter

- Intro

    Create a scatter plot

- Grammar

    See the scatter.md

---

### Colorbar

- Intro

    Create a color bar. Usually used with another plot function such as scatter

- Grammar

    ```matlab
    colorbar
    ```

---

### Grid on

- Intro

    Add grid to the plot

- Grammar

    ```matlab
    grid on
    ```

---

### bar

- Intro

  Create a bar chart

- Grammar

  ```matlab
  bar(data);
  ```

---

### histogram

- Intro

  Create a  histogram chart

- Grammar

  ```matlab
  histogram(data)
  ```

---

### geoscatter

- Intro

  Create a scatter chart on the graph

- Grammar

  ```matlab
  geoscatter(data);
  ```

---

### legend

- Intro

  Add legend to the graph

- Grammar

  ```matlab
  legend('legend')
  ```

---

### xtick

- Intro

  Add tick to the x axis

- Grammar

  ```matlab
  xtick('tick');
  ```

---

### ytick

Similar to the xtick

---

### yline

- Intro

  Creat a line which is vertical to the y axis

- Grammar

  ```matlab
  med = median(p.YData)
  y = yline(med,"--","Median")
  ```
