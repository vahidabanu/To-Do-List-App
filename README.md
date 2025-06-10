# To-Do-List-App
# Todo List Application

A full-stack Todo List application built with Spring Boot, Angular, and MySQL, deployed on Azure App Service.

## Prerequisites

- Java 17 or later
- Node.js 14 or later
- MySQL 8.0 or later
- Maven
- Angular CLI
- Azure CLI (for deployment)

## Backend Setup

1. Configure MySQL:
   - Create a database named `tododb`
   - Update `src/main/resources/application.properties` with your MySQL credentials

2. Build and run the Spring Boot application:
   ```bash
   cd backend
   mvn clean install
   mvn spring-boot:run
   ```

## Frontend Setup

1. Install dependencies:
   ```bash
   cd todo-frontend
   npm install
   ```

2. Start the development server:
   ```bash
   ng serve
   ```

3. Open `http://localhost:4200` in your browser

## Azure Deployment

### Backend Deployment

1. Create an Azure App Service:
   ```bash
   az appservice plan create --name todo-app-plan --resource-group your-resource-group --sku B1 --is-linux
   az webapp create --name todo-backend --resource-group your-resource-group --plan todo-app-plan --runtime "JAVA:17-java17"
   ```

2. Configure MySQL:
   - Create an Azure Database for MySQL
   - Update the application properties with the Azure MySQL connection string

3. Deploy the backend:
   ```bash
   mvn clean package
   az webapp deploy --resource-group your-resource-group --name todo-backend --type jar --src-path target/todo-list-0.0.1-SNAPSHOT.jar
   ```

### Frontend Deployment

1. Build the Angular application:
   ```bash
   cd todo-frontend
   ng build --prod
   ```

2. Create a static web app:
   ```bash
   az staticwebapp create --name todo-frontend --resource-group your-resource-group --location eastus
   ```

3. Deploy the frontend:
   ```bash
   az staticwebapp create --name todo-frontend --resource-group your-resource-group --location eastus
   ```

## Features

- Create, read, update, and delete todos
- Mark todos as complete/incomplete
- Responsive design
- Real-time updates
- Form validation
- Error handling

## Technologies Used

- Backend:
  - Spring Boot 3.2.3
  - Spring Data JPA
  - MySQL
  - Maven

- Frontend:
  - Angular 17
  - Bootstrap 5
  - TypeScript
  - RxJS

- Deployment:
  - Azure App Service
  - Azure Database for MySQL
  - Azure Static Web Apps 
