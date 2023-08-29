## Installing Java with Homebrew

```bash
$ brew update
$ brew search openjdk # check which version are available
$ brew install openjdk@17 
$ echo 'export PATH="/usr/local/opt/openjdk@17/bin:$PATH"' >> ~/.zshrc # update the shell
$ java -version # verify the installation
```