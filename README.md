# nginxWatcher
A program running on linux that lets you monitor any ddns change and restart nginx reverse proxy when a change is detected.
# why
Nginx fails to work as a reverse program when its ddnsed backend has been updated. This program fixes the problem
# compile & install
"# g++ main.cpp && cp a.out /bin/nginxwatcher"
and then auto start this program when your machine boots by using your favorite text editor, adding "/bin/nginxwatcher" to /etc/rc.local and run "chmod +Xx /etc/rc.local" to give it the permission to run itself.
