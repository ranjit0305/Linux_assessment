# Linux Module 1 – Basic File & Process Operations

## 1️) Create a File and Add Executable Permission to All Users

### Create a file:

touch sample1.txt

### Add executable permission: 

chmod +x sample1.txt

<img width="940" height="392" alt="image" src="https://github.com/user-attachments/assets/d25f928c-af94-433d-9663-465a0d534a34" />

## 2) Create a file and remove write permission for group user alone

chmod g-w sample2.txt

<img width="940" height="159" alt="image" src="https://github.com/user-attachments/assets/728b6cb7-b960-4b52-bb33-59fd389c5478" />

## 3) Create a file and add a soft link in a different directory

ln -s ../directory2/file2/.txt file2link.txt

<img width="940" height="150" alt="image" src="https://github.com/user-attachments/assets/12546341-bf31-4d7d-8e9b-b6e3c0033657" />
<img width="940" height="173" alt="image" src="https://github.com/user-attachments/assets/74651041-af63-4a9b-b773-d0c373add406" />

## 4)Use ps command to display all active processes

Ps -ef

<img width="940" height="590" alt="image" src="https://github.com/user-attachments/assets/41516b13-9ba5-4cb3-aa41-8b246131348c" />

## 5) Create 3 files in a directory and redirect sorted list output (by timestamp) to a file

<img width="940" height="263" alt="image" src="https://github.com/user-attachments/assets/b44d2594-05be-4bb7-90be-cfbf7ee0aad7" />

