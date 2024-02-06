We have an interface to connect to HDFS server.
The interface is https://jupyter.polito.it/. It is our Gateway Server to connect BigData@Polito cluster.
We have an access to Reserved 1 CPU threads/8 GB mem, max 8 CPU threads and 24 GB memory.

After logining to the Jupyter Interface we have to upload our Jar file and InputFile to it.
Then we have to use command line approach or just run the bash file(run.sh).

The commands to run the Jar file on cluster are mentioned below:
# Remove folders of the previous run
hdfs dfs -rm -r ex27_data
hdfs dfs -rm -r ex27_out
# Remove the business rules file from hdfs
hdfs dfs -rm businessrules.txt

# Put input data collection into hdfs
hdfs dfs -put ex27_data

# Put the business rules file into hdfs
hdfs dfs -put businessrules.txt

# Run application
hadoop jar target/Exercise27-1.0.0.jar it.polito.bigdata.hadoop.exercise27.DriverBigData ex27_data ex27_out