# Digisuraksha-Parhari-Foundation

# T-pot: The All-in-One Multiple Honeypot Platform

**Team Name:** Tri-force 

**Team members name:**

  1.Anirudh Mehandru 
  2.Aditya Dongare
  3.Yash Yadav
## Problem Statement

In today's evolving threat landscape, understanding attacker behavior is crucial for effective cybersecurity. Deploying and managing multiple honeypots, each simulating different services and vulnerabilities, can provide valuable insights into attacker tactics, techniques, and procedures (TTPs). However, setting up and maintaining a diverse range of honeypots can be complex and time-consuming, often requiring expertise in various technologies and manual configuration.

**T-pot aims to simplify the deployment, management, and analysis of multiple honeypots in a unified platform.** By leveraging containerization, automation, and integrated logging and visualization, T-pot empowers security professionals and researchers to easily deploy a comprehensive deception environment and gain actionable intelligence on potential threats.

## Setup Instructions

This guide will walk you through the steps to set up your T-pot all-in-one multiple honeypot platform.

### Prerequisites

* **Docker:** Ensure Docker is installed and running on your system. You can find installation instructions for your operating system on the official Docker website: [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)
* **Docker Compose:** Docker Compose is required to orchestrate the multiple containers. Installation instructions can be found here: [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
* **Ansible (Optional but Recommended):** For automated deployment, ensure Ansible is installed. Refer to the Ansible documentation for installation instructions: [https://docs.ansible.com/latest/installation_guide/index.html](https://docs.ansible.com/latest/installation_guide/index.html)
* **Bash:** A Bash shell environment is necessary for running the deployment scripts.

### Installation Steps

1.  **Clone the T-pot repository (Hypothetical):**
    ```bash
    git clone [https://github.com/your-organization/t-pot.git](https://github.com/your-organization/t-pot.git)
    cd t-pot
    ```

2.  **Configure the Environment (Optional):**
    * Examine the `ansible/inventory.ini` file to configure target hosts if you are using Ansible for remote deployment.
    * Review the `docker-compose.yml` file to understand the services that will be deployed (various honeypots, Elasticsearch, Kibana, Nginx). You might want to adjust port mappings or environment variables for specific honeypots.

3.  **Deploy with Docker Compose (Local Deployment):**
    ```bash
    docker-compose up -d
    ```
    This command will download the necessary Docker images and start the T-pot containers in detached mode.

4.  **Deploy with Ansible (Automated Remote Deployment):**
    * Ensure your Ansible inventory is correctly configured.
    * Run the Ansible playbook:
        ```bash
        ansible-playbook -i ansible/inventory.ini ansible/deploy.yml -u <remote_user> -k
        ```
        Replace `<remote_user>` with your SSH username on the target machine. Ansible will prompt you for the SSH password.

5.  **Access the Kibana Dashboard:**
    * Once the containers are running, open your web browser and navigate to the IP address of your T-pot server (or `localhost` if deploying locally) on the port exposed for Kibana (e.g., `http://<your_server_ip>:5601`).
    * You should see the Kibana login page. The default credentials (if any) will be mentioned in the documentation or environment files.

### Understanding the Deployment

The `docker-compose.yml` file orchestrates the following key components:

* **Honeypot Containers:** Multiple Docker containers running various honeypots (coded in Python and Go, as per the summary). These simulate different services and vulnerabilities to attract attackers. Examples might include:
    * A low-interaction honeypot simulating common network services.
    * A medium-interaction honeypot emulating application-level vulnerabilities.
    * Potentially specialized honeypots targeting specific protocols or attack vectors.
      
* **Elasticsearch:** This container runs Elasticsearch, which serves as the central log storage for all the deployed honeypots.
  
* **Kibana:** This container runs Kibana, a powerful data visualization and exploration tool that allows you to analyze the logs collected by Elasticsearch.
  
* **Nginx:** This container likely acts as a reverse proxy, potentially providing access to the Kibana dashboard or other web-based interfaces.



