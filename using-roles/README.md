# Playing with roles

1. Generate role using this command
    ```
    ansible-galaxy role init httpd
    ```
2. Test connection to the remote node
    ```
    ansible all -m ping -i inventory.ini --ask-pass
    ```
3. Apply the playbook
    ```
    ansible-playbook -i inventory.init first-playbook.yml
    ```
