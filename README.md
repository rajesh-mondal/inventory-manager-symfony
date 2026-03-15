## Symfony Inventory Management System

This project is a **high-performance Inventory & User Management System** built on the **Symfony framework**. It is designed to bridge the gap between complex ERP systems and simple spreadsheets, providing a streamlined experience for managing assets and user permissions.

The application follows a **Monolithic Architecture** with a strong focus on **developer experience**, utilizing Symfony AssetMapper to manage front-end assets without the overhead of Node.js or Webpack. The system is strictly organized using the **MVC (Model–View–Controller)** pattern, ensuring that database interactions (via Doctrine ORM), business logic, and the UI layer (Twig) remain cleanly decoupled and easy to maintain.


## 🚀 Detailed Key Features

### 1. Advanced User Administration & Salesforce Integration

The admin panel acts as the **core control center** of the system, providing high-level oversight and seamless CRM connectivity.

- **Bulk Processing Engine:**  Utilizes a custom **JavaScript-to-PHP bridge** to handle multiple user actions—such as blocking, role upgrades, and deletions—in a single server request.

- **Salesforce CRM Synchronization:**  A specialized action on the user profile page collects additional data to create an **Account** and a linked **Contact** in Salesforce via **REST API**, streamlining marketing and service workflows.

- **Intelligent UI Stacking:**  Features a responsive design with **"Hide-and-Seek"** logic, ensuring wide columns are intelligently nested for 100% usability on mobile devices.

- **Role-Based Access Control (RBAC):**  Leverages Symfony’s native security to ensure sensitive routes, such as `/admin` and CRM actions, are restricted to authorized users.

### 2. Dynamic Inventory Management & Odoo Integration

Built for scale, this module manages complex data relationships and provides secure external data access.

- **Token-Based API Access:**  Each inventory can generate a unique **API Token** that provides restricted access to aggregated results (average, min, max, or popular values) for external consumption.

- **Odoo Read-Only Viewer:**  An external **Odoo application** acts as a viewer, importing inventory titles and aggregated results via the API token to display detailed health metrics.

- **Entity Relationships:**  Uses **Doctrine ORM** to manage complex One-to-Many and Many-to-Many relationships between Inventories, Items, and Categories.

- **Custom ID Patterns:**  Allows storing and applying **customized ID formats** for inventory items, making it easier to maintain consistent item numbering.

- **Configurable Custom Fields:**  Enables defining which of the **15 optional fields** (e.g., text, number, date fields) are active for a particular inventory, offering maximum flexibility.

### 3. Item Management & Power Automate Workflows 

Item handling is enhanced with automated cloud-based reporting and real-time notification triggers.

- **ID Generation:**  Concatenates fixed text, dates, and sequence numbers based on predefined templates whenever an item is saved.

- **Auto-Save Functionality:** Implements a JavaScript-based auto-save that sends periodic POST requests to a Symfony controller while editing to prevent data loss.

- **Support Ticket Automation:**  Users can trigger a "Create Support Ticket" link from any page to generate a **JSON report** containing their identity, priority level, and contextual links.

- **Cloud Storage Integration:**  Upon submission, the system automatically uploads the JSON ticket to **OneDrive** or **Dropbox** via API.

- **Power Automate Cloud Flows:**  A dedicated flow triggers on file upload to parse the JSON, send **Gmail notifications** to admins, and push real-time mobile notifications to "super-admins".

- **Row Actions:**  Eliminates individual row buttons in favor of a **checkbox-based selection system**, allowing users to perform **global actions** like "Delete" or "Edit" directly from a centralized toolbar.

### 4. Collaborative & Social Features

Enhances engagement through real-time communication and powerful search capabilities.

- **Real-Time Discussion System:**  Uses **JavaScript polling** to fetch new comments since the last received ID, ensuring a lightweight communication layer for teams.

- **Full-Text Search:**  Implements **MySQL FULLTEXT indexes** to allow fast keyword searches across the Inventory and Item tables directly from the navbar.

- **Engagement Tracking:**  Users can toggle "likes" on items, which are stored in a dedicated table to track user interaction.

- **Tag Cloud:**  Displays the most frequently used tags on the homepage to help users quickly navigate popular inventory items.

### 5. Optimized Frontend Architecture

Designed for speed and maintainability without heavy dependencies.

- **Sticky Selection Bar:**  A **floating toolbar** that appears only when items are selected, giving users immediate access to bulk actions without the need to scroll.

- **AssetMapper & Vanilla JS:**  Manages assets without Node.js overhead and uses Vanilla JavaScript for core interactions to ensure faster load times.


### 🛠 Technical Highlights

- **Language & Framework:** PHP 8.2+ (Attributes, Typed Properties), Symfony  
- **Database Migration:** Doctrine Migrations for versioned schema control  
- **Security:** Sodium password hashing, CSRF/XSS/SQL Injection protection  
- **Performance:** Symfony Cache Component for faster loading  
- **Frontend:** Twig, Bootstrap 5, Vanilla JS, AJAX for dynamic interactions


## Installation & Setup

1. **Clone the repository**  
```bash
git clone https://github.com/yourusername/inventory-system.git
cd inventory-system
```

2. **Install Dependencies**
Install the backend dependencies using Composer:
```bash
composer install
```

3. **Environment Configuration**
Configure Environment: Copy `.env` to `.env.local` and update your database connection string:
```bash
DATABASE_URL="mysql://db_user:db_password@127.0.0.1:3306/db_name"
```

4. **Setup Database**
```bash
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
```

5. **Start the Server**

```bash
symfony serve
```
