---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
**Elliot Brainerd**


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**

```python
print("What are LaTeX equations referenced in the Notebook Documents section in the first link?\nWhat's the difference between Python and IPython?\nWhat is a modal user interface?")
```

```python
## Exercises 1-7
print("For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.")
```

## Exercise 1

```python
import numpy as np

arr1 = np.array([[2, 2, 2, 2], [2, 2, 2, 2], [2, 2, 2, 2], [2, 2, 2, 2], [2, 2, 2, 2], [2, 2, 2, 2]])

print(arr1)
```

## Exercise 2

```python
arr2 = np.ones((6,4))
eye_arr = np.eye(6,4)
arr2 = arr2 + (2 * eye_arr)
print(arr2)
```

## Exercise 3

```python
# YOUR SOLUTION HERE
print("The * multiplies the matrices element-wise while the other does the dot product.\nThe dot product does not work because the column size of arr1 does not equal row size of arr2.") 
```

## Exercise 4

```python
# YOUR SOLUTION HERE
print(np.dot(arr1.transpose(), arr2))
print(np.dot(arr1, arr2.transpose()))

print("The dimensions of the arrays flip during a transposition, therefore the dot product will have different dimensions.")
```

## Exercise 5

```python
# YOUR SOLUTION HERE
def my_func():
    print("hello")
my_func()
```

## Exercise 6

```python
# YOUR SOLUTION HERE
def arr_funcs():
    arr1 = np.random.rand(6,4)
    arr2 = np.random.rand(6,4)
    
    print(np.sum(arr1))
    print(np.sum(arr2))
    
    print(np.mean(arr1))
    print(np.mean(arr2))
    
    print(np.linalg.pinv(arr1))
    print(np.linalg.pinv(arr2))
    
arr_funcs()


```

## Exercise 7

```python
# YOUR SOLUTION HERE
def find_ones(arr):
    count = 0
    for i in arr:
        for j in i:
            if j == 1:
                count = count + 1
    return count, len(np.where(arr==1)[0])

find_ones(np.eye(6,4))
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
# YOUR SOLUTION HERE
import pandas as pd
a = pd.DataFrame(np.ones((6, 4)) * 2)
a
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
# YOUR SOLUTION HERE
b = np.ones((6,4))
b = pd.DataFrame(b)

b.iloc[range(4), range(4)] = 3
b
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
# YOUR SOLUTION HERE
print(arr1 * arr2)
print("This is element-wise multiplication (*)")
print("We can't use the dot product because the dimensions of arr1 and arr2 are not aligned properly")

```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
# YOUR SOLUTION HERE
def count_the_ones(a):
    count = 0
    for i in range(a.shape[0]):
        for j in range(a.shape[1]):
            if a.iloc[i, j] == 1:
                count += 1
    return count, len(np.where(a==1)[0])

count_the_ones(a), count_the_ones(b)
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
## YOUR SOLUTION HERE
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)
titanic_df.loc['female']
```

## Exercise 14
How do you reset the index?

```python
## YOUR SOLUTION HERE
titanic_df.reset_index(inplace=True)
titanic_df
```


