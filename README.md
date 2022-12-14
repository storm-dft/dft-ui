# DFT UI

A graphical interface to interact with storm dft. 


# To run the tool:

Make sure you have already installed docker on your computer and is currently running. 

Supported browsers: Google Chrome

Precondition: Remove container and volume if already exists

```
docker container stop storm_dft
docker container rm storm_dft
docker volume rm storm_dft_vol
```

Step 1: Pull the most recent Docker image

```
docker pull --platform=linux/amd64 dgbtechnologies/storm-dft:v1
```


Step 2: Create a docker volume of working directory. $PWD, %cd% is the current directory path; any path can be specified here.

For Linux/Mac OS Terminal:
```
export WORK_DIR=$PWD
docker volume create --driver local --opt type=none --opt device=$WORK_DIR --opt o=bind storm_dft_vol
```

For Windows Command Prompt:
```
set WORK_DIR=%cd%
docker volume create --driver local --opt type=none --opt device=%WORK_DIR% --opt o=bind storm_dft_vol
```

Step 3: Run Docker Container

```
docker run -it -p 8081:8080 -p 5001:5000 --name storm_dft --restart unless-stopped -v storm_dft_vol:/home dgbtechnologies/storm-dft:v1
```

Step 4: Open Link 

- http://127.0.0.1:8081


Note: To restart your docker container.

```
docker container restart storm_dft
```

