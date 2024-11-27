 

# Online Banking System

 Overview
The Online Banking System is a web-based application that allows users to perform banking transactions and manage their accounts online. This system facilitates various banking activities such as account creation, balance inquiries, fund transfers, transaction history, and more, all from the convenience of a web browser. 

## Features
- **User Registration and Authentication**
  - Secure user registration and login functionality.
  - Password encryption for enhanced security.
- **Account Management**
  - Create and manage multiple accounts.
  - Update user profiles.
- **Transactions**
  - Deposit and withdraw funds.
  - Transfer funds between accounts.
  - View transaction history.
- **Balance Inquiry**
  - Check real-time account balances.
- **User Dashboard**
  - Comprehensive dashboard displaying account summaries and recent transactions.
- **Notifications**
  - Email notifications for important account activities.

## Technologies Used
- **Frontend**
  - HTML, CSS, JavaScript
  - React.js
- **Backend**
  - Node.js
  - Express.js
- **Database**
  - MySQL
- **Authentication**
  - JWT (JSON Web Tokens)
- **Additional Tools**
  - Docker for containerization
  - Git for version control

 # Installation

# Prerequisites
- Node.js
- MySQL
- Docker (optional, for containerization)

 # Steps
 
1. **Set Up Database**
   - Create a MySQL database:
     ```sql
     CREATE DATABASE online_banking_system;
     ```
   - Update `config/db.js` with your MySQL credentials.

2. **Run Migrations**
   - Use a migration tool or manually create the necessary tables using SQL scripts provided in the `migrations` folder.

3. **Start the Server**
   ```sh
   npm run dev
   ```

4. **Run the Client**
   ```sh
   cd client
   npm start
   ```

 # Database Schema
- **Users**
  ```sql
  CREATE TABLE users (
      id INT AUTO_INCREMENT PRIMARY KEY,
      username VARCHAR(50) UNIQUE NOT NULL,
      password VARCHAR(255) NOT NULL,
      email VARCHAR(100) UNIQUE NOT NULL,
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

 *Accounts**
  ```sql
  CREATE TABLE accounts (
      id INT AUTO_INCREMENT PRIMARY KEY,
      user_id INT,
      account_number VARCHAR(20) UNIQUE NOT NULL,
      balance DECIMAL(10, 2) DEFAULT 0.00,
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
      FOREIGN KEY (user_id) REFERENCES users(id)
  );
  ```

- **Transactions**
  ```sql
  CREATE TABLE transactions (
      id INT AUTO_INCREMENT PRIMARY KEY,
      account_id INT,
      type ENUM('deposit', 'withdrawal', 'transfer') NOT NULL,
      amount DECIMAL(10, 2) NOT NULL,
      timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
      FOREIGN KEY (account_id) REFERENCES accounts(id)
  );
  ```

# Usage
1. **Register a New User**: Users can sign up by providing their username, email, and password.
2. **Log In**: Users log in with their credentials to access their account.
3. **Manage Accounts**: Users can create and manage their accounts.
4. **Perform Transactions**: Users can deposit, withdraw, and transfer funds.
5. **Check Balance**: Users can view the current balance of their accounts.
6. **View Transaction History**: Users can see the history of all their transactions.

# Contributing
We welcome contributions! Please fork this repository, create a feature branch, and submit a pull request.

# License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

---

If you need any more details or modifications, just let me know! 😊
