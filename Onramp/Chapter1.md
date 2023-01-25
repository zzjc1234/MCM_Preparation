# Chapter1

Theme: Processing the package of data

---

## Menu

1. Organization of Data
2. Data Storation
3. Data Alternation

---

### Organization of Data

Sometimes the data is very large and we need to classify the data and store them in the different directory

### Data Storation

`datastore` can read the data according to the regular expression. For instance, `data=datastore("*_M_*.txt")`

### Data Alternation

- subtract the starting point
- subtract the mean value(use "omitnan" to ignore the nan)

Using the transform function to alter the data set

```matlab
%include the target parkage of the data set
letterds=datastore("*_M_*.txt");

%store the data set to the variable
data1=read(letterds);
data2=read(letterds);

%apply the scale function to the data1 and data2
result=transform(data1,data2,@scale);

function ret=scale(data1,dat2)
%the body of the function is omitted
end
```
