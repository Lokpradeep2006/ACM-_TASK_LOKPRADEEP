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
1.
