## Rows and Columns

Slice with labels for row and single label for column. As mentioned above, note that both the start and stop of the slice are included.

```python
df.loc['cobra':'viper', 'max_speed']
```

Boolean list with the same length as the row axis

```python
df.loc[[False, False, True]]
```

Conditional that returns a boolean Series

```python
df.loc[df['shield'] > 6] 
df.loc[df['shield'] > 6, ['max_speed']] 
df.loc[**lambda** df: df['shield'] == 8]
```

For Series, the row labels are prefixed. For DataFrame, the column labels are prefixed.

```python
df.add_prefix('col_')
df.add_suffix('_col')
```

Possible values or ranges

List the theoretical limits on the values and validate against the data.

## Types and Formats

### Data Types

Create a series:

```python
ser = pd.Series([1, 2], dtype='int32')
ser.astype('int64')
```

Convert to categorical type:

```python
ser.astype('category')
```

Convert to ordered categorical type with custom ordering:

```python
cat_dtype = pd.api.types.CategoricalDtype(categories=[2, 1], ordered=**True**)
ser.astype(cat_dtype)
```

### Data Formats

```python
pd.to_datetime(data_311['created_date'], format='%m/%d/%Y %I:%M:%S %p')

pd.to_datetime([1, 2, 3], unit='D',origin=pd.Timestamp('1960-01-01'))
#DatetimeIndex(['1960-01-02', '1960-01-03', '1960-01-04'], dtype='datetime64[ns]', freq=None)

from datetime import date
water_quality["Week"] = water_quality['created_date_time'].apply(lambda x: x.strftime("%w"))
water_quality["Day"] = water_quality['created_date_time'].apply(lambda x: x.strftime("%x"))
water_quality["Year"] = water_quality['created_date_time'].apply(lambda x: x.year)
water_quality["Month"] = water_quality['created_date_time'].apply(lambda x: x.strftime("%b"))

water_quality["year_month"] = water_quality['created_date_time'].apply(
    lambda x: date(year=x.year, month=x.month, day=1)
)

#change month name to string num
d={'July':'07', 'August':'08', 'September':'09', 'October':'10', 'November':'11', 'December':'12',\\
   'January':'01', 'February':'02', 'March':'03', 'April':'04', 'May':'05', 'June':'06'}
resort_hotel.loc[:,'month_num']=resort_hotel['arrival_date_month'].map(d)

#change year to str
resort_hotel.loc[:,'arrival_date_year']=resort_hotel['arrival_date_year'].apply(
    lambda x :str(x))
#change 1 to 01 day
resort_hotel.loc[:,'arrival_date_day_of_month']=resort_hotel['arrival_date_day_of_month'].apply(
    lambda x:(len(str(x)) ==1 and '0'+str(x)) or str(x))
```

## Missing Values

### Drop NAs

```python
df.dropna(self, axis=0, how='any', thresh=None, subset=None, inplace=False)
# how=‘any’ : If any NA values are present, drop that row or column.
# how=‘all’ : If all values are NA, drop that row or column.
df.dropna(how='all') 
# Keep only the rows with at least 2 non-NA values.
df.dropna(thresh=2) 
# Define in which columns to look for missing values.
df.dropna(subset=['name', 'born'])

```

### Fill NAs

```python
df.fillna(self, value=None, method=None, axis=None, inplace=False, limit=None, downcast=None)
```

### Percentage of missing values and visualizations

## Duplications

```python
df.drop_duplicates(['k'])
# keep{‘first’, ‘last’, False}, default ‘first’:
# Determines which duplicates (if any) to keep.
# - first: Drop duplicates except for the first occurrence. 
# - last: Drop duplicates except for the last occurrence. 
# - False: Drop all duplicates.
```

## Numerical Summarization

Use summary statistics to find out the moments.

-   [ ] Locations
    
    Mean, median, quartiles, mode...
    
-   [ ] Spreads
    
    range, variance, standard deviation, IQR
    
-   [ ] Skewness
    
    asymmetries
    
-   [ ] Kurtosis
    

## Distributions

Visualize the distributions of the values

### Value count bar plot

```python
df.groupby("descriptor").size().plot(kind="barh", title="Requests by Descriptor")
```

### Stack bar plot

