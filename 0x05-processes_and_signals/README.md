0x05. Processes and signals
DevOps            Shell               Bash                  Syscall                   Scripting

Learning Objectives
In this project I have learnt the below lessons:
•	What is a PID
•	What is a process
•	How to find a process’ PID
•	How to kill a process
•	What is a signal
•	What are the 2 signals that cannot be ignored

Tasks
0. What is my PID
Bash script that displays its own PID.

1. List your processes
Bash script that displays a list of currently running processes.
Requirements:
•	Shows all processes, for all users, including those which might not have a TTY
•	Display in a user-oriented format
•	Shows process hierarchy

2. Show your Bash PID
Using the previous exercise command, this Bash script  displays lines containing the bash word, thus allowing me to easily get the PID of my Bash process.
Requirements:
•	cannot use pgrep
•	The third line of your script must be # shellcheck disable=SC2009

3. Show your Bash PID made easy
Bash script that displays the PID, along with the process name, of processes whose name contain the word bash.
Requirements:
•	Cannot use ps
Here we can see that:
•	For the first iteration: bash PID is 4404 and that the 3-show_your_bash_pid_made_easy script PID is 4555
•	For the second iteration: bash PID is 4404 and that the 3-show_your_bash_pid_made_easy script PID is 4557

4. To infinity and beyond
Bash script that displays To infinity and beyond indefinitely.
Requirements:
•	In between each iteration of the loop, add a sleep 2

5. Don't stop me now!
We stopped our 4-to_infinity_and_beyond process using ctrl+c in the previous task, there is actually another way to do this.
Bash script that stops 4-to_infinity_and_beyond process.
Requirements:
•	Used kill

6. Stop me if you can
Bash script that stops 4-to_infinity_and_beyond process.
Requirements:
•	Cannot use kill or killall

7. Highlander
Bash script that displays:
•	To infinity and beyond indefinitely
•	With a sleep 2 in between each iteration
•	I am invincible!!! when receiving a SIGTERM signal
Made a copy of my 6-stop_me_if_you_can script, named it 67-stop_me_if_you_can, that kills the 7-highlander process instead of the 4-to_infinity_and_beyond one.


8. Beheaded process
Bash script that kills the process 7-highlander.

9. Process and PID file
Bash script that:
•	Creates the file /var/run/myscript.pid containing its PID
•	Displays To infinity and beyond indefinitely
•	Displays I hate the kill command when receiving a SIGTERM signal
•	Displays Y U no love me?! when receiving a SIGINT signal
•	Deletes the file /var/run/myscript.pid and terminates itself when receiving a SIGQUIT or SIGTERM signal


10. Manage my process

man: sudo
Programs that are detached from the terminal and running in the background are called daemons or processes, need to be managed. The general minimum set of instructions is: start, restart and stop. The most popular way of doing so on Unix system is to use the init scripts.
a manage_my_process Bash script that:
•	Indefinitely writes I am alive! to the file /tmp/my_process
•	In between every I am alive! message, the program should pause for 2 seconds
Bash (init) script 101-manage_my_process that manages manage_my_process. (both files need to be pushed to git)
Requirements:
•	When passing the argument start:
o	Starts manage_my_process
o	Creates a file containing its PID in /var/run/my_process.pid
o	Displays manage_my_process started
•	When passing the argument stop:
o	Stops manage_my_process
o	Deletes the file /var/run/my_process.pid
o	Displays manage_my_process stopped
•	When passing the argument restart
o	Stops manage_my_process
o	Deletes the file /var/run/my_process.pid
o	Starts manage_my_process
o	Creates a file containing its PID in /var/run/my_process.pid
o	Displays manage_my_process restarted
•	Displays Usage: manage_my_process {start|stop|restart} if any other argument or no argument is passed
Note that this init script is far from being perfect (but good enough for the sake of manipulating process and PID file), for example we do not handle the case where we check if a process is already running when doing ./101-manage_my_process start, in our case it will simply create a new process instead of saying that it is already started.

11. Zombie
A C program that creates 5 zombie processes.
Requirements:
•	For every zombie process created, it displays Zombie process created, PID: ZOMBIE_PID
•	My code uses the Betty style. Its checked using betty-style.pl and betty-doc.pl
•	When my code is done creating the parent process and the zombies, used the function bellow
int infinite_while(void)
{
    while (1)
    {
        sleep(1);
    }
    return (0);
}
