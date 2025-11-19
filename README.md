
# Oracle Mini Database for Relational Database Practice

Welcome! This repository provides a complete, portable environment for practicing SQL and PL/SQL using **Oracle Database Express Edition (XE)** on Docker. It is designed to work seamlessly with **Visual Studio Code** on Linux.

## 📋 Prerequisites

* **Linux OS** (Ubuntu, Fedora, Arch, etc.)
* **Git**
* **Visual Studio Code**
* **Docker & Docker Compose**

---

## 🐧 Phase 1: Environment Installation (Linux Distros)

If you haven't installed Docker yet, run the command for your specific distribution.

### Ubuntu / Debian / Mint
```bash
sudo apt-get update
sudo apt-get install docker.io docker-compose -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
````

### Fedora / RHEL / CentOS

```bash
sudo dnf install docker docker-compose -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
```

### Arch Linux / Manjaro

```bash
sudo pacman -S docker docker-compose
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
```

> **Important:** After running these commands, log out and log back in so your user permissions update.

-----

## 🛠️ Phase 2: Cloning & Setup

1.  **Clone the Repository**
    Open your terminal and download this project:

    ```bash
    git clone https://github.com/LazzouziYoussefEtu/OracleMiniDataBaseOnDockerForRelationnalDatabasesPractice.git  
    cd OracleMiniDataBaseOnDockerForRelationnalDatabasesPractice
    ```

2.  **Start the Database**
    We use `docker-compose` to automate the startup and ensure your data is saved locally in the `oracle-data` folder.

    ```bash
    docker-compose up -d
    ```

    *Wait about 1-2 minutes for the database to fully initialize.*

-----

## 💻 Phase 3: Connecting VS Code

1.  **Install Extensions**
    Open VS Code (`code .`) and install the following extensions from the Marketplace:

      * **Oracle Developer Tools for VS Code** (for connection and standard SQL).
      * **SQL Notebook** (or a similar extension supporting `.sqlnb` for notebook practice).

2.  **Configure the Connection**

      * Click the **Database Icon** in the sidebar.
      * Click the **+ (Plus)** icon to add a connection.
      * Enter the following details:

    | Field | Value |
    | :--- | :--- |
    | **Connection Name** | `OracleDocker` |
    | **User Name** | `SYSTEM` |
    | **Password** | `YourSecurePassword123` (as defined in docker-compose) |
    | **Role** | `Default` |
    | **Connection Type** | `Basic` |
    | **Host Name** | `localhost` |
    | **Port** | `1521` |
    | **Service Name** | `XE` |

      * Click **Save** and then **Connect**.

-----

## 📄 Phase 4: Running Standard SQL

Use this method to initialize your database tables.

1.  Navigate to the `scripts/` folder in the VS Code file explorer.
2.  Open the `setup.sql` file.
3.  Right-click anywhere in the editor and select **Execute All**.
4.  This will create your practice tables and insert your initial dummy data.

-----

## 📓 Phase 5: PL/SQL with SQL Notebooks (.sqlnb)

SQL Notebooks allow you to mix documentation (Markdown) with executable code blocks, which is perfect for learning PL/SQL logic.

1.  **Create a Notebook:**

      * Create a new file named `practice_plsql.sqlnb`.

2.  **Add a Code Cell:**

      * Click **+ Code** in the notebook interface.
      * Select your `OracleDocker` connection from the dropdown menu on the cell.

3.  **Write PL/SQL:**
    Paste a PL/SQL block into the cell:

    ```sql
    SET SERVEROUTPUT ON;
    DECLARE
        v_message VARCHAR2(50) := 'Hello from PL/SQL Notebook!';
    BEGIN
        DBMS_OUTPUT.PUT_LINE(v_message);
    END;
    /
    ```

4.  **Run the Cell:**

      * Click the **Play** button next to the cell.
      * View the output directly below the code block.

-----

## 🧹 Cleanup

To stop the database and free up resources:

```bash
docker-compose down
```

To restart it later (your data will still be there):

```bash
docker-compose up -d
```

```
