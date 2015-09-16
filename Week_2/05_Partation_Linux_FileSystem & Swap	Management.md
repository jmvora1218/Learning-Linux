# Partitioning Linux FileSystem

  * Resize Logical volume : <br>
   lvextend <br>
   resize2fs

   * **Reduce :**
   ```
   umount fs (logical volume) --- unmount
   e2fsck -f lv2   --- Checking the fs
   resize2fs lv2 4G
   lvreduce -L 50M -n lv2
   ```

# Swap Management in Linux :

  - Swap is an area of the HDD that is used to store the IDEAL processes in RAM.
  ```
  Convention :
    if RAM < 2GB => Swap = 2xRAM
    if RAM > 2GB => Swap = 2+RAM
    ```
  - create a partition using fdisk.
    ```
  make the type of partition to SWAP (82)
  format the partition as : mkswap /dev/sda3
  activate the swap as : swapon /dev/sda3
  check the free space : free -h
  check the status of swap : swapon -s
  To turn off the swap use : swapoff /dev/sda3
```

* **PS :** Process status.<br>
  - ps => display process running in current terminal.
  - ps a => display process running in all terminal.
  - ps x => display process not running in terminal.
    process which is not running in a terminal is a background process
  - ps aux => Display the user also who has started the process.<br>
      The above set of commands gives OP in terms of resources comsumed
  - ps -ef => Gives output of all process with all process details.
  - for background processes : append '&'.
  ```
    Example : vi &
    [root@localhost jay]# vi &
    [1] 12816
    job | PID
```
  - **jobs:** To list all background jobs.<br>
  - to bring process from background to foreground use : fg %1  (job num)
    ```
    Example : fg %1
    [root@localhost jay]# jobs %1
    [1]+  Stopped                 vi
    ```
* **Get PID :**
    pidof processname
    ```
    Example :
    pidof vim
    Display lists of PID.
      ```
* **Kill a process :** <br>
    kill -l : list all signals.
    ```
    Example :
      kill -9 9811
      ```
* **PKILL :** use name of process to kill a process. <br>
    pkill -9 vim <br>
    If there are multiple processes with same name **pkill** will kill all the process.

* **ZOMBIE Process:** When Chain process, which has completed the execution but has not yet released the **pid** and **signelled** the parennt process of it's completition is a ZOMBIE process.

* **TOP :** Command to see the task-mangager like logs.<br>
    Example:
  ```
  top - 18:51:21 up 1 day,  7:45,  2 users,  load average: 0.13, 0.19, 0.22
Tasks: 198 total,   1 running, 196 sleeping,   1 stopped,   0 zombie
%Cpu(s):  1.9 us,  1.3 sy,  0.0 ni, 91.3 id,  5.5 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  1830576 total,    19092 free,  1244648 used,   566836 buff/cache
KiB Swap:  2097148 total,  1385924 free,   711224 used.   331124 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1190 root      20   0  465852  62672  33920 S   4.3  3.4  11:09.26 Xorg.bin
 1990 jay       20   0 2003696 166976  25508 S   4.0  9.1  20:35.01 cinnamon
 2613 jay       20   0  534572  11952   7188 S   2.6  0.7   0:16.18 gnome-terminal-
   72 root      20   0       0      0      0 S   0.7  0.0   0:22.91 kswapd0
   25 root      20   0       0      0      0 S   0.3  0.0   0:15.61 rcuos/2
  ```
* **Nice ID :** The priority of the process.<br>
    - The value determines the priority of process Value from -20 to +19 the lesser the more priority
    - Nice value can only be increased for normal users Only for root users it can be reduced to below 0
    - With top to kill the process
    ```
    top
      -> k (to kill)
      -> enter pid
      -> enter signal to send
      -> q to quit top utility
      ```


*  **PS** with -o : options <br>
    ```
    ps -o "%c %y %u %n %p"

    %c = command
    %y = tty
    %u = user
    %n = nice
    %p = pid
    ```


- **Renice :** to reset the nice ID.
      ```
      renice -20 10523<pid>
      ```


- Using top utility also renice can be done.
      ```
      top
        -> r (to renice)
        -> enter pid
        -> value of nice id
      ```
