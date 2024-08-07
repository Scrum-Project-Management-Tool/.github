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

### Maintain this folder structure on your local machine:

```
Scrum-Project-Management-Tool/
├── Scrum-Project-Management-Tool/
│   ├── Dockerfile
│   ├── src/
│   ├── package.json
│   ├── ...
├── Frontend-Scrum-Project-Management-Tool/
│   ├── Dockerfile
│   ├── src/
│   ├── package.json
│   ├── ...
├── docker-compose.yml
```
  
</details>

<details>
  <summary>Data Model</summary>
  
  ## [Data Model](https://app.eraser.io/workspace/R5oEkooQ06f92gM4qVXJ?origin=share) 

This document provides an in-depth description of the data model for a Scrum Project Management Tool. The model includes several entities: user, project, backlog, sprint, userStory, task, and issue. Each entity and the relationships between them are detailed below.

## Entities
### User
Represents a user within the system.

| Field | Type | Description |
| ----- | ----- | ----- |
| _id | objectId | Primary key, unique identifier |
| username | string | User's username |
| email | string | User's email |
| password | string | User's password |
| projectsId | string | ID of the projects the user is part of |
| refreshToken | string | Token for refreshing authentication |
### Project
Represents a project within the system.

| Field | Type | Description |
| ----- | ----- | ----- |
| _id | objectId | Primary key, unique identifier |
| assignees | string | ID of users assigned to the project |
| title | string | Title of the project |
| description | string | Description of the project |
| visibility | string | Visibility status of the project |
| backlogId | string | ID of the backlog associated with the project |
| sprintsId | string | ID of the sprints associated with the project |
| issuesId | string | ID of the issues associated with the project |
### Backlog
Represents a backlog within a project.

| Field | Type | Description |
| ----- | ----- | ----- |
| _id | objectId | Primary key, unique identifier |
| userStoriesId | string | ID of user stories in the backlog |
### Sprint
Represents a sprint within a project.

| Field | Type | Description |
| ----- | ----- | ----- |
| _id | objectId | Primary key, unique identifier |
| name | string | Name of the sprint |
| startDate | Date | Start date of the sprint |
| endDate | Date | End date of the sprint |
| userStoriesId | string | ID of user stories in the sprint |
### User Story
Represents a user story within a sprint or backlog.

| Field | Type | Description |
| ----- | ----- | ----- |
| _id | objectId | Primary key, unique identifier |
| subject | string | Subject of the user story |
| tag | string | Tag for categorizing the user story |
| description | string | Description of the user story |
| attatchement | string | Attachment related to the user story |
| status | string | Status of the user story |
| assignees | string | ID of users assigned to the user story |
| tasksId | string | ID of tasks related to the user story |
### Task
Represents a task within a user story.

| Field | Type | Description |
| ----- | ----- | ----- |
| _id | objectId | Primary key, unique identifier |
| subject | string | Subject of the task |
| status | string | Status of the task |
| assignee | string | ID of the user assigned to the task |
### Issue
Represents an issue within a project.

| Field | Type | Description |
| ----- | ----- | ----- |
| _id | objectId | Primary key, unique identifier |
| subject | string | Subject of the issue |
| description | string | Description of the issue |
| tag | string | Tag for categorizing the issue |
| attachement | string | Attachment related to the issue |
| status | string | Status of the issue |
| assignee | string | ID of user assigned to the issue |
| type | string | Type of the issue (e.g., bug, enhancement) |
| severity | string | Severity level of the issue |
| priority | string | Priority level of the issue |
## Relationships
### User - Project
A user can be part of multiple projects.

- `user.projectsId`  > `project._id` 
### Project - Assignees
Multiple users can be assigned to a single project.

- `project.assignees`  > `user._id` 
### Project - Backlog
A project can have one backlog.

- `project.backlogId`  > `backlog._id` 
### Project - Sprints
A project can have multiple sprints.

- `project.sprintsId`  > `sprint._id` 
### Project - Issues
A project can have multiple issues.

- `project.issuesId`  > `issue._id` 
### Backlog - User Stories
A backlog can contain multiple user stories.

- `backlog.userStoriesId`  > `userStory._id` 
### Sprint - User Stories
A sprint can contain multiple user stories.

- `sprint.userStoriesId`  > `userStory._id` 
### User Story - Assignees
Multiple users can be assigned to a single user story.

- `userStory.assignees`  > `user._id` 
### User Story - Tasks
A user story can contain multiple tasks.

- `userStory.tasksId`  > `task._id` 
### Task - Assignee
A task is assigned to a single user.

- `task.assignee`  > `user._id` 
### Issue - Assignees
Multiple users can be assigned to a single issue.

- `issue.assignees`  > `user._id` 

  
</details>

<details>
  <summary>Contributor Guidelines</summary>
  
  ## Contributors Guidelines

  We have two main repositories: one for the frontend and one for the backend. Below are detailed guidelines to help you get started with contributing to each repository.

---

### Frontend Repository: Frontend-Scrum-Project-Management-Tool

#### Technologies Used
- React.js

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
   npm run dev
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

- Follow the React style guide.
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


