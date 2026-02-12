# Linux Module 3

## Scenario: Automating file backup and Reporting to the system. Create a shell script called "backup_manager.sh" that performs the following tasks incorporating the concepts suggested.


#Backup_manager.sh

#!/bin/bash

src=$1
dest=$2
ext=$3

if [ $# -ne 3 ]; then
    echo "Usage: $0 <source_dir> <dest_dir> <extension>"
    exit 1
fi

if [ ! -d "$src" ]; then
    echo "Source directory not found"
    exit 1
fi

if [ ! -d "$dest" ]; then
    mkdir "$dest"
fi

export BACKUP_COUNT=0
shopt -s nullglob

for file in "$src"/*"$ext"
do
    if [ -f "$file" ]; then
        name=$(basename "$file")
        cp "$file" "$dest/$name"
        BACKUP_COUNT=$((BACKUP_COUNT + 1))
    fi
done

echo "Backup report" > "$dest/backup_report.log"
echo "Total file backed up: $BACKUP_COUNT" >> "$dest/backup_report.log"
echo "Backup directory: $dest" >> "$dest/backup_report.log"
echo "Backup finished" >> "$dest/backup_report.log"


<img width="940" height="349" alt="image" src="https://github.com/user-attachments/assets/6dcb3133-f6a2-470f-bcd0-88ba1421ab87" />

<img width="940" height="375" alt="image" src="https://github.com/user-attachments/assets/2a6e99b1-a448-4bf3-b304-8651bf3bc141" />

<img width="940" height="215" alt="image" src="https://github.com/user-attachments/assets/4153a85f-8672-40c8-8830-f288ce68bf4b" />



