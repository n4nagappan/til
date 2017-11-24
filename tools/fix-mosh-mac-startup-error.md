# Fix mosh connection error on mac

If you have installed mosh on mac via ```brew```, you may come across this error message :
```
mosh-server needs a UTF-8 native locale to run.

Unfortunately, the local environment ([no charset variables]) specifies
the character set "US-ASCII",

The client-supplied environment ([no charset variables]) specifies
the character set "US-ASCII".

LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=
Connection to server closed.
/usr/bin/mosh: Did not find mosh server startup message.
```

To **fix**, add this to ```bashrc``` file :

```
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
```
