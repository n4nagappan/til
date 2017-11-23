### Executing a command on every line in VIM   

Let's say for example that you want to insert a '*' character at the end of each line in a file

```
:%norm A*
%       = for every line
norm    = type the following commands
A*      = append '*' to the end of current line
```

[Source](https://stackoverflow.com/a/599416/868791)
