# Basic Command-||
* **sed:** stream editor. <br>
  - sed 's/linux/unix' file1 <br>
    search for case-sensitive linux in a file and replace it with **"unix"**. <br>
    it replaces only in OutPut stream and preview and not the file.<br>
    It replaces only first occurance in a file. <br>
  - sed 's/linux/unix/g' file1 <br>
    replaces all occurances in a line.
  - sed 's/linux/unix/gi' <br>
    global and case insensitive search.
  - sed -i 's/linux/unix/gi' <br>
    -i permanently changes a file.
  - sed -e <br>


* **awk:** <br>
  - awk -F ':' '{print $3,$5}' /etc/passwd  (-- printing fields)<br>
  - awk -F ':' '/1000/ {print $3,$5}' /etc/passwd  (--search query on display)
  - awk '{print $3}' file1  (-- default delimiter is space)
  - awk -F ':' '{ if ( $1 == "jkdihenkar" && $3 == "1000" ) print $5 }' /etc/passwd  (--if conditions in awk)


* **tty:** To know about your terminal. <br>
  O/P : /dev/pts/0 => pseudo terminal

* **/etc/passwd:** files information.

  ```
  jkdihenkar:x:1000:1000:jay dihenkar:/home/jkdihenkar:/bin/bash
    username|encrypted-pass|userid|groupid|commentGECOS|HomeDir|loginShell
    GECOS :: General Elastic Common operating system.

    ```

 - If GUI is started :
  you are in <br>

  ```
  ctrl+alt+F1 : go in command mode.
  ctrl+alt+F2 : virtual console tty2
  ctrl+alt+F3 : tty3
  ctrl+alt+F4 : tty4
  ctrl+alt+F5 : tty5
  ctrl+alt+F6 : tty6
  ```


* **who:** Who has logged in to which terminal.<br>

* **whoami:** Howto know who you are.

* **chmod:** change permissions for dile and dir.<br>
  chmod perm target/

  - Sample :<br>
    ``` chmod
    chmod 777 file1
    chmod -R 777 dir1/
    ```
* **chown:** changing owner of a file.
  - chown new-owner filename


  - Sample:
    ```
    chown jkdihenkar file1
      only root can change owner
    chown -R
      to change the owner of complete dir tree
      ```


* **chgrp:** change group.<br>
```
  chgrp new-group filename
  chgrp -R (-- recursively change grp in entire dir tree)<br>
```
* **whats :** displays online manual page description.

* **umask** -- controls the default file creation and hence
  default permissions for file creation is 666 and dir is 777. <br>
  so file created will be 666-umask. <br>
  and dir creation will be 777-umask. <br>

* **su :** For a switching user.
  - su - username : is switch user
  hence "su - jkdihenkar" will change to user to "jkdihenkar"

* Symbolic Links SoftLinks and HardLinks
   - INODE number is for kernel while filename is for endusers

  - hardlinks :  
     - ln file1 hlink
      both points to the same INODE number
      and both file are updated if anyone file is updated
  - softlinks :
    - ln -s file1 slink
      size of slink is the number of chars in file/dir name
      once the file is deleted and even of it has hardlink it will be broken.
