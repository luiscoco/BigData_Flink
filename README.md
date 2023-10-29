# BigData Apache Flink

https://flink.apache.org/

# What is Apache Flink?

Stateful Computations over Data Streams

Apache Flink is a framework and distributed processing engine for stateful computations over unbounded and bounded data streams

Flink has been designed to run in all common cluster environments, perform computations at in-memory speed and at any scale

# Apache Flink downloads

https://flink.apache.org/downloads/

# Apache Flink examples

https://github.com/apache/flink/tree/master/flink-examples

# Get started with Flink

https://nightlies.apache.org/flink/flink-docs-stable/docs/try-flink/local_installation/

Flink is designed to process continuous streams of data at a lightning fast pace. 

This short guide will show you how to download the latest stable version of Flink, install, and run it. You will also run an example Flink job and view it in the web UI.

## Downloading Flink #
Note: Flink is also available as a Docker image.

Flink runs on all UNIX-like environments, i.e. Linux, Mac OS X, and Cygwin (for Windows). 

You need to have Java 11 installed. 

To check the Java version installed, type in your terminal:

```
java -version
```

Next, download the latest binary release of Flink, then extract the archive:

![image](https://github.com/luiscoco/BigData_Flink/assets/32194879/c4aa3c09-c42e-40ce-ace3-d635676d0313)

![image](https://github.com/luiscoco/BigData_Flink/assets/32194879/cb556c93-b761-4086-a158-ad5827dc7d39)

## Browsing the project directory

Navigate to the extracted directory and list the contents:


For now, you may want to note that:

**bin/** directory contains the flink binary as well as several bash scripts that manage various jobs and tasks

**conf/** directory contains configuration files, including flink-conf.yaml

**examples/** directory contains sample applications that can be used as is with Flink

Also see the exmples source code in this github repository: https://github.com/apache/flink/tree/master/flink-examples

## Starting and stopping a local cluster #

To **start a local cluster**, run the bash script that comes with Flink:

```
/bin/start-cluster.sh
```

You should see an output like this:

![image](https://github.com/luiscoco/BigData_Flink/assets/32194879/2403bf09-aae5-4558-b9ae-e4d423c572d9)

Flink is now running as a background process. You can check its status with the following command:

```
ps aux | grep flink
```

You should be able to navigate to the web UI at **localhost:8081** to view the Flink dashboard and see that the cluster is up and running

To quickly **stop the cluster** and all running components, you can use the provided script:

```
/bin/stop-cluster.sh
```

## Submitting a Flink job #

Flink provides a CLI tool, **bin/flink**, that can run programs packaged as Java ARchives (JAR) and control their execution

Submitting a job means uploading the job’s JAR ﬁle and related dependencies to the running Flink cluster and executing it

Flink releases come with example jobs, which you can ﬁnd in the **examples/ folder**

To deploy the **example word count** job to the running cluster, issue the following command:

```
/bin/flink run examples/streaming/WordCount.jar
```

You can verify the output by viewing the logs:

$ tail log/flink-*-taskexecutor-*.out

Sample output:

![image](https://github.com/luiscoco/BigData_Flink/assets/32194879/ed3b778d-d5f0-48f0-b183-7238ca839d91)

Additionally, you can check Flink’s web UI to monitor the status of the cluster and running job.

You can view the data flow plan for the execution:

![image](https://github.com/luiscoco/BigData_Flink/assets/32194879/cc4ea8c1-2cb8-4f10-8390-8320e1cbca17)

Here for the job execution, Flink has two operators. 

The ﬁrst is the source operator which reads data from the collection source. 

The second operator is the transformation operator which aggregates counts of words. 

Learn more about DataStream operators: https://nightlies.apache.org/flink/flink-docs-release-1.18/docs/dev/datastream/operators/overview/

You can also look at the timeline of the job execution:
