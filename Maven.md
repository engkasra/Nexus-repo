## Installing JDK on Linux/Ubuntu

#### step 1: Download the JDK Binaries
Go to the [JDK-website](https://jdk.java.net/13/) Copy the download link for Linux/x64 build.<br>Then use the below command to download and extract it.
```bash
$ wget https://download.java.net/java/GA/jdk13.0.1/cec27d702aa74d5a8630c65ae61e4305/9/GPL/openjdk-13.0.1_linux-x64_bin.tar.gz
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
#### Step 2: Setting M2_HOME and Path Variables
Add the following lines to the user profile file (.profile).
```bash
M2_HOME='/opt/apache-maven-3.6.3'
PATH="$M2_HOME/bin:$PATH"
export PATH
```
Relaunch the terminal or execute `source .profile` to apply the changes.

### Step 3: Verify the Maven installation
Execute `mvn -version` command and it should produce the following output.
```bash
$ mvn -version
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: /opt/apache-maven-3.6.3
Java version: 13.0.1, vendor: Oracle Corporation, runtime: /opt/jdk-13.0.1
Default locale: en, platform encoding: UTF-8
OS name: "linux", version: "4.15.0-47-generic", arch: "amd64", family: "unix"
```
## Connect Maven to Nexus repository
```bash
nano ~/.m2/settings.xml
```
add following lines to settings.xml
```xml
<settings>
  <mirrors>
    <mirror>
      <!--This sends everything else to /public -->
      <id>nexus</id>
      <mirrorOf>*</mirrorOf>
      <url>https://repo.asax.ir/repository/maven-public</url>
    </mirror>
  </mirrors>
  <profiles>
    <profile>
      <id>nexus</id>
      <!--Enable snapshots for the built in central repo to direct -->
      <!--all requests to nexus via the mirror -->
      <repositories>
        <repository>
          <id>central</id>
          <url>http://central</url>
          <releases><enabled>true</enabled></releases>
          <snapshots><enabled>true</enabled></snapshots>
        </repository>
      </repositories>
     <pluginRepositories>
        <pluginRepository>
          <id>central</id>
          <url>http://central</url>
          <releases><enabled>true</enabled></releases>
          <snapshots><enabled>true</enabled></snapshots>
        </pluginRepository>
      </pluginRepositories>
    </profile>
  </profiles>
  <activeProfiles>
    <!--make the profile active all the time -->
    <activeProfile>nexus</activeProfile>
  </activeProfiles>
</settings>
```
