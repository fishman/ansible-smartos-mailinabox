# Ansible playbook to create a mailinabox LX zone on SmartOS

It will create a zfs volume called `mailbox_{domain}`.

## Configuration

You will have to modify `production` and add a `group_vars/mailbox_{domain}`
file.

    ---
    hypervisor_host: smartos.root

    boxname: somedomain
    tld: com

    nics:
      - nic_tag: admin
        ip: externalip
        netmask: 255.255.255.0
        mac: 00:00:00:00:00:00
        gateway: 123.123.123.1
        primary: true

    root_authorized_keys: ssh-rsa something Client

## Running the playbook

Make sure to the check hypervisor_host variable to your SmartOS Global Zone

    ansible-playbook provision_vm.yml
    ansible-playbook setup_mailbox.yml
