# Task 4: User and Group Management

## Description
Create a new user and group, set their permissions, and explore user management commands like `useradd`, `usermod`, and `userdel`.

## Instructions
1. **Create a New User**
    ```sh
    sudo useradd newuser
    ```
    ![Screenshot (48)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/b354fbdf-930f-4a04-9bab-a24d0910794c)
    ![Screenshot (52)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/510cac9e-1d80-4aef-b5fb-be47b9ac4272)
   
3. **Create a New Group**
    ```sh
    sudo groupadd newgroup
    ```
    ![Screenshot (50)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/31c0332b-3f63-42d2-aa70-32722b0b1d03)
    ![Screenshot (51)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/e8ba863f-ce44-4ad7-8548-96a0f13f8889)

5. **Add User to Group**
    ```sh
    sudo usermod -aG newgroup newuser
    ```

6. **Set Permissions for User and Group**
    ```sh
    sudo chmod 750 /path/to/directory
    ```
    ![Screenshot (53)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/47788ce0-8799-4ce9-9994-b6cce6e0a8dd)
   
8. **Delete a User**
    ```sh
    sudo userdel newuser
    ```
    ![Screenshot (54)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/a0ae6e10-decc-4f10-81a9-8a454ef1f227)
    ![Screenshot (55)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/de464a19-86ad-4d56-ac62-d7b7d9874f41)

## Resources
- [Red Hat: Manage Permissions](https://www.redhat.com/sysadmin/manage-permissions)
