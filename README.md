# Ansible Infrastructure

This repository sets up an infrastructure using Ansible to manage Docker and Docker Compose services. The playbook manages various services defined as submodules.

## Directory Structure

```
AutoContentLabs-ansible-infrastructure/
├── ansible
│   ├── playbook.yml             # Main Ansible playbook file
│   ├── inventory                # Ansible inventory (target hosts)
│   ├── roles
│   └───├── git
│       │   └── tasks
│       │       └── update.yml   # git submodules are initialized and updated
│       └── docker
│           └── tasks
│               │── clean.yml     # All containers, volumes, images, and networks clean
│               └── start.yml     # Create shared Docker network if not exists
└── services
    ├── fetcher                  # Fetcher service
    ├── messaging-utils          # Messaging-utils service
    ├── messaging                # Messaging service
    ├── databases                # Database service
    ├── data-collection-service  # Data-collection-service
    ├── data-processing-hub      # Data-processing-hub
    └── job-scheduler-service    # Job-scheduler-service
```

## Add Submodules

The services in the services directory are added as Git submodules. Run the following commands to add them:

```
# Add services as submodules
git submodule add https://github.com/AutoContentLabs/fetcher.git services/fetcher
git submodule add https://github.com/AutoContentLabs/messaging-utils.git services/messaging-utils
git submodule add https://github.com/AutoContentLabs/messaging.git services/messaging
git submodule add https://github.com/AutoContentLabs/databases.git services/databases
git submodule add https://github.com/AutoContentLabs/data-collection-service.git services/data-collection-service
git submodule add https://github.com/AutoContentLabs/data-processing-hub.git services/data-processing-hub
git submodule add https://github.com/AutoContentLabs/job-scheduler-service.git services/job-scheduler-service

# Commit the changes
git commit -m "Add services as submodules"

# Push the changes to the remote repository
git push
```

## Install Ansible

### For Windows:

Create a virtual environment:

```
python -m venv .venv
```

Activate the virtual environment:

```
.venv\Scripts\activate
```

Install Ansible:

```
pip install ansible
```

Alternatively, you can install WSL (Windows Subsystem for Linux) and run the following commands:

```
wsl --install
```

### For Linux:

Update your system and install Ansible:

```
sudo apt update
sudo apt install ansible
```

Verify the Ansible installation:

```
ansible --version
```

## Git Submodule Initialization

After cloning the repository, initialize and update the submodules:

```
git submodule init
git submodule update
```

To update the submodules to the latest versions:

```
git submodule update --remote --merge
```

## Run the Playbook

To execute the playbook, run the following command:

```
ansible-playbook -i ansible/inventory ansible/playbook.yml --ask-become-pass
```

This will start the services defined in the Docker Compose files using Ansible. It will also ensure that Docker networks and services are created and started correctly.
