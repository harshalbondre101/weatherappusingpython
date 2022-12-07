# weatherappusingpython

A weather app using python, json, pandas and oikolab API


As we build our weather tracker, our first task will be to accurately get the temperatures and weather condition of given locations.

In our first milestone, using OIKO as a the weather tracker, we want to find out the temperature of a given city at a given time.

# Input Format
The first line contains the name of the first city
The second line contains the date in the format YYYY-MM-DD.
You need to print the temperature of the given city at the particular date.

Check the examples for the required format

Example Input
Delhi
2022-09-01

# Output
Temperature for Delhi on 2022-09-01 = 31.97C


# JSON in Python
JSON stands for JavaScript Object Notation. It is widely used in internet communication. The internet is full of systems that speak to each other. To do this, they need to all speak in one common format. One of the most popular formats is JSON.

We will soon start writing code that will need to communicate with other systems. In that case, we will be using the JSON format.

Luckily, Python has a great library to help us deal with JSON.

#JSON Format
First, let's see how the JSON format looks like:

{
  "firstName": "Jim",
  "lastName": "Halpert",
  "departments": [ "sales", "finance", "marketing"],
  "age": 25,
  "friends": [
    {
      "firstName": "Pam",
      "age": 20
    },
    {
      "firstName": "Dwight",
      "age": 30
    }
  ]
}
This looks very similar to a Python Dictionary. There are some differences though: JSON doesn't have tuples. Here is how Python data types translate to JSON data types:

Python	JSON
dict	object
list, tuple	array
str	string
int, long, float	number
True	true
False	false
None	null
JSON library in Python - Serialization & Deserialization
Serialization is the process of encoding data into the JSON format.

Deserialization is the process of taking the JSON format and decoding it back to a Python dictionary.

Serialization
We can use the dumps() method to create a json string, or the dump() method to write to a file.

Let's look at an example:

import json
 
data = {
  "firstName": "Jim",
  "lastName": "Halpert",
  "departments": [ "sales", "finance", "marketing"],
  "age": 25,
  "friends": [
    {
      "firstName": "Pam",
      "age": 20
    },
    {
      "firstName": "Dwight",
      "age": 30
    }
  ]
}
 
json_string = json.dumps(data) # will dump data into json_string
print(json_string)
Output

{"firstName": "Jim", "lastName": "Halpert", "departments": ["sales", "finance", "marketing"], "age": 25, "friends": [{"firstName": "Pam", "age": 20}, {"firstName": "Dwight", "age": 30}]}
Alternatively, if we want the output string to be better formatted, we can use the indent parameter:

import json
 
data = {
  "firstName": "Jim",
  "lastName": "Halpert",
  "departments": [ "sales", "finance", "marketing"],
  "age": 25,
  "friends": [
    {
      "firstName": "Pam",
      "age": 20
    },
    {
      "firstName": "Dwight",
      "age": 30
    }
  ]
}
 
json_string = json.dumps(data, indent=4) # notice the indent parameter
print(json_string)
Output

{
    "firstName": "Jim",   
    "lastName": "Halpert",
    "departments": [      
        "sales",
        "finance",        
        "marketing"       
    ],
    "age": 25,
    "friends": [
        {
            "firstName": "Pam",
            "age": 20
        },
        {
            "firstName": "Dwight",
            "age": 30
        }
    ]
}
# Writing JSON to a file
We can use the json.dump() method to write to a file

import json
 
data = {
  "firstName": "Jim",
  "lastName": "Halpert",
  "departments": [ "sales", "finance", "marketing"],
  "age": 25,
  "friends": [
    {
      "firstName": "Pam",
      "age": 20
    },
    {
      "firstName": "Dwight",
      "age": 30
    }
  ]
}
 
with open("data_file.json", "w") as write_file:
    json.dump(data, write_file)
The above code creates a file data_file.json with the following data:

{"firstName": "Jim", "lastName": "Halpert", "departments": ["sales", "finance", "marketing"], "age": 25, "friends": [{"firstName": "Pam", "age": 20}, {"firstName": "Dwight", "age": 30}]}
Deserializing JSON
Similarly, we can convert the JSON objects to Python dictionaries as follows:

import json
 
json_string = '''
{
    "firstName": "Jim",   
    "lastName": "Halpert",
    "departments": [      
        "sales",
        "finance",        
        "marketing"       
    ],
    "age": 25,
    "friends": [
        {
            "firstName": "Pam",
            "age": 20
        },
        {
            "firstName": "Dwight",
            "age": 30
        }
    ]
}
'''
 
data = json.loads(json_string) # use the loads method to read from a string
print(data)
 
with open("data_file.json") as read_file:
    data = json.load(read_file) # use the load() method to read from a file
 
print(data)
Output

{'firstName': 'Jim', 'lastName': 'Halpert', 'departments': ['sales', 'finance', 'marketing'], 'age': 25, 'friends': [{'firstName': 'Pam', 'age': 20}, {'firstName': 'Dwight', 'age': 30}]}
{'firstName': 'Jim', 'lastName': 'Halpert', 'departments': ['sales', 'finance', 'marketing'], 'age': 25, 'friends': [{'firstName': 'Pam', 'age': 20}, {'firstName': 'Dwight', 'age': 30}]}


# Requests library in Python
As mentioned earlier, Python is widely used in web development, particularly in the backend web development.

An important concept in software programming, and particularly in web development, is that of an API - an Application Programming Interface

Simply put, an API for a particular system defines how different entities will interact with the system. It gives rules and format on how one can interact with the system.

For example, when you log in to your email or social media account, the frontend and web browser send information like your name, email id, phone number to the backend of the web application. But they send this in a particular format.

This format, and what methods are to be used in this format, are the APIs.

The concept becomes much clearer when you start developing projects and applications of your own.

For web related APIs, Python has a very useful library for us: the requests library. Before we dive deeper into that, let's understand some verbs of APIs.

# HTTP verbs
Most APIs over the internet happen over HTTP -  a very well-defined protocol.

HTTP has many verbs, but the primary or most-commonly-used HTTP verbs (or methods, as they are properly called) are POST, GET, PUT, PATCH, and DELETE.

The POST verb is most-often utilized to create new resources. Example: create a new user account
The GET method is used to read (or retrieve) a representation of a resource
Example: get information about a user account
PUT is most-often utilized for update capabilities
Example: update all details of a user account
PATCH is used for modify capabilities.
Example: update only 1 or 2 details, like name or age, of a user account
DELETE is pretty easy to understand. It is used to delete a resource
Example: delete a user account
If you wish to deep-dive into the world of HTTP verbs, be sure to pick up Web Development once you complete the basics of Python.

The requests library
The requests library allows us to very easily explore any APIs. There are a lot of use-cases for requests library, but for the scope of this course, let us explore the GET verb.

As mentioned, GET is used to read a resource. To use it, we need to have a resource that we would like to read.

Generally speaking, most APIs are authenticated or have a key: for example if we need to get someone's name and phone number from the server of a social media account, we would need to indeed verify that the user has given us access. This is generally in the form of an API KEY.

Luckily for us, the good folks at NASA have a an amazing set of APIs that we can use without needing an authentic key.

Let's explore this API from NASA: APOD: Astronomy Picture of the Day

The details of the API behind this service can be found here: https://api.nasa.gov/

This service allows us to get the picture of the day, by giving as input the date on which we want it.
