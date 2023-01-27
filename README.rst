demo-deployment
---------------

Deployment of Selinon's demo.

A: Kubernetes deployment
========================

You can deploy demo to a Kubernetes cluster or use `minikube <https://minikube.sigs.k8s.io/docs/>`__:

::

  # install minikube, follow installation instructions in the linked docs
  minikube start

Deploy to Kubernetes, see manifests in `kubernetes/` directory:

::

  kubectl apply -f kubernetes/

B: OpenShift deployment
=======================

To do the deployment, run the following commands. Note that you have to have Travis CLI installed and you have to be logged in to Travis CI using `travis login <https://github.com/travis-ci/travis.rb#readme>`_ and to OpenShift cluster using ``oc login <URL>``.

::

  export OCP_URL=$(oc whoami --show-server)
  export OCP_TOKEN=$(oc whoami --show-token)
  export SELINON_NAMESPACE='selinon'
  export TRAVIS_CI_TOKEN=$(travis token | awk '{ print $NF }')
  ansible-playbook ansible/provision.yaml

If you would like to deploy different storages and databases, see main Ansible configuration file and adjust deployed databases.

.. figure:: https://raw.githubusercontent.com/selinon/demo-deployment/master/fig/openshift.png
   :alt: OpenShift deployment
   :align: center

Running the demo
================

Once the project is deployed, check API service. You can find two main endpoints exposed:

1. listing flows available (GET)
2. submitting a new workflow (POST)

You can submit a testing workflow called ``hello`` which will print text to worker stdout. This way you verify that Selinon works.

Another workflow is more sophisticated and can aggregate logs from Travis CI (token needs to be provided).

All flows available implemented and listed in the `selinon/demo-worker repository <https://github.com/selinon/demo-worker>`__.
