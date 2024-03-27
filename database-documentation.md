# Database Documentation: "Shop Database"

## Tables

### Customers

- **customer_id** (Primary Key, INT): Unique identifier for customers.
- **first_name** (VARCHAR(50)): First name of the customer.
- **last_name** (VARCHAR(50)): Last name of the customer.
- **gender** (VARCHAR): Gender of the customer.
- **address** (VARCHAR(200)): Customer's address.
- **phone** (VARCHAR(20)): Customer's phone number.
- **email** (VARCHAR(100)): Customer's email address.
- **city** (VARCHAR(20)): City where the customer resides.
- **country** (VARCHAR(50)): Country where the customer resides.

### Employees

- **employee_id** (Primary Key, INT): Unique identifier for employees.
- **first_name** (VARCHAR(50)): First name of the employee.
- **last_name** (VARCHAR(50)): Last name of the employee.
- **email** (VARCHAR(100)): Employee's email address.
- **job_title** (VARCHAR(20)): Job title of the employee.

### Orders

- **order_id** (Primary Key, INT): Unique identifier for orders.
- **product_id** (INT): References Products table (product_id).
- **payment_id** (INT): References Payments table (payment_id).
- **fulfilled_by_employee_id** (INT): References Employees table (employee_id).
- **date_required** (DATE): Date when the order is required.
- **date_shipped** (DATE): Date when the order is shipped.
- **status** (VARCHAR(20)): Status of the order.

### Payments

- **payment_id** (Primary Key, INT): Unique identifier for payments.
- **customer_id** (INT): References Customers table (customer_id).
- **payment_date** (DATE): Date of the payment.
- **amount** (DECIMAL): Payment amount.

### Products

- **product_id** (Primary Key, INT): Unique identifier for products.
- **product_name** (VARCHAR(100)): Name of the product.
- **description** (VARCHAR(300)): Description of the product.
- **buy_price** (DECIMAL): Price of the product.

## Relationships

- The Customers table's **customer_id** is referenced by the Payments table's **customer_id**.
- The Employees table's **employee_id** is referenced by the Orders table's **fulfilled_by_employee_id**.
- The Orders table's **product_id** is referenced by the Products table's **product_id**.
- The Orders table's **payment_id** is referenced by the Payments table's **payment_id**.

#  How to run the database

## Setting Up PostgreSQL Database with Docker Compose

### 1. Clone the Repository
```
git clone https://github.com/Umuzi-org/Fumani-Masingi-200-sql-.git
```

### 2. Navigate to the  repository
```
cd Fumani-Masingi-200-sql-
```

### 3. Check docker installation
Ensure that Docker is installed and running.

### 4. Update Docker Compose File
Update Docker Compose File Open the docker-compose.yaml file and ensure it has the correct configurations for PostgreSQL and Adminer.

### 5.  Start the Containers
Start container using the command below.
```
docker-compose up
```
This command will download necessary Docker images, create containers, and start the PostgreSQL database and Adminer.

### 6. Access Adminer

Adminer will be accessible at http://localhost:8080. Use PostgreSQL credentials from docker-compose.yaml to log in.

### 7. Connect to PostgreSQL
Connect to PostgreSQL using the credentials below

- **System:** PostgreSQL
- **Server:** postgres
- **Username:** user
- **Password:** pass
- **Database:** postgres

### 8. Run SQL Scripts
Ensure your SQL script files (create-database.sql, create-tables.sql, populate-database.sql, query-database.sql) are in the src directory. Docker Compose will run these scripts during container initialization.

### 9. Stop Containers
stop container using the command below.
```
docker-compose down
```
