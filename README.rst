demo-deployment
---------------


Deployment of Selinon's demo into OpenShift

To do the deployment, run the following commands. Note that you have to have Travis CLI installed and you have to be logged in using `travis login <https://github.com/travis-ci/travis.rb#readme>`_.

::

  export OCP_URL=$(oc whoami --show-server)
  export OCP_TOKEN=$(oc whoami --show-token)
  export SELINON_NAMESPACE='selinon'
  export TRAVIS_CI_TOKEN=$(travis token | awk '{ print $NF }')
  ansible-playbook ansible/provision.yaml

