# Linux Command 
Wiki Welcome to the Linux command wiki, providing information about commonly used Linux commands. 
## Table of Contents 
1. [Navigation Commands](#navigation-commands) 
2. [File Management Commands](#file-management-commands) 
3. [System Information Commands](#system-information-commands) 
4. [Process Management Commands](#process-management-commands) 
5. [Package Management Commands](#package-management-commands)
## Basic list
|Name|Category|Status (Option code)|Description|First appeared|
|---|---|---|---|---|
|[`admin`](https://en.wikipedia.org/w/index.php?title=Admin_(Unix)&action=edit&redlink=1 "Admin (Unix) (page does not exist)")|[SCCS](https://en.wikipedia.org/wiki/Source_Code_Control_System "Source Code Control System")|Optional (XSI)|Create and administer [SCCS](https://en.wikipedia.org/wiki/Source_Code_Control_System "Source Code Control System") files|PWB UNIX|
|[`alias`](https://en.wikipedia.org/wiki/Alias_(command) "Alias (command)")|Misc|Mandatory|Define or display aliases||
|[`ar`](https://en.wikipedia.org/wiki/Ar_(Unix) "Ar (Unix)")|Misc|Mandatory|Create and maintain [library](https://en.wikipedia.org/wiki/Library_(computing) "Library (computing)") archives|Version 1 AT&T UNIX|
|[`asa`](https://en.wikipedia.org/wiki/Asa_(Unix) "Asa (Unix)")|Text processing|Optional (FR)|Interpret carriage-control characters|System V|
|[`at`](https://en.wikipedia.org/wiki/At_(command) "At (command)")|Process management|Mandatory|Execute commands at a later time|Version 7 AT&T UNIX|
|[`awk`](https://en.wikipedia.org/wiki/AWK "AWK")|Text processing|Mandatory|Pattern scanning and processing language|Version 7 AT&T UNIX|
|[`basename`](https://en.wikipedia.org/wiki/Basename "Basename")|Filesystem|Mandatory|Return non-directory portion of a pathname; see also dirname|Version 7 AT&T UNIX|
|[`batch`](https://en.wikipedia.org/wiki/Batch_(Unix) "Batch (Unix)")|Process management|Mandatory|Schedule commands to be executed in a batch queue||
|[`bc`](https://en.wikipedia.org/wiki/Bc_(programming_language) "Bc (programming language)")|Misc|Mandatory|[Arbitrary-precision arithmetic](https://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic "Arbitrary-precision arithmetic") language|Version 6 AT&T UNIX|
|[`bg`](https://en.wikipedia.org/wiki/Bg_(Unix) "Bg (Unix)")|Process management|Optional (UP)|Run jobs in the background||
|[`cc`](https://en.wikipedia.org/wiki/C_compiler "C compiler")/[`c99`](https://en.wikipedia.org/wiki/C99 "C99")|C programming|Optional (CD)|[Compile](https://en.wikipedia.org/wiki/Compiler "Compiler") standard [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") programs|IEEE Std 1003.1-2001|
|[`cal`](https://en.wikipedia.org/wiki/Cal_(command) "Cal (command)")|Misc|Optional (XSI)|Print a calendar|Version 5 AT&T UNIX|
|[`cat`](https://en.wikipedia.org/wiki/Cat_(Unix) "Cat (Unix)")|Filesystem|Mandatory|Concatenate and print files|PDP-7 UNIX|
|[`cd`](https://en.wikipedia.org/wiki/Cd_(command) "Cd (command)")|Filesystem|Mandatory|Change the working directory|Version 6 AT&T UNIX|
|[`cflow`](https://en.wikipedia.org/wiki/Cflow "Cflow")|C programming|Optional (XSI)|Generate a C-language [call graph](https://en.wikipedia.org/wiki/Call_graph "Call graph")|System V|
|[`chgrp`](https://en.wikipedia.org/wiki/Chgrp "Chgrp")|Filesystem|Mandatory|Change the file group ownership|PWB UNIX|
|[`chmod`](https://en.wikipedia.org/wiki/Chmod "Chmod")|Filesystem|Mandatory|Change the file modes/attributes/permissions|PDP-7 UNIX|
|[`chown`](https://en.wikipedia.org/wiki/Chown "Chown")|Filesystem|Mandatory|Change the file ownership|PDP-7 UNIX|
|[`cksum`](https://en.wikipedia.org/wiki/Cksum "Cksum")|Filesystem|Mandatory|Write file [checksums](https://en.wikipedia.org/wiki/Checksum "Checksum") and sizes|4.4BSD|
|[`cmp`](https://en.wikipedia.org/wiki/Cmp_(Unix) "Cmp (Unix)")|Filesystem|Mandatory|Compare two files; see also diff|Version 1 AT&T UNIX|
|[`comm`](https://en.wikipedia.org/wiki/Comm "Comm")|Text processing|Mandatory|Select or reject lines common to two files|Version 4 AT&T UNIX|
|[`command`](https://en.wikipedia.org/wiki/Command_(Unix) "Command (Unix)")|Shell programming|Mandatory|Execute a simple command||
|[`compress`](https://en.wikipedia.org/wiki/Compress "Compress")|Filesystem|Optional (XSI)|Compress data|4.3BSD|
|[`cp`](https://en.wikipedia.org/wiki/Cp_(Unix) "Cp (Unix)")|Filesystem|Mandatory|Copy files|PDP-7 UNIX|
|[`crontab`](https://en.wikipedia.org/wiki/Crontab "Crontab")|Misc|Mandatory|Schedule periodic background work|System V|
|[`csplit`](https://en.wikipedia.org/wiki/Csplit "Csplit")|Text processing|Mandatory|Split files based on context|PWB UNIX|
|[`ctags`](https://en.wikipedia.org/wiki/Ctags "Ctags")|C programming|Optional (SD)|Create a tags file|3BSD|
|[`cut`](https://en.wikipedia.org/wiki/Cut_(Unix) "Cut (Unix)")|Text processing|Mandatory|Cut out selected fields of each line of a file|System III|
|[`cxref`](https://en.wikipedia.org/wiki/Cxref "Cxref")|C programming|Optional (XSI)|Generate a [C-language](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") program cross-reference table|System V|
|[`date`](https://en.wikipedia.org/wiki/Unix_time#Command_line "Unix time")|Misc|Mandatory|Display the date and time|Version 1 AT&T UNIX|
|[`dd`](https://en.wikipedia.org/wiki/Dd_(Unix) "Dd (Unix)")|Filesystem|Mandatory|Convert and copy a file|Version 5 AT&T UNIX|
|[`delta`](https://en.wikipedia.org/wiki/Delta_(Unix) "Delta (Unix)")|SCCS|Optional (XSI)|Make a delta (change) to an SCCS file|PWB UNIX|
|[`df`](https://en.wikipedia.org/wiki/Df_(Unix) "Df (Unix)")|Filesystem|Mandatory|Report free disk space|Version 1 AT&T UNIX|
|[`diff`](https://en.wikipedia.org/wiki/Diff "Diff")|Text processing|Mandatory|Compare two files; see also cmp|Version 5 AT&T UNIX|
|[`dirname`](https://en.wikipedia.org/wiki/Dirname "Dirname")|Filesystem|Mandatory|Return the directory portion of a pathname; see also basename|System III|
|[`du`](https://en.wikipedia.org/wiki/Du_(Unix) "Du (Unix)")|Filesystem|Mandatory|Estimate file space usage|Version 1 AT&T UNIX|
|[`echo`](https://en.wikipedia.org/wiki/Echo_(command) "Echo (command)")|Shell programming|Mandatory|Write arguments to standard output|Version 2 AT&T UNIX|
|[`ed`](https://en.wikipedia.org/wiki/Ed_(text_editor) "Ed (text editor)")|Text processing|Mandatory|The standard text editor|PDP-7 UNIX|
|[`env`](https://en.wikipedia.org/wiki/Env_(shell) "Env (shell)")|Misc|Mandatory|Set the environment for command invocation|System III|
|[`ex`](https://en.wikipedia.org/wiki/Ex_(text_editor) "Ex (text editor)")|Text processing|Optional (UP)|Text editor|1BSD|
|[`expand`](https://en.wikipedia.org/wiki/Expand_(Unix) "Expand (Unix)")|Text processing|Mandatory|Convert tabs to spaces|3BSD|
|[`expr`](https://en.wikipedia.org/wiki/Expr "Expr")|Shell programming|Mandatory|Evaluate arguments as an expression|Version 7 AT&T UNIX|
|[`false`](https://en.wikipedia.org/wiki/False_(Unix) "False (Unix)")|Shell programming|Mandatory|Return false value|Version 7 AT&T UNIX|
|[`fc`](https://en.wikipedia.org/wiki/Fc_(Unix) "Fc (Unix)")|Misc|Optional (UP)|Process the command history list||
|[`fg`](https://en.wikipedia.org/wiki/Fg_(Unix) "Fg (Unix)")|Process management|Optional (UP)|Run jobs in the foreground||
|[`file`](https://en.wikipedia.org/wiki/File_(command) "File (command)")|Filesystem|Mandatory|Determine file type|Version 4 AT&T UNIX|
|[`find`](https://en.wikipedia.org/wiki/Find_(Unix) "Find (Unix)")|Filesystem|Mandatory|Find files|Version 1 AT&T UNIX|
|[`fold`](https://en.wikipedia.org/wiki/Fold_(Unix) "Fold (Unix)")|Text processing|Mandatory|Filter for folding lines|1BSD|
|[`fort77`](https://en.wikipedia.org/wiki/Fort77 "Fort77")|FORTRAN77 programming|Obsolescent (FD)|[FORTRAN](https://en.wikipedia.org/wiki/FORTRAN "FORTRAN") compiler|XPG4|
|[`fuser`](https://en.wikipedia.org/wiki/Fuser_(Unix) "Fuser (Unix)")|Process management|Optional (XSI)|List [process IDs](https://en.wikipedia.org/wiki/Process_identifier "Process identifier") of all processes that have one or more files open|System V|
|[`gencat`](https://en.wikipedia.org/wiki/Gencat "Gencat")|Misc|Mandatory|Generate a formatted message catalog||
|[`get`](https://en.wikipedia.org/w/index.php?title=Get_(Unix)&action=edit&redlink=1 "Get (Unix) (page does not exist)")|SCCS|Optional (XSI)|Get a version of an SCCS file|PWB UNIX|
|[`getconf`](https://en.wikipedia.org/wiki/Getconf "Getconf")|Misc|Mandatory|Get configuration values||
|[`getopts`](https://en.wikipedia.org/wiki/Getopts "Getopts")|Shell programming|Mandatory|Parse utility options||
|[`grep`](https://en.wikipedia.org/wiki/Grep "Grep")|Misc|Mandatory|Search text for a pattern|Version 4 AT&T UNIX|
|[`hash`](https://en.wikipedia.org/wiki/Hash_(Unix) "Hash (Unix)")|Misc|Mandatory|Hash database access method||
|[`head`](https://en.wikipedia.org/wiki/Head_(Unix) "Head (Unix)")|Text processing|Mandatory|Copy the first part of files|PWB UNIX[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|[`iconv`](https://en.wikipedia.org/wiki/Iconv "Iconv")|Text processing|Mandatory|Codeset conversion|HP-UX|
|[`id`](https://en.wikipedia.org/wiki/Id_(Unix) "Id (Unix)")|Misc|Mandatory|Return user identity|System V|
|[`ipcrm`](https://en.wikipedia.org/wiki/Ipcrm "Ipcrm")|Misc|Optional (XSI)|Remove a message queue, semaphore set, or shared memory segment identifier|System V|
|[`ipcs`](https://en.wikipedia.org/wiki/Ipcs "Ipcs")|Misc|Optional (XSI)|Report interprocess communication facilities status|System V|
|[`jobs`](https://en.wikipedia.org/w/index.php?title=Jobs_(Unix)&action=edit&redlink=1 "Jobs (Unix) (page does not exist)")|Process management|Optional (UP)|Display status of jobs in the current session||
|[`join`](https://en.wikipedia.org/wiki/Join_(Unix) "Join (Unix)")|Text processing|Mandatory|Merges two sorted text files based on the presence of a common field|Version 7 AT&T UNIX|
|[`kill`](https://en.wikipedia.org/wiki/Kill_(command) "Kill (command)")|Process management|Mandatory|Terminate or signal processes|Version 4 AT&T UNIX|
|[`lex`](https://en.wikipedia.org/wiki/Lex_programming_tool "Lex programming tool")|C programming|Optional (CD)|Generate programs for [lexical tasks](https://en.wikipedia.org/wiki/Lexical_analyzer "Lexical analyzer")|Version 7 AT&T UNIX|
|[`link`](https://en.wikipedia.org/wiki/Link_(Unix) "Link (Unix)")|Filesystem|Optional (XSI)|Create a hard link to a file|Version 1 AT&T UNIX|
|[`ln`](https://en.wikipedia.org/wiki/Ln_(Unix) "Ln (Unix)")|Filesystem|Mandatory|Link files|Version 1 AT&T UNIX|
|[`locale`](https://en.wikipedia.org/w/index.php?title=Locale_(Unix_command)&action=edit&redlink=1 "Locale (Unix command) (page does not exist)")|Misc|Mandatory|Get locale-specific information||
|[`localedef`](https://en.wikipedia.org/wiki/Localedef "Localedef")|Misc|Mandatory|Define locale environment||
|[`logger`](https://en.wikipedia.org/w/index.php?title=Logger_(Unix)&action=edit&redlink=1 "Logger (Unix) (page does not exist)")|Shell programming|Mandatory|Log messages|4.3BSD|
|[`logname`](https://en.wikipedia.org/wiki/Logname "Logname")|Misc|Mandatory|Return the user's login name|4.4BSD|
|[`lp`](https://en.wikipedia.org/wiki/Lp_(Unix) "Lp (Unix)")|Text processing|Mandatory|Send files to a printer|System V|
|[`ls`](https://en.wikipedia.org/wiki/Ls "Ls")|Filesystem|Mandatory|List directory contents|Version 1 AT&T UNIX|
|[`m4`](https://en.wikipedia.org/wiki/M4_(computer_language) "M4 (computer language)")|Misc|Mandatory|Macro processor|PWB UNIX|
|[`mailx`](https://en.wikipedia.org/wiki/Mailx "Mailx")|Misc|Mandatory|Process messages|Version 1 AT&T UNIX|
|[`make`](https://en.wikipedia.org/wiki/Make_(software) "Make (software)")|Programming|Optional (SD)|Maintain, update, and regenerate groups of programs|PWB UNIX|
|[`man`](https://en.wikipedia.org/wiki/Man_page "Man page")|Misc|Mandatory|Display system documentation|Version 2 AT&T UNIX|
|[`mesg`](https://en.wikipedia.org/wiki/Mesg "Mesg")|Misc|Mandatory|Permit or deny messages|Version 1 AT&T UNIX|
|[`mkdir`](https://en.wikipedia.org/wiki/Mkdir "Mkdir")|Filesystem|Mandatory|Make directories|Version 1 AT&T UNIX|
|[`mkfifo`](https://en.wikipedia.org/wiki/Mkfifo "Mkfifo")|Filesystem|Mandatory|Make [FIFO](https://en.wikipedia.org/wiki/FIFO_(computing_and_electronics) "FIFO (computing and electronics)") special files|4.4BSD[_[dubious](https://en.wikipedia.org/wiki/Wikipedia:Accuracy_dispute#Disputed_statement "Wikipedia:Accuracy dispute") – [discuss](https://en.wikipedia.org/wiki/Talk:List_of_Unix_commands#mkfifo "Talk:List of Unix commands")_]|
|[`more`](https://en.wikipedia.org/wiki/More_(command) "More (command)")|Text processing|Optional (UP)|Display files on a page-by-page basis|3BSD|
|[`mv`](https://en.wikipedia.org/wiki/Mv_(Unix) "Mv (Unix)")|Filesystem|Mandatory|Move or rename files|Version 1 AT&T UNIX|
|[`newgrp`](https://en.wikipedia.org/wiki/Newgrp "Newgrp")|Misc|Mandatory|Change to a new group|Version 6 AT&T UNIX|
|[`nice`](https://en.wikipedia.org/wiki/Nice_(Unix) "Nice (Unix)")|Process management|Mandatory|Invoke a utility with an altered nice value|Version 4 AT&T UNIX|
|[`nl`](https://en.wikipedia.org/wiki/Nl_(Unix) "Nl (Unix)")|Text processing|Optional (XSI)|Line numbering filter|System III|
|[`nm`](https://en.wikipedia.org/wiki/Nm_(Unix) "Nm (Unix)")|C programming|Optional (SD, XSI)|Write the name list of an [object file](https://en.wikipedia.org/wiki/Object_file "Object file")|Version 1 AT&T UNIX|
|[`nohup`](https://en.wikipedia.org/wiki/Nohup "Nohup")|Process management|Mandatory|Invoke a utility immune to [hangups](https://en.wikipedia.org/wiki/SIGHUP "SIGHUP")|Version 4 AT&T UNIX|
|[`od`](https://en.wikipedia.org/wiki/Od_(Unix) "Od (Unix)")|Misc|Mandatory|Dump files in various formats|Version 1 AT&T UNIX|
|[`paste`](https://en.wikipedia.org/wiki/Paste_(Unix) "Paste (Unix)")|Text processing|Mandatory|Merge corresponding or subsequent lines of files|Version 32V AT&T UNIX|
|[`patch`](https://en.wikipedia.org/wiki/Patch_(Unix) "Patch (Unix)")|Text processing|Mandatory|Apply changes to files|4.3BSD|
|[`pathchk`](https://en.wikipedia.org/wiki/Pathchk "Pathchk")|Filesystem|Mandatory|Check pathnames||
|[`pax`](https://en.wikipedia.org/wiki/Pax_(command) "Pax (command)")|Misc|Mandatory|Portable archive interchange|4.4BSD[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|[`pr`](https://en.wikipedia.org/wiki/Pr_(Unix) "Pr (Unix)")|Text processing|Mandatory|Print files|Version 1 AT&T UNIX|
|[`printf`](https://en.wikipedia.org/wiki/Printf_(Unix) "Printf (Unix)")|Shell programming|Mandatory|Write formatted output|4.3BSD-Reno|
|[`prs`](https://en.wikipedia.org/w/index.php?title=Prs&action=edit&redlink=1 "Prs (page does not exist)")|SCCS|Optional (XSI)|Print an SCCS file|PWB UNIX|
|[`ps`](https://en.wikipedia.org/wiki/Ps_(Unix) "Ps (Unix)")|Process management|Mandatory|Report process status|Version 4 AT&T UNIX|
|[`pwd`](https://en.wikipedia.org/wiki/Pwd "Pwd")|Filesystem|Mandatory|Print working directory|Version 5 AT&T UNIX|
|[`qalter`](https://en.wikipedia.org/wiki/Qalter "Qalter")|Batch utilities|Obsolescent (BE)|Alter batch job||
|[`qdel`](https://en.wikipedia.org/w/index.php?title=Qdel&action=edit&redlink=1 "Qdel (page does not exist)")|Batch utilities|Obsolescent (BE)|Delete batch jobs||
|[`qhold`](https://en.wikipedia.org/w/index.php?title=Qhold&action=edit&redlink=1 "Qhold (page does not exist)")|Batch utilities|Obsolescent (BE)|Hold batch jobs||
|[`qmove`](https://en.wikipedia.org/w/index.php?title=Qmove&action=edit&redlink=1 "Qmove (page does not exist)")|Batch utilities|Obsolescent (BE)|Move batch jobs||
|[`qmsg`](https://en.wikipedia.org/w/index.php?title=Qmsg&action=edit&redlink=1 "Qmsg (page does not exist)")|Batch utilities|Obsolescent (BE)|Send message to batch jobs||
|[`qrerun`](https://en.wikipedia.org/w/index.php?title=Qrerun&action=edit&redlink=1 "Qrerun (page does not exist)")|Batch utilities|Obsolescent (BE)|Rerun batch jobs||
|[`qrls`](https://en.wikipedia.org/w/index.php?title=Qrls&action=edit&redlink=1 "Qrls (page does not exist)")|Batch utilities|Obsolescent (BE)|Release batch jobs||
|[`qselect`](https://en.wikipedia.org/wiki/Qselect "Qselect")|Batch utilities|Obsolescent (BE)|Select batch jobs||
|[`qsig`](https://en.wikipedia.org/w/index.php?title=Qsig&action=edit&redlink=1 "Qsig (page does not exist)")|Batch utilities|Obsolescent (BE)|Signal batch jobs||
|[`qstat`](https://en.wikipedia.org/w/index.php?title=Qstat_(Unix)&action=edit&redlink=1 "Qstat (Unix) (page does not exist)")|Batch utilities|Obsolescent (BE)|Show status of batch jobs||
|[`qsub`](https://en.wikipedia.org/wiki/Qsub "Qsub")|Batch utilities|Obsolescent (BE)|Submit a script||
|[`read`](https://en.wikipedia.org/wiki/Read_(Unix) "Read (Unix)")|Shell programming|Mandatory|Read a line from standard input||
|`readlink`|Misc||Returns the target of a [symbolic link](https://en.wikipedia.org/wiki/Symbolic_link "Symbolic link")|2.1BSD[[1]](https://en.wikipedia.org/wiki/List_of_Unix_commands#cite_note-1)|
|[`renice`](https://en.wikipedia.org/wiki/Renice "Renice")|Process management|Mandatory|Set nice values of running processes|4BSD|
|[`rm`](https://en.wikipedia.org/wiki/Rm_(Unix) "Rm (Unix)")|Filesystem|Mandatory|Remove directory entries|Version 1 AT&T UNIX|
|[`rmdel`](https://en.wikipedia.org/wiki/Rmdel "Rmdel")|SCCS|Optional (XSI)|Remove a delta from an SCCS file|PWB UNIX|
|[`rmdir`](https://en.wikipedia.org/wiki/Rmdir "Rmdir")|Filesystem|Mandatory|Remove directories, if they are empty.|Version 1 AT&T UNIX|
|[`sact`](https://en.wikipedia.org/w/index.php?title=Sact_(Unix)&action=edit&redlink=1 "Sact (Unix) (page does not exist)")|SCCS|Optional (XSI)|Print current SCCS file-editing activity|System III|
|[`sccs`](https://en.wikipedia.org/wiki/Source_Code_Control_System "Source Code Control System")|[SCCS](https://en.wikipedia.org/wiki/Source_Code_Control_System "Source Code Control System")|Optional (XSI)|Front end for the SCCS subsystem|4.3BSD|
|[`sed`](https://en.wikipedia.org/wiki/Sed "Sed")|Text processing|Mandatory|Stream editor|Version 7 AT&T UNIX|
|[`sh`](https://en.wikipedia.org/wiki/Bourne_shell "Bourne shell")|Shell programming|Mandatory|[Shell](https://en.wikipedia.org/wiki/Unix_shell "Unix shell"), the standard command language interpreter|Version 7 AT&T UNIX (in earlier versions, sh was either the [Thompson shell](https://en.wikipedia.org/wiki/Thompson_shell "Thompson shell") or the [PWB shell](https://en.wikipedia.org/wiki/PWB_shell "PWB shell"))|
|[`sleep`](https://en.wikipedia.org/wiki/Sleep_(command) "Sleep (command)")|Shell programming|Mandatory|Suspend execution for an interval|Version 4 AT&T UNIX|
|[`sort`](https://en.wikipedia.org/wiki/Sort_(Unix) "Sort (Unix)")|Text processing|Mandatory|Sort, merge, or sequence check text files|Version 1 AT&T UNIX|
|[`split`](https://en.wikipedia.org/wiki/Split_(Unix) "Split (Unix)")|Misc|Mandatory|Split files into pieces|Version 3 AT&T UNIX|
|[`strings`](https://en.wikipedia.org/wiki/Strings_(Unix) "Strings (Unix)")|C programming|Mandatory|Find printable strings in files|2BSD|
|[`strip`](https://en.wikipedia.org/wiki/Strip_(Unix) "Strip (Unix)")|C programming|Optional (SD)|Remove unnecessary information from executable files|Version 1 AT&T UNIX|
|`stty`|Misc|Mandatory|Set the options for a terminal|Version 2 AT&T UNIX|
|[`tabs`](https://en.wikipedia.org/w/index.php?title=Tabs_(Unix)&action=edit&redlink=1 "Tabs (Unix) (page does not exist)")|Misc|Mandatory|Set terminal tabs|PWB UNIX|
|[`tail`](https://en.wikipedia.org/wiki/Tail_(Unix) "Tail (Unix)")|Text processing|Mandatory|Copy the last part of a file|PWB UNIX[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_]|
|[`talk`](https://en.wikipedia.org/wiki/Talk_(software) "Talk (software)")|Misc|Optional (UP)|Talk to another user|4.2BSD|
|[`tee`](https://en.wikipedia.org/wiki/Tee_(command) "Tee (command)")|Shell programming|Mandatory|Duplicate the [standard output](https://en.wikipedia.org/wiki/Standard_streams "Standard streams")|Version 5 AT&T UNIX|
|[`test`](https://en.wikipedia.org/wiki/Test_(Unix) "Test (Unix)")|Shell programming|Mandatory|Evaluate [expression](https://en.wikipedia.org/wiki/Expression_(computer_science) "Expression (computer science)")|Version 7 AT&T UNIX|
|[`time`](https://en.wikipedia.org/wiki/Time_(Unix) "Time (Unix)")|Process management|Mandatory|Time a simple command|Version 3 AT&T UNIX|
|[`touch`](https://en.wikipedia.org/wiki/Touch_(command) "Touch (command)")|Filesystem|Mandatory|Change file access and modification times|Version 7 AT&T UNIX|
|[`tput`](https://en.wikipedia.org/wiki/Tput "Tput")|Misc|Mandatory|Change [terminal](https://en.wikipedia.org/wiki/Computer_terminal "Computer terminal") characteristics|System V|
|[`tr`](https://en.wikipedia.org/wiki/Tr_(Unix) "Tr (Unix)")|Text processing|Mandatory|Translate characters|Version 4 AT&T UNIX|
|[`true`](https://en.wikipedia.org/wiki/True_(Unix) "True (Unix)")|Shell programming|Mandatory|Return true value|Version 7 AT&T UNIX|
|[`tsort`](https://en.wikipedia.org/wiki/Tsort_(Unix) "Tsort (Unix)")|Text processing|Mandatory|Topological sort|Version 7 AT&T UNIX|
|[`tty`](https://en.wikipedia.org/wiki/Tty_(unix) "Tty (unix)")|Misc|Mandatory|Return user's [terminal](https://en.wikipedia.org/wiki/Computer_terminal "Computer terminal") name|Version 1 AT&T UNIX|
|[`type`](https://en.wikipedia.org/wiki/Type_(Unix) "Type (Unix)")|Misc|Optional (XSI)|Displays how a name would be interpreted if used as a command||
|[`ulimit`](https://en.wikipedia.org/w/index.php?title=Ulimit&action=edit&redlink=1 "Ulimit (page does not exist)")|Misc|Optional (XSI)|Set or report file size limit||
|[`umask`](https://en.wikipedia.org/wiki/Umask "Umask")|Misc|Mandatory|Get or set the file mode creation mask|System III|
|[`unalias`](https://en.wikipedia.org/wiki/Unalias "Unalias")|Misc|Mandatory|Remove alias definitions||
|[`uname`](https://en.wikipedia.org/wiki/Uname "Uname")|Misc|Mandatory|Return system name|PWB UNIX|
|[`uncompress`](https://en.wikipedia.org/wiki/Uncompress "Uncompress")|Misc|Optional (XSI)|Expand compressed data|4.3BSD|
|[`unexpand`](https://en.wikipedia.org/wiki/Unexpand "Unexpand")|Text processing|Mandatory|Convert spaces to tabs|3BSD|
|[`unget`](https://en.wikipedia.org/w/index.php?title=Unget&action=edit&redlink=1 "Unget (page does not exist)")|SCCS|Optional (XSI)|Undo a previous get of an SCCS file|System III|
|[`uniq`](https://en.wikipedia.org/wiki/Uniq "Uniq")|Text processing|Mandatory|Report or filter out repeated lines in a file|Version 3 AT&T UNIX|
|[`unlink`](https://en.wikipedia.org/wiki/Unlink_(Unix) "Unlink (Unix)")|Filesystem|Optional (XSI)|Call the unlink function|Version 1 AT&T UNIX|
|[`uucp`](https://en.wikipedia.org/wiki/Uucp "Uucp")|Network|Optional (UU)|System-to-system copy|Version 7 AT&T UNIX|
|[`uudecode`](https://en.wikipedia.org/wiki/Uudecode "Uudecode")|Network|Mandatory|Decode a binary file|4BSD|
|[`uuencode`](https://en.wikipedia.org/wiki/Uuencode "Uuencode")|Network|Mandatory|Encode a binary file|4BSD|
|[`uustat`](https://en.wikipedia.org/wiki/Uustat "Uustat")|Network|Optional (UU)|[uucp](https://en.wikipedia.org/wiki/Uucp "Uucp") status inquiry and job control|System III|
|[`uux`](https://en.wikipedia.org/w/index.php?title=Uux_(Unix)&action=edit&redlink=1 "Uux (Unix) (page does not exist)")|Process management|Optional (UU)|Remote command execution|Version 7 AT&T UNIX|
|[`val`](https://en.wikipedia.org/w/index.php?title=Val_(Unix)&action=edit&redlink=1 "Val (Unix) (page does not exist)")|SCCS|Optional (XSI)|Validate SCCS files|System III|
|[`vi`](https://en.wikipedia.org/wiki/Vi "Vi")|Text processing|Optional (UP)|Screen-oriented (visual) display editor|1BSD|
|[`wait`](https://en.wikipedia.org/wiki/Wait_(command) "Wait (command)")|Process management|Mandatory|Await process completion|Version 4 AT&T UNIX|
|[`wc`](https://en.wikipedia.org/wiki/Wc_(Unix) "Wc (Unix)")|Text processing|Mandatory|Line, word and byte or character count|Version 1 AT&T UNIX|
|`what`|[SCCS](https://en.wikipedia.org/wiki/Source_Code_Control_System "Source Code Control System")|Optional (XSI)|Identify SCCS files|PWB UNIX|
|[`who`](https://en.wikipedia.org/wiki/Who_(Unix) "Who (Unix)")|System administration|Mandatory|Display who is on the system|Version 1 AT&T UNIX|
|[`write`](https://en.wikipedia.org/wiki/Write_(Unix) "Write (Unix)")|Misc|Mandatory|Write to another user's terminal|Version 1 AT&T UNIX|
|[`xargs`](https://en.wikipedia.org/wiki/Xargs "Xargs")|Shell programming|Mandatory|Construct argument lists and invoke utility|PWB UNIX|
|[`yacc`](https://en.wikipedia.org/wiki/Yacc "Yacc")|C programming|Optional (CD)|Yet another [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler") compiler|PWB UNIX|
|[`zcat`](https://en.wikipedia.org/wiki/Zcat "Zcat")|Text processing|Optional (XSI)|Expand and concatenate data|4.3BSD|
## Advance list
|   |   |   |
|---|---|---|
|A|||
||[&](https://ss64.com/bash/bg.html)|Start a new process in the background|
||[alias](https://ss64.com/bash/alias.html)|Create an alias •|
||[apropos](https://ss64.com/bash/apropos.html)|Search Help manual pages (man -k)|
||[apt](https://ss64.com/bash/apt.html)|Search for and install software packages (Debian/Ubuntu)|
||[apt-get](https://ss64.com/bash/apt-get.html)|Search for and install software packages (Debian/Ubuntu)|
||[aptitude](https://ss64.com/bash/aptitude.html)|Search for and install software packages (Debian/Ubuntu)|
||[aspell](https://ss64.com/bash/aspell.html)|Spell Checker|
||[at](https://ss64.com/bash/at.html)|Schedule a command to run once at a particular time|
||[awk](https://ss64.com/bash/awk.html)|Find and Replace text, database sort/validate/index|
|B|||
||[basename](https://ss64.com/bash/basename.html)|Strip directory and suffix from filenames|
||[base32](https://ss64.com/bash/base32.html)|Base32 encode/decode data and print to standard output|
||[base64](https://ss64.com/bash/base64.html)|Base64 encode/decode data and print to standard output|
||[bash](https://ss64.com/bash/bash.html)|GNU Bourne-Again SHell|
||[bc](https://ss64.com/bash/bc.html)|Arbitrary precision calculator language|
||[bg](https://ss64.com/bash/bg.html)|Send to background|
||[bind](https://ss64.com/bash/bind.html)|Set or display readline key and function bindings •|
||[break](https://ss64.com/bash/break.html)|Exit from a loop •|
||[builtin](https://ss64.com/bash/builtin.html)|Run a shell builtin|
||[bzip2](https://ss64.com/bash/bzip2.html)|Compress or decompress named file(s)|
|C|||
||[cal](https://ss64.com/bash/cal.html)|Display a calendar|
||[caller](https://ss64.com/bash/caller.html)|Return the context of any active subroutine call •|
||[case](https://ss64.com/bash/case.html)|Conditionally perform a command|
||[cat](https://ss64.com/bash/cat.html)|Concatenate and print (display) the content of files|
||[cd](https://ss64.com/bash/cd.html)|Change Directory|
||[cfdisk](https://ss64.com/bash/cfdisk.html)|Partition table manipulator for Linux|
||[chattr](https://ss64.com/bash/chattr.html)|Change file attributes on a Linux file system|
||[chgrp](https://ss64.com/bash/chgrp.html)|Change group ownership|
||[chmod](https://ss64.com/bash/chmod.html)|Change access permissions|
||[chown](https://ss64.com/bash/chown.html)|Change file owner and group|
||[chpasswd](https://ss64.com/bash/chpasswd.html)|Update passwords in batch mode|
||[chroot](https://ss64.com/bash/chroot.html)|Run a command with a different root directory|
||[chkconfig](https://ss64.com/bash/chkconfig.html)|System services (runlevel)|
||[cksum](https://ss64.com/bash/cksum.html)|Print CRC checksum and byte counts|
||clear|Clear the terminal screen/console (ncurses)|
||clear_console|Clear the terminal screen/console (bash)|
||[cmp](https://ss64.com/bash/cmp.html)|Compare two files|
||[comm](https://ss64.com/bash/comm.html)|Compare two sorted files line by line|
||[command](https://ss64.com/bash/command.html)|Run a command - ignoring shell functions •|
||[continue](https://ss64.com/bash/continue.html)|Resume the next iteration of a loop •|
||[cp](https://ss64.com/bash/cp.html)|Copy one or more files to another location|
||[cpio](https://ss64.com/bash/cpio.html)|Copy files to and from archives|
||[cron](https://ss64.com/bash/cron.html)|Daemon to execute scheduled commands|
||[crontab](https://ss64.com/bash/crontab.html)|Schedule a command to run at a later time|
||[csplit](https://ss64.com/bash/csplit.html)|Split a file into context-determined pieces|
||[curl](https://ss64.com/bash/curl.html)|Transfer data from or to a server|
||[cut](https://ss64.com/bash/cut.html)|Divide a file into several parts|
|D|||
||[date](https://ss64.com/bash/date.html)|Display or change the date & time|
||[dc](https://ss64.com/bash/dc.html)|Desk Calculator|
||[dd](https://ss64.com/bash/dd.html)|Data Duplicator - convert and copy a file, write disk headers, boot records|
||[ddrescue](https://ss64.com/bash/ddrescue.html)|Data recovery tool|
||[declare](https://ss64.com/bash/declare.html)|Declare variables and give them attributes •|
||[df](https://ss64.com/bash/df.html)|Display free disk space|
||[diff](https://ss64.com/bash/diff.html)|Display the differences between two files|
||[diff3](https://ss64.com/bash/diff3.html)|Show differences among three files|
||[dig](https://ss64.com/bash/dig.html)|DNS lookup|
||[dir](https://ss64.com/bash/dir.html)|Briefly list directory contents|
||[dircolors](https://ss64.com/bash/dircolors.html)|Colour setup for 'ls'|
||[dirname](https://ss64.com/bash/dirname.html)|Convert a full pathname to just a path|
||[dirs](https://ss64.com/bash/dirs.html)|Display list of remembered directories|
||[dos2unix](https://ss64.com/bash/dos2unix.html)|Windows/MAC to UNIX text file format converter|
||[dmesg](https://ss64.com/bash/dmesg.html)|Print kernel & driver messages|
||[dpkg](https://ss64.com/bash/dpkg.html)|Package manager (Debian/Ubuntu).|
||[du](https://ss64.com/bash/du.html)|Estimate file space usage|
|E|||
||[echo](https://ss64.com/bash/echo.html)|Display message on screen •|
||[egrep](https://ss64.com/bash/egrep.html)|Search file(s) for lines that match an extended expression|
||[eject](https://ss64.com/bash/eject.html)|Eject removable media|
||[enable](https://ss64.com/bash/enable.html)|Enable and disable builtin shell commands •|
||[env](https://ss64.com/bash/env.html)|Environment variables|
||ethtool|Ethernet card settings|
||[eval](https://ss64.com/bash/eval.html)|Evaluate several commands/arguments|
||[exec](https://ss64.com/bash/exec.html)|Execute a command|
||[exit](https://ss64.com/bash/exit.html)|Exit the shell|
||[expand](https://ss64.com/bash/expand.html)|Convert tabs to spaces|
||[export](https://ss64.com/bash/export.html)|Set an environment variable|
||[expr](https://ss64.com/bash/expr.html)|Evaluate expressions|
|F|||
||[false](https://ss64.com/bash/false.html)|Do nothing, unsuccessfully|
||[fdformat](https://ss64.com/bash/fdformat.html)|Low-level format a floppy disk|
||[fdisk](https://ss64.com/bash/fdisk.html)|Partition table manipulator for Linux|
||[fg](https://ss64.com/bash/fg.html)|Send job to foreground|
||[fgrep](https://ss64.com/bash/fgrep.html)|Search file(s) for lines that match a fixed string|
||[file](https://ss64.com/bash/file.html)|Determine file type|
||[find](https://ss64.com/bash/find.html)|Search for files that meet a desired criteria|
||[fmt](https://ss64.com/bash/fmt.html)|Reformat paragraph text|
||[fold](https://ss64.com/bash/fold.html)|Wrap text to fit a specified width|
||[for](https://ss64.com/bash/for.html)|Expand _words_, and execute _commands_|
||format|Format disks or tapes|
||free|Display memory usage|
||[fsck](https://ss64.com/bash/fsck.html)|File system consistency check and repair|
||[ftp](https://ss64.com/bash/ftp.html)|File Transfer Protocol|
||[function](https://ss64.com/bash/function.html)|Define Function Macros|
||[fuser](https://ss64.com/bash/fuser.html)|Identify/kill the process that is accessing a file|
|G|||
||[gawk](https://ss64.com/bash/awk.html)|Find and Replace text within file(s)|
||[getopts](https://ss64.com/bash/getopts.html)|Parse positional parameters|
||[getfacl](https://ss64.com/bash/getfacl.html)|Get file access control lists|
||[grep](https://ss64.com/bash/grep.html)|Search file(s) for lines that match a given pattern|
||[groupadd](https://ss64.com/bash/groupadd.html)|Add a user security group|
||[groupdel](https://ss64.com/bash/groupdel.html)|Delete a group|
||[groupmod](https://ss64.com/bash/groupmod.html)|Modify a group|
||[groups](https://ss64.com/bash/groups.html)|Print group names a user is in|
||[gzip](https://ss64.com/bash/gzip.html)|Compress or decompress named file(s)|
|H|||
||[hash](https://ss64.com/bash/hash.html)|Remember the full pathname of a name argument|
||[head](https://ss64.com/bash/head.html)|Output the first part of file(s)|
||help|Display help for a built-in command •|
||[history](https://ss64.com/bash/history.html)|Command History|
||[hostname](https://ss64.com/bash/hostname.html)|Print or set system name|
||[htop](https://ss64.com/bash/htop.html)|Interactive process viewer|
|I|||
||[iconv](https://ss64.com/bash/iconv.html)|Convert the character set of a file|
||[id](https://ss64.com/bash/id.html)|Print user and group id's|
||[if](https://ss64.com/bash/if.html)|Conditionally perform a command|
||[ifconfig](https://ss64.com/bash/ifconfig.html)|Configure a network interface|
||[ifdown](https://ss64.com/bash/ifup.html)|Stop a network interface|
||[ifup](https://ss64.com/bash/ifup.html)|Start a network interface up|
||[import](https://ss64.com/bash/import.html)|Capture an X server screen and save the image to file|
||[install](https://ss64.com/bash/install.html)|Copy files and set attributes|
||[iostat](https://ss64.com/bash/iostat.html)|Report CPU and i/o statistics|
||[ip](https://ss64.com/bash/ip.html)|Routing, devices and tunnels|
|J|||
||[jobs](https://ss64.com/bash/jobs.html)|List active jobs •|
||[join](https://ss64.com/bash/join.html)|Join lines on a common field|
|K|||
||[kill](https://ss64.com/bash/kill.html)|Kill a process by specifying its PID|
||[killall](https://ss64.com/bash/killall.html)|Kill processes by name|
||[klist](https://ss64.com/bash/klist.html)|List cached Kerberos tickets|
|L|||
||[less](https://ss64.com/bash/less.html)|Display output one screen at a time|
||[let](https://ss64.com/bash/let.html)|Perform arithmetic on shell variables •|
||[link](https://ss64.com/bash/link.html)|Create a link to a file|
||[ln](https://ss64.com/bash/ln.html)|Create a symbolic link to a file|
||[local](https://ss64.com/bash/local.html)|Create a function variable •|
||[locate](https://ss64.com/bash/locate.html)|Find files|
||[logname](https://ss64.com/bash/logname.html)|Print current login name|
||[logout](https://ss64.com/bash/logout.html)|Exit a login shell •|
||[look](https://ss64.com/bash/look.html)|Display lines beginning with a given string|
||[lpc](https://ss64.com/bash/lpc.html)|Line printer control program|
||[lpr](https://ss64.com/bash/lpr.html)|Print files|
||lprint|Print a file|
||lprintd|Delete a print job|
||lprintq|List the print queue|
||[lprm](https://ss64.com/bash/lprm.html)|Remove jobs from the print queue|
||[lsattr](https://ss64.com/bash/lsattr.html)|List file attributes on a Linux second extended file system|
||[lsblk](https://ss64.com/bash/lsblk.html)|List block devices|
||[ls](https://ss64.com/bash/ls.html)|List information about file(s)|
||[lsof](https://ss64.com/bash/lsof.html)|List open files|
||[lspci](https://ss64.com/bash/lspci.html)|List all PCI devices|
|M|||
||make|Recompile a group of programs|
||[man](https://ss64.com/bash/man.html)|Help manual|
||[mapfile](https://ss64.com/bash/mapfile.html)|Read lines from standard input into an indexed array variable •|
||[mkdir](https://ss64.com/bash/mkdir.html)|Create new folder(s)|
||[mkfifo](https://ss64.com/bash/mkfifo.html)|Make FIFOs (named pipes)|
||[mkfile](https://ss64.com/bash/mkfile.html)|Make a file|
||mkisofs|Create a hybrid ISO9660/JOLIET/HFS filesystem|
||[mknod](https://ss64.com/bash/mknod.html)|Make block or character special files|
||[mktemp](https://ss64.com/bash/mktemp.html)|Make a temporary file|
||[more](https://ss64.com/bash/more.html)|Display output one screen at a time|
||[most](https://ss64.com/bash/most.html)|Browse or page through a text file|
||[mount](https://ss64.com/bash/mount.html)|Mount a file system|
||[mtools](https://ss64.com/bash/mtools.html)|Manipulate MS-DOS files|
||[mtr](https://ss64.com/bash/mtr.html)|Network diagnostics (traceroute/ping)|
||[mv](https://ss64.com/bash/mv.html)|Move or rename files or directories|
||[mmv](https://ss64.com/bash/mmv.html)|Mass Move and rename (files)|
|N|||
||[nc](https://ss64.com/bash/nc.html)|Netcat, read and write data across networks|
||[netstat](https://ss64.com/bash/netstat.html)|Networking connections/stats|
||[nft](https://ss64.com/bash/nft.html)|nftables for packet filtering and classification|
||[nice](https://ss64.com/bash/nice.html)|Set the priority of a command or job|
||[nl](https://ss64.com/bash/nl.html)|Number lines and write files|
||[nohup](https://ss64.com/bash/nohup.html)|Run a command immune to hangups|
||[notify-send](https://ss64.com/bash/notify-send.html)|Send desktop notifications|
||[nslookup](https://ss64.com/bash/nslookup.html)|Query Internet name servers interactively|
|O|||
||[open](https://ss64.com/bash/open.html)|Open a file in its default application|
||[op](https://ss64.com/bash/op.html)|Operator access|
|P|||
||[passwd](https://ss64.com/bash/passwd.html)|Modify a user password|
||[paste](https://ss64.com/bash/paste.html)|Merge lines of files|
||pathchk|Check file name portability|
||[Perf](https://ss64.com/bash/perf.html)|Performance analysis tools for Linux|
||[ping](https://ss64.com/bash/ping.html)|Test a network connection|
||[pgrep](https://ss64.com/bash/pkill.html)|List processes by name|
||[pkill](https://ss64.com/bash/pkill.html)|Kill processes by name|
||[popd](https://ss64.com/bash/popd.html)|Restore the previous value of the current directory|
||[pr](https://ss64.com/bash/pr.html)|Prepare files for printing|
||printcap|Printer capability database|
||[printenv](https://ss64.com/bash/printenv.html)|Print environment variables|
||[printf](https://ss64.com/bash/printf.html)|Format and print data •|
||[ps](https://ss64.com/bash/ps.html)|Process status|
||[pushd](https://ss64.com/bash/pushd.html)|Save and then change the current directory|
||[pv](https://ss64.com/bash/pv.html)|Monitor the progress of data through a pipe|
||[pwd](https://ss64.com/bash/pwd.html)|Print Working Directory|
|Q|||
||[quota](https://ss64.com/bash/quota.html)|Display disk usage and limits|
||[quotacheck](https://ss64.com/bash/quotacheck.html)|Scan a file system for disk usage|
|R|||
||[ram](https://ss64.com/bash/ram.html)|ram disk device|
||[rar](https://ss64.com/bash/rar.html)|Archive files with compression|
||[rcp](https://ss64.com/bash/rcp.html)|Copy files between two machines|
||[read](https://ss64.com/bash/read.html)|Read a line from standard input •|
||[readarray](https://ss64.com/bash/mapfile.html)|Read from stdin into an array variable •|
||[readonly](https://ss64.com/bash/readonly.html)|Mark variables/functions as readonly|
||reboot|Reboot the system|
||[rename](https://ss64.com/bash/rename.html)|Rename files|
||renice|Alter priority of running processes|
||remsync|Synchronize remote files via email|
||[return](https://ss64.com/bash/return.html)|Exit a shell function|
||[rev](https://ss64.com/bash/rev.html)|Reverse lines of a file|
||[rm](https://ss64.com/bash/rm.html)|Remove files|
||[rmdir](https://ss64.com/bash/rmdir.html)|Remove folder(s)|
||[rsync](https://ss64.com/bash/rsync.html)|Remote file copy (Synchronize file trees)|
|S|||
||[screen](https://ss64.com/bash/screen.html)|Multiplex terminal, run remote shells via ssh|
||[scp](https://ss64.com/bash/scp.html)|Secure copy (remote file copy)|
||[sdiff](https://ss64.com/bash/sdiff.html)|Merge two files interactively|
||[sed](https://ss64.com/bash/sed.html)|Stream Editor|
||[select](https://ss64.com/bash/select.html)|Accept user choices via keyboard input|
||[seq](https://ss64.com/bash/seq.html)|Print numeric sequences|
||[set](https://ss64.com/bash/set.html)|Manipulate shell variables and functions|
||[setfacl](https://ss64.com/bash/setfacl.html)|Set file access control lists.|
||sftp|Secure File Transfer Program|
||[sha256sum](https://ss64.com/bash/sha256sum.html)|Compute and check SHA256 (256-bit) checksums|
||[shift](https://ss64.com/bash/shift.html)|Shift positional parameters|
||[shopt](https://ss64.com/bash/shopt.html)|Shell Options|
||[shuf](https://ss64.com/bash/shuf.html)|Generate random permutations|
||[shutdown](https://ss64.com/bash/shutdown.html)|Shutdown or restart linux|
||[sleep](https://ss64.com/bash/sleep.html)|Delay for a specified time|
||[slocate](https://ss64.com/bash/slocate.html)|Find files|
||[sort](https://ss64.com/bash/sort.html)|Sort text files|
||[source](https://ss64.com/bash/source.html)|Run commands from a file '.'  •|
||[split](https://ss64.com/bash/split.html)|Split a file into fixed-size pieces|
||[ss](https://ss64.com/bash/ss.html)|Socket Statistics|
||[ssh](https://ss64.com/bash/ssh.html)|Secure Shell client (remote login program)|
||[stat](https://ss64.com/bash/stat.html)|Display file or file system status|
||[strace](https://ss64.com/bash/strace.html)|Trace system calls and signals|
||[su](https://ss64.com/bash/su.html)|Substitute user identity|
||[sudo](https://ss64.com/bash/sudo.html)|Execute a command as another user|
||[sum](https://ss64.com/bash/sum.html)|Print a checksum for a file|
||[suspend](https://ss64.com/bash/suspend.html)|Suspend execution of this shell •|
||[sync](https://ss64.com/bash/sync.html)|Synchronize data on disk with memory|
|T|||
||[tail](https://ss64.com/bash/tail.html)|Output the last part of a file|
||[tar](https://ss64.com/bash/tar.html)|Store, list or extract files in an archive|
||[tee](https://ss64.com/bash/tee.html)|Redirect output to multiple files|
||[test](https://ss64.com/bash/test.html)|Evaluate a conditional expression|
||[time](https://ss64.com/bash/time.html)|Measure Program running time|
||[timeout](https://ss64.com/bash/timeout.html)|Run a command with a time limit|
||[times](https://ss64.com/bash/times.html)|User and system times|
||[tmux](https://ss64.com/bash/tmux.html)|Terminal multiplexer|
||[touch](https://ss64.com/bash/touch.html)|Change file timestamps|
||[top](https://ss64.com/bash/top.html)|List processes running on the system|
||[tput](https://ss64.com/bash/tput.html)|Set terminal-dependent capabilities, color, position|
||[traceroute](https://ss64.com/bash/traceroute.html)|Trace Route to Host|
||[trap](https://ss64.com/bash/trap.html)|Execute a command when the shell receives a signal •|
||[tr](https://ss64.com/bash/tr.html)|Translate, squeeze, and/or delete characters|
||[true](https://ss64.com/bash/true.html)|Do nothing, successfully|
||[tsort](https://ss64.com/bash/tsort.html)|Topological sort|
||[tty](https://ss64.com/bash/tty.html)|Print filename of terminal on stdin|
||[type](https://ss64.com/bash/type.html)|Describe a command •|
|U|||
||[ulimit](https://ss64.com/bash/ulimit.html)|Limit user resources •|
||[umask](https://ss64.com/bash/umask.html)|Users file creation mask|
||umount|Unmount a device|
||[unalias](https://ss64.com/bash/alias.html)|Remove an alias •|
||[uname](https://ss64.com/bash/uname.html)|Print system information|
||[unexpand](https://ss64.com/bash/unexpand.html)|Convert spaces to tabs|
||[uniq](https://ss64.com/bash/uniq.html)|Uniquify files|
||[units](https://ss64.com/bash/units.html)|Convert units from one scale to another|
||[unix2dos](https://ss64.com/bash/unix2dos.html)|UNIX to Windows or MAC text file format converter|
||[unrar](https://ss64.com/bash/unrar.html)|Extract files from a rar archive|
||[unset](https://ss64.com/bash/unset.html)|Remove variable or function names|
||[unshar](https://ss64.com/bash/unshar.html)|Unpack shell archive scripts|
||[until](https://ss64.com/bash/until.html)|Execute commands (until error)|
||uptime|Show uptime|
||[useradd](https://ss64.com/bash/useradd.html)|Create new user account|
||[userdel](https://ss64.com/bash/userdel.html)|Delete a user account|
||[usermod](https://ss64.com/bash/usermod.html)|Modify user account|
||[users](https://ss64.com/bash/users.html)|List users currently logged in|
||[uuencode](https://ss64.com/bash/uuencode.html)|Encode a binary file|
||[uudecode](https://ss64.com/bash/uuencode.html)|Decode a file created by uuencode|
|V|||
||v|Verbosely list directory contents ('ls -l -b')|
||vdir|Verbosely list directory contents ('ls -l -b')|
||[vi](https://ss64.com/vi.html)|Text Editor|
||[vmstat](https://ss64.com/bash/vmstat.html)|Report virtual memory statistics|
|W|||
||[w](https://ss64.com/bash/w.html)|Show who is logged on and what they are doing|
||[wait](https://ss64.com/bash/wait.html)|Wait for a process to complete •|
||[watch](https://ss64.com/bash/watch.html)|Execute/display a program periodically|
||[wc](https://ss64.com/bash/wc.html)|Print byte, word, and line counts|
||[whereis](https://ss64.com/bash/whereis.html)|Search the user's $path, man pages and source files for a program|
||[which](https://ss64.com/bash/which.html)|Search the user's $path for a program file|
||[while](https://ss64.com/bash/while.html)|Execute commands|
||[who](https://ss64.com/bash/who.html)|Print all usernames currently logged in|
||[whoami](https://ss64.com/bash/whoami.html)|Print the current user id and name ('id -un')|
||wget|Retrieve web pages or files via HTTP, HTTPS or FTP|
||[write](https://ss64.com/bash/write.html)|Send a message to another user|
|X|||
||[xargs](https://ss64.com/bash/xargs.html)|Execute utility, passing constructed argument list(s)|
||[xdg-open](https://ss64.com/bash/xdg-open.html)|Open a file or URL in the user's preferred application.|
||[xxd](https://ss64.com/bash/xxd.html)|Make a hexdump or do the reverse|
||[xz](https://ss64.com/bash/xz.html)|Compress or decompress .xz and .lzma files|
||[yes](https://ss64.com/bash/yes.html)|Print a string until interrupted|
||[zip](https://ss64.com/bash/zip.html)|Package and compress (archive) files|
||[.](https://ss64.com/bash/source.html)|[Run](https://ss64.com/bash/source.html) a command script in the current shell|
||[!!](https://ss64.com/bash/bang.html)|Run the [last](https://ss64.com/bash/bang.html) command again|
||[###](https://ss64.com/bash/rem.html)|Comment / [Rem](https://ss64.com/bash/rem.html)ark|
# Bash How-to guides and examples

|   |   |
|---|---|
|[Arguments](https://ss64.com/bash/syntax-parameters.html)|Shell parameters.|
|[Array variables](https://ss64.com/bash/syntax-arrays.html)|Array Variables.|
|[Functions](https://ss64.com/bash/function.html)|Define Function Macros.|
|[Permissions](https://ss64.com/bash/syntax-permissions.html)|Allow or Deny actions.|
|[Redirection](https://ss64.com/bash/syntax-redirection.html)|Spooling to and from files.|
|[Pipes](https://ss64.com/bash/syntax-pipe.html)|Redirect the output from one command as input for another.|
|[Shell variables](https://ss64.com/bash/syntax-variables.html)|Default Shell variables / bash variables.|
|[Local vars](https://ss64.com/bash/syntax-env.html)|Create environment variables in bash.|

## Looping constructs:

|   |   |
|---|---|
|[if-then-else](https://ss64.com/bash/if.html)|Conditionally perform a command.|
|[for](https://ss64.com/bash/for.html)|Expand _words_, and execute commands.|
|[until](https://ss64.com/bash/until.html)|Execute commands (until error).|
|[while](https://ss64.com/bash/while.html)|Execute commands.|
|[break](https://ss64.com/bash/break.html)|Control loop execution.|
|[continue](https://ss64.com/bash/continue.html)|Control loop execution.|

## Evaluating expressions:

|   |
|---|
|[Arithmetic](https://ss64.com/bash/syntax-math.html) expressions.|
|[Using brackets](https://ss64.com/bash/syntax-brackets.html) to Group and expand expressions.|
|[Conditional Execution](https://ss64.com/bash/syntax-execute.html) command_A_ AND/OR command_B_|
|[Command Substitution](https://ss64.com/bash/syntax-substitution.html)|
|[Escape Characters, delimiters and Quotes](https://ss64.com/bash/syntax-quoting.html)|
|[File operators/Comparisions](https://ss64.com/bash/syntax-file-operators.html) - exists, greater than,-a, -nt|
|[Shell expansion](https://ss64.com/bash/syntax-expand.html) { } $ ~ &{} $()|
|[Wildcards](https://ss64.com/bash/syntax-wildcards.html) Pattern matching|

## Working with the bash Shell:

|   |   |
|---|---|
|[Run script](https://ss64.com/bash/syntax-script.html)|Run a bash shell script.|
|[Here documents](https://ss64.com/bash/syntax-here.html)|and [Here Strings](https://ss64.com/bash/syntax-here-string.html)|
|[Job Control](https://ss64.com/bash/syntax-jobs.html)|Suspend and resume a process.|
|[Keyboard](https://ss64.com/bash/syntax-keyboard.html)|Cursor control - Cut & paste.|
|[.bashrc](https://ss64.com/bash/syntax-bashrc.html)|Startup files (Startup scripts and Aliases).|
|[.inputrc](https://ss64.com/bash/syntax-inputrc.html)|Startup files (Set Key bindings and Tab completion).|
|[Prompt](https://ss64.com/bash/syntax-prompt.html)|Prompt variable.|
|[###](https://ss64.com/bash/rem.html)|Comment / Remark.|
|[BashBangSplat](https://ss64.com/bash/syntax-pronounce.html)|Pronunciation guide for unix.|
|[vi editor](https://ss64.com/vi.html)|vi commands.|
|[Xterm colours](https://ss64.com/bash/syntax-colors.html)|256 Colors for the XTerm prompt (console).|

The pronounciation for Linux is 'Lyn-ux' not 'Line-ux' [Listen to Linus](http://www.youtube.com/watch?v=5IfHm6R5le0) .

See also: [Websites, Books, OS Downloads, Apps & Utilities for GNU/Linux.](https://ss64.com/links/bash.html)
# doc
[doc](https://ss64.com)
