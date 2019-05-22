.. _awsbest:

AWS Best practise
=================

AWS CLI
-------

Configuration
~~~~~~~~~~~~~~
``aws configure --profile PROFILE_NAME``  
``AWS Access Key ID [None]: YOURKEY``  
``AWS Secret Access Key [None]: YOURSECRETKEY``  
``Default region name [None]: us-west-2``  
``Default output format [None]: json``



S3 commands
~~~~~~~~~~~~
``aws --profile profilename s3 ls s3://bucketname`` For listing of all files in a bucket  
``aws --profile profilename s3 cp filename s3://bucketname/``  For copy a file from local to  bucket  
``aws --profile profilename s3 sync s3://bucketname/foldername`` For copy all bucket of a folder to bucket folder  
``aws --profile profilename s3 cp s3://bucketname/filename /serverpath`` For copy a file from local to  bucket  
``aws --profile profilename s3 sync . s3://bucketname/MyFolder`` For copy all bucket of a folder to bucket folder  

.. Tip::

    Space in S3 Bucket    
    aws s3api --profile PROFILE_NAME list-objects --bucket BUCKETNAME --output json --query "[sum(Contents[].Size), length(Contents[])]" | awk 'NR!=2 {print $0;next} NR==2 {print $0/1024/1024/1024" GB"}'


AWS load balancer
-----------------

Scaling Vertically
~~~~~~~~~~~~~~~~~~
	Scaling vertically takes place through an increase in the specifications of an individual resource (e.g., upgrading a server with a larger hard drive or a faster CPU). On Amazon EC2, this can easily be achieved by stopping an instance and resizing it to an instance type that has more RAM, CPU, IO, or networking capabilities. This way of scaling can eventually hit a limit and it is not always a cost efficient or highly available approach. However, it is very easy to implement and can be sufficient for many use cases especially in the short term.

Scaling Horizontally
~~~~~~~~~~~~~~~~~~~~
	Scaling horizontally takes place through an increase in the number of resources (e.g., adding more hard drives to a storage array or adding more servers to support an application). This is a great way to build Internet-scale applications that leverage the elasticity of cloud computing. Not all architectures are designed to distribute their workload to multiple resources, so let’s examine some of the possible scenarios.