```python
order_ratio=resort_hotel.pivot_table(
    index='Year-Month', columns='reservation_status', 
    values='is_canceled', aggfunc=len
)

p1 = plt.bar(order_ratio.index,'Check-Out', width=10,data=order_ratio)
p2 = plt.bar(order_ratio.index,'Canceled',bottom='Check-Out',width=10,data=order_ratio)
p3=plt.bar(order_ratio.index,'No-Show',bottom='Check-Out',width=10,data=order_ratio)
#plt.ylabel('Scores')
plt.title('Reservation Status of Booking Orders Per Month ')
#plt.xticks(ind, ('G1', 'G2', 'G3', 'G4', 'G5'))
#plt.yticks(np.arange(0, 81, 10))
plt.legend((p1[0], p2[0],p3[0]), ('Check-Out', 'Canceled','No-Show'))

plt.show()
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2dfbdcaa-5d48-488b-947b-35035413d0ea/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2dfbdcaa-5d48-488b-947b-35035413d0ea/Untitled.png)

### Histogram

```python
plt.hist(water_quality['solving_time_num'],bins=100)
```

### KDE

```python
import seaborn as sns

sns.distplot(quick_solve['solving_time_num'], hist=True, kde=True, 
             bins=int(180/5), 
             hist_kws={'edgecolor':'red'},
             kde_kws={'linewidth': 4})
```

### Box plot

```python
df.boxplot(column='solving_time_num',by='borough')
```

### Point plot

```python
import seaborn as sns
fig1=plt.figure()
ax1 = fig1.add_subplot(211)
ax1=sns.pointplot(y="meal", x="is_canceled",data=resort_hotel,join=False,capsize=.05)
ax1.set(xlim=(0,1))
ax2 = fig1.add_subplot(212)
ax2=sns.pointplot(y="customer_type", x="is_canceled",data=resort_hotel,join=False,capsize=.05)
ax2.set(xlim=(0,1))

fig2=plt.figure()
ax4 = fig2.add_subplot(211)
ax4=sns.pointplot(y="reserved_room_type", x="is_canceled",data=resort_hotel,join=False,capsize=.1)
ax4.set(xlim=(0,1))
ax5 = fig2.add_subplot(212)
ax5=sns.pointplot(y="market_segment", x="is_canceled",data=resort_hotel,join=False,capsize=.1)
ax5.set(xlim=(0,1))
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/92410985-9ea9-43f6-8261-104d82c6df2d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/92410985-9ea9-43f6-8261-104d82c6df2d/Untitled.png)

### Pivot table plot

```python
water_quality.pivot_table(
    index='year_month', columns='borough', 
    values='solving_time_num', aggfunc=len
).plot().legend(loc='center right', bbox_to_anchor=(1.2, 0.5))
```

### Geography

```python
plt.scatter(water_quality['longitude'],water_quality['latitude'],alpha=1,s=20)
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.show()

# 3 dims
plt.scatter(water_quality['longitude'],water_quality['latitude'],c=water_quality['solving_time_num'])
plt.clim(0,100)
plt.colorbar()
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a870cb5b-ac78-496e-ab5d-1eccc137395c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a870cb5b-ac78-496e-ab5d-1eccc137395c/Untitled.png)

```python
# Categories of geography
fig1=plt.figure()
descriptor=list(water_quality['descriptor'].unique())
c=['#c41832','#ef342a','#a84d18','#f68f26','#faca07','#07594a',
   '#4ba946','#5fc0a7','#0376c2','#6dade2','#4dc7ec','#a8b7d8','#b8a1a9','#f8c9cb','#f2f1f6']
for index in range(14):
    longi = water_quality.loc[water_quality['descriptor'] == descriptor[index]]['longitude']
    lati = water_quality.loc[water_quality['descriptor'] == descriptor[index]]['latitude']
    plt.scatter(longi, lati,c=c[index],cmap='brg',alpha=1,s=20)  

ax = fig1.gca()
plt.xlabel('Longitude')
plt.ylabel('Latitude')
#added this to get the legend to work
handles,labels = ax.get_legend_handles_labels()
ax.legend(handles, labels = descriptor, loc='center right', bbox_to_anchor=(1.5, 0.5))

plt.show()
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be4182d1-b8ea-4432-b8ca-4ce67a4c6311/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/be4182d1-b8ea-4432-b8ca-4ce67a4c6311/Untitled.png)

### Contour plot

## Bin values into discrete intervals

```python
pd.cut([0, 1, 1, 2], bins=4, labels=False)
# Quantile-based discretization function.
pd.qcut(range(5), 3, labels=["good", "medium", "bad"])

resort_hotel['stays_in_weekend_nights'].apply(lambda x :(x>4 and '>4') or str(x))
```

## Dummy variables

