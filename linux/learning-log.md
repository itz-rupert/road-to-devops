## MY LEARNING LOG
-NOTE:- I write commands in quotes sometimes, so it does not mean the quote is part of the command. Sometimes the quote is part of the command, and not all text in quotes is a command.
## UPDATES (28th July 2026)
- chmod and chown use capital R for recursive, so Chmod -R (same with cp)
- mv does use recursive, and rm uses small r for recursive
- You need to use sudo for the chown (change owner command), so sudo chown -R (new owner) (file or directory)

## UPDATES (29th July 2026)
- The which command tells you the location of an installed command-line program, e.g which sh
- Two types of programs - Compiled and interpreted programs
- Compiled programs can run directly on your machine without an interpreter, while an interpreted program needs to run with an interpreter
- Shell scripts are run in the terminal, but they have a shell interpreter that runs under the hood
- Need more clarification and understanding about the shebang command
- No space when running scripts, e.g ./genids.sh, not ./ genids.sh
- Created a script using hello_bash.sh file using nano command that says hello rupert( gained better understanding of shebang and how to handle files)
- You can view all the environment variables currently set in your shell. This may contain private information.
- The export command is used to set environment variables (these variables are readable by all programs in your shell).
- export NAME="Rupert" (note the use of a capital letter) is an environment variable, whereas name="rupert" is a local variable.
- When using wildcards(also called globbing), asterisks match any number of characters, including zero, while question marks rep. single characters
- Learn about more wildcards like [..] (matches any one of the characters enclosed within the bracket); then we have [!..] or [^..] (exclamation mark or caret used for negation, i.e matches any character not inside the bracket). e.g temp_? matches only if there is exactly one character after the underscore.
- head command views the first 10 lines while the tail views the last 10. head -n 5 /etc/passwd (format to view the first five lines in the passwd file)
- echo "New log entry at $(date)" >> ~/project/app.log (This writes to a file at the end of it without overwriting what is already there; >> is the append-to operator. So it means write this text to this path).

## UPDATES (30th July 2026)
- today I found a new way to list in long format but with "h" like ls-lh, which lists in long format but it allows you to easily know the file size
- experienced first hand how different using "less" to view a file and using "cat" actually is. With cat, you can't scroll through the pages(you get previous commands), but you can do that with less using the spacebar, arrow keys(up and down), and use the letter "b" to go back.
- While using "less" to view a file, you can search for keywords in these huge files using "/keyword you need", e.g "/critical". I think this will help in viewing things like system logs; you use "N" to move through the different places it appears and then use "shift + N" to move backward. Then 'q' to quit.
- Linux does not use file names to know the file type; rather, it examines the file itself by its content using unique (magic numbers at the beginning of the file). Filenames are just labels and can be wrong.
- Using the command "file" followed by the file name you want to read is a very safe way to know the file type of a file you do not know, e.g 'file filename.txt'. This will tell you the file type, be it a text file or pdf etc.
- ELF (Executable and Linkable Format) represents a Linux executable, like the way on Windows you have an ".exe" file (program file). So you run them and not read them.
- Now I understand the difference between using "grep" and the method of searching when you open a file with the less command "/error". With grep, you can search quickly without opening the file.
-grep is case-sensitive, but you can use grep -i to make it case-insensitive, e.g (grep -i "root" /etc/passwd); the program finds the superuser in passwd. The -v option helps to find lines that do not match your search pattern (the "root" in the previous example is the pattern). Also, you can use -e or -E for multiple patterns, e.g (grep -e "group" -e "find" file.txt or grep -E "root|user" file.txt). The '|' stands for pipe ("or").

