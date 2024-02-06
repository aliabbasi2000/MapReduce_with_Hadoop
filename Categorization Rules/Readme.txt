Problem Details:
 Input: 
▪ A large textual file containing a set of records
▪ Each line contains the information about one single user
▪ Each line has the format: UserId,Name,Surname,Gender,YearOfBirth,City,Education
▪ A small file with a set of business rules that are used to assign each user to a category
▪ Each line contains a business rule with the format: Gender=<value> and YearOfBirth=<value> -> Category
▪ Rules are mutually exclusive
 Output:
▪ One record for each user with the following format
▪ The original information about the user plus the category assigned to the user by means of the business rules
▪ Since the rules are mutually exclusive, there is only one rule applicable for each user
▪ If no rules is applicable/satisfied by a user, assign the user to the “Unknown” category


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