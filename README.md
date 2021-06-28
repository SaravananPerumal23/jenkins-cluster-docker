# jenkins-master-slave-docker
Repo for maintaining docker-compose script which spins up Jenkins master and slave instances

### Pre-requisites for running this scripts
  1. Install docker
  2. Install docker-compose

### Instructions for running jenkins-master-docker-compose
  1. Create directories to store the Jenkins data which will be attached as Volume ($HOME/jenkins is the folder in your local to which Jenkins master data will be stored. $HOME refers to current User Directory- /Users/<CurrentUser>)
  2. Use below command to execute jenkins master setup script
  ```
  docker-compose -f jenkins-master-docker-compose.yml up -d
  ```

### Post Jenkins Master Setup
  1. Need to setup a Node as Slave in Jenkins master manually
    <ul>a. Login to Jenkins master</ul>
    <ul>b. Manage Jenkins -> Manage Nodes & clouds -> New Node</ul>
    <ul>c. Set Node Name as any name which refers to the slave (For Ex. 'jenkins_slave') and choose as 'Permanent Agent'</ul>
    <ul>d. In the next screen set <b>Executors</b> as '1' and <b>Remote Root</b> as '/var/jenkins_home' and all others set with default values you can save the configuration</ul>
    <ul>e. Click on the 'Node' which we have created (In our example it is jenkins_slave node) which will open a view that provides the Secret information that can be used to establish connection with master node. Make note of this Secret code which will be used for Slave setup</ul>

### Pre-requisite for running Jenkins-slave-docker-compose
  1. Modify the jenkins-slave-docker-compose.yml with the IP_ADDRESS and Secret identified from previous step

### Instructions for running jenkins-slave-docker-compose
  1. Create directories to store the Jenkins data which will be attached as Volume ($HOME/jenkins is the folder in your local to which Jenkins master data will be stored. $HOME refers to current User Directory- /Users/<CurrentUser>)
  2. Use below command to execute jenkins master setup script
  ```
  docker-compose -f jenkins-slave-docker-compose.yml up -d
  ```
