# CML PVC Spark Pushdown

CML in Private Cloud provides two options for running Spark workloads: Spark on Yarn and Spark on Kubernetes.

Spark on Kubernetes is the recommended choice. However, in certain scenarios you can use Spark on Yarn.

This quickstart contains instructions to configure and run Spark on Yarn.

## Requirements

* Familiarity with Spark and Python
* Previous experience with CML
* A CML workspace in CDP Private Cloud 1.5.2+

## Project Setup

Create a CML Project and clone this git repo.

## Documentation

Please reference the official documentation for more details: https://docs.cloudera.com/machine-learning/1.5.3/spark/topics/ml-spark-pushdown.htm

## Configuration Steps

SSH into the PVC nodes and check the Python version. Remember this version as you will need to deploy a CML Session with it when you run the Spark examples.

In your Project Settings, check the "Enable Spark Pushdown" option under the "General" tab.

Place spark-defaults.conf in your CML Project home directory. This will be used to override Spark on Kubernetes and set Spark on Yarn configurations. In this example, we specify the log directory for the Spark History Server in Cloudera Manager.

## Running the Example Scripts

Launch a CML Session with the Python version corresponding to the Python version installed on your CDP Base nodes. Make sure to enable the Spark Runtime Addon with the Spark version corresponding to the one available to you in the CDP Base cluster.

Run the "pysparksimple.py" and the "sparkml.py" scripts.

## Validating your Spark Applications in Cloudera Manager

Navigate to Knox and open the Spark History Server. There typically are two Spark History Server options, one for Spark 2 and one for Spark 3. Pick the one corresponding to the Spark version you used. Validate the existence of your Spark Application.

If you don't see your Spark application here, it's probably because you need to update the value of "spark.eventLog.dir" in spark-defaults.conf to the directory specified in the top left corner of the History Server UI (look for "Event Log Dir" in bold, copy that value and place that in spark-defaults.conf).

Navigate back to Knox and open the Yarn Resource Manager Web UI v2, then open the Applications tab and validate the existence of your Spark application.
