# NetVisn's Dockerized Version

## Overview
The NetVisn server operates as a web application, delivering a comprehensive and interactive view of your CRN (Cognos ReportNet) content to users via a web browser.

To enhance performance and facilitate administrative analysis tasks, NetVisn maintains its own local data store. This store contains information extracted from your CRN content and is periodically updated to ensure synchronization. As a NetVisn administrator, you have the flexibility to configure the synchronization interval according to your needs. The Analysis tab within NetVisn provides a synchronization status message, indicating the time of the last synchronization or if it is currently running.

During the initial startup of the NetVisn server, it lacks any local data and must generate it by retrieving information from CRN. As a consequence, the first synchronization process may take some time, and certain analysis functions may not function correctly until it is completed. We advise refraining from using analysis functions until the initial synchronization has finished. Once you have familiarized yourself with the server's default synchronization interval, you can fine-tune it to strike a balance between the concurrency of NetVisn data and the CPU impact of synchronization.

## Prerequisites

- **Licensing**: NetVisn requires a license file generated for the system you intend to run it on. Contact Envisn to acquire this file: netvisn.l4j.

- **Cognos Namespace account**: NetVisn requires a Cognos Namespace account that is an explicit member of the System Administrators group. It is suggested to create a new account specifically for NetVisn administration, for example, `NetvisnAdmin`. When creating this account, ensure that the proper 'Content Language' is selected in the Preferences dialog in Cognos Connection. This account requires System Administrator permissions to access information from the content store.

- **Computing resources**: We recommend a minimum of 12GB RAM, 8GB CPU, and 50GB disk space.

## Installing the Docker Desktop

Install Docker Desktop on your preferred operating system by following the official documentation for Docker Desktop installation. Docker Desktop provides an easy-to-use interface for managing Docker containers on your local machine. Instructions for installing Docker Desktop on different operating systems can be found at the following links:

- Docker Desktop for Windows: Official documentation for installing Docker Desktop on Windows can be found at [https://docs.docker.com/desktop/windows/install/](https://docs.docker.com/desktop/windows/install/).

- Docker Desktop for macOS: Official documentation for installing Docker Desktop on macOS can be found at [https://docs.docker.com/desktop/mac/install/](https://docs.docker.com/desktop/mac/install/).

- Docker Desktop for Linux: Official documentation for installing Docker Desktop on Linux can be found at [https://docs.docker.com/desktop/linux/install/](https://docs.docker.com/desktop/linux/install/).

## Pull Code from GitHub Repository

Retrieve the necessary Docker Compose artifacts from Envisn's GitHub repository. The repository contains the required configuration files and dependencies to run NetVisn as a Docker container. Use the following instructions to pull the code:

```bash
git clone https://github.com/envisn/dockerized-netvisn.git
```

## Configure NetVisn

Once you have pulled the code, locate the NetVisn license file (you can request one by sending an email to support@envisn.com) and add it to the `<gitrepo_pull_dir>/dockerized-netvisn/netvisn/config` folder. The license file is necessary to activate and enable the full functionality of NetVisn. Additionally, modify the `netvisn.properties` file in the same directory to include your IBM Cognos dispatcher URL and gateway URL. These configurations allow NetVisn to connect to your Cogn

os environment.

## Start NetVisn

From your command line tool, navigate to the root directory of the pulled code where the Docker Compose file is located. Run the following command to launch the NetVisn stack:

```bash
docker-compose up
```

This command will build the necessary Docker images and start the NetVisn containers. It may take a few minutes to download the required images and set up the environment.

## Access NetVisn Application

Once the NetVisn stack is up and running, you can access the NetVisn application by launching `http://localhost:8080/netvisn` in your web browser. This URL points to the NetVisn web interface running inside the Docker container. You will be directed to the login page, where you can use your IBM Cognos Server Admin credentials to log in to the application.

## Synch and Configure

NetVisn provides an intuitive and user-friendly interface that allows you to explore the various features and functions it offers. You can perform tasks such as version control, promotion, documentation, impact analysis, security editing, and auditing within the NetVisn environment. Feel free to utilize the capabilities of NetVisn to enhance your IBM Cognos Analytics implementation.

For any questions or additional support, you can reach out to the Envisn team at support@envisn.com. They will be happy to assist you with any queries or concerns.

