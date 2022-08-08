VARIABLE MAKING
var_a="Hello World"  <----- No spaces after or before the =
echo $var_a  <----- Call the variable made with a $
CONSTANT VARIABLES
$#  <----- Number of arguments
$0  <----- The name of the script
$2  <----- The nth argument passed
$*  <----- All of the arguments passed
$?  <----- Exit status, should be sero
$_  <----- Last argument povided, should be zero
$$  <----- PID
#-  <------ flags set in shell

#!/bin/bash
# This is a comment

ESTABLISHING FUNCTIONS
function print_somefun {
echo $2
}

print_somefun $1

OR

somefun() {
echo $1
}

somefun $1      <------- call the function once its been made (within the script)


EXAMPLE of Function
#!/bin/bash
# This is a basic function

lines_in_file() {
      cat $1 | wc -l
}

function num_lines=$( lines_in_file $1 )

echo The file $1 has $num_lines in it.
echo Good day sir


ANOTHER EXAMPLE
function f1 {
        echo Hello I\'m function
        echo Bye!
}

function f2 { Hello I\'m function 2; echo Bye! Bye!; }
f3() {
        echo Hello I\'m function 3
        echo Bye!!!
}
f4 () { echo Hello I\'m function 4; echo Bye!! Bye!!; }

#lets look at our functions
f4
f3
f2
f1


FUNCTIONS IN YOUR SHELL
my_function () {echo "This is my function"; }

OR

function redirection_out {
> declared -a output=("baeldung" "lorem" "ipsum")


WHEN SCRIPTING:
"" = interprets variables
'' = interprets literal
\ = escape individual characters




VARIABLE SUBSTITUTION
https://www.gnu.org/software/libc/manual/html_node/Variable-Substitution.html 

{variable:-default}
Substitute the value of variable, but if that is empty or undefined, use default instead.

${variable:=default}
Substitute the value of variable, but if that is empty or undefined, use default instead and set the variable to default.

${variable:?message}
If variable is defined and not empty, substitute its value.

Otherwise, print message as an error message on the standard error stream, and consider word expansion a failure.

${variable:+replacement}
Substitute replacement, but only if variable is defined and nonempty. Otherwise, substitute nothing for this construct.



PRACTICE QUESTIONS
1. Using find, find all files under the $HOME directory with a .bin extension ONLY.
   Once the file(s) and their path(s) have been found, remove the file name from the absolute path output.
   Ensure there is no trailing / at the end of the directory path when outputting to standard output.
   You may need to sort the output depending on the command(s) you use.

find $HOME/ -type f -name "*.bin" | rev | cut -d/ -f2- | rev | sort -u

OR

find $HOME -type f -iname "*.bin" -printf "%h\n" |sort -u

OR

find $HOME -type f -iname "*.bin" | awk 'BEGIN{FS="/";OFS="/'"}{NF=NF-1; print $0}



2.Find all executable files under the following four directories:
  /bin, /sbin, /usr/bin, /usr/sbin
  Sort the filenames with absolute path, and get the md5sum of the 10th file from the top of the list.

md5sum $(find /sbin /bin /usr/bin /usr/sbin -executable -type f | sort | head | tail -1) | cut -d" " -f1
      Indicator of 
      command substitution



3. Write a script which will copy the last entry/line in the passwd-like file specified by the $1 positional parameter
   Modify the copied line to change:
   User name to the value specified by $2 positional parameter
   Used id and group id to the value specified by $3 positional parameter
   Home directory to a directory matching the user name specified by $2 positional parameter under the /home directory
   The default shell to `/bin/bash'
   Append the modified line to the end of the file

tail -1 $1 | awk -F: -v "name=$2" -v "id=$3" 'BEGIN {OFS=":"} {$1=name} {$3=id} {$4=id} {$6="/home/"name} {$7="/bin/bash"} {print}' >> $1
                                                                                                         or $NF (last field)


4. Using any BASH command complete the following:
   Sort the /etc/passwd file numerically by the GID field.
   For the 10th entry in the sorted passwd file, get an md5 hash of that entry’s home directory.
   Output ONLY the MD5 hash of the directory's name to standard output.

cat /etc/passwd | cut -d: -f4- | sort -n | head | tail -1 | cut -d: -f3 | md5sum | cut -d" " -f1



5.Write a script which will find and hash the contents 3 levels deep from each of these directories: /bin /etc /var
  Your script should:
  Exclude named pipes. These can break your script.
  Redirect STDOUT and STDERR to separate files.
  Determine the count of files hashed in the file with hashes.
  Determine the count of unsuccessfully hashed directories.
  Have both counts output to the screen with an appropriate title for each count.

md5sum $(find {/bin,/etc,/var} -maxdepth 3 -not -type p) 2>stderr.txt 1>MD.txt
a=$(wc -l MD.txt | cut -d" " -f1)
b=$(grep "directory" stderr.txt | wc -l)
echo "Successfully Hashed Files: $a"
echo "Unsuccessfully Hashed Directories: $b"

chmod +x script.sh <-------- MUST DO TO RUN A SCRIPT