## UPDATES (31th July 2026)
- There are several environment variables, and one of the most important is the "PATH"
- So the "PATH" is an environment variable that stores a list of directories, and any file in any of these directories can be run without having to type the full path. This is why you can run commands like ls, cat, etc. For example, if you run "which ls", it will show you the absolute path where the command is; now this command lives inside a directory that is inside the "PATH". You can run $PATH to check (you will see the bin directory in the PATH).
- So if you want to have a program that can be run system-wide in your terminal, the directory has to be in your path and also needs permission to run. You can also reset your path variable to an empty string, e.g export PATH="" but this is only temporary, and when you start a new shell session it goes back to normal. When you try to use some commands like ls, it won't work.
- When you install programs or anything in your shell, the path to where it is installed is usually displayed at the end. Now, if this file has programs that you want to run without having to specify the path, you will have to add the absolute path of this program into your "PATH".
- Export PATH="$PATH:new path". This command will add the new path to "PATH" and the semicolon just means like a comma.
- PATH config allows you to permanently add a new path to your PATH. So basically, you just open your config file, which is .bashrc for Windows and .zshrc for Mac using nano, and then you add the command to add a new path to the end of the line. This is permanent until you delete the line.
- The word count command (wc) is pretty unique, and it can help to find the largest file size in a directory using wildcards e.g wc -c *.txt (-c is for byte count, -l for number of lines, and -w is for number of words). Using wc alone gives you all three.
- env is a command that searches for the given program in your PATH and runs it. /usr/bin/env bash means find bash in the directories listed in $PATH and run it.
- The command vim is like nano but more advanced and with different modes like normal mode(the default mode used for editing and navigating with commands), insert mode(used to type text, you press "i" to enter this mode and "esc" to exit), visual mode (used to select text, v for whole lines and ctrl v for rectangular block), command line mode(used for commands such as saving and quiting, when in normal mode you press ":" and the "w" to save and "q" to quit) and replace mode(used to overwrite existing text and then replce with new text, you press R in normal mode to enter this mode). 
- Some helpful commands in vim normal mode (dd-deletes an entire line, u-undo, x-deletes one character, p-paste deleted character under the cursor, dw-delete one word)

## UPDATES (1st August 2026)

- Linux does not just print text but follows a structured flow of data. This idea is the standard stream model, which consists of standard input (stdin), standard output(stdout), and standard error (stderr). Now the standard input (file descriptor 0) is the text coming from you keyboard like "echo somefile.txt", the standard output (the good chute with file descriptor 1) is the response when the command is correct (in this case, somefile.txt is displayed on screen) while the standard error (the bad chute with file descriptor 2) occurs when there are errors in your command or when a file you want to list in long format does not exist. A key point to understand is that the terminal watches this stream and displays but it is only the default destination. Standard output is not permanently tied to the terminal and can be saved or redirected elsewhere.
- You can append the output of an error or a good result into a text using the file descriptor e.g ls -l /file 2>error.txt (this appends the error msg if file is not a directory into error.txt but since you used >, it will overwrite file.txt if something is in it, use >> not to overwrite), ls -l rupert 1>>output.txt (this appends the output into output.txt)

## UPDATES (2nd August 2026)

- The pipe operator or command (|) takes info is like a middle man taking info from one command and passing it to the other, e.g cat file.txt | grep "Linux" (now cat reads and pours file.txt content into the pipe, and then grep looks through for Linux). Also wc -l (word count). This operator can be very useful in search, word count, and many other things.
- The command "!!" is a quick way to tell the shell to run the previous command again, while using "ctrl +R" helps you to search for old commands you used previously.
-"sort" (Groups identical lines together like organizing a deck of cards), "uniq" (Filters out the duplicates from those groups). uniq -c can tell you exactly how many duplicates were found. This "sort | uniq" combination is a classic Linux "power move" for data processing.

