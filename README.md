# --Internet-of-things-and-data-systems.Week-4-assignments
This repository offers:
# A web page that uses the GET method to send and store values to the database .
* Project description:
as the web page contains an entry field and a button to send to the database.
When you enter a numeric value and press the submit button, the number is sent to the database directly.
The database contains one table and one column to store the values sent to it 
* Requirements :
- Visual Studio Code
- HTML
- CSS
- php
- phpMyAdmin
 * The sent values will be saved to the database
<img width="923" alt="181361579-4d156295-7573-4131-9e26-88f734d074e8ff" src="https://user-images.githubusercontent.com/108256116/182549741-a810085e-0363-4580-b0a4-34585326c7d0.png">



#  Using the Function POST
Similar to the GET function, an HTML and CSS file is created to receive user input. Instead of using the same HTML file, a separate PHP file will be used. To connect the HTML with the PHP file, the following line should be written inside the form div in the HTML file.

             <form action="connect.php" method="post">
    
The following PHP file will connect with the database, then will take the input Svalue and save it.

                <?php
    $Svalue = $_POST['Svalue'];
      // Database connection
      $conn = new mysqli('localhost','root','','database');
       if($conn->connect_error){
       echo "$conn->connect_error";
        die("Connection Failed : ". $conn->connect_error);
                         } else {
      $stmt = $conn->prepare("insert into data(Svalue) values(?)");
      $stmt->bind_param("i", $Svalue);
      $execval = $stmt->execute();
      echo $execval;
      $execval = $stmt->execute();
      echo "The value have been added successfully...";
      $stmt->close();
      $conn->close();
       }
        ?>
  
  
#  References:
https://www.guru99.com/difference-get-post-http.html
https://youtu.be/UzwyDdX3TS8
https://demo.phpmyadmin.net/master-config/
