# LAAP
Linux Admin Automation Project
# Welcome to the Linux Admin Automation Project LAAP
# Created and maintained by Mark Patterson vcpmark@gmail.com

# The LAAP allows you to run a command and collect data from many servers
# at one point I used it to manage 1000's of linux servers of all flavors
# it works on basic tools that are available on almost every linux server

# Step 1, Understand what this collection of scripts does
# Please do not use this if you are not comfortable with bash and linux administration

# Step 2, Decide if you feel comfortable with using LAAP, Understand that any mistakes are amplified and your sole responsibility

# Step 3, Determine what username you will use , ( can you logon as root?,  do you log on as another user and sudo ?)

# Step 4, Configure LAAP to work for you and your environment

a. edit the collect/go.sh file and update the username to your required username

b. If you do not have existing keys that you use, Generate your SSH key pair by runing the following:

#keep the passphrase empty

ssh-keygen -t dsa -f key

C. copy the key.pub file to the authorized_keys2 file
cat key.pub > autor/resource/laap/authorized_keys2

D. Add your servers to LAAP
 Edit the collect/server.txt file to include all the servers you want to manage

E.   Edit collect/autor/autor.sh to add your ssh keys to the servers in server.txt

Find the "#### Add SSH AUTH Keys to servers####" Section and uncomment the line
"#~/autor/resource/laap/add_srvr.sh"     -- Again at this point you should have already looked in this file to see what it is doing.

Be aware that the script currently overwrites the existing authorized keys file if it exists for the user, modify autor/resource/laap/add_srvr.sh if you would like to change this behavior

F.  Run LAAP for the first time

collect/go.sh

It will show a status,  during the first run and any time you add in a new server.  You will have to enter the password.

G.   Review logs in collect/output
cd collect/output
ls

it should show a directory for each server you ran against  also there is a log.txt file

less log.txt   -- Review the log and see that your keys were added

H. Edit collect/autor/autor.sh to comment out the "#### Add SSH AUTH Keys to servers####" Section and comment the line
"~/autor/resource/laap/add_srvr.sh

I: LAAP is now ready to use.   Edit the user edit section in collect/autor/autor.sh to change what commands you want to run
if you want to copy existing scripts to all your servers and run them, then copy the script to collect/autor/resources/ and call it from collect/autor/autor.sh 

J:   In normal usage you edit the user edit section in  in collect/autor/autor.sh make sure servers.txt has just the servers you want to run against..   then run collect/go.sh

Once you understand what this is doing, it is an extremly powerful tool to manage any linux based system.  Combine that with your scripting or command line knowledge of 
VMware ESX full and you can do some really intersting things.

Enjoy!

