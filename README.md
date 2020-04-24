Hyperfoil test runner
=========

Processes a template for Hyperfoil benchmark, uploads it to Controller, starts the test and waits for its completion

Requirements
------------

Hyperfoil should be already deployed. See `hyperfoil-setup` role.

Role Variables
--------------

* ansible hosts under `hyperfoil_controller` and `hyperfoil_agent` groups
* `test_name` (required): Name of the test, in `benchmarks` folder, with `yaml.j2` extension. This name must match the benchmark name in the file.
* `hyperfoil_controller_group` (optional): Ansible group that hosts the controller. Default is `hyperofoil-controller`.
* `hyperfoil_controller_port` (optional): Port on which Hyperfoil should listen
* `hyperfoil_deployer` (optional): Method of deployment. Either `ssh` (default) or `k8s`.
* `hyperfoil_agent_group` (optional): Ansible group that hosts the agents. Default is `hyperofoil-agent`.
* `hyperfoil_agent_port` (optional): SSH port on agent. Default is 22.


License
-------

Apache License, Version 2.0

Example
-------

As the example references role names as installed by Ansible first install all hyperfoil roles:
```
ansible-galaxy install hyperfoil.hyperfoil_setup
ansible-galaxy install hyperfoil.hyperfoil_shutdown
ansible-galaxy install hyperfoil.hyperfoil_test
```

This example deploys Hyperfoil on localhost (controller and agent as separate instances), uploads a minimal benchmark doing single request to GitHub main page and reports #of requests from statistics.

```
ansible-playbook -i hosts.example example.yml
```
