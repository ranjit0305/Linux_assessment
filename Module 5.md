# Linux Module 5 

## Directory & File Keyword Search Script

## search_script.sh

```bash
#!/bin/bash

show_help() {
cat << EOF
Usage:
$0 -d <directory> -k <keyword>
$0 -f <file> -k <keyword>
$0 --help

Options:
-d   Directory search (recursive)
-f   File search
-k   Keyword to search
--help   Display help menu
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
    echo "No arguments provided" | tee -a errors.log >&2
    exit 1
fi

if [[ "$1" == "--help" ]]; then
    show_help
    exit 0
fi

while getopts ":d:f:k:" opt
do
case $opt in
d) dir=$OPTARG ;;
f) file=$OPTARG ;;
k) key=$OPTARG ;;
\?) echo "Invalid option: -$OPTARG" | tee -a errors.log >&2; exit 1 ;;
esac
done

if [[ -z "$key" || ! "$key" =~ ^[a-zA-Z0-9_]+$ ]]; then
    echo "Invalid or empty keyword" | tee -a errors.log >&2
    exit 1
fi

if [ -n "$file" ]; then
    if [ ! -f "$file" ]; then
        echo "File missing: $file" | tee -a errors.log >&2
        exit 1
    fi
    content=$(cat "$file")
    grep "$key" <<< "$content"
fi

if [ -n "$dir" ]; then
    if [ ! -d "$dir" ]; then
        echo "Directory missing: $dir" | tee -a errors.log >&2
        exit 1
    fi
    search_dir "$dir"
fi

echo "Script Name: $0"
echo "Total Arguments: $#"
echo "All Arguments: $@"
echo "Last Exit Status: $?"

```

<img width="940" height="239" alt="image" src="https://github.com/user-attachments/assets/30b7a9bc-c9af-4383-bbf4-f493b2718f1a" />

<img width="940" height="454" alt="image" src="https://github.com/user-attachments/assets/8b797467-1bf0-47f4-8156-dcd21d4fb0b7" />

