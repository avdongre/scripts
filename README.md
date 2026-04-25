# SEMESTER 2 EXAMINATIONS 2021/2022
### Create a file named file-2022.txt in current working directory and then move it to home directory.
```bash
touch file-2022.txt
mv file-2022.txt $HOME
```
### Compress all the files in /home/John directory into /tmp/John.tar.gz
```bash
tar cvfz /tmp/John.tar.gz /home/Jonh
```
### Output a list of the files in the current working directory in the reverse order.
```bash
ls -r
```
### Remove all files and directories in /usr/share directory.
```bash
rm -rf /usr/share/*
```
### Output only a count of the number of lines in poem.txt which match the pattern “Mary”
```bash
cat poem.txt | grep "Mary" | wc -l
```
# AUGUST/RESIT EXAMINATIONS 2021/2022

### Output a list of all regular files in the current working directory.
```bash
ls -p | grep -v /
```
### Remove all PDF files in /home/ca114-directory.
```bash
rm -rf /home/ca114/*.pdf
```
### Output each line of mary.txt which contains the word "a". 
```bash
grep 'a' mary.txt
```

```declarative
For the following questions, write the command that would accomplish the given
task. Each command is worth 5 marks.
1. Show the last 10 lines of log.txt and add the output to archive.txt without
overwriting its content.
2. Show the number of lines in report.txt.
3. Show the contents of data.txt and save only the lines containing the word
‘success’ in a new file called success.txt.
```
```bash
tail -10 log.txt >> archive.txt
wc -l report.txt
cat data.txt
grep 'success' data.txt > success.txt
```

```declarative
A user writes a shell script named check-file-exists.sh that takes a file path as a
command-line argument and checks whether the file exists. If the file exists, the
script prints a success message and exits with status 0; otherwise, it prints an error
message and exits with status 1.
```
```bash
if [ -e "$1" ]; then
  echo "Success: File exists."
  exit 0
else
  echo "Error: File does not exist."
  exit 1
fi
```
```declarative
You are asked to write a shell script named procwatch.sh that continuously checks if
a process (given as an argument) is running and prints a message if it is not found.
```

```bash
PROCESS="$1"
# Infinite loop to monitor the process
while true; do
  if pgrep -x "$PROCESS" > /dev/null; then
    echo "Process '$PROCESS' is running."
  else
    echo "Alert: Process '$PROCESS' is NOT running!"
  fi
  sleep 5  # wait 5 seconds before checking again
done
```

```declarative
Modify the script so that it automatically stops monitoring after 5 checks, even if the process is still running.
```

```bash
ROCESS="$1"
COUNT=0
MAX_CHECKS=5

while [ $COUNT -lt $MAX_CHECKS ]; do
  if pgrep -x "$PROCESS" > /dev/null; then
    echo "Process '$PROCESS' is running."
  else
    echo "Alert: Process '$PROCESS' is NOT running!"
  fi

  COUNT=$((COUNT + 1))
  sleep 5
done

echo "Monitoring stopped after $MAX_CHECKS checks."
exit 0
```
### Write a single command to create report_1.txt, report_2.txt, …, report_10.txt.
```bash
touch report_{1..10}.txt
```

```declarative
Given a file name “historical-figures.txt” with the following content:
    Name,Year of Birth,Field
    Isaac Newton,1643,Physics
    Albert Einstein,1879,Physics
    Marie Curie,1867,Chemistry
    William Shakespeare,1564,Literature
    Yuri Gagarin,1934,Astronautics
    Pythagoras,570,Mathematics
    John von Neumann,1903,Mathematics
    Leonardo da Vinci,1452,Art
    Charles Darwin,1809,Biology

Write a command to output the names of all people born after 1800.
```
```bash
while IFS=',' read -r name year field
do
    if [ "$year" -gt 1800 ]; then
        echo "$name"
    fi
done < historical-figures.txt
```

```bash
In the password file (/etc/passwd), each line consists of seven colon-delimited fields
in the following format: username:password:UID:GID:GECOS:directory:shell.
Write a shell script which outputs to standard output, a list of usernames who doesn't
use bash as their login shell.
```

```bash
#!/bin/sh

while IFS=: read -r username password uid gid gecos directory shell
do
    if [ "$shell" != "/bin/bash" ]; then
        echo "$username"
    fi
done < /etc/passwd
```