# Installing and managing multiple versions of go

Discovered [GVM](https://github.com/moovweb/gvm), a Golang version manager. Very similar to [NVM](https://github.com/creationix/nvm) ( node version manager ). A neat way to install multiple versions of Go and switch between them when required.

To install GVM

```
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
```

Setting up Go
```
gvm install go1.4
gvm use go1.4
```

** If you want versions above go1.5, read https://github.com/moovweb/gvm#a-note-on-compiling-go-15
