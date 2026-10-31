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
```
 #include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <stdlib.h>

int main()
{
   pid_t pid;

   pid = fork();

   if (pid == 0)
   {
      printf("Child process executing ls command\n");
      execlp("ls", "ls", "-1", NULL);
      perror("exec failed");
      exit(1);
   }
   else if (pid > 0)
   {
      wait(NULL);
      printf("Parent process completed\n");
   }
   else
   {
      printf("Fork failed\n");
   }

   return 0;

}
```


 








## OUTPUT

<img width="555" height="151" alt="{8B19AC54-6E1E-4855-8E0C-39A911A13BBC}" src="https://github.com/user-attachments/assets/22fe7eb9-9072-4ddf-af53-5c5d50b2b392" />







## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family

```
#include<stdio.h>
#include<unistd.h>
#include<sys/types.h>
#include<sys/wait.h>

int main()
{
   pid_t pid;

   pid = fork();

   if (pid < 0)
   {
      printf("Fork failed\n");
   }
   else if (pid == 0)
   {
     printf("Child Process\n");
     printf("Child PID: %d\n", getpid());
     printf("Parent PID: %d\n", getppid());
   }
   else
   {
     wait(NULL);
     printf("Parent Process\n");
     printf("Parent PID: %d\n", getpid());
     printf("Child PID: %d\n", pid);

   }


   return 0;
}
```





















## OUTPUT

<img width="557" height="168" alt="{A297101C-FAAD-4960-8800-ABE181AEBEDA}" src="https://github.com/user-attachments/assets/8c535d3c-d4e1-4568-b915-3cd9b47620b1" />
















# RESULT:
The programs are executed successfully.
