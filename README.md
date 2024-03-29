# Sample Docker projects

1. Node JS
    *This project shows a basic hello world static page*

    2 options to have an image of this project:
    1. Pull image from Dockerhub repository
        ```
            docker pull reinierjavier/node-hello-world:latest 
        ```

    2. Clone this project, then build an image
        ```
            docker build -t <image name> .      
        ```

    Run it using the command

            docker run -d -p 3000:3000 --name <container name> <image name>:<tag>

    Verify that application is running by loading *localhost:3000* in the browser

2. Python
    *This project functions as a BMI calculator*

    2 options to have an image of this project:
    1. Pull image from Dockerhub repository
        ```
            docker pull reinierjavier/python-bmi:latest
        ```

    2. Clone this project, then build an image
        ```
            docker build -t <image name> .
        ```

    Run it using the command

            docker run -it --name <container name> <image name>:<tag>


    It will then show an interactive terminal for the execution of the BMI calculator.

3. Node JS - Volume
    *A simple Node JS application that stores feedback*

    2 options to have an image of this project:
    1. Pull image from Dockerhub repository
        ```
            docker pull reinierjavier/node-volume-feedback:volume 
        ```

    2. Clone this project, then build an image
        ```
            docker build -t <image name> .      
        ```

    Run it using the command

            docker run -d -p 80:80 --name <container name> -v <volume name>:<path> <image name>:<tag>

   *Adding the -v <volume name>:<path> ensures that the data inside this path will not get lost even after shutting down the container*

   BIND MOUNT
   In cases where you are developing a program and there are changes in your program and want to have it reflected in the running container immediately without building a new docker image, then do a bind mount by connecting your local folder to container folder


        docker run -d -p 3000:80 --name feedback-container -v ${pwd}/node-volume-app:/app -v /app/node_modules -v feedback:/app/feedback reinierjavier/node-volume-feedback:volume


    Changes are:
    1. Project folder is mounted to the running instance /app folder
    2. Since local machine is to be followed, exempt the /app/node_modules by adding an anonymous volume /app/node_modules

    Now, any changes in your project local folder will be reflected immediately in the running container. Try to edit anything in the HTML files. This will allow development to be easier and faster.
   
    Verify that application is running by loading *localhost:80* in the browser
