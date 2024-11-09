Switch to root à su -
listing with time reverse à ls  -ltr
To find files or directories à Use command find or locate (if locate command is not found, then as root, run “updated”). This requires “mlocate” package. To make sure “mlocate” is sintalled, to check use “rpm -qa | grep mlocate”.
Create multiple files à touch abcd{1..9}-xyz.txt
Wildcard à *, ? , []
Hard Link and Soft Link à command is ln -s
File permissions are of the order à User, Group and Others
ACLs can also be used to provide access to files to any user. Commands are getfacl and setfacl. ACL permission prohibits to delete a file even if write access is provided.
Route errors à ls -l /root 2> errorfile
“tee” command à used to store and view the output at the same time. Ex: à echo “abcd” | tee testfile. Use -a flag to append like “tee -a”
Using “cut” command à cut -c1 <file name> gives the first character of each line in the file. To cut base on fields / columns, use “cut -d: -f 6 <filename>”
Using “awk” for text extraction à awk ‘{print $1}’ filename. It can even search and print “awk ‘/Jerry/ {print}’ filename”. We can use awk to display fields based on delimiter. It can even do string replace like “awk ‘{$2=”Adam”; print $0}’”. Also get lines that have column length greater than 15 characters. Can also use IF condition to search.
Using “grep” for search à use “grep -c” to count the matches. -n gives matches and line numbers. -v for inverse of keyword search. You can use egrep too.
Using “sort” & “uniq” à by column “sort -k2 filename”. Always run sort followed by uniq. “uniq -c” will give the count. “-d” will give only the dups.
Using “wc” à gives new line count, word count and bytes.
Combine and Split files using cat and split command.
Using “sed” for string substitution à it’s a powerful command. Always search on how to do something with sed command in google.
/etc/login.defs file has default for user password aging control parameters. This is used in “chage” command.
Monitor Commands à who, last, w, finger, id
System Commands à which, cal, bc
Process Commands à run “ps -ef” its preferred.
Use “nohup process & “ to continue running the process even after existing the terminal.
“jobs” command to view all jobs. Send a process to background using Ctrl + Z.
System Monitoring commands à df -h (disk info), dmesg (system errors), iostat, netstat -rnv, free, cat /proc/cpuinfo, cat /proc/meminfo
/var/log/secure will have all info about user logins.
/var/log/messages are machines trace logs.
“dmidecode” pr “uname -a” will give you system information
Ctrl + d à Suspend a Program
Ctrl + u à erase whatever you have typed
You can use “script” command to record everything that is being done on the terminal.
SOS report is provided to RedHat for diagnostics
Set special permission on executables (C or C++) using setuid, setgid, sticky bit. Ex: chmod u+s xyz.sh
Use backticks or tilde to evaluate a command inside shell script
Use “ethtool” command to get info on the NICs or Interfaces. We can combine two NICs into one using NIC Bonding.
Use “wget” or “curl -O” to download the file
User “rsync” for remote synchronization
You can create a local repository and have it available to yum. The local repository can be created from DVD when you don’t have access to internet. To list all repos, run command “yum repolist all”
Using “which” command we can know which script is being used but to find out which package it belongs to, use command “rpm -qf /usr/bin/pwd”
“yum history undo #” to rollback the previous update
For DNS lookup, use nslookup or dig.
“timedatectl” is a new utility replacing date
“rsysylog” is a central logger in linux
Check on listening ports use command “netstat -tunlp” 
You can use command ssh-keygen to generate keys and then use ssh-copy-id to copy of the public key to server to which we will connect. The public key will be written to authorized_keys files automatically.
Cockpit is used for web-based linux administration. Runs on port 9090.
With firewalld, we can add 3rd party service too.
Tuned is for tuning system performance. There are pre-defined profiles.
Podman is RedHat’s version of Docker.
Systems is running slow troubleshooting. Check disk space, processing, disk issues, networking, system uptime, logs, check hardware status, use other tools.

Ubuntu is Linux Distribution
APT - Advanced Package Tool like pip or conda
GNOME Desktop and Unity on top of that for Ubuntu
Supported by Canonical and Ubuntu Community
LTS version is always more state release. done during April by Canconical
LibreOffice is from OpenOffice. doc as .odt, ppt as odp and visio as .ods
gedit is the text editor
 
