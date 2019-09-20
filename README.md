Systemd-service
=========

The purpose of this role is to configure and run various servers as a systemd-service, enabling the process to be 
controlled and supervised by systemd.


Requirements
------------

The server must be installed and configured before executing this role.
Furthermore, the tasks of this role require the ansible priviledge escalation.


Role Variables
--------------

This role requires variables set in the global scope defined in the respective service_vars file of the desired service. In the following a list of these variables is depicted:


| Variable name                   | Type    | Default  | Description                                             |
| ------------------------------- | ------- | -------- | ------------------------------------------------------- |
| nodejs_service_owner            | string  |  *(N/A)* | User with priviledges to copy files                     |
| nodejs_exec_path                | string  |  *(N/A)* | Path to startup.sh                                      |
| nodejs_working_dir (optional)   | string  |  *(N/A)* | Path to where to service should run                     |
| nodejs_env_path                 | string  |  *(N/A)* | Path to the env-file of the service                     |
| **nodejs_service_props** |||| 
| &nbsp;&nbsp;&nbsp;&nbsp;.name                         | string  |  *(N/A)* | Name of the service                                     |
| &nbsp;&nbsp;&nbsp;&nbsp;.state                        | string  |  *(N/A)* | Denotes whether the service is started (started/stopped)|
| &nbsp;&nbsp;&nbsp;&nbsp;.autostart                    | string  |  *(N/A)* | Denotes whether the service should start on boot        |
| &nbsp;&nbsp;&nbsp;&nbsp;.user (optional)              | string  | root     | Service run as user                                     |



Dependencies
------------

None.


Example Configuration
----------------

In the following an example configuration of the update-server is shown. Note in this case no working directory is required:

    nodejs_service_owner: updater
    nodejs_exec_path: /usr/src/update-server/startup.sh
    nodejs_env_path: /usr/src/update-server/env

    nodejs_service_props:
      name: update-server
      state: started
      autostart: yes
      user: updater

License
-------

GPL

Author Information
------------------

This role was created in 2019 by Lenhard Reuter