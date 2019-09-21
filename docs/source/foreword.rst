Foreword
========

In a secure outsourcing system, the clients would like to perform operations
that are computationally complex while their local machines do not have enough
resources to solve the problem. With the emerging cloud technology, the clients
could easily obtain computational resources they needed from cloud hosts.
Currently, the major cloud hosts include Google Cloud Platform (GCP), Amazon Web
Services (AWS), and Microsoft Azure. However, the problem might contain sensitive
information that the clients would not want to disclose and computed outside of a
controlled environment. This imposes a challenge: how to securely outsource
computationally intensive computations to cloud servers without expose sensitive
information.


Currently, there are existing algorithms that resolve the problem to limited
scopes. Some of them relies on specific mathematical properties of the input
problem, while some others requires a large amount of computational resources on
local. Most importantly, almost all existing method imposes a lot of memory I/O
operations on local machine. The resource limitations on local machines has been
barely addressed, as in most of the cases, local machines lacks enough random
access memory (RAM) to load the problem. Our algorithm fixed the problem by
only perform necessary secure transformation locally to keep the task simple for
the client machine while outsource computationally complex operations to the
cloud.


In this project, we implemented the algorithms using the proposed schemes. That
is, the cloud cooperates with the local machine to compute the result without
compromising the privacy and security. To perform the outsourcing, we used Dask,
a distributed parallel computing platform and library [1]_. Users may setup
their Dask server in a potentially unsafe environment and is able to solve their
problems securely using our algorithms.


References
----------

.. [1] M. Rocklin, “Dask: Parallel Computation with Blocked algorithms and Task Scheduling,” presented at the Python in Science Conference, Austin, Texas, 2015, pp. 126–132 [Online]. Available: https://conference.scipy.org/proceedings/scipy2015/matthew_rocklin.html. [Accessed: 14-Jul-2019]
