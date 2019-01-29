# An example for using xargs

```
echo "abc\n def" | xargs -I % sh -c 'echo %'
```
