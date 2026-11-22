Mini Project: Linux Log & Configuration File Analyzer Using sed
Beginner friendly
25 commands
Linux project

Project objective: Automate text processing in Linux using sed. We will create a sample log/configuration file, replace text, remove unwanted lines, extract information, and edit files.
Step 1: Create project folder
Run:
mkdir -p ~/sed-mini-project


Step 2: Enter project folder
cd ~/sed-mini-project


Step 3: Create sample file
cat << 'EOF' > file.txt
# Configuration and Log File
user:alice:1001:admin:/home/alice:/bin/bash
user:bob:1002:developer:/home/bob:/bin/zsh
error: failed to load /var/www/html/index.php at line 10
debug: checking memory limit 512 and timeout 30

old value is old and another old word
OLD case check with foo and bar
status: failed connection on port 8080
user:charlie:1003:guest:/home/charlie:/bin/sh
# End of file
EOF


Step 4: Verify the file
cat file.txt


You should see your sample data.
Step 5: Perform 25 practical sed operations
Run each command separately. These commands demonstrate different text-processing tasks.
Part A: Find and replace
Command 1 – Replace first occurrence
sed 's/old/new/' file.txt


Purpose: Replace the first old on each line.

Command 2 – Replace all occurrences
sed 's/old/new/g' file.txt


Purpose: Replace every occurrence of old.

Command 3 – Case-insensitive replacement
sed 's/old/new/gi' file.txt


Purpose: Replace both old and OLD.

Command 4 – Replace second occurrence
sed 's/old/new/2' file.txt


Purpose: Replace only the second occurrence on each line.

Command 5 – Replace second and later occurrences
sed 's/old/new/2g' file.txt


Purpose: Replace from the second occurrence onwards.

Command 6 – Replace file path
sed 's|/var/www|/srv/http|g' file.txt


Purpose: Change the website directory path.

Command 7 – Replace text on a specific line
sed '7s/old/new/g' file.txt


Purpose: Replace text only on line 7.

Command 8 – Replace within a line range
sed '7,9s/old/new/g' file.txt


Purpose: Replace text between lines 7 and 9.

Command 9 – Replace on matching lines
sed '/error/s/failed/ERROR/g' file.txt


Purpose: Replace failed with ERROR only on lines containing error.

Command 10 – Add px after numbers
sed -E 's/[0-9]+/&px/g' file.txt


Purpose: Add px after numeric values.
Part B: Delete unwanted lines
Command 11 – Delete line 3
sed '3d' file.txt


Command 12 – Delete the last line
sed '$d' file.txt


Command 13 – Delete lines 2 to 5
sed '2,5d' file.txt


Command 14 – Delete debug messages
sed '/debug/d' file.txt


Command 15 – Delete empty lines
sed '/^$/d' file.txt


Command 16 – Delete comment lines
sed '/^#/d' file.txt


Part C: Display selected information
Command 17 – Display line 5
sed -n '5p' file.txt


Command 18 – Display lines 7 to 10
sed -n '7,10p' file.txt


Command 19 – Display failed messages
sed -n '/failed/p' file.txt


Command 20 – Display odd-numbered lines
sed -n '1~2p' file.txt


Part D: Insert, append and edit
Command 21 – Insert a new header
sed '4i\New Header Line' file.txt


Command 22 – Append a footer
sed '4a\New Footer Line' file.txt


Command 23 – Edit original file
sed -i 's/foo/bar/g' file.txt


Command 24 – Edit and create backup
sed -i.bak 's/old/new/g' file.txt


Command 25 – Execute multiple replacements
sed -e 's/alice/ALICE/g' -e 's/bob/BOB/g' file.txt


Note: Commands 1–22 and 25 display results without changing the original file. Commands 23–24 modify file.txt. Command 24 also creates file.txt.bak. Run command 24 after command 23 if you want the backup of the file as it exists at that point.