```python
pd.get_dummies(water_quality['descriptor'],prefix='descriptor')
pd.get_dummies(pd.cut(values,bins)
```

## Dispersion of the target value

Is the dispersion of the target value small enough for the algorithm to perform a good prediction?

## Correlations and Similarities

### Pairplot

### Correlations

Pearson, Kendall Tau Correlation

```python
fig, ax = plt.subplots()
im = ax.imshow(resort_hotel_le[categoricals].corr())

# We want to show all ticks...
ax.set_xticks(np.arange(len(categoricals)))
ax.set_yticks(np.arange(len(categoricals)))
# ... and label them with the respective list entries
ax.set_xticklabels(categoricals)
ax.set_yticklabels(categoricals)

# Rotate the tick labels and set their alignment.
plt.setp(ax.get_xticklabels(), rotation=45, ha="right",
         rotation_mode="anchor")

ax.set_title("Correlation between Each Feature")
fig.tight_layout()
plt.show()
```

### Distances

Calculate the distance between features or rows to understand the relations between them; Euclidean distance, Mahalanobis distance, Minkowski distance, Jaccard distance

## Combining Data Files

### Merge

```python
pd.merge(left, right, how= 'inner', on=None, left_on=None, right_on=None)
# how: inner, outer, left, right
```

### Concat

```python
pd.concat([s1,s2],axis=1)# if with same index
```

## Reshape

### Stack and unstack

```python
#Single level columns
df_single_level_cols = pd.DataFrame([[0, 1], [2, 3]],
                                    index=['cat', 'dog'],
                                    columns=['weight', 'height'])
#Stacking a dataframe with a single level column axis returns a Series:
df_single_level_cols
#     weight height
#cat       0      1
#dog       2      3
df_single_level_cols.stack()
#cat  weight    0
#     height    1
#dog  weight    2
#     height    3

#Multi level columns: simple case

multicol1 = pd.MultiIndex.from_tuples([('weight', 'kg'),
                                       ('weight', 'pounds')])
df_multi_level_cols1 = pd.DataFrame([[1, 2], [2, 4]],
                                    index=['cat', 'dog'],
                                    columns=multicol1)
#Stacking a dataframe with a multi-level column axis:

df_multi_level_cols1
#     weight
#         kg    pounds
#cat       1        2
#dog       2        4
df_multi_level_cols1.stack()
#            weight
#cat kg           1
#    pounds       2
#dog kg           2
#    pounds       4
```

### Pivot table and melt

```python
table = pd.pivot_table(df, values=['D', 'E'], index=['A', 'C'],
                    aggfunc={'D': np.mean,
                             'E': [min, max, np.mean]})

df = pd.DataFrame({'A': {0: 'a', 1: 'b', 2: 'c'},
                   'B': {0: 1, 1: 3, 2: 5},
                   'C': {0: 2, 1: 4, 2: 6}})
#df
#   A  B  C
#0  a  1  2
#1  b  3  4
#2  c  5  6

df.melt(id_vars=['A'], value_vars=['B'],
        var_name='myVarname', value_name='myValname')
#   A myVarname  myValname
#0  a         B          1
#1  b         B          3
#2  c         B          5
```

### Crosstab

```python
pd.crosstab(data.Nationality,data.Handedness,margin=True)
```

## Group by and Agg

```python
prices['Return']=prices.groupby('Code')['Close'].apply(lambda x:x/x.shift(1)-1)

tips.groupby(['day','smoker'],as_index=False).mean()

frame=pd.DataFrame({'data1':np.random.randn(1000),
'data2':np.random.randn(1000)})
quartiles=pd.cut(frame.data1,4)
def get_stats(group):
	return {'min':group.min(),'max':group.max(),'count':group.count(),'mean':group.mean()}
grouped=frame.data2.groupby(quartiles)
grouped.apply(get_stats).unstack()

# fill NA by group
data.groupby(group_key).apply(lambda g:g.fillna(g.mean()))

# regression
import statsmodels.api as sm
def regress(data,yvar,xvars):
	Y=data[yvar]
	X=data[xvars]
	X['intercept']=1.
	result=sm.OLS(Y,X).fit()
	return result.params
by_year.apply(regress,'AAPL',['SPX'])
```

## Objectives of EDA

### Polish the Questions

Check if the questions to be answered are valid or well stated; If not, modify them or come up with new ones

### Validate Data I/O Methods

Check and validate the methods to load and save the datasets

### Retrieve Domain Knowledge and Anomalies

Determine the ranges, outliers of the dataset; Talk to domain experts and validate with domain experts.

### Does the result make sense?