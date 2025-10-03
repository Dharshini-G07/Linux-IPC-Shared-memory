# Linux-IPC-Shared-memory
Ex06-Linux IPC-Shared-memory

# AIM:
To Write a C program that illustrates two processes communicating using shared memory.

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - Shared Memory

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## Write a C program that illustrates two processes communicating using shared memory.

```
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/shm.h>

int main() {
    key_t key = ftok("shmfile", 65);
    int shmid = shmget(key, 1024, 0666 | IPC_CREAT);
    printf("Shared memory id = %d\n", shmid);

    char* str = (char*)shmat(shmid, (void*)0, 0);
    printf("Write Data : ");
    fgets(str, 1024, stdin);
    printf("Data written in memory: %s\n", str);

    shmdt(str);
    shmctl(shmid, IPC_RMID, NULL);

    return 0;
}
```




## OUTPUT
<img width="946" height="472" alt="Screenshot 2025-10-03 143252" src="https://github.com/user-attachments/assets/82182c91-6a0b-4b05-bcf8-957ae034cc25" />


# RESULT:
The program is executed successfully.
