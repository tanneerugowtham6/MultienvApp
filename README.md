# Multi-Environment Ticket Management System

---

## Project Execution Overview

This project is executed in **5 phases**, each containing a set of clear deployment tasks required to fully host and scale the Travel Memory MERN application on AWS.

### Phases of Deployment

- **Phase 1:** Local Environment Setup
- **Phase 2:** Containerization Strategy
- **Phase 3:** Orchestration & Networking
- **Phase 4:** Application Deployment
- **Phase 5:** Verification & Testing

---

## Environment

### Services
- Docker
- Docker-Compose

### Database
- MongoDB Atlas

## Technology Stack

### Frontend
- React
- JavaScript
- npm

### Backend
- Node.js

### Version Control
- Git

---

## Phase 1: Local Environment Setup 

### Task-1: Installing Docker Desktop

1. Install Docker Desktop from https://docs.docker.com/desktop/
2. Verify the installation from Terminal/Command Prompt/CLI
   ```sh
   docker --version
   ```

### Task-2: Configure the MongoDB

1. Sign in to your MongoDB Atlas account (https://www.mongodb.com/cloud/atlas)
2. Once logged in, click on `Create a cluster`

    <img width="1204" height="578" alt="image" src="https://github.com/user-attachments/assets/88a8357c-78ed-4b35-aa26-328495bbe0c6" />

3. Select the required plan, since it's a demo, going with a `free` plan

    <img width="1419" height="483" alt="image" src="https://github.com/user-attachments/assets/09dc27b3-acd8-4c6b-a459-f9fe9df443b3" />

4. Enter the required details under the **Configurations** section like, **Name, Provider, Region**

    <img width="708" height="504" alt="image" src="https://github.com/user-attachments/assets/86805543-023a-476d-8fad-55609e63fe87" />

5. Click on **Create Deployment**

    <img width="513" height="91" alt="image" src="https://github.com/user-attachments/assets/28f40b1f-32dc-49dd-b2bd-eb19f26a4bd1" />

6. Once created, Connect to <your-cluster-name> window will be popped up. Click on **Compass**

    <img width="829" height="838" alt="image" src="https://github.com/user-attachments/assets/6d52e18a-926b-45b5-b895-5edfa52041f7" />

7. Select **I have MongoDB Compass installed**, copy the connection string [Save this for later steps]

    <img width="829" height="856" alt="image" src="https://github.com/user-attachments/assets/de0720af-df4b-4c55-9a5f-486360f4b99b" />

    **NOTE:** If you do not have MongoDB Compass installed, download it from https://downloads.mongodb.com/compass/mongodb-compass-1.48.2-darwin-arm64.dmg

8. Click on **Done**

9. On the left sidebar, click on **Database & Network Access**

    <img width="469" height="697" alt="image" src="https://github.com/user-attachments/assets/65cb8e4e-4cb7-4c98-a8b5-bbc1e40421e8" />

10. Click on **ADD NEW DATABASE USER**

    <img width="1440" height="113" alt="image" src="https://github.com/user-attachments/assets/925f3321-40fd-40c0-bba3-323013dcba1b" />

11. Enter a username and password

    <img width="978" height="599" alt="image" src="https://github.com/user-attachments/assets/197c01f6-db9c-4226-bb8b-eaf2bf93f9c0" />

12. Goto **Database User Privileges** section, under **Built-in Role**, select **Read and write to any database**. Click on **Add User**

    <img width="953" height="720" alt="image" src="https://github.com/user-attachments/assets/676d6a56-996e-4b62-9eff-a5761c065813" />

13. Click on **IP Access List** on the left sidebar. Click on **ADD IP ADDRESS**

    <img width="1433" height="109" alt="image" src="https://github.com/user-attachments/assets/79fa3f63-ad1f-4760-a9df-514639826637" />
    <img width="613" height="474" alt="image" src="https://github.com/user-attachments/assets/7b815764-4fc2-4120-b5a6-864d89727cb6" />

14. Click on **Save Changes**

### Task-3: Connect to Database using MongoDB Compass

1. Launch MongoDB Compass, click on **Add new connection**

    <img width="1424" height="747" alt="image" src="https://github.com/user-attachments/assets/23dbfac0-9624-4d06-afc9-f56a054ddcc8" />

2. Enter the **Connection string** copied from the previous task in the **New Connection** tab under **URI**

    <img width="1921" height="1000" alt="image" src="https://github.com/user-attachments/assets/00d151c1-5abb-4b00-a283-16dca6503218" />

    Replace <db_password> with your password created in the previous task.
   
4. Click on **Save & Connect**
5. In the **Connections** tab on the Left sidebar, hover the mouse on the cluster name, then click on **+** to **Create database**

    <img width="329" height="272" alt="image" src="https://github.com/user-attachments/assets/abc05e04-a167-4b62-b0d1-a7d2311b8f44" />

6. Enter the Database details, **Database Name, Collection Name** then click on **Create Database**

    <img width="609" height="480" alt="image" src="https://github.com/user-attachments/assets/7ca63b8a-8993-494a-9062-59a6d31452be" />

7. Save your MongoDB Connection URI, as this may be required for further configuration.

---

## Phase 2: Containerization Strategy 

1. Go to the `backend/dev` directory, create a `.env` file, and insert your MongoDB URI [Refer to the files in this repository]

    ```
    cd /MultienvApp/backend/dev
    ```

    Refer `.env` file from the `backend/dev` folder in this repository.

    <img width="853" height="97" alt="image" src="https://github.com/user-attachments/assets/e1a6e27d-8839-4c36-8563-521f2ddca898" />

2. Create a Dockerfile for backend development deployment
    Refer `dockerfile` file from the `backend/dev` folder in this repository.

    <img width="398" height="227" alt="image" src="https://github.com/user-attachments/assets/55e21dcd-ac83-450c-b722-7b04bf05482e" />

3. Go to the `backend/prod` directory, create a `.env` file, and insert your MongoDB URI [Refer to the files in this repository]

    ```
    cd /MultienvApp/backend/prod
    ```

    Refer `.env` file from the `backend/dev` folder in this repository.

    <img width="848" height="100" alt="image" src="https://github.com/user-attachments/assets/ae37f125-a68a-49fb-b7ba-fa891dbdfd20" />

4. Create a Dockerfile for backend production deployment
    Refer `dockerfile` file from the `backend/dev` folder in this repository.

    <img width="395" height="224" alt="image" src="https://github.com/user-attachments/assets/63b8d2d1-48c0-457d-8ac1-c12487f7675c" />

5. Go to the `frontend` directory, create a Dockerfile for frontend deployment

    ```
    cd /MultienvApp/frontend
    ```

    Refer `dockerfile` file from the `frontend` folder in this repository.

    
7. dca
8. ds
9. vds
10. v
