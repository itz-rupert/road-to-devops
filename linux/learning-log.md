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
- When using wildcards(also called globbing), asterisks say match any number of characters, including zero, while question marks rep. single characters
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
