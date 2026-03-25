# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls


#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    int pid = fork();

    if (pid == 0) {
        printf("Child Process\n");
        printf("PID: %d\n", getpid());
        printf("Parent PID: %d\n", getppid());
    } else {
        printf("Parent Process\n");
        printf("PID: %d\n", getpid());
        wait(NULL);
    }

    return 0;
}










##OUTPUT
<img width="712" height="432" alt="Screenshot 2026-03-25 113236" src="https://github.com/user-attachments/assets/0c7c0ff1-a8d2-480b-b6b4-652b10d77768" />








## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family



#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    int status;

    printf("Running ps command\n");

    if (fork() == 0) {
        execl("/bin/ps", "ps", "-f", NULL);
        perror("exec failed");
        exit(1);
    }

    wait(&status);

    printf("Child process completed\n");

    return 0;
}






















##OUTPUT
<img width="658" height="473" alt="Screenshot 2026-03-25 113256" src="https://github.com/user-attachments/assets/8d8a23a2-16c4-430f-a8e7-2d2898b04115" />


















# RESULT:
The programs are executed successfully.
