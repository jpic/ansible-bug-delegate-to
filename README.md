# delegate_to doesn't port ansible_python_interpreter

Run vagrant up and see for yourself:

    $ vagrant provision
    ==> arch: Configuring proxy environment variables...
    ==> arch: Running provisioner: ansible...
    PYTHONUNBUFFERED=1 ANSIBLE_FORCE_COLOR=true ANSIBLE_HOST_KEY_CHECKING=false ANSIBLE_SSH_ARGS='-o UserKnownHostsFile=/dev/null -o ControlMaster=auto -o ControlPersist=60s' ansible-playbook --private-key=/home/jpic/.vagrant.d/insecure_private_key --user=vagrant --connection=ssh --limit='arch' --inventory-file=/home/jpic/ansible-bug-delegate-to/.vagrant/provisioners/ansible/inventory --extra-vars={"ansible_python_interpreter":"/usr/bin/python2"} Vagrantplaybook.yml

    PLAY [all] ******************************************************************** 

    GATHERING FACTS *************************************************************** 
    ok: [arch]

    TASK: [setup ] **************************************************************** 
    failed: [arch -> arch] => (item=arch) => {"failed": true, "item": "arch", "parsed": false}
      File "/home/vagrant/.ansible/tmp/ansible-tmp-1423141910.6-89532618035001/setup", line 569
        except OSError, e:
                      ^
    SyntaxError: invalid syntax


    FATAL: all hosts have already failed -- aborting

    PLAY RECAP ******************************************************************** 
               to retry, use: --limit @/home/jpic/Vagrantplaybook.retry

    arch                       : ok=1    changed=0    unreachable=0    failed=1   

    Ansible failed to complete successfully. Any error output should be
    visible above. Please fix these errors and try again.

