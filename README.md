# Openmrs 350 patients dataset Exploration using docker services


## What You'll Need Before Starting

- **Docker Desktop** installed on your computer ([Download here](https://www.docker.com/products/docker-desktop/))
- **Basic command line knowledge** (we'll show you the exact commands to type)
- About **30 minutes** for the initial setup


#### Installing Docker

<details>
<summary>mac OS</summary>


1. **Manual Installation:**
   - Download Docker Desktop from [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
   - Install and launch Docker Desktop
   - Ensure Docker is running (you should see the Docker icon in your menu bar)
2. Or ** Using Homebrew:**
   ```bash
   brew install --cask docker
   ```
   Then launch Docker Desktop from Applications.
</details>

<details>
<summary>Windows</summary>

1. Download Docker Desktop from [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Install and launch Docker Desktop
3. Ensure WSL 2 is enabled if prompted
</details>

<details>
<summary>Linux (Ubuntu/Debian)</summary>


```bash
# Update package index
sudo apt-get update

# Install prerequisites
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release

# Add Docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker repository
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

# Start Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Add your user to docker group (optional, to avoid sudo)
sudo usermod -aG docker $USER
```

</details>

## Git Repository Setup

This project is hosted as a Git repository. Git is required to clone the repository, manage updates, and retrieve the latest changes.

The repository uses **Git Large File Storage (Git LFS)** to store large files, such as the OpenMRS SQL dump dataset. After cloning the repository, Git LFS is required to download these large files locally.

Ensure that both **Git** and **Git LFS** are installed before proceeding with the setup.

## Git Installation


- ### Windows

1. Download the latest Git installer from:
 https://git-scm.com/download/win
2. Run the installer.
3. Accept the default installation options unless you have specific preferences.
4. Complete the installation.
5. Verify the installation:
   ```sh
    git --version
    ```
---

- ### Ubuntu
```sh 
 sudo apt update && sudo apt install git -y
```

- ### macOS
```sh 
brew install git
```


## Setting Up Git LFS for This Repository

This repository uses **Git Large File Storage (LFS)** to handle large files like `openmrs-2.8-refapp-demo-350-patients-2026-07-01.sql`. After cloning or pulling the repository, make sure that the sql file has been downloaded successfully located at `synthetic-data`.

### Step 1: Install Git LFS
Before cloning, install Git LFS:

- **macOS (Homebrew)**
  ```sh
  brew install git-lfs
  ```

- **Linux (Ubuntu/Debian)**
  ```sh
  sudo apt update && sudo apt install git-lfs
  ```

- **Windows**  
  Download and install Git LFS from [Git LFS official site](https://git-lfs.github.com/).

### Step 2: Clone the Repository
After installing Git LFS, clone the repository:

```sh
git clone https://github.com/abertnamanya/openmrs-350-patients-dataset.git
cd openmrs-350-patients-dataset
```

Git LFS will automatically download the large files.

### Step 3: Pulling Updates
If you have already cloned the repository before installing Git LFS, or if you are pulling new changes, run:

```sh
git lfs install
git lfs pull
```

This ensures all large files are properly downloaded.



---


</details>

# Install Visual Studio Code

Visual Studio Code (VS Code) is a lightweight and powerful code editor used to view, edit, and manage project files. It is recommended for working with this repository.

Follow the installation steps based on your operating system.

---

- Windows

Download Visual Studio Code from the official website:
   https://code.visualstudio.com/download
- Ubuntu
```sh
sudo snap install code --classic
```
- macOS
```sh 
brew install --cask visual-studio-code
```


# Open Project in Visual Studio Code

After installing Visual Studio Code, you can open the project repository in the editor.

1. Open Visual Studio Code.
2. Select:
`File → Open Folder`
3. Browse to the location where you cloned the repository.
4. Select the project folder.
5. Click Open.

The repository files will now be available in the VS Code Explorer.



## Start up docker container services

Visual Studio Code includes an integrated terminal that allows you to run Git, Docker, and other project commands without leaving the editor.

## Open Terminal
1. Go to Menu:
2. The click terminal 
3. New terminal
4. Copy : `docker compose up -d` command and run it in the terminal.


**What this does:** Starts all the services including databases and web interfaces.

---


## Viewing Your Data with CloudBeaver

CloudBeaver is a web-based tool that lets you explore your databases without needing to install additional software.

#### First Time Setup (Only do this once)

1. **Open CloudBeaver**: Go to http://localhost:8979 in your web browser

2. **Create Your Admin Account** (First time only):
   - You'll see a Setup Wizard
   - Choose any username (suggestion: `superuser`)
   - Choose any password (suggestion: `Admin@123` - remember this!)
   - Click through to complete the setup
   - Log in with these credentials

#### Connect to Your Openmrs Database
- Click the Home button icon to access the connection configuration settings.

**Connect to MySQL (For source data and previews):**

1. Click **"New Connection"** again
2. Select **"MariaDB"** from the list
3. Fill in these exact details:
   - **Host**: `synthetic-data`
   - **Port**: `3306`
   - **Database**: *(leave empty)*
   - **Username**: `root`
   - **Password**: `openmrs`
4. Click the checkbox to Save credentials for all users with access 
5. Click **"Create"** button in the top right corner

**Important:** Once connected, you'll see:
- **MariaDB@synthetic-data** on the left handside of the navigation bar
- Expand the MariaDB@synthetic-data by clicking the arrow icon. 
- Now you should be able to see the databases:
- Expand the Openmrs database to be able to see the tables. 


**Congratulations on successfully setting up the OpenMRS dataset in a MySQL server using Docker! 🎉**
---