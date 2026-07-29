## MY LEARNING LOG

## UPDATES (28th July 2026)
- chmod and chown use capital R for recursive, so Chmod -R (same with cp)
- mv does use recursive, and rm uses small r for recursive
- you need to use sudo for the chown (change owner command), so sudo chown -R (new owner) (file or directory)

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
