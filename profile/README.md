# Scrum Project Management Tool 

## Sections

<details>
  <summary>Introduction</summary>

## Introduction

Welcome to the Scrum Project Management Tool, an efficient and robust platform designed to streamline the management of Scrum-based projects. This tool provides an organized structure for managing users, projects, backlogs, user stories, tasks, sprints, and issues, ensuring that your team's workflow is smooth and effective.

### Key Features

- **User Management:** Keep track of users, their roles, and their associations with various elements of the project.
- **Project Tracking:** Manage multiple projects, each with its own set of user stories, tasks, and backlog items.
- **Backlog Management:** Organize and prioritize backlog items to ensure that the most critical tasks are addressed first.
- **User Stories:** Create, assign, and track user stories, complete with detailed descriptions, tags, attachments, and statuses.
- **Task Management:** Break down user stories into manageable tasks, assign them to team members, and track their progress.
- **Sprint Planning:** Organize work into sprints, with clearly defined start and end dates, to maintain a consistent and focused workflow.
- **Issue Tracking:** Identify, categorize, and prioritize issues, ensuring that any obstacles to project progress are swiftly addressed.

### Why Use This Tool?

Managing Scrum projects can be challenging, especially as teams grow and projects become more complex. This tool provides a centralized platform for all your project management needs, allowing you to:

- **Improve Collaboration:** By providing a shared space for all project-related information, this tool enhances team collaboration and communication.
- **Increase Transparency:** With clear visibility into each aspect of the project, team members and stakeholders can easily stay informed about progress and challenges.
- **Boost Productivity:** By organizing work into sprints and managing tasks and issues effectively, your team can maintain a steady and productive workflow.
- **Ensure Accountability:** Assigning tasks and user stories to specific team members ensures that everyone knows their responsibilities and deadlines.

This Scrum Project Management Tool is designed to help you achieve your project goals efficiently, keeping your team organized and focused on delivering high-quality results.

</details>

<details>
  <summary>Repository Structure</summary>

  ## Repository Structure

This organization contains three repositories:

1. **Scrum-Project-Management-Tool**: This repository contains the backend of the project, handling all server-side operations, data management, and API endpoints.
2. **Frontend-Scrum-Project-Management-Tool**: This repository contains the frontend of the project, providing a user-friendly interface for interacting with the tool.
3. **.github**: This repository includes configuration files, workflows, issue templates, and other GitHub-specific settings that enhance collaboration and project management within the organization.  
  
</details>

<details>
  <summary>Data Model</summary>
  
  ## [Data Model](https://app.eraser.io/workspace/R5oEkooQ06f92gM4qVXJ?origin=share) 

This section provides a detailed explanation of the data model for a Scrum Project Management Tool. Each table in the model is described, including its fields and relationships with other tables.

## Tables

### Users

- **Icon:** user
- **Color:** blue

| Field      | Type   | Description                             |
|------------|--------|-----------------------------------------|
| id         | string | Primary Key                             |
| username   | string | Username of the user                    |
| email      | string | Email address of the user               |
| password   | string | Encrypted password                      |
| projectId  | string | Foreign Key to the projects table       |
| backlogId  | string | Foreign Key to the backlog table        |
| userStoryId| string | Foreign Key to the userStories table    |
| taskId     | string | Foreign Key to the tasks table          |
| sprintId   | string | Foreign Key to the sprints table        |
| issueId    | string | Foreign Key to the issues table         |

### Projects

- **Icon:** folder
- **Color:** green

| Field        | Type   | Description                             |
|--------------|--------|-----------------------------------------|
| id           | string | Primary Key                             |
| assignee     | string | Foreign Key to the users table (assignee)|
| title        | string | Title of the project                    |
| description  | string | Description of the project              |
| visibility   | string | Project visibility (e.g., public, private) |
| backlogId    | string | Foreign Key to the backlog table        |
| userStoriesId| string | Foreign Key to the userStories table    |
| taskId       | string | Foreign Key to the tasks table          |

### Backlog

- **Icon:** skip-back
- **Color:** yellow

| Field        | Type   | Description                             |
|--------------|--------|-----------------------------------------|
| id           | string | Primary Key                             |
| userStoriesId| string | Foreign Key to the userStories table    |

### User Stories

- **Icon:** users
- **Color:** purple

| Field        | Type   | Description                             |
|--------------|--------|-----------------------------------------|
| id           | string | Primary Key                             |
| subject      | string | Subject of the user story               |
| tag          | string | Tag for categorizing user stories       |
| description  | string | Detailed description of the user story  |
| attachment   | string | Link to any attached file               |
| status       | string | Current status of the user story        |
| assignee     | string | Foreign Key to the users table          |
| taskId       | string | Foreign Key to the tasks table          |

### Tasks

- **Icon:** file
- **Color:** red

| Field      | Type   | Description                             |
|------------|--------|-----------------------------------------|
| id         | string | Primary Key                             |
| subject    | string | Subject of the task                     |
| status     | string | Current status of the task              |
| assignee   | string | Foreign Key to the users table          |

### Sprints

- **Icon:** timer
- **Color:** pink

| Field        | Type | Description                             |
|--------------|------|-----------------------------------------|
| id           | string | Primary Key                             |
| name         | string | Name of the sprint                      |
| startDate    | Date   | Start date of the sprint                |
| endDate      | Date   | End date of the sprint                  |
| userStoriesId| string | Foreign Key to the userStories table    |

### Issues

- **Icon:** crosshair
- **Color:** white

