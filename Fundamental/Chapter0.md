# Review ML Onramp

 Author: Zhaojicheng Zhou

## Menu

1. Import Data
2. Group and Merge Data

### Import Data

Please see the details in the Onramp

### Group and Merge Data

1. Function `groupsummary`

    The groupsummary function performs grouped calculations. For example, the following command calculates the standard deviation (std) of the data in data, grouped by data.Label.

    ```matlab
    stdevData = groupsummary(data,"Label","std")
    ```

2. Table Properties

    Use the table.properties.??? to alter the properties of the table. Eg.

    ```matlab
    %replace the variable names of the playerStats with the variable names of the table allStats
    playerStats.Properties.VariableNames=allStats.Properties.VariableNames;
    ```

3. `join` and `innerjoin`

    The function `join` needs the keys appear in all table. For instance:

    ```matlab
    A
    Employee        DepartmentID
    Rafferty        31
    Jones           33
    Steinberg       33
    Robinson        34
    Smith           34
    Jasper          35

    B
    DepartmentID   DepartmentName
    31             Sales
    32             Foundation
    33             Engineering
    34             HR
    35             Marketing

    C
    Employee        DepartmentID
    Rafferty        31
    Jones           33
    Steinberg       33
    Robinson        34
    Smith           34
    Jasper          36

    join(A,B);  %work
    join(C,B);  %don't work
    t3 = outerjoin(C,B,'Type','left','MergeKeys',true)
        LastName      DepartmentID    DepartmentName
        ___________    ____________    ______________

        'Rafferty'     31              'Sales'       
        'Jones'        33              'Engineering' 
        'Steinberg'    33              'Engineering' 
        'Robinson'     34              'HR'          
        'Smith'        34              'HR'          
        'Jasper'       36              ''
        t4 = outerjoin(C,B,'Type','right','MergeKeys',true)
        LastName      DepartmentID    DepartmentName
        ___________    ____________    ______________

        'Rafferty'     31              'Sales'       
        ''             32              'Foundation' 
        'Jones'        33              'Engineering' 
        'Steinberg'    33              'Engineering' 
        'Robinson'     34              'HR'          
        'Smith'        34              'HR'          
        ''             35              'Marketing'
        t5 = outerjoin(C,B,'MergeKeys',true)
        LastName      DepartmentID    DepartmentName
        ___________    ____________    ______________

        'Rafferty'     31              'Sales'       
        ''             32              'Foundation'  
        'Jones'        33              'Engineering' 
        'Steinberg'    33              'Engineering' 
        'Robinson'     34              'HR'          
        'Smith'        34              'HR'          
        ''             35              'Marketing'  
        'Jasper'       36              ''
        innerjoin(C,B)
        LastName      DepartmentID    DepartmentName
        ___________    ____________    ______________

        'Rafferty'     31              'Sales'       
        'Jones'        33              'Engineering' 
        'Steinberg'    33              'Engineering' 
        'Robinson'     34              'HR'          
        'Smith'        34              'HR'    
    ```

### Plot function

1. Function `boxplot`
    Example:

    ```matlab
    boxplot(table.data,table.categorical)
    ```

2. Function `gscatter`
   plot the points by group
