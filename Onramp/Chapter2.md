# Chapter2

Theme: Engineering Features

---

## Menu

1. Statistical Function
2. Find Peaks
3. Computing Derivatives(approxiamtely)
4. Calculating Correlations
5. Automating Feature Extraction

---

### Statistical Function

#### Measures of Central Tendency

|function|description|
|---|---|
|mean|Arithmetic mean|
|median|Median|
|mode|Most frequent value|
|trimmean|Trimmed mean|
|geomean|Geometric mean|
|harmean|Harmonic mean|

#### Measure of Speed

|function|description|
|---|---|
|range|Range of values (largest – smallest)|
|std|Standard deviation|
|var|Variance|
|mad|Mean absolute deviation|
|iqr|Interquartile range ($75^{th}$ percentile minus $25^{th}$ percentile)|

#### Measures of Shape

|Function|Description|
|---|---|
|skewness|Skewness (third central moment)|
|kurtosis|Kurtosis (fourth central moment)|
|moment|Central moment of arbitrary order|

---

### Find Peaks

|Function|Description|
|---|---|
|islocalmin|return the index and prominence of the local minimum|
|islocalmax|return the index and prominence of the local maximum|

"MinProminence" flag can be added to set the thresholdx

---

### Computing Derivatives(approxiamately)

|Function|Description|
|---|---|
|diff|The diff function calculates the difference between successive elements of an array.|
|standardizeMissing|convert a set of values to NaN|

The demonstration of the standardizeMissing fucntion

```matlab
%set all 0, -Inf and Inf to NaN
xclean = standardizeMissing(x,[-Inf 0 Inf]);
```

---

### Calculating Correlations

|Function|Description|
|---|---|
|corr|The corr function calculates the linear correlation between variables.|

Set use the "rows" "complete" flag to ignore the NaN

---

### Automating Feature Extraction

#### Creating a Feature Extraction Function

|Function|Description|
|---|---|
|table|create a table(use 'VariableName' to set the Variable name)|

#### Extracting Features from Multiple Data Files

Demostration code is below:

```matlab
letterds = datastore("*.txt");  %load the data
preprocds = transform(letterds,@scale); %normalize the data

%transform the data 
featds=transform(preprocds,@extract);

%read the data and visualize it
data = readall(featds);
scatter(data.AspectRatio,data.CorrXY);

%store the character stand for the data information into a string
knownchar = extractBetween(letterds.Files,"_","_");

%transform the string into a categorical type
knownchar=categorical(knownchar);

%create a new column in the table variable data and
%visualize the classifcation of the data according to
%the categorical variable
data.Character=knownchar;
gscatter(data.AspectRatio,data.CorrXY,data.Character);

%subfunction is here
function data = scale(data)
% Normalize time [0 1]
data.Time = (data.Time - data.Time(1))/(data.Time(end) - data.Time(1));
% Fix aspect ratio
data.X = 1.5*data.X;
% Center X & Y at (0,0)
data.X = data.X - mean(data.X,"omitnan");
data.Y = data.Y - mean(data.Y,"omitnan");
% Scale to have bounding box area = 1
scl = 1/sqrt(range(data.X)*range(data.Y));
data.X = scl*data.X;
data.Y = scl*data.Y;
end

function feat = extract(letter)
% Aspect ratio
aratio = range(letter.Y)/range(letter.X);
% Local max/mins
idxmin = islocalmin(letter.X,"MinProminence",0.1);
numXmin = nnz(idxmin);
idxmax = islocalmax(letter.Y,"MinProminence",0.1);
numYmax = nnz(idxmax);
% Velocity
dT = diff(letter.Time);
dXdT = diff(letter.X)./dT;
dYdT = diff(letter.Y)./dT;
avgdX = mean(dXdT,"omitnan");
avgdY = mean(dYdT,"omitnan");
% Correlation
corrXY = corr(letter.X,letter.Y,"rows","complete");
% Put it all together into a table
featurenames = ["AspectRatio","NumMinX","NumMinY","AvgU","AvgV","CorrXY"];
feat = table(aratio,numXmin,numYmax,avgdX,avgdY,corrXY,'VariableNames',featurenames);
end

```
