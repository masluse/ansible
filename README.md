# Ansible Playbooks

This repository contains a collection of Ansible playbooks for various automation tasks.

## Key Features & Benefits

This repository provides Ansible playbooks for:

*   **Application Deployment:** Automate the deployment of applications such as Portainer and Minecraft servers.
*   **System Updates:** Easily update and upgrade systems to the latest versions.
*   **Infrastructure Management:** Manage and configure infrastructure components.
*   **Configuration Management:** Maintain consistent configurations across multiple servers.
*   **Automated Upgrades:** Automate major version upgrades.

## Prerequisites & Dependencies

To use these Ansible playbooks, you'll need:

*   **Ansible:** Version 2.9 or higher.  Install using `pip install ansible` or your system's package manager.
*   **Python:** Python 3 is recommended.
*   **Target Servers:** Access to the target servers where the playbooks will be executed, with SSH access enabled.
*   **Inventory File:** A properly configured Ansible inventory file that lists the target servers.
*   **SSH Keys:** SSH keys set up for passwordless access to target servers from the Ansible control machine.
*   **Jinja2:** Templating language used by Ansible. Usually comes preinstalled with Ansible.

## Installation & Setup Instructions

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/masluse/ansible.git
    cd ansible
    ```

2.  **Install Ansible (if not already installed):**

    ```bash
    pip install ansible
    ```

3.  **Configure your Ansible inventory file:**

    Edit the `hosts` file (or create a custom inventory file) to define your target servers:

    ```ini
    [your_group_name]
    server1 ansible_host=192.168.1.10 ansible_user=your_user
    server2 ansible_host=192.168.1.11 ansible_user=your_user
    ```

    Replace `your_group_name`, `server1`, `server2`, IP addresses, and `your_user` with your actual values.

4.  **Verify connectivity:**

    ```bash
    ansible -m ping all
    ```

    This command should return "pong" from all target servers.

## Usage Examples

Here are some examples of how to use the playbooks:

1.  **Deploying Portainer:**

    ```bash
    ansible-playbook portainer.yml -i hosts
    ```

    This will deploy Portainer to the servers defined in your inventory file.

2.  **Updating and Upgrading Systems:**

    ```bash
    ansible-playbook update-and-upgrade.yml -i hosts
    ```

    This will update and upgrade the packages on your target servers.

3.  **Upgrading Ubuntu from 22.04 to 24.04:**

    ```bash
    ansible-playbook upgrade-22.04-to-24.04.yml -i hosts
    ```

    This will perform a full upgrade from Ubuntu 22.04 to 24.04.

## Configuration Options

Most playbooks have configurable variables. You can override the default values by:

*   **Passing variables via the command line:**

    ```bash
    ansible-playbook myplaybook.yml -i hosts -e "variable1=value1 variable2=value2"
    ```

*   **Defining variables in the inventory file:**

    ```ini
    [your_group_name]
    server1 ansible_host=192.168.1.10 ansible_user=your_user variable1=value1
    ```

*   **Defining variables in a separate variables file (vars.yml):**

    Include the variables file in your playbook:

    ```yaml
    - hosts: all
      vars_files:
        - vars.yml
      tasks:
        # your tasks here
    ```

Check the specific playbook for available configuration options and their default values.

## Contributing Guidelines

We welcome contributions! Here's how you can contribute:

1.  **Fork the repository.**
2.  **Create a new branch for your feature or bug fix.**
3.  **Make your changes.**
4.  **Test your changes thoroughly.**
5.  **Submit a pull request.**

Please ensure your code follows Ansible best practices and includes appropriate documentation.

## License Information

This project has no specified license. All rights are reserved to the owner.

## Acknowledgments

*   Ansible community for providing a powerful automation tool.
