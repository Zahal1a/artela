# artela

### **Prerequisites**
Before starting, ensure you have the following:
1. **System Requirements**:
   - OS: Linux (Ubuntu recommended) or macOS
   - RAM: Minimum 8 GB
   - Disk: At least 500 GB of SSD storage
   - Network: A stable internet connection with sufficient bandwidth
2. **Software**:
   - `curl` for downloading files
   - `git` for version control
   - Docker (optional for containerized setups)

---

### **Step 1: Install Dependencies**

First, update your system and install essential tools:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl git build-essential -y
```

For macOS, use Homebrew:

```bash
brew update
brew install curl git
```

---

### **Step 2: Clone the Repository**

Clone the official Artela repository:

```bash
git clone https://github.com/artela-network/artela-node.git
cd artela-node
```

---

### **Step 3: Build the Node Software**

Build the node software using the following commands:

1. Navigate to the directory:
   ```bash
   cd node
   ```

2. Compile the software:
   ```bash
   make build
   ```

3. Verify installation:
   ```bash
   ./artela-node --version
   ```

---

### **Step 4: Configure the Node**

Generate the default configuration:

```bash
./artela-node init --chain-id artela-mainnet
```

Edit the configuration file to set up your node parameters:
```bash
nano ~/.artela/config/config.toml
```

Key parameters to update:
- **Peers**: Add seed nodes to ensure connectivity.
- **RPC Port**: Ensure the RPC port is accessible.

---

### **Step 5: Start the Node**

Start your full node using the following command:

```bash
./artela-node start
```

This command launches the node and begins syncing with the Artela network. Monitor the logs for sync progress.

---

### **Step 6: Monitor and Maintain**

Use these commands to monitor your node:
- **Check logs**:
  ```bash
  tail -f ~/.artela/logs/node.log
  ```
- **Verify sync status**:
  ```bash
  ./artela-node status
  ```

---

### **Optional: Running with Docker**

If you prefer a containerized setup, follow these steps:

1. Pull the Docker image:
   ```bash
   docker pull artela/artela-node:latest
   ```

2. Run the container:
   ```bash
   docker run -d -p 26656:26656 -p 26657:26657 \
   --name artela-node \
   -v ~/.artela:/root/.artela \
   artela/artela-node:latest
   ```

---

### **Common Issues and Troubleshooting**
1. **Node not syncing**:
   - Check your internet connection and ensure peers are correctly added.
2. **High disk usage**:
   - Use SSDs for better performance and sufficient storage space.
