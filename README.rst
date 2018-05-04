demo-deployment
---------------


Deployment of Selinon's demo into OpenShift

::

  export OCP_URL=$(oc whoami --show-server)
  export OCP_TOKEN=$(oc whoami --show-token)
  export SELINON_NAMESPACE='selinon'
  ansible-playbook ansible/provision.yaml

