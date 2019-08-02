
# **Docker-Hadoop Example**

### Installation

**Donwload hadoop:**

https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe

**Download Released docker-hadoop image:**

`docker pull sequenceiq/hadoop-docker:2.7.0
`

**Download Tutorial Files From:**

`git clone https://github.com/alperenssahin/WordCountTutorial <HOST_WORKNG_DIRECTORY>`

**Start docker-hadoop image:**

`docker run -v <HOST_WORKING_DIRECTORY>:/home/WordCountTutorial -it sequenceiq/hadoop-docker:2.7.0 /etc/bootstrap.sh -bash
`

**Example:**

`docker run -v /home/user1/WordCountTutorial:/home/WordCountTutorial -it sequenceiq/hadoop-docker:2.7.0 /etc/bootstrap.sh -bash
`


## Tutorial

`export HADOOP_CLASSPATH=$(/usr/local/hadoop/bin/hadoop classpath)
`

`/usr/local/hadoop/bin/hadoop fs -mkdir /WordCountTutorial`

`/usr/local/hadoop/bin/hadoop fs -mkdir /WordCountTutorial/Input`

`/usr/local/hadoop/bin/hadoop fs -put '/home/WordCountTutorial/input_data/input.txt' /WordCountTutorial/Input
`

`javac -classpath ${HADOOP_CLASSPATH} -d '/home/WordCountTutorial/tutorial_classes' '/home/WordCountTutorial/WordCount.java'
`

`jar cvf wordCountExample.jar -C tutorial_classes/ .
`

`/usr/local/hadoop/bin/hadoop jar /home/WordCountTutorial/wordCountExample.jar  WordCount /WordCountTutorial/Input /WordCountTutorial/Output
`

`/usr/local/hadoop/bin/hadoop dfs -cat /WordCountTutorial/Output/*
`

#### **Utilities**

**Docker remove all container:**

`docker stop $(docker ps -a -q)
`

`docker rm $(docker ps -a -q)
`