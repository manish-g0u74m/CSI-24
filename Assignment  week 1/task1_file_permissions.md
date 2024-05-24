# Task 1: File Permissions

## Description
Create a file named `manish.txt`, assign permissions (read, write, execute) to different user categories (owner, group, others), and practice changing permissions using `chmod`.

## Instructions

1. **Create the File**
    ```sh
    touch manish.txt
    ```
    ![Screenshot (11)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/f9060f21-dff6-463e-aa56-f6222be30249)


2. **Assign Permissions**
    - **Owner (User)**: Read, write, execute (`rwx`)
    - **Group**: Read, execute (`r-x`)
    - **Others**: Read only (`r--`)

    The corresponding numeric mode for these permissions is `754`:
    - `7` (Owner): `r` (4) + `w` (2) + `x` (1) = `7`
    - `5` (Group): `r` (4) + `-` (0) + `x` (1) = `5`
    - `4` (Others): `r` (4) + `-` (0) + `-` (0) = `4`

    Apply these permissions using `chmod`:
    ```sh
    chmod 754 manish.txt
    ```
    ![Screenshot (13)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/74e7a9ff-2b19-427e-acad-b40683653b6a)
   
3. **Verify Permissions**
    Use the `ls -l` command to check the permissions of the file:
    ```sh
    ls -l manish.txt
    ```
    You should see an output like this:
    ```
    -rwxr-xr--. 1 root root 0 May 23 14:50 manish.txt

    ```
    ![Screenshot (12)](https://github.com/manish-g0u74m/celebaltech-inturn/assets/148465299/3fcaccfe-d6d1-4c41-8e84-a55027d5c0d1)
   
    The breakdown of `-rwxr-xr--` is:
    - `-`: File type (regular file)
    - `rwx`: Owner permissions (read, write, execute)
    - `r-x`: Group permissions (read, execute)
    - `r--`: Others permissions (read)

## Resources
- [YouTube: Understanding File Permissions](https://www.youtube.com/watch?v=iwolPf6kN-k)
- [Pluralsight: Linux File Permissions](https://www.pluralsight.com/blog/it-ops/linux-file-permissions)
