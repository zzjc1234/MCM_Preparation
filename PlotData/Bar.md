# Bar

Author: Zhaojiacheng Zhou

This file introduces some common options of the function `bar`

---

## Menu

1. Intro
2. Grammar
3. "FaceColor"
4. "BarWidth"
5. "EdgeColor"

---

### Intro

Create a bar chat

---

### Grammar

```matlab
bar(data,option)
```

---

### "FaceColor"

- Intro
  Change the face color of the bar chart.

- Advanced

  ```matlab
  colors = [0 0 1; 1 0 0; 1 0 0; 1 0 0;];
  bar(data,"FaceColor","flat","CData",colors)
  ```

  The `"flat"` flag allows the user to create the bar chart with color map, while the `"CData"` flag specify the data of the color map.

### BarWidth

- Intro

  Set the bar width

- Sample Code

    ```matlab
    bar(us,"FaceColor","k","BarWidth",.5)
    ```

### EdgeColor

- Intro

  Set the the edge color of the bar chart

- Sample Code

    ```matlab
    bar(us,"FaceColor","k","BarWidth",.5,"EdgeColor","w")
    ```
