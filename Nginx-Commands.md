# Nginx Commands

## Open Ports:

    C:\> netstat -l

## Start nginx

    C:\> start nginx

## Verify nginx process

    C:\> tasklist /fi "imagename eq nginx.exe"

## Stop nginx

    C:\> nginx -s stop

## Other commands

    C:\> nginx -s quit
    C:\> nginx -s reload
    C:\> nginx -s reopen

## Kill nginx process

    C:\> taskkill /F /IM nginx.exe

## To find which process is holding port 80:

    C:\> netstat -n -a -o | findstr "0.0.0.0:80"

## Get process name

    C:\> tasklist /svc /FI "PID eq <ProcessID>"


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY1NjIxMjk1MV19
-->