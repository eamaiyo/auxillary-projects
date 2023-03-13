## Documentation for Aux Project 1
## SHELL SCRIPTING - aws virtual server

## STEP 1 — Onboard New Users to a remote Server

-- Create our shell script that reads a csv file.
-- Then by ssh into my remote server labelled 'Aux-Project 1' from my vscode terminal in windows machine 

`vi onboard.sh`--(Copied and paste my onboard script on how to execute  into onboard-1.sh file)
![nboardUsers-Onboard.shFile](./ImageAux-1/OnboardUsers-Onboard.shFile-1.PNG)  

`mkdir shell-1 && cd shell-1 && touch id_rsa id_rsa.pub names.csv`--(running command to create shell-1 directory in ubuntu home. In shell-1 directory created id_rsa id_rsa.pub names.csv files)
![OnboardUsers-Shell-1Dir](./ImageAux-1/OnboardUsers-Shell-1Dir-2.PNG)

`vi id_rsa`--(Using the vi text editor in the shell-1 directory in ubuntu home to Populate id_rsa file with the private key pair)
![OnboardUsers-PrivateKey](ImageAux-1/OnboardUsers-PrivateKey-3.PNG)

`vi id_rsa.pub`--(Using the vi text editor in the shell-1 directory in ubuntu home to Populate id_rsa file with the public key)
![OnboardUsers-PublicKey](./ImageAux-1/OnboardUsers-PublicKey-4.PNG)

`vi names.csv`--(Using the vi text editor in the shell-1 directory in ubuntu home to Populate names.csv file with new user first names)
![OnboardUsers-names.csvFile](./ImageAux-1/OnboardUsers-names.csvFile-5.PNG)

`sudo groupadd developers`--(In Shell-1 directory in ubuntu home create a developers group)
![OnboardUsers-CreateGroup](./ImageAux-1/OnboardUsers-CreateGroup-6.PNG)

`sudo chmod tx onboard.sh`--(In Shell-1 directory in ubuntu home create a developers group)
![OnboardUsers-CreateGroup](./ImageAux-1/OnboardUsers-CreateGroup-6.PNG)

`mv onboard-1.sh /home/ubuntu/shell-1/`--(Moving Onboard-1.sh script file to In Shell-1 directory in ubuntu home, we ran "ls -l" to view more properties for onboard for example the Readwrite permission)
![OnboardUsers-MoveOnboard](./ImageAux-1/OnboardUsers-MoveOnboard-7.PNG)

`sudo chmod +x onboard-1.sh `--(Ran command to ensure onboard-1.sh file is executeable)
![OnboardUsers-ExecuteOnboard-1.shFile](./ImageAux-1/OnboardUsers-ExecuteOnboard-1.shFile-8.PNG)

`./onboard-1.sh `--(Ran command to test onboard-1.sh file without sudo privileges)
![OnboardUsers-TestOnboard-1.shFile](./ImageAux-1/OnboardUsers-TestOnboard-1.shFile-9.PNG)

`sudo su`; `./onboard-1.sh`--(Ran command as a superuser privileges before testing onboard-1.sh file)
![OnboardUsers-Run-SuperUser-Onboard-1.shFile](./ImageAux-1/OnboardUsers-Run-SuperUser-Onboard-1.shFile-10.PNG)

`ls -l /home`--(confirming list of users created in remote server)
![OnboardUsers-User-Created](./ImageAux-1/OnboardUsers-User-Created-11.PNG)

`getent group developers`--(confirming developers group created in remote server, displaying group id in output)
![OnboardUsers-Confirm-DevelopersCreated](./ImageAux-1/OnboardUsers-Confirm-DevelopersCreated-12.PNG)

`cat /etc/passwd`--(Confirming password in etc directory in shell-1 in ubuntu home. we can see users created with group id attached)
![OnboardUsers-CheckingPasswd](./ImageAux-1/OnboardUsers-CheckingPasswd-13.PNG)

`cat /etc/passwd`--(Confirming password in etc directory in shell-1 in ubuntu home. we can see users created with group id attached)
![OnboardUsers-CheckingPasswd](./ImageAux-1/OnboardUsers-CheckingPasswd-13.PNG)

`cat /etc/passwd | awk -F':' '{ Print $1}' | xargs -n1 groups`--(AWK command is used for filtering and analysing text. Tt shows text in  a more readable format)
![OnboardUsers-awkCommand-Passwd](./ImageAux-1/OnboardUsers-awkCommand-Passwd-14.PNG)

## Task - Test users randomly to ensure connectivity to server using private key.

`cat id_rsa.pub`--(In terminal-1 run command to spit out public key saved in id_rsa.pub configured to server dovument out of  '/home/ubuntu/shell-1' directory in onboard-1.sh)
![OnboardUsers-id_rsa.pub](./ImageAux-1/OnboardUsers-id_rsa.pub-15a.PNG)

`vi aux-project.pem`--(open a new terminal-2 and Create a aux-project.pem key file . Copy and paste private ssh key to connect to remote server as a developer listed in develpers' group)
![OnboardUsers-Aux-Project.pem-PrivateKey](./ImageAux-1/OnboardUsers-Aux-Project.pem-PrivateKey-15.PNG)

`ls /home/`--(In terminal-1 displays users in develpers group that can connect to remote server)
![OnboardUsers-listDeveloper-HomeDir](./ImageAux-1/OnboardUsers-listDeveloper-HomeDir-16.PNG)

`ssh -i aux-project.pem Bonny@18.207.110.26`--(In terminal-2 test random user to connect to remote server. using private key pair (aux-project-pem) and remote server public IP address - copy from asw console. Output:WARNING: UNPROTECTED PRIVATE KEY FILE!)
![OnboardUsers-TestConnectionRemotely](./ImageAux-1/OnboardUsers-TestConnectionRemotely-17.PNG)

`sudo chmod 600 aux-project.pem`--(In terminal-2 set protection for our private key "aux-project.pem")
![OnboardUsers-Protect-AuxProject.pem](./ImageAux-1/OnboardUsers-Protect-AuxProject.pem-18.PNG)

`ssh -i aux-project.pem Bonny@18.207.110.26`--(In terminal-2 second attention to connectto remote server as a user whilst we set protection for our private key "aux-project.pem" )
![OnboardUsers-Attempt2-TestConnection](./ImageAux-1/OnboardUsers-Attempt2-TestConnection-19.PNG)

`sudo apt update`--(In terminal-2 second connection established to remote server)
![OnboardUsers-TestConnection-Successful](./ImageAux-1/OnboardUsers-TestConnection-Successful-20.PNG)


