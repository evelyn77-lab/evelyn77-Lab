## Lab 02

- Name: Evelyn
- Email: enoma.5@wright.edu

## Part 1 Answers

Full / absolute path to your private key file: /Users/osarumwenseenoma/labsuser.pem

Command to SSH to AWS instance:
```
[ssh -i labsuser.pem ubuntu@34.227.129.160]
```

## Part 2 Answers

1. `chmod u+r bubbles.txt`
    - Means: This command adds the read premission to the file owner of bubbles.txt.
    - Assessment: It's a good command to use if the user was previously denied access.
2. `chmod u=rw,g-w,o-x banana.cabana`
    - Means: This command sets the file user's premission to read and write only, it removes the write premission from the file group, and lastly removes the execute premission from other users.
    - Assessment: Not recommended because if the original setting allowed all users access to all premissions, then the file onwer can only read and write, the file group members can read and execute the file, while other users can read and write the file. This is bad because other user can literaly be anyone and if anyone can read AND edit a private file that's going to cause problems.
3. `chmod a=w snow.md`
    - Means: This command sets everyone on the system's permission of the show.md file to write only.
    - Assessment: This is generally not recommended as that would mean everyone that can access your system(computer) will be able to edit the file making it unsafe.
4. `chmod 751 program`
    - Means: This command gives the user all premissions (Read, Write and execute) over the directory(Program), it gives the directory group the read and execute premissions only, while it gives other users execute permissions only.
    - Assessment: This command is not necessarily ideal, usually if a user is given write premission, they are also given read permissions in order to see what they are writing to execute it. For this command however, the group directory users can't see anything in the directory, therefore they can't execute or even write anything. Additionally, it's not safe to give anyone that can access your computer or server the permission to execute a file in a secure directory.
5. `chmod -R ug+w share`
    - Means: This command adds the write premission to the permissions of the file owner, the group file users and all other users in the share directory.
    - Assessment: This command is not recommended as it gives every user in the share directory the ablity to edit a file in the share directory. It's not safe, as anyone that can access your system/server can change files that don't need changing.

## Part 3 Answers

1. Command to create new user: I used "sudo useradd MAnthony" to create a user named Mary Anthony 
2. Path to new user's home directory: This is Mary Anthony's directory path /Home/MAnthony
3. Evaluate if `ubuntu` can add files to new user's home directory: Yes ubuntu can add files to Mary Anthony's directory, ubuntu would just need to add sudo in front of the command, like this: sudo touch /home/MAnthony/tester.txt
4. Command to switch to new user: I used the command " su MAnthony" to switch users.
5. Command(s) to go to new user's home directory: I used the command "cd /home/MAnthony" to go to the user's home directory
6. Evaluate if new user can add files to user's home directory: Mary Anthony cannot create a new file in her home directory, I tried using this command "touch NewFile" but my permission was denied.
7. Command to return to `ubuntu` user: I used the command "cd ~" to switch back to ubuntu.
8. Command to return to `ubuntu` home directory: I used the command "cd /home/ubuntu" to go back to ubuntu's home directory.

## Part 4 Answers

1. Command(s) to create group named `squad` and add members: I used the command 'sudo groupadd squad' to create the group squad. 
2. Command(s) to add `ubuntu` & user to group `squad`: I used the command 'sudo gpasswd -a MAnthony squad' and 'sudo gpasswd -a ubuntu squad' to add ubuntu and Mary Anthony to the group, squad.
3. Command(s) to allow `squad` to view the `ubuntu` user's home directory contents: I used the command 'chmod -R g=r /home/ubuntu' to set the premissions of the members of the squad group to view only on ubuntu's user home directory contents.
4. Command(s) to modify `share` to have group ownership of `squad`: First I created a share directory in ubuntu with the command 'mkdir share.' Then I used the command 'sudo chgrp -R squad /home/ubuntu/share' to make squad the group for the folder. After that I used the command 'sudo chmod -R 770 /home/ubuntu/share' to give the owner(ubuntu) and the group members of squad full permissions. Lastly, I used the command 'sudo chmod g+s /home/ubuntu/share' to ensure that all new files will belong to the group members of squad.
5. Describe your tests and commands with the user account: It did not work the first time, however I realized that I gave squad write premissions not read, I changed that and it still did not work, I asked chatGPT why this is and it told me that I needed to give the group users execute premissions. I did and it still did not work.
6. Describe the full set of permissions / settings that enable the user to make edits: I woas not able to go into the share directory.

## Part 5 Answers

For each, write the command used or answer the question posed.

1. Command(s) to make file using `sudo`: I used the command 'sudo touch madewithsudo.txt' to make the text file.
2. Command(s) to make file with `root`: I used the command 'sudo -i' to switch users to the root user and then used the command 'touch madewithroot.txt' to make the text file.
3. Describe / compare ownership and permissions of files: For the ubuntu user I had to use sudo to make the file, however, for the root user I was just able to use the regular command without the sudo override.
4. Which account can do what actions? (Type Y or N in columns)

Contents inside of `share`
| Account   | Can View  | Can Edit  | Can Change Permissions    |
| ---       | ---       | ---       | ---                       |
| `root`    |     Y      |     Y      |           Y                |
| `ubuntu`  |     Y      |      Y     |            Y               |
| `BOB`     |    N(but it's supposed too)     |    N(it's supposed too)    |   N(it's supposed to)       |

`madewithsudo.txt`
| Account   | Can View  | Can Edit  | Can Change Permissions    |
| ---       | ---       | ---       | ---                       |
| `root`    |     Y      |      Y     |           Y                |
| `ubuntu`  |     Y      |      Y     |           Y                |
| `BOB`     |     N      |      N     |            N               |

5. Command(s) to modify permissions: 
6. How to give user account `sudo`: I didn't do this but, the professor talked about it in class. Ok so first you have to use the command 'sudo -i' to switch to root user then you have to use the command 'usermod -aG sudo username' to add which ever user to the sudo group. After all that you have to make the user logout and log back in to test if it worked!

## Citations

For this lab I enlisted the help of chatGPT, Google and Redhat. Also the TA's helped alot with most of the questions I had.