| Field        | Type   | Description                             |
|--------------|--------|-----------------------------------------|
| id           | string | Primary Key                             |
| subject      | string | Subject of the issue                    |
| description  | string | Detailed description of the issue       |
| tag          | string | Tag for categorizing issues             |
| attachment   | string | Link to any attached file               |
| status       | string | Current status of the issue             |
| assignee     | string | Foreign Key to the users table          |
| type         | string | Type of issue (e.g., bug, task, improvement) |
| severity     | string | Severity level of the issue             |
| priority     | string | Priority level of the issue             |

## Relationships

### Users Table Relationships

- `projectId` > `projects.id`: Each user can be associated with a project.
- `backlogId` > `backlog.id`: Each user can be associated with a backlog.
- `userStoryId` > `userStories.id`: Each user can be associated with a user story.
- `taskId` > `tasks.id`: Each user can be associated with a task.
- `sprintId` > `sprints.id`: Each user can be associated with a sprint.
- `issueId` > `issues.id`: Each user can be associated with an issue.

### Projects Table Relationships

- `assignee` > `users.id`: Each project has an assignee (a user).
- `backlogId` > `backlog.id`: Each project has a backlog.
- `userStoriesId` > `userStories.id`: Each project contains user stories.
- `taskId` > `tasks.id`: Each project contains tasks.

### Backlog Table Relationships

- `userStoriesId` > `userStories.id`: A backlog contains user stories.

### User Stories Table Relationships

- `assignee` > `users.id`: Each user story is assigned to a user.
- `taskId` > `tasks.id`: Each user story can have associated tasks.

### Tasks Table Relationships

- `assignee` > `users.id`: Each task is assigned to a user.

### Sprints Table Relationships

- `userStoriesId` > `userStories.id`: Each sprint contains user stories.

### Issues Table Relationships

- `assignee` > `users.id`: Each issue is assigned to a user.

This data model provides a structured approach to managing Scrum projects, allowing for clear relationships between users, projects, backlogs, user stories, tasks, sprints, and issues.
  
</details>

<details>
  <summary>Contributor Guidelines</summary>
  
  ## Contributors Guidelines

  We have two main repositories: one for the frontend and one for the backend. Below are detailed guidelines to help you get started with contributing to each repository.

---

### Frontend Repository: Frontend-Scrum-Project-Management-Tool

#### Technologies Used
- Angular.js

#### Getting Started

1. **Fork the Repository**
   - Navigate to the [Frontend-Scrum-Project-Management-Tool](#) repository.
   - Click the "Fork" button at the top right corner.

2. **Clone the Forked Repository**
   ```sh
   git clone https://github.com/your-username/Frontend-Scrum-Project-Management-Tool.git
   cd Frontend-Scrum-Project-Management-Tool
   ```

3. **Install Dependencies**
   ```sh
   npm install
   ```

4. **Start the Development Server**
   ```sh
   ng serve
   ```

5. **Create a Branch**
   ```sh
   git checkout -b feature/your-feature-name
   ```

#### Making Changes

- Make your changes in the code.
- Ensure the code follows the project's coding standards.
- Test your changes thoroughly.

#### Committing and Pushing Changes

1. **Commit Your Changes**
   ```sh
   git add .
   git commit -m "Add feature: your feature description"
   ```

2. **Push to Your Fork**
   ```sh
   git push origin feature/your-feature-name
   ```

#### Creating a Pull Request

1. **Navigate to Your Fork**
   - Go to your fork on GitHub.
   - Click the "New Pull Request" button.

2. **Describe Your Changes**
   - Provide a clear and detailed description of the changes you have made.

3. **Submit the Pull Request**
   - Submit the pull request for review.

#### Code Style Guidelines

- Follow the Angular style guide.
- Ensure your code is linted and formatted according to the project's settings.

#### Reporting Issues

- If you encounter any issues, please report them on the [issue tracker](#) with a detailed description.

---

### Backend Repository: Scrum-Project-Management-Tool

#### Technologies Used
- Express
- Node.js
- MongoDB

#### Getting Started

1. **Fork the Repository**
   - Navigate to the [Scrum-Project-Management-Tool](#) repository.
   - Click the "Fork" button at the top right corner.

2. **Clone the Forked Repository**
   ```sh
   git clone https://github.com/your-username/Scrum-Project-Management-Tool.git
   cd Scrum-Project-Management-Tool
   ```

3. **Install Dependencies**
   ```sh
   npm install
   ```

4. **Set Up Environment Variables**
   - Create a `.env` file in the root directory.
   - Add the necessary environment variables (e.g., MongoDB URI, PORT).

5. **Start the Development Server**
   ```sh
   npm run dev
   ```

6. **Create a Branch**
   ```sh
   git checkout -b feature/your-feature-name
   ```

#### Making Changes

- Make your changes in the code.
- Ensure the code follows the project's coding standards.
- Test your changes thoroughly.

#### Committing and Pushing Changes

1. **Commit Your Changes**
   ```sh
   git add .
   git commit -m "Add feature: your feature description"
   ```

2. **Push to Your Fork**
   ```sh
   git push origin feature/your-feature-name
   ```

#### Creating a Pull Request

1. **Navigate to Your Fork**
   - Go to your fork on GitHub.
   - Click the "New Pull Request" button.

2. **Describe Your Changes**
   - Provide a clear and detailed description of the changes you have made.

3. **Submit the Pull Request**
   - Submit the pull request for review.

#### Code Style Guidelines

- Follow the Node.js and Express best practices.
- Ensure your code is linted and formatted according to the project's settings.

#### Reporting Issues

- If you encounter any issues, please report them on the [issue tracker](#) with a detailed description.


  
  
  
</details>


