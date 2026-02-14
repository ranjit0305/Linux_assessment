# Module 4

## For the attached file, write a bash script which should take the file as input and have to go through it line by line and need to generate an output file (say output.txt) with listings of following parameters fetched from the input file.
## Params expected to be fetched from input.txt file : "frame.time", "wlan.fc.type", "wlan.fc.subtype"
## Sample output expected in output.txt:
"frame.time": "Nov 14, 2024 11:44:48.219200000 India Standard Time",
"wlan.fc.type": "1",
"wlan.fc.subtype": "9"
"frame.time": "Nov 14, 2024 11:44:48.219208000 India Standard Time",
"wlan.fc.type": "0",
"wlan.fc.subtype": "1",
and so on.

## input.txt

```text
"frame.time": "Nov 14, 2024 11:44:48.219200000 India Standard Time",
"wlan.fc.type": "1",
"wlan.fc.subtype": "9",
"random": "ignore this"

"frame.time": "Nov 14, 2024 11:44:48.219208000 India Standard Time",
"wlan.fc.type": "0",
"wlan.fc.subtype": "11",
"other": "skip this"
```

## extract.sh

```bash
#!/bin/bash

input=$1
output=output.txt

while read line
do
    echo "$line" | grep -E '"frame.time"|"wlan.fc.type"|"wlan.fc.subtype"' >> "$output"
done < "$input"

echo "Done"
```
<img width="940" height="549" alt="image" src="https://github.com/user-attachments/assets/f4974436-e972-423e-bbdf-f4427c7b3f8a" />
<img width="940" height="214" alt="image" src="https://github.com/user-attachments/assets/0e0e1bbb-2c96-4bbe-8895-c7e2b5b481cf" />


