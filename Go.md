## Install Golang from the Official Binary Package

```bash
$ sudo apt update
$ wget https://go.dev/dl/go1.20.1.linux-amd64.tar.gz  #to get new veriosn, go to official website https://go.dev/dl/
$ sudo tar -C /usr/local -xzf go1.20.1.linux-amd64.tar.gz
$ ls /usr/local/go
$ nano ~/.bashrc #or nano ~/.profile

#Paste the following line.
export PATH=$PATH:/usr/local/go/bin
#Save the changes and exit the file.

$ source ~/.bash_profile
$ go version
```
## Connect Golang to Nexus repository to get packages
```bash
$ nano ~/.bashrc #or nano ~/.profile
#Paste the following line.
export PATH=$PATH:/usr/local/go/bin
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
export GOPROXY=https://localhost/repository/<repository-name>
#Save the changes and exit the file.
#After that, enter the following commands in shell.
go env -w 'GOSUMDB=sum.golang.org https://nexus.example.com/repository/golang-sum-proxy'
source ~/.bashrc
source ~/profile
