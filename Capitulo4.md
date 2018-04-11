# ps e jobs
 As atividades rodando conjuntamente com um sistema UNIX são chamadas "processos"
 
 `ps command: process status`
 
 example
 `ps -u username`
 
   	 PID  TTY          TIME CMD     
     2423 pts/0    00:00:00 bash
     2469 pts/0    00:00:00 atom
     2471 pts/0    00:00:52 atom
     2473 pts/0    00:00:00 atom
     2489 pts/0    00:00:21 atom
     2501 pts/0    00:01:48 atom
     2599 pts/0    00:00:00 atom
     3531 pts/0    00:00:00 Popcorn-Time
     3534 pts/0    00:00:00 Popcorn-Time
     3535 pts/0    00:00:00 nacl_helper
     3557 pts/0    00:00:00 exe
     3562 pts/0    00:00:05 Popcorn-Time
     3631 pts/0    00:00:00 ps


 
 * PID é o identificador de um processo, você pode usar o comando kill por exemplo para "matar" o processo `kill 3562` 
 * todo processo tem uma colecão de  variáveis de ambiente associadas. (Variáveis de ambiente podem ser listadas com o comando `env` )

`jobs`

* "job control", por definicão é uma facilidade shell, que permite você criar grupos de processos chamados JOBS e controla-los de sua sessão usando comandos shell.
 Um job, pode ser pensado como uma colecão de um ou mais processos.
 * Pode haver um job rodando em foreground e um ou mais rodando em background.
 * os comandos `fg` e `bg` podem ser usados para passar um job existente para foreground e background respectivamente. 


find 
-----
*   find is used to locate files on a UNIX or Linux
    system;

    *   find will search any set of directories you
        specify for files that match the search
        criteria you specify

        (you can search by attributes such as
	 name, owner, group, type, permissions,
         date, and etc.!)

    *   note it IS recursive -- it WILL search
        all subdirectories, too;

    *   basic syntax:
    
        find where-to-look criteria what-to-do

      find (without any options) prints all files recursively (including
   sub-directory paths) on Linux.
   
Common find commands:

find . -type f -name *txt -ls
    (prints all files of type File from the current path ending in "txt", and
    shows their long directory listing (permission, owner, group, length, etc.)

find /var/log -type d -ls
    (prints all directories under /var/log with permissions, owner, group,
    etc.)
   

find, part 2
-------------
*   when a find criterion involves a numeric argument,
    it can be given in 1 of 3 ways:

    n by itself - it indicates exactly the value n
    -n          - that indicates a value LESS THAN n
    +n          - that indicates a value GREATER THAN n

    so, the criterion:
    -size +1000c
    ...is satisfied by files containing MORE than 1000
       characters (bytes)

*   a few more find criteria of note:

    -type typecode
    ...is true if the file is of the specified type

    -type d    - true if file is a directory
    -type f    - true if file is an ordinary file
    -type l    - true if file is a symbolic link
    ...and a few other special kinds of files

*   -links n - true of the file has n hard links (subject to
               the numerical bit discussed earlier

*   -user uname - true if the owner of the file is user
                  uname

*   -group gname - true if the file belongs to group gname

    *   groups command lists your groups...

*   -size n
    -size nc   <-- that's a letter c following the number

    ...be true if the file is that number of 512-byte
       blocks (without the c) or that number of bytes (with
       the c)
       (subject to the number notation above)

*   -atime n - true if file was ACCESSED n days ago
    -mtime n - true if file was MODIFIED n days ago
    -ctime n - true if i-node info was modified n days ago

*   -newer fname - true if current file modified
                   MORE RECENTLY than the given file

*   -perm 
    *   octnum - true if file has exactly those permissions
    *   -octnum - true if file has at LEAST those permissions
    *   mode - CAN'T start with a dash - must match exactly
               -perm =r,u+w
    *   -mode - must match AT LEAST these permissions
                -perm -x

*   -exec cmd 
     true if the cmd returns an exit status of 0 when 
       executed as a child process

    *   often used for the SIDE-EFFECTS of cmd...!
        (e.g., removal)

    *   end of cmd (and all of its arguments) must be
        marked with a semicolon
	(and the semicolon has to be escaped so the
	shell doesn't try to interpret it)

    *   within cmd, the notation {} indicates the
        pathname of the current file being considered
 
        find crud -name "*.bak" -type f -mtime 365 -exec rm {} \;
 

