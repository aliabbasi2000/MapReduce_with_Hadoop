Problem Details: Max and Min function with MapReduce
▪ Input: a collection of (structured) textual csv files containing the daily value of PM10 for a set of sensors
Each line of the files has the following format
sensorId,date,PM10 value (μg/m3)\n
▪ Output: report for each sensor the maximum and the minimum value of PM10


We have an interface to connect to HDFS server.
The interface is https://jupyter.polito.it/. It is our Gateway Server to connect BigData@Polito cluster.
We have an access to Reserved 1 CPU threads/8 GB mem, max 8 CPU threads and 24 GB memory.

After logining to the Jupyter Interface we have to upload our Jar file and InputFile to it.
Then we have to use command line approach or just run the bash file(run.sh).

The commands to run the Jar file on cluster are mentioned below:
# Remove folders of the previous run
hdfs dfs -rm -r ex6_data
hdfs dfs -rm -r ex6WithCombiner_out

# Put input data collection into hdfs
hdfs dfs -put ex6_data

# Run application
hadoop jar target/Exercise6WithCombiner-1.0.0.jar it.polito.bigdata.hadoop.exercise6withcombiner.DriverBigData 1 ex6_data/  ex6WithCombiner_out

Finally we can check the output by these commands:
#To check if output folder created or not
hdfs dfs -ls

#check the content of output folder
hdfs dfs -ls example_out

#To see the results
hdfs dfs -cat example_out/part-r-00000