## UPDATES (3rd August 2026)
- With flags, the order they are written doesn't matter, but with positional arguments it does matter. e.g mv file.txt ../private/file.txt (now the mv command takes two positional arguments, which are the source argument and the destination or file path)
- The "curl" command stands for client URL, which is a command-line tool that helps you to make network requests(send and receive data between computers and servers) from the terminal using various network protocols.
-Exit codes or return codes are how programs communicate back when they run successfully or not. Zero (0) is the exit code for success, while any other numbers represent an error, and most of the time it's the number 1. These exit codes are really important when it comes to CI/CD to check if command-line automations ran successfully.
- In a shell, you can access the exit code of the last program you ran using the question mark (?) variable, e.g cd ~ (this will run correctly), and when you add echo $? it will print zero or 1 if there is an error.
- The command "alias" is a way to set up short-hands for other commands, e.g (alias name="command"), then run the command, but you use (unalias command) to undo.
- The "read" command is used to take text that gets run through standard in, e.g read NAME. Here, NAME is a variable, and what you type is taken as a new line (text) that gets run through standard in.
- The pipe operator takes standard output from the left and pipes it into standard input on the right.
- (--exclude-dir="directory name") and (--exclude-from="filename") are both useful grep flags used to search but exclude a directory or file.
- When you use "ctrl + c", what happens is a "SIGINT," which is a signal interrupt, is sent to the program that is running to tell it to stop, and sometimes this doesn't work, but it mostly does. Now, when a program is in such a bad state that it refuses to respond to SIGINT, the best way is to use a new terminal window to kill the program.
- To kill the program, you use the command "KILL PID" where PID stands for process ID. Every process running on your machine has a unique ID, and this ID can be found by using the command "PS" which means process status. With the "aux" option, you are able to show all processes, including those owned by other users, and show more information about these processes. You can also use "shift M or shift P" while the top command is running to sort by memory or CPU usage.
- The "top" command allows you to see what programs are using the most resources, like cpu, memory, on your local machine.
- You reload your .bashrc or .zshrc by using the command "source ~/.bashrc" or "source ~/.zshrc" depending on your machine (Windows or macOS), allowing changes to reflect without closing the windows
-APT (Advanced Package Tool) is the primary package manager for Ubuntu. It is the default and most common.

## UPDATES (7th August 2026)
- I installed Neovim (nvim), and you use:w to save and :q to quit, then "i" to insert text and Esc to go back to normal mode.
- In Linux, one of the ways to run a command first is by using $(), e.g mkdir $(date +%F) now what this gives is a directory with the name as the current date. It runs the bracket first and then the other later. The +%F is a flag to use a custom format for date(you can check the manual).
- In Linux, UID 0 (user identification zero) means unlimited power. Also learnt how to change group permissions (sudo chgrp) so (sudo chgrp newgrp filename). use the command "id" to find out the ID of anything you need. It also displays the UID and other stuff.
- read, write, execute (4,2,1); hence, 7 grants a user all three, 6 grants read and write, 5 grants read and execute, 3 grants write and execute. This is the octal notation, which is a point system.
-When a file is created, Linux uses "umask" which stands for user masks, to decide its commands. zero (o) stands for remove nothing, two (2) stands for remove write and 7 stands for remove everything. So understand that it is referring to the default permission that come directly with a file or directory that has been created.

## UPDATES (14th August 2026)
- SSH means secure shell and it is a secure protocol and command line tool that helps you to connect to another computer over a network securely. SSHD (ssh deamon) is a background service that listens for ssh connections primarily on port 22 but it can be changed in the configuration.
-sleep command pauses the execution of a certain program or script for a specified period of time before it can be continued. Now there is also a way to allow this program to run in the background and allow for other work to continue. Sleep 5 (a line in a script will pause the script for 5 seconds before running the next line) while "sleep 5 &" will cause the sleep program to run in the background and then other lines will continue regardless of even if the background job is done.
- You can use the "jobs" command to see all background processes that are running, and it will reveal their job ID and PID. Now you can bring some of these jobs to the foreground using the job ID or even kill those jobs e.g " fg % (job ID) or kill % (job ID). you can also make lines of script to wait for the background job to be complete using the wait command e.g "wait % (job id) or you can save the pid using (pid=$! and then do wait "$pid"). You can also suspend a job in the foreground using Ctrl+Z or ctrl + c to kill it.
-pkill -f script name is a way to find the PID of script name and kill it automatically. Kill(SIGTERM) always you to kill a program or script, but you will not lose data ( i.e you can save the data); when you use kill -9(SIGKILL), you forcefully stop a stubborn program.
-pgrep is used to check for the PID of running processes whose command matches what is in the string e.g pgrep -f "sleep 3000". The -f is used to check the process's full command line and not just the name of the string.
- Now you also have the nice and renice commands that basically set the CPU scheduling priority. A higher nice value is lower priority, e.g 5, lower nice value means higher priority (up to negative values). This "renice -n 5 -p (PID)" reassigns a new PID to a process with the inputted PID (the PID number is not needed in brackets). The -p signifies that the next number is a PID, while for nice -n 10, "a background job".

