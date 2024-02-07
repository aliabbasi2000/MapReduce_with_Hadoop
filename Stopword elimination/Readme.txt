Details of problem:

▪ Input: 
 - A large textual file containing one sentence per line
 - A small file containing a set of stopwords (One stopword per line)
▪ Output: 
 - A textual file containing the same sentences of the large input file without the words appearing in the small file
 - The order of the sentences in the output file can be different from the order of the sentences in the input file

We have an interface to connect to HDFS server.
The interface is https://jupyter.polito.it/. It is our Gateway Server to connect BigData@Polito cluster.
We have an access to Reserved 1 CPU threads/8 GB mem, max 8 CPU threads and 24 GB memory.

After logining to the Jupyter Interface we have to upload our Jar file and InputFile to it.
Then we have to use command line approach or just run the bash file(run.sh).

The commands to run the Jar file on cluster are mentioned below:
# Remove folders of the previous run
hdfs dfs -rm -r ex21_data
hdfs dfs -rm -r ex21_out
# Remove the stopword file from hdfs
hdfs dfs -rm stopwords.txt

# Put input data collection into hdfs
hdfs dfs -put ex21_data

# Remove the stopword file in hdfs
hdfs dfs -put stopwords.txt

# Run application
hadoop jar target/Exercise21-1.0.0.jar it.polito.bigdata.hadoop.exercise21.DriverBigData ex21_data ex21_out


Finally we can check the output by these commands:
#To check if output folder created or not
hdfs dfs -ls

#check the content of output folder
hdfs dfs -ls example_out

#To see the results
hdfs dfs -cat example_out/part-r-00000