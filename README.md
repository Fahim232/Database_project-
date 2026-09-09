# Database Project - User Authentication System

A full-featured web application with user authentication and role-based access control, built with PHP and MySQL.

## 📋 Overview

This is a database-driven authentication system that allows users to register and log in with role-based access levels (User and Admin). The application features secure password hashing, session management, and role-based page routing.

## 🛠️ Tech Stack

- **Backend:** PHP 7.4+
- **Database:** MySQL
- **Frontend:** HTML5, CSS3, JavaScript
- **Language Distribution:**
  - PHP: 72.8%
  - CSS: 24.6%
  - JavaScript: 2.6%

## 📁 Project Structure

```
Database_project-/
├── index.php              # Main login/register page
├── login_register.php     # Authentication handler
├── config.php             # Database configuration
├── admin_page.php         # Admin dashboard
├── user_page.php          # User dashboard
├── logout.php             # Logout handler
├── style.css              # Styling
└── script.js              # Client-side interactions
```

## ✨ Features

### Authentication
- **User Registration** - New users can register with name, email, password, and role selection
- **Login System** - Secure login with email and password verification
- **Password Security** - Passwords are hashed using `PASSWORD_DEFAULT` (bcrypt)
- **Session Management** - User sessions with automatic cleanup

### Role-Based Access Control
- **Admin Role** - Access to admin dashboard (`admin_page.php`)
- **User Role** - Access to user dashboard (`user_page.php`)
- **Automatic Routing** - Users are redirected based on their role after login

### Validation & Error Handling
- Email uniqueness validation
- Password verification with hashed passwords
- Error messages for failed login/registration attempts
- Session error tracking

## 🗄️ Database Setup

### Required Database
Create a MySQL database named `users_db`:

```sql
CREATE DATABASE users_db;
USE users_db;

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('user', 'admin') DEFAULT 'user',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## ⚙️ Configuration

Edit `config.php` to match your database credentials:

```php
$host = "localhost";
$user = "root";
$password = "";
$database = "users_db";
```

## 🚀 Getting Started

### Prerequisites
- PHP 7.4 or higher
- MySQL server
- Web server (Apache, Nginx, etc.)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Fahim232/Database_project-.git
   cd Database_project-
   ```

2. **Setup the database**
   - Create the `users_db` database
   - Run the SQL queries mentioned in the Database Setup section

3. **Configure database connection**
   - Update `config.php` with your database credentials

4. **Start your web server**
   - Place project in your web server's root directory
   - Access via `http://localhost/Database_project-/`

## 📝 Usage

### For Users

1. Navigate to the login page
2. Click **Register** to create a new account
3. Fill in name, email, password, and select your role
4. Click **Login** to access your dashboard
5. Use **Logout** to end your session

### For Admins

1. Follow the same registration/login process
2. Select **Admin** role during registration
3. Access the admin dashboard with extended features

## 🔒 Security Considerations

⚠️ **Important**: This project uses some practices that need improvement for production:

- SQL queries use direct string interpolation (vulnerable to SQL injection)
  - **Recommended:** Use prepared statements with parameterized queries
- Password validation could include strength requirements
- Add CSRF protection tokens
- Implement rate limiting on login attempts
- Use HTTPS in production
- Add input sanitization

**Suggested improvements:**
```php
// Instead of:
$conn->query("SELECT * FROM users WHERE email='$email'");

// Use prepared statements:
$stmt = $conn->prepare("SELECT * FROM users WHERE email=?");
$stmt->bind_param("s", $email);
$stmt->execute();
```

## 📄 File Descriptions

| File | Purpose |
|------|---------|
| `index.php` | Main page with login/register forms using tab switching |
| `login_register.php` | Handles user registration and login logic |
| `config.php` | Database connection configuration |
| `admin_page.php` | Admin-only dashboard page |
| `user_page.php` | User-only dashboard page |
| `logout.php` | Handles user logout |
| `style.css` | Application styling and layout |
| `script.js` | Client-side form switching functionality |

## 🤝 Contributing

Feel free to fork this repository and submit pull requests for improvements or bug fixes.

## 📝 License

This project is open source and available for educational purposes.

## 👨‍💻 Author

**Fahim232** - [GitHub Profile](https://github.com/Fahim232)

## 📞 Support

For issues or questions, please open an issue on the [GitHub repository](https://github.com/Fahim232/Database_project-/issues).

---

**Note:** This project is suitable for learning purposes. Before deploying to production, implement the security recommendations mentioned above.
