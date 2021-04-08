# unix-concepts

## Environments and Shell Variables
Unix, is capable of storing temporarily or indefinitely values or results into variables, like many other languages.

### Types of Variables:

#### 1. Environment Variables
Take particular and default value depending on the Operating System, Hardware,
previously install programs and custom setups

    E.g. $LANG environment variable:
    stores the value of the language that the user understands.
    
    Possible outputs: Eng US, Esp Latinamerican, etc.

<table align="center" border="1" class="table table-striped">
    <tbody>
        <tr>
            <th> Variable </th>
            <th><p align="center"> <strong>Description</strong> </p></th> </tr>
        <tr>
            <td> <strong>PATH</strong> </td>
            <td> This variable contains a colon
            (:)-separated list of directories in which your system looks for executable files.<br>
            </td></tr>
        <tr>
            <td> <strong>HOME</strong> </td>
            <td> Default path to the user's home directory </td>
        </tr>
        <tr>
            <td> <strong>JAVA_HOME</strong> </td>
            <td> Path to Java installation home </td>
        </tr>
        <tr>
            <td> <strong>UID</strong> </td>
            <td> User's unique ID </td> </tr>
        <tr>
            <td> <strong>TERM </strong> </td>
            <td> Default terminal emulator </td> </tr>
        <tr>
            <td> <strong>SHELL</strong> </td>
            <td> Shell being used by the user </td>
        </tr>
    </tbody>
</table>

#### 2. Shell Variables
Are created during the execution of commands or sh files.

    NAME="Nicolas"
    echo "My name is $NAME"

    myDate=date
    echo $myDate

## Basic utilities, Pipes and Filters

### Utilities
Utilities are interface shell commands that helps us with: <br>
<br> - Copying and editing Files

    mv <orgin> <destine>          - move/rename files
    cp <orgin> <destine>          - copy file
    vi <path_to_file> <file_name> - Edit File

<br> - Setting permissions

    chmod [options] <file_name>

<br> - Directories

    ls [options] <path>     - list files in directory
    rmdir [options] <path>  - remove directory
<br> - Process

    ps [options]    - list all process
    kill [options]  - kill or terminate Process

#### Pipes and Filters

You can use grep to filter results

    eg ls -l | grep *.txt

http://www.unix.org/version3/apis/cu.html

## Process Management and communications

Everitime you execute a program on your Unix system.
The operating system tracks processes through a five-digit ID number known as the pid or the process ID.
Each process in the system has a unique pid.

### Types of Process

#### 1. Foreground Processes
Display the output on the screen

    E.G. ls -l
    Displays 

#### 2. Foreground Processes
Hides the output from the screen <br>
You can hide process fro being shown by adding `&` at the end.
    
    E.G. ls -l &

### Listing Process

The esasiest way to view all process is by running the ps (process status) command as follows −

    $ps
    PID       TTY      TIME        CMD
    18358     ttyp3    00:00:00    sh
    18361     ttyp3    00:01:31    abiword
    18789     ttyp3    00:00:00    ps

You can also use the -f flag, to display full information

    $ps -f
    UID      PID  PPID C STIME    TTY   TIME CMD
    amrood   6738 3662 0 10:23:03 pts/6 0:00 first_one
    amrood   6739 3662 0 10:22:54 pts/6 0:00 second_one
    amrood   3662 3657 0 08:10:53 pts/6 0:00 -ksh
    amrood   6892 3662 4 10:51:50 pts/6 0:00 ps -f

<table>
    <tr>
        <td><strong>Parent and Child Processes</strong></td>
        <td>A parent process can create sub process to complete their actions</td>
    </tr>
    <tr>
        <td><strong>Zombie and Orphan Processes</strong></td>
        <td>Sometimes the parent process is killed before its child is killed</td>
    </tr>
    <tr>
        <td><strong>Daemon Processes</strong></td>
        <td>To be precise, a daemon is a process that runs in the background, usually waiting for something to happen that it is capable of working with. For example, a printer daemon waiting for print commands.</td>
    </tr>
</table>

### Finding a process
You can use grep to filter processes

    eg ps -f | grep java

### killing a Process

To stop or kill a process you can use this command:

    kill [options] <process_id>

### FTP

The FTP (File Transfer Protocol) utility program.<br>
Other words is a way to transfer a file from computer to computer.

#### 1. Connect to a FTP site

    $ ftp IP/hostname

or 

    $ ftp
    ftp> open IP/hostname

#### 2. Download a file using ftp

Use the get command to download file from a remote ftp server as shown below.

    ftp> get FILENAME
    
Download the file and save it with another name. In the following example, index.html file will be downloaded and saved as my.html on the local server.

    ftp> get index.html my.html
    Fetching /home/groups/index.html to my.html
    
    /home/groups/index.html           100% 2886     1.4KB/s   00:02

#### 3. Uploading a file to FTP server

Use put command to upload a file to a remote ftp server as shown below.

    ftp> put filename

#### exit ftp mode

Simply type `bye` to exit

    bye

More references:<br>
https://victorroblesweb.es/2013/12/02/comandos-ftp-en-la-consola/

### ping

You can use the ping command to test the connection between the local server/computer and a remote UNIX server.  <br>
The ping command sends ICMP Echo Request (ECHO_REQUEST) packets to the host once per second. <br>

1. If a remote server is up and running.
2. Test network problems.
3. Test network connectivity to your local or remote gateways.
4. Verify network problems.

##### Examples

    ping serverNameHere
    ping ServerIPAddress
    ping 192.168.1.2
    ping www.cyberciti.biz

### Vi Editor

Vim is a text editor that is upwards compatible to Vi. <br>
It can be used to edit all kinds of plain text. <br>
It is especially useful for editing programs.

    vim [options] <filename>

#### Modes

:help [keyword] - Performs a search of help documentation for whatever keyword you enter

:e [file] - Opens a file, where [file] is the name of the file you want opened

:w - Saves the file you are working on

:w [filename] - Allows you to save your file with the name you've defined

:wq - Save your file and close Vim

:q! - Quit without first saving the file you were working on

#### Simple Vim workflow example

Open a new or existing file with vim filename.

     1. Type i to switch into insert mode so that you can start editing the file.
     2. Enter or modify the text with your file.
     3. Once you're done, press the escape key Esc to get out of insert mode and back to command mode.
     4. Type :wq to save and exit your file.

#### Vim commands for searching text

/[keyword] - Searches for text in the document where keyword is whatever keyword,
phrase or string of characters you're looking for



