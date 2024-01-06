We have an interface to connect to HDFS server.
The interface is https://jupyter.polito.it/. It is our Gateway Server to connect BigData@Polito cluster.
We have an access to Reserved 1 CPU threads/8 GB mem, max 8 CPU threads and 24 GB memory.

After logining to the Jupyter Interface we have to upload our Jar file and InputFile to it.
Then we have to use command line approach or just run the bash file(run.sh).

The commands to run the Jar file on cluster are mentioned below:
# Remove folders of the previous run
hdfs dfs -rm -r ex12_data
hdfs dfs -rm -r ex12_out

# Put input data collection into hdfs
hdfs dfs -put ex12_data

# Run application
hadoop jar target/Exercise12-1.0.0.jar it.polito.bigdata.hadoop.exercise12.DriverBigData ex12_data/  ex12_out 21


Finally we can check the output by these commands:
#To check if output folder created or not
hdfs dfs -ls

#check the content of output folder
hdfs dfs -ls example_out

#To see the results
hdfs dfs -cat example_out/part-r-00000