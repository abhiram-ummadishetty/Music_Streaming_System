# Musical-World
Musical World is a web application that basically alow user to ulpoad their own songs and can listen to already uploaded songs and can add their song into favorite list.
This project contains admin side as well as user side.
User has to first register to the portal before uploading songs.
The account verification mechanism have been included in the project to verify user authentication.

## Installation

1. **Start XAMPP:**
   - Open the XAMPP control panel.
   - Start the Apache and MySQL services by clicking on the "Start" buttons next to them.

2. **Create a Database:**
   - Open your web browser and go to `http://localhost/phpmyadmin`.
   - Log in using the default credentials (username: `root`, password: blank).
   - Click on the "Databases" tab and create a new database for your project.

3. **Import Database Schema (Optional):**
   - If you have a database schema file (`.sql`), you can import it into your newly created database using phpMyAdmin.

4. **Create Project Directory:**
   - Navigate to the `htdocs` directory inside your XAMPP installation folder (usually located at `C:\xampp\htdocs` on Windows or `/Applications/XAMPP/htdocs` on macOS).
   - Create a new directory for your project.

5. **Write PHP Scripts:**
   - Inside your project directory, create PHP files for your project's functionality. You can use a text editor or an integrated development environment (IDE) for this purpose.

6. **Access Your Project:**
   - Open your web browser and go to `http://localhost/your_project_directory`.

7. **Test Your Project:**
   - Verify that your project is working as expected by testing the functionality.


*create database named "musical_world" at back-end and import the code tables.sql file inside databse folder to get access to database*

Code for triggers and procedure are given below.

****Trigger code****

*trigger to keep track of user contributions*
```mysql
CREATE TRIGGER `IncrementCount` AFTER INSERT ON `upload_albums`
 FOR EACH ROW update user set user.contributions = user.contributions + 1 where new.singer_id = user.user_id
 ```
 ****procedure code****
 
 *stored procedure to upload songs*
 ```mysql
 DELIMITER $$
CREATE DEFINER=`root`@`localhost` PROCEDURE `uploadsongs`(IN `singer_id` INT(11), IN `song_name` VARCHAR(255), IN `song_format` VARCHAR(255), IN `singer_name` VARCHAR(255), IN `song_image` VARCHAR(255), IN `audio_file` VARCHAR(255))
    NO SQL
INSERT INTO upload_albums(`singer_id`,`song_name`,`song_format`,`singer_name`,`song_image`,`audio_file`) VALUES(singer_id,song_name,song_format,singer_name,song_image,audio_file)$$
DELIMITER ;
```

#  Note: do not forget to add your email credentials validate.php and activate_email.php file so as to send email notifications

