
# Documentation for `Crontasks Dockers` 

## Title

***Docker for task automation using Python and Bash shell scripts***

 
## Overview

The `humbertovarona/debcrontasks:v1`,  `humbertovarona/ubucrontasks:v1`, and `humbertovarona/alpcrontasks:v1` docker images are designed to execute scheduled tasks using cron. This image includes Python 3, various downloading utilities, and provides the capability to mount local scripts and cron tasks. Logs are accessible within the container, facilitating easy monitoring and debugging of cron jobs.

## Version

1.0

## Release date

2024-06-28

## DOI

[https://doi.org/10.5281/zenodo.13340172](https://doi.org/10.5281/zenodo.13340172)

## Cite as

Humberto L. Varona, Silena Herold-Garcia. (2024). Dockers for task automation using Python and Bash shell scripts. (1.0). Zenodo. https://doi.org/10.5281/zenodo.13340172

## How to make this docker

```bash
docker build -t debcrontasks .
```

Or

```bash
docker build -t ubucrontasks .
```

Or

```bash
docker build -t alpcrontasks .
```

## Installation from [Docker](https://hub.docker.com/u/humbertovarona)

### Debian-based Version

To pull the Debian-based version of the `debcrontasks ` Docker image, run the following command:

```bash
docker pull humbertovarona/debcrontasks:v1
```

### Ubuntu-based Version

To pull the Ubuntu-based version of the `ubucrontasks ` Docker image, run the following command:

```bash
docker pull humbertovarona/ubucrontasks:v1
```

### Alpine-based Version

To pull the Ubuntu-based version of the `alpcrontasks ` Docker image, run the following command:

```bash
docker pull humbertovarona/alpcrontasks:v1
```

## Features

- Based on `debian:bullseye-slim`, `ubuntu:22.04`, and `alpine:20240606`  
- Includes Python 3, cron, wget, curl, axel, and wget2
- Mounts local directories for scripts and cron tasks
- Accessible cron logs at `/var/log/cron.log`

## Project Structure

Ensure your project directory is structured as follows:

```
work_directory /
├── crontasks/
│   └── crontab
├── scripts/
│   ├── test_task.py
│   ├── get_datetime.sh
│   ├── getfiles.sh
│   ├── download_data.sh
│   ├── process_data.py
│   └── print_datetime.py
└── shared/
    └── data/
```

## Usage

To run this image, you need to mount your local `crontasks` and `scripts` directories into the container. This ensures that your scripts and cron jobs are correctly picked up and executed by the container's cron daemon.

### Running the Container

Execute the following command to run the container with the necessary volumes mounted:

```sh
docker run -d --name my-cron-container -v "$(pwd)/shared/data:/usr/src/app/shared/data" -v "$(pwd)/crontasks:/usr/src/app/crontasks" -v "$(pwd)/scripts:/usr/src/app/scripts" humbertovarona/debcrontasks:v1
```

Or

```sh
docker run -d --name my-cron-container -v "$(pwd)/shared/data:/usr/src/app/shared/data" -v "$(pwd)/crontasks:/usr/src/app/crontasks" -v "$(pwd)/scripts:/usr/src/app/scripts" humbertovarona/ubucrontasks:v1
```

Or 

```sh
docker run -d --name my-cron-container -v "$(pwd)/shared/data:/usr/src/app/shared/data" -v "$(pwd)/crontasks:/usr/src/app/crontasks" -v "$(pwd)/scripts:/usr/src/app/scripts" humbertovarona/alpcrontasks:v1
```

### Example `crontab` File

Your `crontab` file should be placed in the `crontasks/` directory and might look like this:

```plaintext
# Run test_task.py every minute
* * * * * root python3 /usr/src/app/scripts/test_task.py >> /var/log/cron.log 2>&1

# Run getfiles.sh every 5 minutes
*/5 * * * * root /usr/src/app/scripts/getfiles.sh >> /var/log/cron.log 2>&1
```

### Making Scripts Executable

Ensure that all scripts in the `scripts/` directory are executable. You can do this by running the following command:

```sh
chmod +x scripts/*
```

## Accessing Logs

To monitor the execution of your cron jobs, you can access the cron log inside the container. Use the following command to enter the container's shell:

```sh
docker exec -it my-cron-container /bin/bash
```

Once inside the container, you can view the cron log by executing:

```sh
tail -f /var/log/cron.log
```

## Customization

To customize the scripts and cron tasks, simply edit the files in your local `scripts` and `crontasks` directories. These changes will be reflected in the container the next time it starts.

## Contribution

If you wish to contribute to this project, please open an issue or submit a pull request on [Zenodo](https://doi.org/10.5281/zenodo.13340172) or [GitHub](https://github.com/humbertovarona/crontasks). Contributions to enhance the functionality or fix issues are always welcome.

## License

This project is licensed under the MIT License. Feel free to use and modify the code as per the terms of the license.

---
