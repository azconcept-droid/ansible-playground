# Installing Oracle DB with ansible

1. Install the collection
    ```
    ansible-galaxy collection install opitzconsulting.ansible_oracle
    ```
2. Confirm if the collection is installed
    ```
    ansible-galaxy collection list
    ```
3. View documentation e.g
    ```
    ansible-doc -t module my_namespace.my_collection.module_name
    ```

    ```
    ansible-doc -t module opitzconsulting.ansible_oracle.oracle_db
    ```
