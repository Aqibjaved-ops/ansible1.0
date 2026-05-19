Ansible Lab Setup with Vs Code.

Login as a : root user
setup all prerequisites like : 
Make :- student user with no password, repository , host entry, ssh config with student user.
---
Login as a : student user on workstation

Install : sudo dnf install python3-pip
          sudo dnf install podman
          sudo dnf install git
          sudo pip install podman-compose
   
run : sudo podman-compose --version
---------------
open firefox 
> search : Install vs code on rhel 

search URL : https://code.visualstudio.com/docs/setup/linux
> Check : RHEL, Fedora, and CentOS based distributions

>>  : Install the key and yum repository by running the following script:

sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc &&
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\nautorefresh=1\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null


>> : Then update the package cache and install the package using dnf (Fedora 22 and above):

 
yum check-update &&
sudo yum install code # or code-insiders

podman login registry.redhat.io
USERNAME  : 
PASSWORD : 

cp /run/user/1000/containers/auth.json  /home/student/.auth.json

--------------
Open Vs code >>

Add extensions >>

Ansible : version =  25.9.0
Dev Container : version = 0.427.0

--------------
Then open Dev Container Extension settings:

Dev>Containers:Docker Compose Path
podman-compose

Dev>Containers:Docker Path
podman
------------------
Then open Ansible Extension settings:
Execution Environment >>
Ansible>Execution Environment: Container Engine
podman

Ansible>Execution Environment:Image
registry.redhat.io/ansible-automation-platform-25/ee-supported-rhel8:latest

--------------------------------------
Then Click on left side Ansible Icon >>
Scroll Down 
Devcontainer (Create Dev Cintainer )

-----------------
Add this Image in .devContainer
>> podman >>
devcontainer.json

"image": "registry.redhat.io/ansible-automation-platform-25/ansible-dev-tools-rhel8:26.1.0-1",

----

Add This line as well :
"mounts": ["source=/home/student/.auth.json,target=/tmp/user/0/containers/auth.json,type=bind"],

