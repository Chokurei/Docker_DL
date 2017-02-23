# Some basic and useful orders of docker  

Take ubuntu as an example
-------------------
## Method 1: normal way
### Step 1: get ubuntu system  
    $ docker pull ubuntu
If wanna other system, surf on docker hub  
After that will find an image named ubuntu by:

    $ docker images
### Step 2: run the ubuntu image as a container
    $ docker run -t -i image:Tag /bin/bash # /bin/bash means start from this path, -t: terminal, -i interactive
### Step 3: manipulate in this container 
    $ apt-get update
    $ apt-get install zip
   #its just like a new computer, zip will be installed in this container
### Step 4: make the new container as an image
    $ docker commit -m "comment" image_id image_name:Tag # the way to make new images, image_id is given by checking docker images
### Step 5: change name
After step 4 will find a new image named image_name with its Tag, in order to push into own docker hub, need to change its name by:

    $ docker tag image_old_name image_new_name
### Step 6: submit
    $ docker login  # login to own docker hub
    $ docker push image_name # name need to be docker_bub_name/image_name
 
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
   #FROM ubuntu means pull ubuntu, MAINTAINER is author's information, Run means run the orders, && means run after, \ can omit overlapped oders such as apt-get install
### Step 3: build a image based the Dockerfile:
    $ sudo docker build -t test:1 .  
   #docker build is aimed to build a image based on Dockerfile, -t: image's name and its Tag, '.' the file which contains Dockerfile  
   After that in docker images list will appear new image named test with Tag 1
### Step 4: submit  
Similar with method 1

## Basic orders
    $ docker images
    $ docker ps -a  #-a means check all containers
    $ docker pull
    $ docker run -t -i image:Tag /bin/bash # /bin/bash means start from this path, -t: terminal, -i interactive
    $ docker exit
    $ docker commit -m "comment" image_id image_name:Tag # the way to make new images, image_id is given by checking docker images
    $ docker login 
    $ docker tag image_old_name image_new_name
    $ docker push image_name # name need to be docker_bub_name/image_name
    $ docker rmi image_name
    $ docker rm contrainer_name
    
## Relationship diagrams
### 1.Layers relationship
![image](https://cloud.githubusercontent.com/assets/16301109/23198271/b92a6df0-f909-11e6-98c8-31c672c408b4.png)
### 2.Whole process
![image2](https://cloud.githubusercontent.com/assets/16301109/23198313/071dd56a-f90a-11e6-8b23-dbfc459f54b0.png)
    