CLI
ls -1F ./728391/ | grep -vE /$ | wc –l à get only # of files within a directory
ls -d */ | wc –l à count only directories
sudo tar cvzf workspace_samp.tar.gz workspace_samp/
du -sh directory/ - get size of a directory
OS details --> cat /etc/*release
sudo apt-get update -- to get software updates
sudo apt-get upgrade -- to install them 
whoami - gives user. 
w - gives summary of system activity 
uname -a -- display system information : -m provided 64 or 32 bit
hostname
locate "*mongo*" --> to locate files in directory matching this pattern
Till symbol in command line shows that you are in root directory
pwd - working directory full path
ls -l - long list
ls -l /bin - see the listing of another directory from home directory
ls -l /bin/p* - see the listing of another directory starting with p from home directory
man ls - displays manual
long list order
1 >> - : file or d : directory
2 to 4 >> r or w or x (read / write / execute) premissions for owner of the file
5 to 7 >> r / w / x permission for the group the file belongs to
8 to 10 >> r / w / x for any other user who is not the owner nor present in the group
followed by a number mentions links to the file or file references
followed by name of the owner
followed by name of the group
followed by file size in bytes
followed by modified timestamp
followed by file name
 
ls -l / - lists file from root directory
ls -a  - shows hidden files too
touch /var/a.txt - to create a file or modify the timestamp of the existing file. permission denied
use sudo prefixed to command to run it with root privileges. like sudo touch /var/a.txt.  It will ask for password. it works now. no permission denied error.
echo "line 1" - to echo the text to prompt
echo  "line 1" >> /var/a.txt - to write it to a file instead of prompt
to evelate to root directoty, use sudo su. it might ask for password if not provided recently. to revert back use su <username>. sudo -i does the same thing.
cat /var/a.txt - displays the file content from top. tac displays from bottom.
tail /var/a.txt - to show the few last lines of the file
tail -f ip.txt will continue to show new line of the file when added. -f means follow
less /var/a.txt - shows scrollable page view like "| more"
chmod a+w /var/a.txt - change permission on file to have all user have write permissions. + is to denote that you are adding permissions. Use - for removing permissions. use u for user. Can also do chgmod 700 /user/hue/a.txt
chown <owner name> <file name>- to change the owner . chgrp works similar
find <pattern> - locate files by pattern.
find <pattern> -type f - locate only files type
 
 
command piping or chaining can be done using pipe command. Ex: sudo find /var/log/syslog* -print0 | xargs -0 sudo chgmod a+r . print0 formats the output for the next command neatly. xargs takes the input for each item and execute the sudo chgmod command. xargs does not need formatted output and thus we use print0 option. -0 says there is only one input field.
 
archived files will be of extension gz. to unzip use gunzip
 
grep is to find matching line in the command input. Ex: find /var/log/syslog* -type f -print0 | xargs -0 cat | grep "NetworkManager.*warn"
grep -c 'NetworkManager.*warn' - give the count
to execute ifconfig, need to install net-tools using apt
ifconfig | grep "inet" | head -n 1 - head will give only the first line
to cut only the ip address, use cut like below
ifconfig | grep "inet" | head -n 1 | cut -d ":" -f 2 ----- -f will find the 2nd match and return. Not sure what -d do
 
scripting commands
run the commands using a script 
#!/bin/bash tells to run in bash shell in ubuntu. this is usually the first line
However, to execute the .sh file, need execute permission, so that has to be done manually first.
Do while loop in scripts.
 
 
cron is used to schedule a job in background. Called as cron jobs irrespective of whether user is logged in or not. but as long as the machine is on.
start cron by giving command crontab -e.  learn more about this
 
cp -R * <destination> - recursive copy all files to destination
ln -s <directory name> - creates symbolic links 
rm - remove file directory
service <servicename> restart - to restart a service
 
connect to server using ssh, ex: ssh servername
authentication can be done using pair of keys (public and private) or userid/password. Keys are preferred.
generate keys using command, ssh-keygen -b 2048 -t rsa -C elton@siceyed.com, 2048 is key length, rsa is encryption type and -C is for comment
keys can also be protected via a password
the keys are stored in .ssh folder, and file id_rsa.pub
to copy key into the server use, ssh-copy-id -i .ssh/id_rsa.pub elton@172.312.21.12 (ip is the server), send public key to my server. on server, in the .ssh folder there is an authorized_keys file which will contain the key.
 
one way to copy file to ubuntu server is via FTP but its not secure. server needs to have FTP service installed to listen to ftp connections
secure way is to use scp command which is secure copy. ex: scp <local file name> <user@servername>:<path on server>. optionally use -r command to recursively copy
 
if we are using a connection multiple times, then we can save the connection in .ssh/config file as below
Host azure
HostName  psod-ubuntu.cloudapp.net
User  azureuser
IdentityFile
~/.ssh/id_rsa
 
The connect just by saying, ssh azure. Also it can referenced as such in above scp command too.
 
mkdir -p - make directory command. -p says make parent directory too if not exists
 
Canonical has a s/w Juju to manager cloud server, so we need not manually login into the servers.
Juju is moving towards using docker instead of virutal servers so that it can be provisions quickly
 
Physical consoles are directly on the server / machine
Psuedo consoles are ones which are access via remote. Mostly this is what is used.
remote access might be via telnet (tcp 23) (mostly on windows, unencrypted) or ssh (port 22 mostly on unix and linux systems, encrypted)
bash shell is the most common one and bash history to recall commands.
 
 
physical console has 6 consoles. tt1 to tty 6 acessed via ctrl + alt + f1 to f6
in tty consoles, login as root. Root password can be set using sudo passwd root.
who (or w) command will disaply who is logged in. however, w is more verbose
tty command says what terminal name
to logoff, user exit or logout or Ctrl + D
to switch tty's on the same console, use chvt 2 or chvt 3 (change virtual terminal)
 
Pseudo console
Ctrl + L will clear the screen.
tty command displays /dev/pts/0 which means its a pseudo terminal
echoing $SSH_CLIENT $SSH_CONNECTION $SSH_TTY gives information about the SSH connection. its stored these variables denoted by $.
We can change shells to zsh for example. Not much required to know.
all command history is stored in ~/.bash_history file. Use ! to run last command with that letter. Ex: !l will run ls if its was the last command starting with l.
use !cat to display command history
history -c clears it, -r reads it, -w writes it
!$ represent last argument. Ex: mkdir dir1 then use cd !$ which will be same as cd dir1
Use !? to call command which matches string from anywhere. ex: !?etc will return last command where etc was anywhere and notjust beginning.
Ctrl + r to reverse search the commands. Enter to run the command or Esc to edit the command.
command history to show a history of the commands but which is not saved in bash history file. history -a will write it to bash history.
history is usually written during logout login procedure
setting variable HISTCONTROL=erasedups, will not write duplicate commands to history file
 
analyzing files
cat and tac commands
cat -vet - to display new line characters too
chmod +x <shell script> to make it executable
dos2unix <filename> will convert windows file to unix by correcting new characters
linux running configuration is under the /proc folder. 
head -n 1 <file name> - first 1 file. default is 10 lines
tail -n 1 <file name> - last 1 file. default is 10 lines
tail or head -f means follow and it will keep of printing last 10 or n lines. Like if restarting a web service and looking at log file while it restarts.
wc -l <filename> - get # of lines of a file
and then more !$ to view the file. enter it go line by line. space to go page by page. hit q to quit this.
and less allows to move forward and backword, goto a line or search for text. use page up and down. then 10g to goto 10th line of line. to search, use /<text> and n for got next .hit q to quit this. 
use more and less commands with pipe to work efficiently.
cut -f1,3 -d":" /etc/passwd - field 1 to field 3 and delimited is :
sort -r is reserve sort. -k for column -t is demilitter. --> sort -k4 -t":" /etc/passwd. -u for unqiue, -n is numeric sort.
 
 
cp - copy -i to prompt/interactive mode -R for recursion -a for ownership maintains when copied. 
mv - move or rename. move to previous directory. try "mv a.txt .."
rm or rmdir - delete. options -rf recursive force. rmdir to delete empty directory. rm -rf to delete directory and content.
"readlink" command to view where a link is referring to.
ls -ld <dir name> to view directory information rather the contents of the file
ls -F <dirname> - append indicator to entires
ls -lt will give long listing with time.
alias ls='ls --color=auto'. so when you use ls. it will by default include the color command. alias will list all aliases. to run ls without the alias, use \ls (i.e. use backslash)
a directory has two name linked to the file. The name itself and then the . (dot)
 
fdisk -l will give disk names. 
dd - image copy. command is dd if=/dev/mmcblk0 of=mbr count=1 bs=512. this means input file from boot disk written to local output file mbr and do once copy of block size 512.
 
rsync - keeing in sync. -v for verbose
rsync -av man1/ man2/ will copy contents from man1 to man2. if just man1 is given. it will copy the directoy and also the contents to man2. 
Try rsync again and nothing will copied. because its in sync. to sync the deletions use option --delete
 
add a user using "useradd -m bob". similarly, remove user by doing "userdel -r bob"
 
tar - archive (tar is tape archive)
tar -cvf etc.tar - c for create, v is verbose, f for file
ls -lh etc.tar - gives size in human readable format.
du is disk usage. du -sh . s for summary
to zip it use, tar -czvf etc.tgz
put time in fromt of the tar command and get time taken to archive and zip it.
use "file etc.tgz" to find out what type of file it is.
to look inside the zip file, then use tar -tzf . -t is for test
to unzip or to expand the file, use tar -xzvf etc.tgz
 
find - search
find . -newer file1 or find -newer file1 - this will find all files which are newer than file1
by default, the outcome is to print it but if we have to delete files?? then use find -newer file1 -type f -delete.
to search for pdf, find /usr/share -name '*.pdf'. this would be recursive search. But if we give option as -maxdepth 1, then it will look only in the current folder.
to execute on every hit, then use -exec <command> {} \; ex: -exec ls -lh {} \; the {} is a placeholder for the file name.
to search based on size, use option -size +138k. this means find for files which are greater than 138 kb.
 
 
file operations
> write to a file creating new or overwrite. or 1> file1.txt. both are same. 1 says output one which is standard output as opposed to standard error. 
standard error like ls /etc 2> file1.txt. just take the errors.
above combined as ls /etc > file.txt 2>&1. both standard output and errors are going to file.txt
ls /home /etc should listing from both the directories.
>> append to a file. 1>> file1.txt 2>> file_errors.txt or ls /home /hime 2>out.txt >&2 which directs all output and error to the same file
user /dev/null to send no-where. discard the data.
set -o shows all the shell options
noclobber which will prevent overwrite files, set -o noclobber. turn in clobber by using set +C or set +o noclobber
to ignore clobber use >|. Ex: ls /home >| out.txt. This will overwrite the file. This can be set during login script as once logged off this option goes off.
read from file <
df command displays disk free space.
to mail -> mail -s df user < df.txt where -s is subject. then type mail to show the mail message itself.
 
pipelines |
named pipe. create with mkfifo. with named pipe we can save pipe into a file and can be used for inter channel communication.
mkfifo mypipe, ls /etc > mypipe, wc -l < mypipe
use command "tee", output to both on screen and file.
"which tee" will show where tee is located and command is ls | tee myfile. output gets displayed in screen as well in myfile.
 
process management
all commands comes from package "procps" family.
ubuntu is debian based. so use dpkg.
"which ps" - is present in /bin/ps. "which" tells where the command resides.
dpkg -S /bin/ps -- this tells from which package ps comes from. which is procps. same command can be written as dpkg -S $(which ps)
dpkg -L procps -- display contents of the package
command "uptime" - shows load averages. data comes from /proc/uptime and /proc/loadavg
cat /proc/uptime shows uptime is seconds and then seconds the system was idle.
cat /proc/loadavg also shows # of process running (will be 1 if its single core) / total number of active process. Then the number followed is the last process ID which was issued.
ps command - list all process running. ps –l for long listing. ps -f is full listing including users. ps -e shows all processes. Ps (with no switch) will show just from current shell / session.
bg command will start the job or process in background which has + sign against it.
to start a process directly in background suffix the command with &. Ex: sleep 20 &
fg <job id> - to start the job in foreground. ^Z will pause the command. and giving fg 1 will bring that job to foreground. If you want to continue in background give bg <job id>. Can also use fg %1
send those jobs to background that does not need input else it will mess up with command line. Prompts for user input will not be shown properly.
this allows running multiple jobs in single console.
jobs - lists running jobs
kill - to kill a process id.
kill -l lists all kill all signals. some app does not respond to terminate. then do kill -9 <process id>. -9 will force terminate. Hard kill is done by giving –KILL switch
pgrep <process name> - instead of doing ps -ef | grep bash we can do pgrep bash will list the process id.
pkill – search a command and kill it. Ex: pkill sleep. Try to avoid pkill as it will search and kill everything that matches.
killall - kill a group of process. killall sleep
top - does kill, renice. sort and display. its an interactive session.
top -n 2 -d 3 - run two times with a delay of 3 seconds.
Hit u and enter the user name to show processes under that user. Use k for kill a process id
in top interactive, press f to show the list of fields, to select / de-select fields, hit space and then to select field to sort on, move to the field using arrow and hit "S"
in top interactive, press r to do renice, press k to kill
 
searching files regular expression
we can use grep or sed
grep Server /etc -> case sensitive --> use switch -i for case in-sensitive
search for word, \b to represent word boundary. like grep '\bserver\b' /etc/a.conf
for beginning of line use ^ --> grep '^server\b' /etc/a.conf
-v swtich reverse the switch like flip in mainframe
"-e" allows to give more than one expression. grep -ve '^#' -ve '^$' filename. ^# removes comments. ^$ removes blank lines.
command sed is used to do an inline edit of the file
sed -i '/^#/d;/^$/d' filename --> -i says inplace, remove it to just display and edit the file. expressions are seperated by semicolon. /d says delete.
use egrep or switch -E if we have to use more complex regular expression.
"[A-Z] {1,2}" looking for A to Z ocurrence 1 or 2 similarly [0-9] {1,2}
[A-Z]? makes A to Z as options
then to identify space, give \s
 
VI editor
: goto last line then q to exit or wq (or x) to save and exit. use q! to quit without making any changes.
to make changes, hit "i" for insert. make changes, then pres esc :wq (orx) to quit
to go end of line during insert use "A". to goto first line use "I". "o" to add a new line below the cursor. "O" to add line above the cursor. "x" to delete current letter. 3x will delete 3 characters from cursor position
"dw" will delete the work. "3dw" will delete 3 words. "u" for undo.
navigation - 7G to goto 7th line. move forward one word in "w" and back "b". "^" start of line. "$" goto end of line. 1G will take to beginning of file and G will take to end. 5w will jump 5 words. 3b will jump back 3 words.
vi +127 file name will take for 127th line
vi +/DocuemntRoot fielanme --> goto to line where doucumentroot is present.
:set number or nonumber to show/unshow line numbers. or use set invnumber which will acts toggle.
:r /etc/hosts --> this will read the hsots file into the next line of the cursor into the exiting VI editor.
:r!id --> this will write the output of command id to the VI
:3,7w ip.txt --> will write 3 to 7 lines from VI into a new file.
search and replace --
:%s/abc/def/ --> % is whole document. s is for search, followed by find and replace string. "n" to goto next. "N" will take back
for search use :/abc --> "n" to goto next.  "N" will take back
range for line is given as :1,20s/IANA/cabbage --> 1 to lines 20 search and replace
suppose we want to ident lines use this. :14,20s/^/    / 
 
set the line number permananently, vim give option to configure. /etc/vimrc for system wide. ~/.vimrc for personal config.
mapping and setting --> macros by key. nmap <C-N> :set invnumber<CR> --> this mean ctrl N will be set to set invnumber + carriage return command. this and set number nohlsearch will goto to vimrc file.
 
get help using --help, help, -h and man
curl -O <url> to download the file directly.
apt-get to update and compile software
arasan@arasan-VirtualBox$ --> arasan is user, next is server. $ is a normal user. if #, then its super user. ~ means home directory.
/bin contains all items required for system operation like ls, cp etc
/user/bin is important not necessary for system to work. Like program files. apt-get, perl, tree etc
/sbin and /usr/sbin are critical sysadmin utilities. not needed by typical user.-
/etc is system config, password database, config files.
/tmp for temp file and /var contains file which increase overtime like databases, wesbites
/usr/home or /home - all user directories
 
tree - recursive listing of files and folders in tree format.
sudo nano - brings up nano editor
sudo reboot - reboots
chmod u or user, g for group, o for others, a for all. ex: chmod u=rwx, go=r filename
chggrp will allow to change group on files / directories
for transferring files, use scp <source> <destination>. scp bigfile.txt server:~/folder or scp -r folder server:~/folder
 
important files
.bashrc -- loaded during logins and scripts. can run scripts. Don’t have anything in this which will run for long time during startup. Loads when using terminal only.
.bash_profile -- only for interactive bash mode. Like SSH. Bashrc is not loaded here.
.ssh/config
sometime you need to use a source controlled configs, then just create a link of .bashrc to source control file.
 
command env will print all environment variables.
$PS1 – will show what details should be prompt have. You can change it include time as \t
use below on bash terminal
crtl a - move to start
ctrl e - move to end
ctrl w - delete one word
ctrl k - delete everything to right of the cursor
Esc b - to go back one word
Esc f - to go forward one word
 
less a.txt, will show you the contents of the file. When hit v, then the editor opens. The editor to open is defined in the $EDITOR vairable
 
!! - execute previous command.
!$ - last argument of previous command. !:1 for first argument. !:2 for second argument but these are rarely used.
!560 - will execute command from 560th row from history
Ctrl r - search command. enter to execute for Ctrl G to exit
mv readme.{txt,txtile} is same as mv readme.txt readme.textile. only differences were put into a {} list
alias & function - shorten commands 
alias zipr = "zip -r". anytime i use zipr, it will include -r by default.
"cd -" - this will take you to the last used directory.
Use function if there are multiple commands you have to do.$1 first argument. $* all arguments.
use ~/bin directory to store custom scripts which can be called directly from cmd line. have this in source control too.
zshell is a new shell. has little bit of intellisense.
 
bash is good at file manipulation, running programs, processing text
to run a program use ./filename. If you just give filename, it will consider it as command and it will not run.
bash is an interpreter. specify #!/bin/bash at the beginning. This is called a Shebang or hasbang
$* will hold all arguments passed to script from cli
denote variable as $(date) inside shell script. its called command substitution. Ex: count=$(ls -l . | wc -l). Make sure there is no spaces between = else it will fail.
add bind directory to PATH variable to directly call the script from any working directory
to test if a name is a built in. user type <name>
assign variable in command line as a='1' and access as $a
read from cli, use read <variable name>. user -p to show as prompt with label. if not variable is provided, then the reply will be stored in $REPLY. 
-r disallows the need for doing escape. -n tell how many key press is allowed. -s will not echo whatever is being typed.
a vairable boundary is defined under {}. like ~/${topic}notes.txt. here topic is variable.
use escape backslash to print variable with quotes. similary, to group string with spaces into a variable, use "". Example "$filename". dont use single quotes.
use $HOME instead of ~ so that name resolution is correct.
call bash with -x with debugging option. #!/bin/bash -x or set it where you need it. ex: set -x / set +x
if <condition>; then
#code;
else or use elif
#code;
fi
while/until <expression>; do
#code
done
or write the above in a single like
return codes is set using exit(0) or exit(255)
[[ expression ]] --> [[$str]] will return true if str hold any value at all. mak sure there is space between = when comparing, else it will be considered as a single string.
[[ -e $filname ]] --> if file exists, -d if directory exists. ! is not operator. -eq, -ne, -lt, && (and), || (or) etc
$# is the number of arguments a script received. $? is the exit status of the last command. length of a variable user ${#var} like ${#HOME}
if a file is exectable, so when you do ls /bin/<filename>, its suffixed with a *
for complex prints, use printf instead of echo. printf used format string.
if provided more arguments in print than what formatted string used, then it gets into loop printing.
user -v <variable> to put output of printf into a variable.
variable IFS is delimitter. by default it space.
 
whole WHILE statement is a command and can do <"$1"
for var in words; do
;CODE
done
in for loop don't use quote around a variable.
for i in *"$1" --> * is for wild card matching
for ((init;test;update)); do -> this is another for loop in C style
echo mv $1 $2 --> prefixing echo wil tell what hhe command will do, rather than actually executing it.
touch {a..h}.txt -> to create files from a.txt to h.txt
basename command will give file name without extension.
for printf use formatting like --> print "%s\n" "$line" so that if line starts with - then printf does not take it to be an option.
there is CASE statement for multiple matching. matching can be pattern too. otherwise is *)
command groups are seperated by semicolon;
and ifs are sometimes not required --> [[ $# -ne 2 ]] && { echo "test"; exit 1 } --> this itself is a IF statement.
declare variable using switch like --> declar -i p --> will assign integer datatype to variable p. -r means readonly. the variable will be constant. also can initialize a variable here. 
-x is for export variable (similar to export var="value"). This also allows to pass variable between shell scripts when calling. when calling we can pass variable but not vairable attributes. This is why we use export in .bashrc. 
-a is declaring an array. -p will print it when youe declare.
-A will create an associative array
In .bashrc, we can define customer variables which can be used by shell scripts.
$((..)) is substitution and return value. however, ((..)) does the substituion but not return value.
$RANDOM variable return a random value
array length ${#a[@]}, indexes ${!a[@]}. We can define random indices as well without errors.i.e. indexes need not be in sequence
all values in array ${a[*]} or ${a[@]}. define array as a=(1 2 3 a b c)
 
special variables --> $1, $2, $3... $0 holds the name of script it was called. $@ or $*(rarely) mean all vairables. $# give # of arguments passed to script.
shift command moves $2 to $1 and so on. #@ will get decremented by 1. but if shift 3 is given the step happens by 3. however, better option is using getopts command
getopts does options checking also in addition to parms passed. OPTARG contains the value. OPTIND gives the next index getopts is going to handle.
getopts in silent mode start option check with : --> like --> ":b:s:r" this will allow the coder itself to handle errors. Unknown option provided will return ?. and missing argument option provide will return : (colon)
 
functions: can execute like any command. like a shell script inside a shell script
sum() {
return $(( $1 + $2 ))
}
sum 4 5
function will return the value of the last command, so explicit return may not be required.
in a function, variable are global but can be set as local using local or declare 
we can export function using export -f func, similar to vairable, so its avaiable to other sub-processes.
if you have to print a text area (like what cat does), then provide cat input direction with a multiline string. This can be put in a function and called many times. called as "Here documents"
tput variable gives value of how big / lengthy the standard out window is.
when a function call after pipe, <command> | <func>, the bash variable may not get passed to the func. to get around this, save the value to temp file and the direct the temp file as argument to the function.
 
string manipulation
${var#pattern} and ${var##pattern} - remove substring which matches start of string. # shortest match, ## longest match. 
${var%pattern} and ${var%%pattern} - remove substring which matches end of string
pattern can be *, ?, [] etc
search and replace -->  ${var/pattern/string} for first match. ${var//pattern/string} for all matches
set default value if empty or unset --> ${var:-value} or ${var:-value} or ${var:=value} or ${var=value} 
=~ does regular expression matching. similar to "import re" package in python.
ls -- , the -- tells that all options have ended. file names with - can create problems with commands if not given. 
 
use source demo.sh to improt the code into the shell process. similar to refreshing .bashrc
nohup - no hangup. it will run when you log off the session. Ex: nohup dostuff &
nice - will run the script with lower priority
to run command in background --> end with &
exec command to redirect i/o for the whole script. Ex: exec > logfile. so instead of writing output to stdout, it will write to logfile.
schedule scripts --> utilities are AT --> at -f myscript nooon tomorrow or use cron command. in ubuntu, latest one replace all is upstart.
set and shopt for handle bash behaviour. ex: -x, -u, -v, -n etc
