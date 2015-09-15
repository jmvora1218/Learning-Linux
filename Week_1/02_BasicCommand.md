# **_Basic Commands in Linux_**

* **touch** : Creates an Empty file.<br>
  Usage : touch filename1

* **cat** : make and view text files
  cat > file -- will add data to file. ctrl+d to save and exit

  - Sample :<br>
  ```sh
  [jkdihenkar@h4ck3r-b14ckh4t ~]$ cat > testcat
  Hello
  I am Jay<br> Now Press [ctrl+d]
  [jkdihenkar@h4ck3r-b14ckh4t ~]$ cat testcat
  Hello
  I am Jay.
  [jkdihenkar@h4ck3r-b14ckh4t ~]$ cat >> testcat
  Appended Line
  Press [ctrl d].
  [jkdihenkar@h4ck3r-b14ckh4t ~]$ cat testcat
  Hello<br>
  I am Jay<br>
  Appended(add new line) Line
  ```
* **mkdir** : creates directory
  mkdir dirname <br>
   -> mkdir -p : create chain of dir with sub dir

  - Sample :<br>
  ```sh
  [jkdihenkar@h4ck3r-b14ckh4t pragathiPlayground]$ ls
  testcat
  [jkdihenkar@h4ck3r-b14ckh4t pragathiPlayground]$ mkdir -p dir7/dir8/dir9
  [jkdihenkar@h4ck3r-b14ckh4t pragathiPlayground]$ tree
    .
    ├── dir7
    │   └── dir8
    │       └── dir9
    └── testcat

    3 directories, 1 file
    ```

* **rm** : removes file
  rm filename  <br>
  rm -r : recursively removes dir and all contents

* **rmdir** : removes empty dir

* **ls** : List Contents <br>
  ls -a : shows hidden files and dir with normal Contents.<br>
    Create hidden file : "touch .filename" ( anything begins with a "." is hidden ) <br>
  ls -l : Longlisting the contents of a dir.<br>
     Also Lists the metadata of inode.

* **ABOUT PERMISSIONS:** <br>
    - Sample: <br>
    ```PERMISSIONS
    [jkdihenkar@h4ck3r-b14ckh4t pragathiPlayground]$ ls -l
    total 8
    drwxrwxr-x. 3 jkdihenkar jkdihenkar 4096 Sep  8 08:19 dir7
    -rw-rw-r--. 1 jkdihenkar jkdihenkar   28 Sep  8 08:14 testcat
    ```
    here first char = type of inode:<br>
    d=dir -=file and c,b,l,s,l <br>
    "rwxrwxr-x" can be divided as<br>
    "rwx | rwx | r-x" <br>
    "user | group | others" permission <br>
    "3" is the link count : num of ways the file can be reached<br>
    "jkdihenkar jkdihenkar" : user | group <br>
    "4096 Sep  8 08:19 dir7" : size in bytes | timestamp of creation or updation | name of inode

  - ls -i : show inode number of a file/dir<br>
    Sample :

      [jkdihenkar@h4ck3r-b14ckh4t pragathiPlayground]$ ls -i
      1872386 dir7  1833211 testcat
  - ls -r : will recursively list everything in given path

* **pwd** : present working directory
  complete path of the dir

* **cd** : change dir
  go one level up : "cd .." : in dir hirearchy<br>
  - "./" is the current dir<br>
  - "cd ~" go to home dir<br>
  - "cd -" go to previous working dir<br>

* **cp** : copy <br>
  - cp source dest/ : copies source to dir "dest/"<br>
  - cp -R dir1 newdir/ : recursively copy everything to "newdir"

* **mv** : move / rename <br>
  mv dir1 dir2 :: moves complete dir tree dir1 to dir2/ [mv doesn't need -R]. <br>

* **df** : report free disk space
  Sample: <br>
    ```df
    [jkdihenkar@h4ck3r-b14ckh4t pragathiPlayground]$ df
    Filesystem     1K-blocks     Used Available Use% Mounted on
    devtmpfs         1964792        0   1964792   0% /dev
    tmpfs            1974812    28448   1946364   2% /dev/shm
    tmpfs            1974812     1120   1973692   1% /run
    tmpfs            1974812        0   1974812   0% /sys/fs/cgroup
    /dev/sda1       38314312 26738064   9606896  74% /
    tmpfs            1974812       32   1974780   1% /tmp
    /dev/sda2       57542652 44824412   9772192  83% /home
    tmpfs             394964        4    394960   1% /run/user/42
    tmpfs             394964       28    394936   1% /run/user/1000

  Expln :
    /dev/sda1       38314312 26738064   9606896  74% /

    df -h : will give in human readable format
```
    Sample :
      /dev/sda1        37G   26G  9.2G  74% /
* **du** : disk utilization<br>
   Size of dirs under pwd or given path

   Sample :<br>
```
    [jkdihenkar@h4ck3r-b14ckh4t pragathiPlayground]$ du -h
    4.0K	./dir7/dir8/dir9
    8.0K	./dir7/dir8
    12K	./dir7
    20K	.
    [jkdihenkar@h4ck3r-b14ckh4t pragathiPlayground]$ du -hs
    20K	.
```
* **date** : Display system's date and time.
  change date :<br>
    format -> "date MMDDhhmmYYYY.ss"

* **cal** : display calender
  Sample : <br>
  ```calender
  cal 2015
```
* **more** : displays page by page.<br>
  Sample :<br>

    "cal 2015 | more" -- "|" redirects the standart OP of cal cmd to more cmd.<br>

* **";"** : combining commands<br>
  Sample :<br>
  ```sh
  cal 2015 ; date
  ```
* **touch {a..z}** : creates empty files a b c d ... upto z

**NOTE:** Remaing Topic(ls, cat, grep, find, tty) in Book(JV).
