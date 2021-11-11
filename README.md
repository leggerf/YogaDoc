# YogaDoc
This repo mirrors documentation on confluence

## Yoga
The Yoga cluster is a dedicated cluster on local premises provided by the INFN Torino Cloud, offering a variety of services for:

- ML tasks: Jupyter + spark cluster or access to a T4 GPU
- high performance computing (nodes with many cores and lots of RAM).

Yoga can be accessed through a web interface based on JupyterHub.

### Step-by-step guide

**First time user:**
- Open a ticket to our [service desk](https://servicedesk.infn.it/servicedesk/customer/portal/39) with the following information:
   - Your use case
   - Your github account (username) which is needed for authentication. If you don't have an account yet on github, please create one.
   - *Note*: The username should be all lower case, and shouldn't contain any special character (-,_,.,...). If it does, please create a new one to be used for yoga
- You will get a notification from us when you can access the cluster
- Point your browser to https://yoga.to.infn.it/ and sign in with your github account
- You will be prompted to choose among three profiles :
   - **Spark**: use this for workflows requiring spark. The home directory is on the main server yoga. The server is shared, but users can use Spark to launch executors on the other nodes. 
   - **Private server**: if available you will get an entire server in the cluster mlwn. The home directory is a shared Gluster volume that aggregates the disks from the mlwn servers.
   - **GPU server**: two users can share the GPU server, getting a GPU each.
- You will be greeted by the JupyterHub interface.
   - If you are not familiar with Jupyter, please read this [guide](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html)
- You can also open a terminal by clicking on *New → Terminal* (top right of the Home screen)
- Happy coding!

### Storage

- Profile **Spark**:
  - private home folder is mounted as */home/jovyan*
  - shared folder available in r/w for all users in */data/*
- Profiles **private** and **GPU** server:
  - private home folder is mounted as */home/jovyan*
  - shared folder available in r/w for all users in */data/*
  - **Note**: these paths are NOT the same as those for the spark profile
- Additional storage space is available on HDFS

### Spark

- Select the **Spark** profile when starting your JupyterHub server
- Create a notebook with kernel *pyspark*
- You can use the following code to start the spark context:

spark=%sc

from pyspark.sql import SparkSession
spark_session = SparkSession(spark)

An example [notebook](sparkHDFS_example.ipynb) that shows how to start spark and read/write from HDFS is available.

**Yoga is not a production cluster. As such, it is provided with support on a best effort basis, and may be subject to downtimes on short notice.**

### Related articles

CHEP paper 2019: [Delivering a machine learning course on HPC resources](https://baltig.infn.it/INFNTO-Calcolo/yogacluster/-/blob/main/notebooks/sparkHDFS_example.ipynb)
