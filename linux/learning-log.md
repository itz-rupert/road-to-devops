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
