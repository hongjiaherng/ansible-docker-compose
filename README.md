# Ansible on Docker Compose

This project sets up a development environment for creating and testing Ansible playbooks using Docker Compose. It includes an Ansible control machine and two managed nodes, all running in Docker containers.

## Getting Started

### Prerequisites

- Docker (version that has compose built-in)

### Setup

1. **Clone the Repository:**

   ```sh
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Build and Start the Containers:**

   ```sh
   docker-compose up --build -d
   ```

   This command builds the Docker images and starts the containers in detached mode.

## Usage

### Connecting to the Ansible Control Node

To access the Ansible control machine, use the following SSH command:

```sh
ssh root@localhost -p 2222
```

### Running Ansible Commands

Once logged into the control machine, you can run Ansible commands to manage and test your nodes. For example, to ping all managed nodes:

```sh
ansible -m ping all
```

To ping a specific node:

```sh
ansible -m ping ansible-node1
ansible -m ping ansible-node2
```

### Connecting to Managed Nodes

From the control node, you can SSH into the managed nodes:

```sh
ssh root@ansible-node1
ssh root@ansible-node2
```

Ensure you are connected to the control node before attempting to SSH into the managed nodes.

## Alternative: Using Docker for Direct Commands

You can also use Docker commands to interact with the containers:

- **To start an interactive bash session in the Ansible control container or a managed node container:**

  ```sh
  docker exec -it ansible-control /bin/bash
  docker exec -it ansible-node1 /bin/bash
  docker exec -it ansible-node2 /bin/bash
  ```

- **To run Ansible commands from within the control container without going into an interactive session:**

  ```sh
  docker exec ansible-control ansible -m ping ansible-node1
  docker exec ansible-control ansible -m ping ansible-node2
  docker exec ansible-control ansible --version
  docker exec ansible-control python3 --version
  ```

## License

MIT License
