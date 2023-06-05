How to run program:

PREREQUISITES
- Must have python installed and in PATH.
- Must have flask installed with the command pip install flask.
- Ensure React is installed and updated properly. 


Steps:
1: Install and set-up the SQL server.

Installing MySQL
MySQL is a popular open-source relational database management system that allows you to store, organize and retrieve data in a flexible and efficient manner. Here's how you can install MySQL on your system:
Go to the official MySQL website (https://dev.mysql.com/downloads/mysql/).
Choose the appropriate version for your Windows operating system and download the installer file.
Once the download is complete, run the installer and choose the "Developer Default" installation option.
Click the "Execute" button to begin the installation process.
Select the components you want to install. At a minimum, you'll need the "MySQL Server" component.
Choose the installation directory for MySQL. The default location is usually fine.
Set a root password for MySQL. This password will be required to log in to the MySQL server.
Additionally, you may choose to configure MySQL Server as a Window Service, which will allow it to run continuously in the background. To do so, select "Configure MySQL Server as a Window Service" from the "Window Service" option in the installation menu. You can change the Window Service Name if desired, but keeping the default name is recommended.
After selecting "Next" and "Finish" in the installation menu, you will be prompted to connect to the server. Enter the root username and password that you set up in step 7, and select "Check" to ensure that the connection is working correctly.
Finally, select "Execute" and the MySQL Server will be installed on your machine.

MySQL in VScode
Visual Studio Code (VScode) is a popular code editor that provides a range of extensions to help developers work with different technologies, including databases. Here's how you can install the MySQL extension in VScode:
Open Visual Studio Code and go to the "Extensions" tab on the left-hand side.
Search for "MySQL" in the search bar.
Click on the "Install" button for the "MySQL" extension by Jun Han.
Once you have installed the MySQL extension, you can connect to your MySQL server and manage your databases and tables directly from VSCode. Here are the steps to connect to your MySQL server:
Open VSCode and go to the "Explorer" tab on the left-hand side.
Click on the MySQL icon to open the MySQL view.
To create a new connection, click on the + button next to ‘MySQL’. Enter the server address, which is ‘localhost’ if you installed the server locally. Provide your username and password, and use the default port number. Press enter when prompted for the certificate file path.
A new connection called ‘localhost’ should appear under MySQL. However, when you click on it, you may receive an error message if you are using version 8 of the MySQL server. This version uses a new authentication method instead of the old MySQL native password.
To fix this error, you need to create a new SQL user that uses the old authentication method. To do this, go to the folder where MySQL is installed (usually in the C drive), then go to Program Files > MySQL > bin. Type ‘cmd’ in the window next to ‘bin’ to open the command prompt.
To connect to the server, type the following command: 
mysql -u root -p
‘mysql -u’ means you need to provide the username (which is ‘root’), and ‘-p’ means you need to provide the password. Type in your password and press enter.
Now you need to create a new user. Type the following command: 
CREATE USER 'bank'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
Give this user all privileges by typing: 
GRANT ALL PRIVILEGES ON *.* TO 'bank'@'%';
Validate the privileges by typing: 
FLUSH PRIVILEGES;
Delete the old ‘localhost’ connection in VsCode and create a new one by clicking the + button. Use ‘localhost’ as the server name and the new username and password created in step 7.

Creating and Adding Data
Once you have connected to your MySQL server in VSCode, you can create databases and tables and add data to them. Here are the steps to create a database, table, and add data to it:
To create a new query and a database, right-click on ‘localhost’ and select ‘New Query’. Inside the file type: 
CREATE DATABASE atm;
to create a new database. Right-click and select ‘Run MySQL Query’.
Create a new table by typing a SQL CREATE TABLE statement. For example:
CREATE TABLE atm.users (
    user_num INT NOT NULL,
    card_num BIGINT NOT NULL,
    name VARCHAR(50) NOT NULL,
    pin VARCHAR(4) NOT NULL,
    chequing_balance DECIMAL(10,2),
    saving_balance DECIMAL(10,2),
    PRIMARY KEY (card_num)
);
This creates a new table called "users" with six columns: "user_num", "card_num", "name", “pin”, “chequing_balance”, and "saving_balance". The "card_num" column is the primary key, which means that it uniquely identifies each row in the table.
Insert data into the table using a SQL INSERT statement. For example:
INSERT INTO atm.users (user_num, card_num, name, pin, chequing_balance, saving_balance) 
VALUES
(1, 1234567890123456, 'Cheska Santos', '1234', 5000.00, 10000.00),
(2, 2345678901234567, 'Dylan Ha', '5678', 2000.00, 15000.00),
(3, 3456789012345678, 'William Chau', '2468', 7000.00, 5000.00),
(4, 4567890123456789, 'Sparsh Soni', '4321', 9000.00, 12000.00),
(5, 5678901234567890, 'Ihtishamul Haque', '7890', 3000.00, 8000.00);
This inserts fiverows of data into the "users'' table. Each row corresponds to a single employee and contains values for the "user_num", "card_num", "name", “pin”, “chequing_balance”, and "saving_balance".
Save the SQL file, and then run the query by right-clicking and selecting "Run MySQL Query."
Finally, open MySQL Workbench and log in as the "root" user. In the navigator, select "Schemas," then "atm," and then "Tables." Hover over "users" and select the table icon. This will display the new query and the inputted data.

Congratulations! You have now installed MySQL, connected to your MySQL server in VSCode, and created a database, table, and added data to it. You can now use MySQL to manage your data.


2: Open a Terminal and access the flask-server folder with the following command: cd flask-server
3: Create and start Flask virtual environment with the following commands:
	py (or python) -m venv venv
	venv\Scripts\activate
	py server.py
4: In a separate terminal, access the client folder with the following command: cd client
5: Finally, start the react program with the following command: npm start
The app will launch on localhost:3000.

Now, login and enter some commands to test out the app!  