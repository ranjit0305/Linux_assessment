# Linux Module 5 

## Directory & File Keyword Search Script

## search_script.sh

```bash
#!/bin/bash

show_help() {
cat << EOF
Usage:
$0 -d directory -k keyword
$0 -f file -k keyword
$0 --help

Options:
-d   Directory search
-f   File search
-k   Keyword
EOF
}

search_dir() {
for item in "$1"/*
do
    if [ -f "$item" ]; then
        grep "$key" "$item"
    elif [ -d "$item" ]; then
        search_dir "$item"
    fi
done
}

if [ $# -eq 0 ]; then
    echo "No arguments" | tee errors.log
    exit 1
fi

while getopts "d:f:k:" opt
do
case $opt in
d) dir=$OPTARG ;;
f) file=$OPTARG ;;
k) key=$OPTARG ;;
*) show_help; exit 1 ;;
esac
done

if [[ "$*" == *"--help"* ]]; then
    show_help
    exit 0
fi

if ! [[ "$key" =~ ^[a-zA-Z]+$ ]]; then
    echo "Invalid keyword" | tee errors.log
    exit 1
fi

if [ ! -z "$file" ]; then
    if [ ! -f "$file" ]; then
        echo "File missing" | tee errors.log
        exit 1
    fi
    grep "$key" "$file"
fi

if [ ! -z "$dir" ]; then
    if [ ! -d "$dir" ]; then
        echo "Directory missing" | tee errors.log
        exit 1
    fi
    search_dir "$dir"
fi

echo "Script name: $0"
echo "Total args: $#"
echo "All args: $*"
echo "Exit status: $?"
```

<img width="940" height="239" alt="image" src="https://github.com/user-attachments/assets/30b7a9bc-c9af-4383-bbf4-f493b2718f1a" />

<img width="940" height="454" alt="image" src="https://github.com/user-attachments/assets/8b797467-1bf0-47f4-8156-dcd21d4fb0b7" />

