# Task 2: Execute Basic Linux Commands

## Description
Execute basic Linux commands to manipulate files and directories, with an emphasis on understanding their usage. This task includes listing files, creating and deleting directories, changing directories, and more.

## Instructions and Commands

1. **List Files and Directories**
    - **ls**: List the files and directories in the current directory.
    ```sh
    ls
    ```
    ![Screenshot (14)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/1dd8fe4c-63c1-40a7-97aa-915d6501e63d)

    - **ls -l**: List files and directories with detailed information.
    ```sh
    ls -l
    ```
    ![Screenshot (15)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/50de1334-a263-45bc-bb1e-59c04cac49c0)
   
    - **ls -a**: List all files, including hidden files (those starting with a dot).
    ```sh
    ls -a
    ```
    ![Screenshot (17)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/bf1c4e5c-6855-414c-a63b-b59a42186547)
   
    - **ls -la**: Combine detailed and hidden file listing.
    ```sh
    ls -la
    ```
    ![Screenshot (29)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/2daa74c2-1de6-4a53-81c9-8afdbbaff2c5)
   

2. **Change Directory**
    - **cd directory_name**: Change to the specified directory.
    ```sh
    cd directory_name
    ```
    ![Screenshot (30)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/5912f378-be83-4f70-a226-5b1cdf1677ef)
   
    - **cd ..**: Move up one directory level.
    ```sh
    cd ..
    ```
    ![Screenshot (32)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/0c7c9c33-d5d2-4cda-8f41-ba413248a6b7)

    - **cd ~**: Change to the home directory.
    ```sh
    cd ~
    ```
    ![Screenshot (33)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/d2e7c763-a4ff-4ddc-b45c-a6de149397e2)
   

3. **Make Directory**
    - **mkdir new_directory**: Create a new directory.
    ```sh
    mkdir new_directory
    ```
    ![Screenshot (34)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/8c7fd205-93df-455a-950e-ab8a4b3c83b6)

    - **mkdir -p parent_directory/new_directory**: Create nested directories with a single command.
    ```sh
    mkdir -p parent_directory/new_directory
    ```
    ![Screenshot (36)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/93805655-1cf5-45e4-b578-3be03027fda4)

4. **Remove Directory**
    - **rmdir directory_name**: Remove an empty directory.
    ```sh
    rmdir directory_name
    ```
    ![Screenshot (35)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/1d4758d7-bb69-4b44-8196-8536212c0fd0)
   
    - **rm -r directory_name**: Remove a directory and its contents recursively.
    ```sh
    rm -r directory_name
    ```
    ![Screenshot (37)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/50d05b43-a0dc-4df5-bca4-0a98be3487f0)

5. **Create a File**
    - **touch newfile.txt**: Create a new, empty file.
    ```sh
    touch newfile.txt
    ```
    ![Screenshot (39)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/d9c2d767-49cd-480b-836e-58e903500d24)

6. **Remove a File**
    - **rm filename**: Remove a file.
    ```sh
    rm filename
    ```
    ![Screenshot (38)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/7bcac94f-bfa2-4403-9d38-39f2d7e130e0)

7. **Move/Rename a File or Directory**
    - **mv old_name new_name**: Rename a file or directory.
    ```sh
    mv old_name new_name
    ```
    ![Screenshot (41)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/372ceac3-f6e1-4e8c-a412-6060b4255de1)

    - **mv filename /path/to/destination**: Move a file to a different directory.
    ```sh
    mv filename /path/to/destination
    ```
    ![Screenshot (42)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/7c596138-dbc7-4217-8ae1-c263923cbaa9)

8. **Copy a File or Directory**
    - **cp filename /path/to/destination**: Copy a file to a different directory.
    ```sh
    cp filename /path/to/destination
    ```
    ![Screenshot (43)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/97e7fa3e-ee59-495b-8395-0ad6c965a086)
   
    - **cp -r source_directory /path/to/destination**: Copy a directory and its contents recursively.
    ```sh
    cp -r source_directory /path/to/destination
    ```
    ![Screenshot (44)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/7c506789-0459-4696-a9a2-c77f805b2826)
   
10. **Display File Contents**
    - **cat > filename**: Add Content in a file.
    ```sh
    cat > filename
    ```
    ![Screenshot (46)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/cd6b6194-fb0a-4f03-81a9-4132ce8c214b)
     - **cat filename**: Display the contents of a file.
    ```sh
    cat filename
    ```
    ![Screenshot (45)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/17051da8-3e30-4259-aa94-aaa290483ec2)


11. **Print Working Directory**
    - **pwd**: Display the current directory.
    ```sh
    pwd
    ```
    ![Screenshot (47)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/cfbc6c9f-b473-47bb-b562-b35d47285759)

## Resources
- [Red Hat: Create and Delete Files and Directories in Linux](https://www.redhat.com/sysadmin/create-delete-files-directories-linux)

    




