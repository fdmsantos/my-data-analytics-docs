# HDFS

The Hadoop Distributed File System ([HDFS](https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html)) is a distributed file system designed to run on commodity hardware.

## Basic Operations

### List

```shell
hadoop fs -ls /
hadoop fs -ls
hadoop fs -ls /user/user
```

### Create

```shell
hadoop fs -mkdir hadoop-test1
```

### Copy Operations

* Copy From Local

```shell
hadoop fs -copyFromLocal  /hirw-starterkit/hdfs/commands/dwp-payments-april10.csv hadoop-test1
```

* Copy from hdfs

```shell
hadoop fs -copyToLocal hadoop-test1/dwp-payments-april10.csv .
```

* Copy/Move Files

```shell
hadoop fs -cp hadoop-test1/dwp-payments-april10.csv hadoop-test2
hadoop fs -mv hadoop-test1/dwp-payments-april10.csv hadoop-test3
```

### Replication Commands

* Check Replication

```shell
hadoop fs -ls hadoop-test3
```

* Change or set replication factor

```shell
hadoop fs -Ddfs.replication=2 -cp hadoop-test2/dwp-payments-april10.csv hadoop-test2/test_with_rep2.csv
```

### Change Permissions

```shell
hadoop fs -chmod 777 hadoop-test2/test_with_rep2.csv
```

### File System Check

```shell
sudo -u hdfs hdfs fsck /user/hirwuser150430/hadoop-test2 -files -blocks -locations
sudo -u hdfs hdfs fsck /user/ubuntu/input/yelp/yelp_academic_dataset_review.json -files -blocks -locations
```

### Delete files

```shell
hadoop fs -rm hadoop-test2/test_with_rep5.csv
```