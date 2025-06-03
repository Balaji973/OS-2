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
~~~
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{
        pid_t process_id;
        pid_t p_process_id;
        process_id = getpid();
        p_process_id = getppid();
        printf("The process id: %d\n",process_id);
        printf("The process id of parent function: %d\n",p_process_id);
        return 0; 
}
~~~

##OUTPUT
![WhatsApp Image 2025-05-06 at 11 39 30_67014dce](https://github.com/user-attachments/assets/82f20007-5f43-495f-a2e3-faec91230dc0)


![WhatsApp Image 2025-05-06 at 11 40 45_76bee0e6](https://github.com/user-attachments/assets/9971b7f2-0545-44e9-adfd-0a1599b7a67d)



~~~
#include <sys/types.h>
#include <unistd.h>
#include <stdio.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}
~~~

##OUTPUT

![WhatsApp Image 2025-05-07 at 18 20 27_0297d9fd](https://github.com/user-attachments/assets/a0e67fdf-1a89-4f61-9535-6cf2386d64d7)



## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family


~~~
#include <stdio.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);
}
~~~

##OUTPUT
![WhatsApp Image 2025-05-07 at 18 32 07_8da658f4](https://github.com/user-attachments/assets/1133e3f4-1ec7-4985-a539-267bc4be2f6d)



# RESULT:
The programs are executed successfully.
