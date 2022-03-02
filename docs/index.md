Brooke Biscoe  
March 1, 2022  
Foundations of Programming: Python  
Assignment 07

# Error Handling and Pickling

## Introduction

This week I learnt about how to use built in python commands in customer functions and different type of file format. I also learnt some more advanced concepts on error handling and how to generate custom error messages to make things more readable. Finally, I reviewed the markdown language and GitHub and how to generate professional looking written documents.

## Built-in Python Commands and Binary Files

One the key things that I learnt about this week was the advantages of putting built-in Python commands into custom functions. The key advantage to doing this is that you can build more customization and error handling in your own function versus compared to simply using the built in commands. 

I also learned about a different kind of file which is a binary file. A binary file is a set of serialized data that obscure’s the files content and potentially reduces size. Python does this using a technique known as pickling. Unlike a plain text file which requires that user simply store data to a file, when pickling a binary file, you can store any python object in there including lists, dictionaries or class objects. A full list of objects that can be pickled can be found on the following website https://www.datacamp.com/community/tutorials/pickle-python-tutorial. I learnt that pickling can be useful for data science to save models that have been trained rather than having to clean them up again. I also found some more information about pickling on the following website https://pythonprogramming.net/python-pickle-module-save-objects-serialization/


## Error Handling

One of the major topics that I learnt about in this lecture was error handling . Specifically, I learnt that one of the key advantages to structured error handling is that you can handle common errors that a user a runs into and write custom messages that are more user friendly than the built-in python messages. Also, using a Try-Except block can prevent a code from crashing if there is an error. 

The except class is a class in Python that provides information about errors that may appear in someone’s code. The exception class can be called in order to handle errors that may come up as a result of user error.  You can call methods off of the exception class in order to make an error message more readable.

One can derive a new class from the exception class by creating a new class and passing ‘Exception’ as the only argument for the class. Then you can create a variety of methods to call similar to the built-in error handling methods. Below is snippet of some of my code from the assignment where I built in some custom error handling:
```
class InvalidOptionError(Exception):
    def __str__(self):
        global options
        return 'This is an invalid option. The available options are {}.'.format(options)
class NotUniqueEmployeeIDError(Exception):
    def __str__(self):
        return 'This employee ID is already in use. You must create a unique ID'
class MustNotBeNumericError(Exception):
    def __str__(self):
        return 'This variable MUST NOT contain numbers. Please enter it again.'
class MustBeNumericError(Exception):
    def __str__(self):
        return 'This variable MUST contain POSITIVE numbers. Please enter it again.'
class NoSearchResultError(Exception):
    def __str__(self):
        return 'There was no with data with this value in this column.\n' \
               'Try changing your search parameters'
class AvailableDepartmentsError(Exception):
    def __str__(self):
        global departmentNames
        return 'That is not a valid department. The available departments are {}.'.format(departmentNames)
class ValidNameError(Exception):
    def __str__(self):
        return 'Employee name must be entered as <First Name> <Last Name>, ' \
               'with only a single space between them.'
class AvailableColumnsError(Exception):
    def __str__(self):
        global keys
        return 'That is not a valid search field. The available fields are {}.'.format(keys)
```


It would be work creating a custom error message if there are specific errors that you think users of your program might make. I made a few custom error messages in my code. For example, the code below is something I created in order to handle an error that would occur if a user did not input a name correctly.

```
class ValidNameError(Exception):
    def __str__(self):
        return 'Employee name must be entered as <First Name> <Last Name>, ' \
               'with only a single space between them.'
```
 
## Markdown Language

The markdown language is the language used by GitHub in order to format documents that are hosted on their website. The Markdown code is converted to HTML using a conversion process application called Jekyll. Since Markdown can be converted to HTML they can be used for GitHub webpages.

## Assignment

In the assignment this week I had to demonstrate my ability to work with binary files and structured error handling. Admittedly, I went a bit overboard and ended up developing a whole program that stores and employee database in a binary file as well as handles multiple errors to ensure that data is stored consistently. Below is an example of some code I used whereby a user can search for data and remove it from the database (or more accurately not add it to a new database). The code includes a structured error handling which will return a message if the data that is searched for is not found.

```
def DeleteData(lst,key,search):
    new_lst = []
    try:
        cntr = 0
        for row in lst:
            if not row[key] == search:
                new_lst.append(row)
            else:
                cntr += 1
        if cntr == 0:
            raise NoSearchResultError
        print('Data Deleted')
    except NoSearchResultError as e:
        print(e)
    return new_lst

class NoSearchResultError(Exception):
    def __str__(self):
        return 'There was no with data with this value in this column.\n' \
               'Try changing your search parameters'
```

My code was able to be used in both PyCharm as well as the OS Command Shell as shown below.

![Code in PyCharm](https://github.com/Brocoe/IntroToProg-Python-Mod07/blob/main/docs/Screen%20Shot%202022-03-01%20at%209.36.19%20PM.png "Code in PyCharm") 
 
 

## Conclusion

This week I learnt about binary files and how they are different from plain texts files. I learnt how to create custom error messages and how structured error handling can really improve my code. Finally, I learned about the markdown language and how to use it create a a very nice GitHub Web Page.

