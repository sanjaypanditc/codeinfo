.. _awsbest:

AWS Best practise
=================

AWS load balancer
-----------------

Scaling Vertically
~~~~~~~~~~~~~~~~~~
:: 
   Scaling vertically takes place through an increase in the specifications of an individual resource (e.g., upgrading a server with a larger hard drive or a faster CPU). On Amazon EC2, this can easily be achieved by stopping an instance and resizing it to an instance type that has more RAM, CPU, IO, or networking capabilities. This way of scaling can eventually hit a limit and it is not always a cost efficient or highly available approach. However, it is very easy to implement and can be sufficient for many use cases especially in the short term.

Scaling Horizontally
~~~~~~~~~~~~~~~~~~~~
::
   Scaling horizontally takes place through an increase in the number of resources (e.g., adding more hard drives to a storage array or adding more servers to support an application). This is a great way to build Internet-scale applications that leverage the elasticity of cloud computing. Not all architectures are designed to distribute their workload to multiple resources, so let’s examine some of the possible scenarios.