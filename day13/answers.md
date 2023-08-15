# Basics of Python 

## What is Python?

- Python is a Open source, general purpose, high level, and object-oriented programming language.
- It was created by **Guido van Rossum**
- Python consists of vast libraries and various frameworks like Django,Tensorflow, Flask, Pandas, Keras etc.


## How to Install Python?

You can install Python in your System whether it is window, MacOS, ubuntu, centos etc. Below are the links for the installation:
- [Windows Installation](https://www.python.org/downloads/)
- Ubuntu: apt-get install python3.6  


## Task Todo

1. Install Python and check version
    ```shell
    sudo apt install python3

    python3 --version
    ```
2. 
    Numeric data types is used to hold numeric values

    int - holds signed integers of non-limited length.

    float - holds floating decimal points and it's accurate up to 15 decimal places.

    complex - holds complex numbers.

    ```python
    num1 = 5

    num2 = 2.0

    num3 = 1+2j
    ```

    List is an ordered collection of similar or different types of items separated by commas and enclosed within brackets [ ]. For example,
    ```python
    languages = ["Docker", "Shell Scripting", "Git and Github"]
    ```

    Tuple is an ordered sequence of items same as a list. The only difference is that tuples are immutable. Tuples once created cannot be modified.

    In Python, we use the parentheses () to store items of a tuple. For example,

    ```python
    product = ('Xbox', 499.99)
    ```

    String is a sequence of characters represented by either single or double quotes. For example,

    ```python
    name = 'Python'
    ```

    Set is an unordered collection of unique items. Set is defined by values separated by commas inside braces { }. For example,

    ```python
    student_id = {112, 114, 116, 118, 115}
    ```

    Python dictionary is an ordered collection of items. It stores elements in key/value pairs.

    Here, keys are unique identifiers that are associated with each value.
    for example,

    ```python
    capital_city = {'Nepal': 'Kathmandu', 'Italy': 'Rome', 'England': 'London'}
    ```

    Boolean data type in python either holds True of False value, this data type is usually used as a flag in programming language to navigate to the correct flow of the program.

    ```python
    flag = True
    ```



![Python Data types](https://media.geeksforgeeks.org/wp-content/uploads/20191023173512/Python-data-structure.jpg)