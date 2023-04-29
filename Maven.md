## Installing JDK on Linux/Ubuntu

#### step 1: Download the JDK Binaries
```bash
$ wget https://download.java.net/java/GA/jdk13.0.1/cec27d702aa74d5a8630c65ae61e4305/9/GPL/openjdk-13.0.1_linux-x64_bin.tar.gz
#for get new version: https://jdk.java.net/13/
$ tar -xvf openjdk-13.0.1_linux-x64_bin.tar.gz
$ mv jdk-13.0.1 /opt/
```
#### Step 2: Setting JAVA_HOME and Path Environment Variables
Open .profile file from the home directory and add the following lines to it.
```bash
JAVA_HOME='/opt/jdk-13.0.1'
PATH="$JAVA_HOME/bin:$PATH"
export PATH
```
You can relaunch the terminal or execute `source .profile` command to apply the configuration changes.

#### Step 3: Verify the Java Installation
You can run `java -version` command to verify the JDK installation.
```bash
$ java -version
openjdk version "13.0.1" 2019-10-15
OpenJDK Runtime Environment (build 13.0.1+9)
OpenJDK 64-Bit Server VM (build 13.0.1+9, mixed mode, sharing)
```
## Installing Maven on Linux/Ubuntu

#### step 1: Download the Maven Binaries

Go to the [Maven-website](https://maven.apache.org/download.cgi) Copy the link for the “Binary tar.gz archive” file.<br> Then run the following commands to download and untar it.
```bash
$ wget https://mirrors.estointernet.in/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
$ tar -xvf apache-maven-3.6.3-bin.tar.gz
$ mv apache-maven-3.6.3 /opt/
```
