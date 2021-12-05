## About the Project/Project Title : Mongo CRUD for Animal Community Center
This project was developed to be a showcase for uploading a file, specifically a CSV file, from a local computer to a MongoDB server. After the initial upload the user will have the ability to use CRUD functions in order to alter their data and have everything stored on a reliable Mongo server. They will also be able to set different users and permissions for security purposes. 

## Motivation
This project was developed for SNHU’s CS:340 class where I practiced Client/Server side development. Using large data sets, I was able to showcase my abilities and aptitude in receiving data, uploading it to a live system and creating methods to maintain the data with CRUD functions. By learning and understanding these basic concepts and then making an actual project with them, shows how I can take what was learned in the classroom and apply it in a real life scenario that can be replicated across multiple tech sectors.

## Getting Started
It is imperative that you have a system that can support the current versions of software that I used in order to get the programs up and running. When you are following this tutorial you may be able to use upgraded versions and achieve similar results, but by using a previous or deprecated version from the ones listed, might cause an error. 

### Note: This is also for a Windows setup, some functions might be different on a Mac or Linux system

## Installation

Run
```
python 
```

If you have it it will give you a version number or take you to a place to install it on your computer, then it will be usable in any dir on your PC
my current version for this program is 3.9.9

```
pip install --upgrade 
```

This will update you to the lastest version of pip 
my current version for this program is 21.3.1

```
pip install pymongo
```

This will allow you to connect with the mongo server you create on MongoDB using the python language

```
pip install pandas
```

This will allow you to import a csv file and potentially other files that pandas supports such as JSON since it allows you to use the pandas library

```
m pip install "pymongo[srv]"
```

This will allow you to communicate with your MongoDB server through your application such as an IDE, Terminal or Jupyter Notebook

### Note: If using Jupyter Notebook follow these directions otherwise skip to the MongoDB setup

## Jupyter Setup

Run
```
pip install jupyter
```
This will allow you to use Jupyter commands in the terminal

```
pip install jupyter notebook
```
This will allow you to use jupyter notebooks

```
jupyter notebook
```
This command will open up a local server for you to use Jupyter notebooks

### Troubleshooting
-Sometimes your jupyter commands won’t work if you don’t have the python environment vcariables set in the PATH before you start the jupyter installs. In that case look at this video to properly get the PATH variables set up for python 
- https://www.youtube.com/watch?v=4bUOrMj88Pc 

## MongoDB setup

Register and set up MongoDB Online with this video
-https://www.youtube.com/watch?v=rE_bJl2GAY8

## Insert a CSV file into Mongo DB with pyMongo
Follow this video to upload a CSV file into your mongo server through a python script
-https://www.youtube.com/watch?v=f3q5aM9onnc

The animal CSV file is included to use for this example

## Import animal.py

Run

```python

Import animal.py
```

-Have this line at the beginning of the Jupyter Notebook file or run it in your python terminal before trying to access the methods below or creating your AnimalShelter object

## Code Example
### Create Method
```python
def create(self, data):
        print("Creating")
        if data is not None:
            self.database.animals.insert_one(data)  
            print("Created")        
        else:
            raise Exception("Nothing to save, because data parameter is empty”)
```

### Read Method
```python
    def read(self, key, value):
        if self.database.animals.find_one({key : value}) is not None:
            print(self.database.animals.find_one({key : value}))
        else:
            print("Value doesn't exist")
            raise Exception("This is not a proper Key : Value Pair")
```

### Update Method
```python
    def update(self, animal_id, key, changed_value):
        if self.database.animals.find_one({"animal_id" : animal_id}) is not None:
            self.database.animals.update_one({"animal_id" : animal_id}, {"$set":{key:changed_value}})
            print(self.database.animals.find_one({key : changed_value}))
        else:
            print("Value doesn't exist")
            raise Exception("Not a valid animal_id")
```

### Delete Method
```python
    def remove(self, animal_id):
        if self.database.animals.find_one({"animal_id" : animal_id}) is not None:
            self.database.animals.delete_one({"animal_id" : animal_id});
        else:
            print("Value doesn't exist")
            raise Exception("Not a valid animal_id")
```


