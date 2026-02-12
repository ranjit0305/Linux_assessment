# Linux Module 2 

## 1) List All Files Larger Than 1 MB and Save Output

du -m * | awk '$1>1'

<img width="940" height="85" alt="image" src="https://github.com/user-attachments/assets/0996e1b7-3fde-42cf-9a7f-d328064e08d9" />

## 2)	Replace all occurrences of "localhost" with "127.0.0.1" in config.txt and save as updated_config.txt

sed 's/localhost/127.0.0.1/g' config.txt > updated_config.txt

<img width="940" height="198" alt="image" src="https://github.com/user-attachments/assets/c747fcc7-4746-4407-95f3-29e725769087" />

## 3)	Search for lines containing "ERROR" but exclude lines containing "DEBUG" and save results

grep "ERROR" filename.txt | grep -v "DEBUG" > result.txt

<img width="940" height="468" alt="image" src="https://github.com/user-attachments/assets/1f24d873-1c05-4242-a97c-c56cf9764e92" />

## 4) Identify the process with highest memory usage and terminate it

ps a --sort = -%mem | head -n 2
kill 2051

<img width="940" height="80" alt="image" src="https://github.com/user-attachments/assets/cca091d7-ccb4-49ac-95a9-49d08345346b" />

## 5)	Print all available gateways in a sorted manner

ip route | grep default | sort

<img width="940" height="55" alt="image" src="https://github.com/user-attachments/assets/fe14f03a-4c5b-4396-b073-65eb073af9b5" />