## UPDATES (15th August 2026)
- The Kernel is the heart of Linux. More precisely, the kernel is the core software layer that manages hardware, processes, memory, and many low-level system services. The Linux kernel and the distribution built around it are related, but they are not the same thing. Use uname -a (Unix Name - All) to see details. You will see the kernel name, hostname, the version or build identifier, the machine architecture, processor architecture, hardware system architecture and other things, including the operating system environment.
- You can find the operating system version in /etc/os-release.
- you can use "uptime" to check how long the computer has been running. Long uptime can be a sign of stability, but it is not automatically proof that a system is healthy. It is just one clue among many.
- The "free" command answers “How much memory is available overall?” Use top to find “Which processes are using the memory?”. Free gives output in kilobytes, which can be hard to read, but when you add the attribute "-h" it gives it in gigabytes. In Linux monitoring, Low "free" memory is not automatically bad, because Linux intentionally uses spare memory for caching to improve performance. The rule is to worry if available is low, not free.
- Swap is like a storage option on your SSD where inactive memory pages—small blocks of memory containing parts of programs or their data—are moved from RAM to free up RAM for other, more active or higher-priority tasks. When those pages are needed again, Linux moves them back into RAM. When swap usage starts to increase, the system can become slower because swap lives on storage, such as an SSD, and storage is much slower than RAM. If the system constantly moves pages between RAM and swap, this is called thrashing. Thrashing means the system spends too much time swapping memory pages in and out instead of running programs, which can make applications respond slowly or even appear to freeze. Use "free -h" command or "swapon --show" to see your swap details.
- The command "watch" repeatedly runs a command and refreshes the display and you can also set the time for it, e.g "watch -n 1 swapon --show" etc.
- df (disk free) measures how much free and used space on something like a drive, while du(disk usage) measures how much space a file or directory consumes.

## UPDATES (21th August 2026)
- Load average values, which are the last three values shown when you use the command "uptime," show the amount of work waiting for or using the CPU. It is reported for the last 1minute, 5 minutes, and 15minutes respectively. Now, on a one-core system, a load average of 1.00 shows that the CPU is fully busy, and on a 4-core system, when the load average is 4.00, the CPU is fully busy. When the load average exceeds the number of cores, it shows that processes are waiting for CPU time.
- The "awk" command is kind of similar to the grep command, but it has a major difference. The awk command processes text and is able to split this text into, for example, fields one and two ($1 and $2) and print out any of the fields. So it is mainly used to divide text into parts and perform actions on those parts. e.g (uptime | awk -F'load average: ' '{print $2}') the -F attribute tells awk where to split the text, and notice that there is a space between the apostrophe, which is needed else the command throws an error.
- nproc is a command to list the number of processing units available to the system (4 cores, 1 core, etc).
- The watch command is useful, and it acts just like top, where you can watch how a system changes over time (basically it allows you to run a command repeatedly and see the changes), e.g watch date. It automatically updates every 2 seconds but you can add the "-n 5" to update to five seconds or whatever. The command "free" is a Linux command that reports your computer’s RAM and swap usage
