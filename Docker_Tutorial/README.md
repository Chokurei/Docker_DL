# Some basic and useful orders of docker  

Take ubuntu as an example
-------------------
## Method 1: normal way
### Step 1: get ubuntu system  
    $ sudo docker pull ubuntu
If wanna other system, surf on docker hub
### Step 2: 
## Method 2: Dockerfile  
### Step 1: make Dockerfile:
    $ mkdir filename
    $ cd filename
    $ touch Dockerfile
### Step 2: write contents in Dockerfile:
    FROM ubuntu
    MAINTAINER guozhiling <guozhiling@gmail.com>
    
    # Install some dependencies
    RUN apt-get update && apt-get install -y \
                           zip \
                           unzip 
### Step 3: build a image based the Dockerfile:
    $ sudo docker build -t test:1 .
#docker build is aimed to build a image based on Dockerfile, -t: image's name and its Tag, '.' the file which contains Dockerfile
