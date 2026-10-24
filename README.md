# PHP Registration Form on AWS EC2

A responsive registration form built with **HTML, CSS, JavaScript, and PHP**, deployed on an **AWS EC2 instance** using **Nginx** and connected to **Amazon RDS for MariaDB**. The EC2 instance uses **Amazon EBS** for persistent block storage.

The application collects user details, displays a registration-success page, and stores submitted records in a MariaDB database.

## Project Preview
## 📸 Project Preview

### Registration Form

![Registration Form](screenshots/Screenshot%202026-10-08%20205836.png)

### Registration Success

![Registration Success](screenshots/Screenshot%202026-10-08%20205813.png)

### MariaDB Records

![MariaDB Records](screenshots/Screenshot%202026-10-08%20211213.png)

## 🏗️ Architecture

```text
              +----------------------+
              |   User / Web Browser |
              +----------------------+
                         |
                    HTTP / HTTPS
                         |
                         v
              +----------------------+
              |   Nginx Web Server   |
              |      AWS EC2         |
              +----------------------+
                         |
                         v
              +----------------------+
              | PHP Application      |
              | Logic                |
              +----------------------+
                         |
                         v
              +----------------------+
              |   MariaDB Database   |
              |   Hosted on EC2      |
              +----------------------+

              +----------------------+
              |     Amazon EBS       |
              | Persistent Block     |
              | Storage for EC2      |
              +----------------------+
                         |
                 Attached to EC2
```

### Request Flow

1. **User:** Accesses the registration form through a web browser.
2. **Nginx:** Receives HTTP/HTTPS requests on the AWS EC2 instance.
3. **PHP:** Processes the submitted registration details.
4. **MariaDB:** Stores the registration records on the EC2 instance.
5. **Amazon EBS:** Provides persistent block storage attached to EC2, when configured for application or database files.

**Note:** Amazon EBS is a storage service, not a database service. MariaDB runs directly on EC2 in this architecture.
## Features

- Responsive registration form interface
- Fields for name, email, website, comment, and gender
- PHP-based form processing
- MariaDB database integration
- Registration confirmation page
- Deployment on an AWS EC2 Linux instance
- Nginx web server configuration
- EC2 storage backed by Amazon EBS

## Technology Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript |
| Backend | PHP |
| Web server | Nginx |
| Database | MariaDB |
| Compute | Amazon EC2 |
| Storage | Amazon EBS |
| Cloud platform | Amazon Web Services (AWS) |

## Database Structure

The application uses a `users` table to store submitted registration information.

| Column | Description |
|---|---|
| `id` | Unique record identifier |
| `name` | Registered user's name |
| `email` | User's email address |
| `website` | Website URL |
| `comment` | User's comment |
| `gender` | Selected gender |

Example query to view stored records:

```sql
SELECT * FROM users;
```

## Deployment Overview

The project was deployed on AWS using the following high-level workflow:

1. **Launch an EC2 instance** with a suitable Linux AMI.
2. **Configure security groups** to allow only the required traffic, such as SSH for administration and HTTP/HTTPS for web access.
3. **Attach and configure EBS storage** for the instance as required.
4. **Install and configure Nginx** to serve the web application.
5. **Install PHP and the required PHP-FPM/database extensions** compatible with the chosen Linux distribution.
6. **Deploy the application files** to the configured web root and set appropriate file permissions.
7. **Configure MariaDB connectivity** and create the database and `users` table.
8. **Configure Nginx and PHP-FPM**, validate the configuration, and restart or reload the relevant services.
9. **Test the application** by submitting the form and verifying that the record is stored in the database.

Exact installation commands vary by Linux distribution and by whether MariaDB is hosted on Amazon RDS or directly on EC2.

## What I Learned

- Deploying a PHP web application on an AWS EC2 Linux instance
- Configuring Nginx to serve a PHP-based application
- Connecting a web application to a MariaDB database
- Understanding the role of Amazon EBS in EC2 storage
- Testing form submissions and verifying database records
- Applying basic cloud networking and deployment practices

## Author

**Aditya Annasaheb Shelar**
