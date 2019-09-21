Setup
#####

This page describes a few practical ways to setup the necessary computing resources needed
for Secout on different hardware / platforms.

By design, Secout utilizes the distributed platform provided by Dask. You could
deploy Dask on your local machine or on a distributed cluster.

Deploy on Local Machine
-----------------------

It is quite easy to use Dask on local machine.

.. code-block:: python

    from dask.distributed import Client
    client = Client() # start a new client that uses local client

The detailed documentation for Dask client could be found `here <https://distributed.dask.org/en/latest/client.html>`_

Deploy on Distributed cluster
-----------------------------

Here we are showing a way of deploying a Dask cluster with 1 scheduler node, 3
worker node, and 1 jupyter notebook node on Google Cloud Platform (GCP). We use the
Active Cloud Shell provided in the GCP Console Workspace.

#. Start a Kubernetes Cluster from Kubernetes Engine. Tweak the options if you want.

    - Use the graphical interface provided of GCP Kubenetes Engine

    - Use the `gcloud` command-line tool.
        .. code-block:: sh

            gcloud container clusters create MY_KUBERNETES_CLUSTER \
              --enable-cloud-logging \
              --enable-cloud-monitoring \
              --subnetwork default
              --num-nodes 5

    You must also obtain the credentials to the cluster you just created.\

    .. code-block:: sh

        # obtain the cluster credentials so that you could operate with kubectl and helm
        gcloud container clusters get-credentials MY_KUBERNETES_CLUSTER

#. Setting up helm with your cluster.

    .. code-block:: sh

        # add a service account within a namespace to segregate tiller
        kubectl --namespace kube-system create sa tiller
        # create a cluster role binding for tiller
        kubectl create clusterrolebinding tiller \
            --clusterrole cluster-admin \
            --serviceaccount=kube-system:tiller

        echo "initialize helm"
        # initialized helm within the tiller service account
        helm init --service-account tiller
        # updates the repos for Helm repo integration
        helm repo update

#. Install `dask` using helm.

    You could install at default setting by

    .. code-block:: sh

        helm install stable/dask

    This will create a dask compute cluster that contains 1 scheduler, 3 worker, and 1 jupyter notebook.
