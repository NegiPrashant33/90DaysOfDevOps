# Python Data Types and Data Structures for DevOps

## Data Types
- Data types are the classification or categorization of data items. It represents the kind of value that tells what operations can be performed on a particular data. 
- Since everything is an object in Python programming, data types are actually classes and variables are instance (object) of these classes.
- Python has the following data types built-in by default: Numeric(Integer, complex, float), Sequential(string,lists, tuples), Boolean, Set, Dictionaries, etc

To check what is the data type of the variable used, we can simply write:
```python
your_variable=100
type(your_variable)
```


## Data Structures

 Data Structures are a way of organizing data so that it can be accessed more efficiently depending upon the situation. Data Structures are fundamentals of any programming language around which a program is built. Python helps to learn the fundamental of these data structures in a simpler way as compared to other programming languages.

- Lists
Python Lists are just like the arrays, declared in other languages which is an ordered collection of data. It is very flexible as the items in a list do not need to be of the same type

- Tuple
Python Tuple is a collection of Python objects much like a list but Tuples are immutable in nature i.e. the elements in the tuple cannot be added or removed once created. Just like a List, a Tuple can also contain elements of various types.

- Dictionary
Python dictionary is like hash tables in any other language with the time complexity of O(1). It is an unordered collection of data values, used to store data values like a map, which, unlike other Data Types that hold only a single value as an element, Dictionary holds the key:value pair. Key-value is provided in the dictionary to make it more optimized

## Tasks

1. Difference between list, tuple and set

    List is an ordered collection of data. List in python are declared with square brackets `[]`. List is mutable in nature.


    ![Python List](/day14/images/Screenshot%20from%202023-08-16%2009-22-18.png)



    ![List output](/day14/images/Screenshot%20from%202023-08-16%2009-22-46.png)



    Tuple is an ordered collection of data. Tuples are declared with round brackets `()`. Tuples are immutable in nature.



    ![Python Tuple](/day14/images/Screenshot%20from%202023-08-16%2009-25-11.png)

    

    ![Tuple output](/day14/images/Screenshot%20from%202023-08-16%2009-26-17.png)


    Set is an unordered collection of data. Sets are represented using curly brackets `{}`. Sets are mutable in nature. Sets consist of uniqure elements in comparison  to List and tuple which can have duplicate elements.


    ![Python Set](/day14/images/Screenshot%20from%202023-08-16%2009-27-04.png)

    

    ![Set output](/day14/images/Screenshot%20from%202023-08-16%2009-27-20.png)


2.
    ```python

        fav_tools = {
        1:"Linux",
        2:"Git",
        3:"Docker",
        4:"Kubernetes",
        5:"Terraform",
        6:"Ansible",
        7:"Chef"
        }

        # Create a list of your fav tools
        lst_of_fav_tools = ["Linux", "Git", "Docker"]

        for key in fav_tools:
            # If tool part of your list of fav tools then print
            if fav_tools[key] in lst_of_fav_tools:
                print(fav_tools[key])

    ```

3. 
    ```python
        
        '''
        Function to add to a list and sort the list in alphabetical order
        '''

        def add_and_sort(str):
            cloud_providers.append(str)
            cloud_providers.sort()
            print(cloud_providers)

        cloud_providers = ["AWS","GCP","Azure"]

        # Function call
        add_and_sort("Digital Ocean")
    ```