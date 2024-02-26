## LEVEL-0
using SSH login into the bandit server through terminal.<br>
## LEVEL 0-1
1.The password for the next level is stored in a file called readme located in the home directory.<br>
2.Using ls and cat i got the password in readme file.<br>
## LEVEL 1-2
1.The password for the next level is stored in a file called - located in the home directory.<br>
2.Using cat we can open ,but in this way -- cat ./-<br>
## LEVEL 2-3
1.The password for the next level is stored in a file called spaces in this filename located in the home directory<br>
2.we can wrap the spaces in name of the file using doulbe codes<br>
EX: cat   "spaces in the file name"<br>
## LEVEL 3-4
1.The password for the next level is stored in a hidden file in the inhere directory.<br>
2.using cd inhere and ls -a we can find the name of hidden file, after that we use cat to see password.<br>
## LEVEL 4-5
1.The password for the next level is stored in the only human-readable file in the inhere directory. <br>
2.First we need to identify file type whether it is humna readble or not so, we use file  ./*   (file name starts with "-")<br>
3.Then we use cat  ./-filename <br>
## LEVEL 5-6
1.The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
<br>
human-readable, 
1033 bytes in size, 
not executable.
<br>
2.we will use find command in this format ---  find . -type f -size 1033c ! -executable -exec file {} + | grep ASCII <br>
## LEVEL 6-7
1.The password for the next level is stored somewhere on the server and has all of the following properties:
<br>
owned by user bandit7,
owned by group bandit6,
33 bytes in size.<br>

2.so first we need to find the path of the file over the bandit server<br>

3.according to my research we can use find command and we need the user and group where the files are, we need to specify the size particularly<br>

4.find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null<br>

5.by given info we can get user is bandit7 and group is bandit6 and size is 33bytes and we need file so type is -f.<br>

6.we use 2>/dev/null <br>This prevents error messages from being displayed on the screen.<br>
## LEVEL 7-8
1.The password for the next level is stored in the file data.txt next to the word millionth.<br>
2.we acn use cat and grep to find password :<br>
cat data.txt  | grep "millionth"<br>
## LEVEL 8-9
1.The password for the next level is stored in the file data.txt and is the only line of text that occurs only once<br>
2.according to given info the password is unique so we can use "sort" command to sort them to small n.o of lines<br>
3.but we need a unique one , so for that the command is "sort FILEname | uniq -u"<br>
## LEVEL 9-10
1.The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.<br>
2.we can use "strings" command to print printable stings on the terminal screen and by the == we can use "grep ===="<br>
## LEVEL 10-11
1.The password for the next level is stored in the file data.txt, which contains base64 encoded data<br>
2.we can use cat & base64 -d commands combined to display the decrypted text<br>
## LEVEL 11-12
1.The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions<br>
2. ROT13 ENCRYPTION AND DECRYPTION METHODS USIN "tr command"<br>
3.we can decrypt by "tr '[A-Za-z]' '[N-ZA-Mn-za-m]' " <br>
## LEVEL 12-13
1.The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.<br>
2.For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv.<br>
3.we will do reverse hexdump & save that in a new file using command  xxd -r  <input_file> <output_file> .<br>
4.after that we will do repetadely decompression of new file with gzip -d and bz2 -d commands ,tar -xf.<br>
## LEVEL 13-14
1.he password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14<BR>
2.we can copy ssh_private key to main host user and we use this command with saved private key in host<br>
sudo ssh -i "SAVED FILE_NAME" bandit14@bandit.labs.overthewire.org -p2220  <br>
3.now we can go to bandit_pass and we can save level 14 password.<br>
## LEVEL 14-15
1.The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.<br>
2.we can use netcat command to get next level password by entering current level password<br>
nc localhost  30000 .<br>
## LEVEL 15-16
1.The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.<br>
2.we can do that by entering current password and we can get next level password by this command<br>
openssl s_client -connect localhost:30001   .<br>
## LEVEL 16-17
1.The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000.<br>
2.we check which ports are active by the command "netstat -lntup",but we need to with state of service so we can use another command: <br>
"nmap -sV localhost -p 31000-32000"<br>
3.Then we can use command "openssl s_client -connect localhost:31790"
4.then we will obtain private-RSA key,then we can save the rsa key in host machine with a filename and then we can use the below command:<br>
"sudo ssh -i lok17 bandit17@bandit.labs.overthewire.org -p 2220"<br>
## LEVEL 17-18
1.There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new<br>
2.we can use the command to find the password "diff passwords.old passwords.new",then the diff line of password will be given on second line.<br>
3.after login to server bnadit18 ,we will see "Byebye !".<br>
## LEVEL 18-19
1.The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.<br>
2.so,Instead of logging into the machine with SSH, we execute a command through SSH instead as folow:<br>
ssh bandit18@bandit.labs.overthewire.org -p 2220 ls ---to know whether readme file is present or not
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme --to open the readme file for password
## LEVEL 19-20
1.To gain access to the next level, you should use the setuid binary in the homedirectory<br>
2."ls -la" to check bandit20 uid file owner,we can see permissions like "-rwsr-x---" so the group is bandit 19 it can excute but cannot read it<br>
3.so we will exicute but we will not read through file owner named as bandit20 through below commands : <br>
"./bandit20-do ls /etc/bandit_pass"<br>
"./bandit20-do cat /etc/bandit_pass/bandit20"
4.now we can get the password for bandit20.<br>
## LEVEL 20-21
1.
