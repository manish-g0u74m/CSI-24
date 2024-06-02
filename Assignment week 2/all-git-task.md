## Task 1: Setup a Remote Repository in Local, Add a File and Commit, Save the Changes, and Push to Master Branch

**Solution:**  

    **First we need to configure Git**
    ```bash
    git config --global user.name "your Name"
    git config --global user.email "your_email@example.com" 
    ```

    **make a directory:**
    ```bash
    mkdir my-project
    cd my-project
    '''
    
    **Clone the Remote Repository in Local**
    ```bash
    git clone https://github.com/username/our-repo-name.git
    ```
1. **Initialize a Local Repository:**
    ```bash
    git init
    ```

2. **Add a Remote Repository:**
    ```bash
    git remote add origin https://github.com/username/our-repo-name.git
    ```

3. **Create a File and Add Content:**
    ```bash
    echo "Hello, World!" > hello.txt
    ```

4. **Add the File to Staging Area:**
    ```bash
    git add hello.txt
    ```

5. **Commit the Changes:**
    ```bash
    git commit -m "Add hello.txt with initial content"
    ```

6. **Push to the Master Branch:**
    ```bash
    git push -u origin main
    ```
