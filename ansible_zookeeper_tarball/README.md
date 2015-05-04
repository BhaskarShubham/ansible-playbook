
<a name="AnsibleZooKeeperInstallationFromtarball"></a>

# Ansible ZooKeeper Installation From `tarball`


---

###Table of Contents

* <a href="#Step1DownloadZookeeperfromCDH5">Step 1: Download Zookeeper from CDH5.</a>
* <a href="#Step2UpdatePathinansiblezookeeperyml">Step 2: Update Path in `ansible_zookeeper.yml`.</a>
* <a href="#Step3UpdateHostsintheHostsfile">Step 3: Update Hosts in the Hosts file.</a>
* <a href="#Step4OptionalUpdateUserWeuseausercalledhdadminforZookeeper">Step 4: (Optional) Update User - We use a user called `hdadmin` for Zookeeper.</a>
* <a href="#Step5NowwearereadytoExecute">Step 5: Now we are ready to Execute.</a>

---


This Installation is configuration of Zookeeper from `tar.gz` file.


<a name="Step1DownloadZookeeperfromCDH5"></a>

## Step 1: Download Zookeeper from CDH5.

Download the file in `zookeeper` directory.

    wget http://archive.cloudera.com/cdh5/cdh/5/zookeeper-3.4.5-cdh5.1.2.tar.gz



<a name="Step2UpdatePathinansiblezookeeperyml"></a>

## Step 2: Update Path in `ansible_zookeeper.yml`.

Update path in the `ansible_zookeeper.yml` file so that it reflects the path required.
As shown below.

    # Remote Destination path on Zookeeper Nodes.
    remote_dest_path: /root/ansible/zookeeper

    # Source Base path where the ansible script is running.
    src_base_path: /root/ansible_scripts/learn_ansible

    # Data Storage path on Destination Zookeeper Nodes.
    zookeeper_data_store: /data1/ansible/zookeeper

    # Logging Directory on Destination Zookeeper Nodes
    zookeeper_logging: /data1/ansible/zookeeper_logging

    # Zookeeper Install Directory on Destination Zookeeper Nodes.
    zookeeper_base: /opt/zookeeper


<a name="Step3UpdateHostsintheHostsfile"></a>

## Step 3: Update Hosts in the Hosts file.

Updated IP address as per your requirement.
Make sure you use unique ids for `zookeeper_id`, as this will be used to create the quorum.


<a name="Step4OptionalUpdateUserWeuseausercalledhdadminforZookeeper"></a>

## Step 4: (Optional) Update User - We use a user called `hdadmin` for Zookeeper.

Change this to any user you like as per requirement. Currently we are using `hdadmin`.
Note : Just find and replace `hdadmin` to any user you like. user will be created with password `hdadmin@123`

Password can be changed using the below python script.

    python -c "from passlib.hash import sha512_crypt; import getpass; print sha512_crypt.encrypt(getpass.getpass())"



<a name="Step5NowwearereadytoExecute"></a>

## Step 5: Now we are ready to Execute.

    # ansible-playbook ansible_zookeeper.yml --ask-pass
