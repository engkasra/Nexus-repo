## Install Go from the Official Binary Package

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
