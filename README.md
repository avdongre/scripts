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
