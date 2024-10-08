Install pnpm using curl.
```
curl -fsSL [https://get.pnpm.io/install.sh](https://get.pnpm.io/install.sh) | sh -
```

after installation 

in you install root user so please mv pnpm file to user `.local/share/` directory.
```
mv pnpm /home/users/devendra.singh/.local/share/
```
add entry in `.bashrc`
```
export PNPM_HOME="/home/users/devendra.singh/.local/share/pnpm"
export PATH="$PNPM_HOME:$PATH"

```

```
source .bashrc
```

