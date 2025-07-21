# BASH1

Script Execution

    Scripts need an interpreter in the first line (#!/bin/bash, #!/bin/python, etc.)

    Scripts are plain text but must be executable:

chmod u+x script.sh
./script.sh  # Use ./ for current dir

🔁 When to Script?

    To repeat tasks

    To handle complex commands or service controls

    For automation (e.g. certificate renewal)

🧮 BASH Variables

var="Example"
echo $var

    No spaces before/after =, accessed via $var

🧠 Built-in Variables

    PATH — where to find executables

    IFS — field separator (default: whitespace)

    PWD, USER, HOME — current directory, user, home dir
    ➡️ More info

🔢 Positional Parameters

    $0 — script name

    $1 to $9 — script arguments

    $? — exit code of last command

    $@ — all args (quoted)

    $* — all args as one string

    $# — number of arguments

    $$ — PID of script

📂 Spaces & IFS

To include spaces in names:

mkdir My\ Documents
mkdir "My Documents"
mkdir 'My Documents'

🗣️ Quoting in BASH

echo '$PATH'  # literal
echo "$USER"  # parses variable

    ' = literal, " = parsed

🌟 Wildcards

ls *.*         # all files with extensions  
cat *          # all files  
cat /home/*/public_html/index.html  # every user's index.html

🔣 Brace Expansion

echo {1..10}                        # 1 to 10  
mkdir Output{1..3}                 # Output1, Output2, Output3  
cat file{.log,.err}               # file.log and file.err  
mv file{,.txt}                   # mv file file.txt

🧾 Conditionals

if {command}; then
  # run if true
fi

if ping -c 1 google.ca; then
  elinks google.ca
fi

With else/elif:

if ping -c 1 google.ca; then
  elinks google.ca
elif ping -c 1 bing.com; then
  elinks bing.com
else
  echo "No connection"
fi

backticks or $()

files=`ls`
files=$(ls)

📥 read command

read input
echo $input

    Captures one line from input

🔍 test and [ ]

if [ $1 -gt 5 ]; then
  echo "$1 is greater than 5"
fi

    [ ] is same as test, must be spaced correctly

🔁 Loops Overview

    for in, while, C-style for

for in loop

for i in `ls`; do
  echo $i
done

while loop

while read line; do
  echo $line
done < input.txt

C-style for loop

for (( i=0; i<10; i++ )); do
  echo "Iteration $i"
done

🧩 Functions

function firstFun() {
  echo "Hello World!"
}
firstFun

With parameter:

function funArg() {
  echo $1
}
funArg test
