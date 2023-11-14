# Programming Cheatsheet

## Macro Testing Guidelines

Ensure the macro runs accurately and effectively both locally and externally.

### 1. **Running the Macro Locally from Itself**

To test the macro from within its own environment:

1. Uncomment the the macro call lines at the macro's end.
2. Run the macro : `ctrl + alt + E`

### 2. **Running the Macro Locally from Outside**

To invoke the macro from an external file:

1. Make sure to comment the the macro call lines at the macro files' end.
2. Create a new file: `ctrl + n`.
3. Save as  a `warpscript file i.e  ".mc2"`.
4. Copy the example of the macro call from the end of the macro file to be tested. 
5. Replace in the last line : `'testingmacro'` with the main macro's relative path changed to forward slashes and without the `'.mc2'` file extension.
6. In `general_utility/local_macros_list`, ensure that all other macros are commented out and only the macro you intend to run is uncommented.
7. Make sure to include this comment in the first line: `// @include macro: general_utility/local_macros_list`

Example:
```
// @include macro: general_utility/local_macros_list/      // 6.

 [ '200' '224' ] 'msn_list' STORE
 [ '51000_pbit_wshld_defog_normalized_curr_l_median' '51401_brk_press_main' '51301_brk_press_main' '51000_operation_number' ] 'signals_xmlid_list' STORE
 0 'start_time' STORE
 NOW 'end_time' STORE
 1 s 'undersample_dt' STORE

{ 'msn_list' $msn_list   'signals_xmlid_list' $signals_xmlid_list     'extra_labels' { 'msn' [ '220' '224' ] 'type' [ 'pc24' ] }   'start_time' $start_time    'end_time' $end_time    'undersample_dt' $undersample_dt    'bucketizer' true   'merge_labels_list' [ 'hdr-pkt-version' ]   } 

'pc-24/aircraft_utility/fetch_signals' RUN                       // 4.
```


---
## Streamlit
  Run streamlit in terminal
```
streamlit run streamlit.py
```
---
## Python & Virtual Environments in VSCode
Create a virtual environment
```
python -m venv .venv
```
Create with a specific version
```
py -3.7 -m venv venv1
```
Activate the environment
```
.venv\Scripts\activate
```
Check python version
```
python --version
```
Use specific python versions
```
py -3.10  # or py -3.11
```  
Install packages for specific python version
```
pip3.10 install serial  # or pip3.11 install serial
``` 
Find all installed Python versions on Windows
```
py -0p
```
---
## Package Management
Install from requirements.txt
```
pip install -r requirements.txt
```
Create requirements.txt
```
pip freeze > requirements.txt
```
Install Jupyter Notebook
```
pip install ipykernel
```
Add virtual env to Jupyter Notebook
```
python -m ipykernel install --user --name=.venv
```
---
## Windows Program Checks
Check if a program is installed
```
PROGRAM-NAME --version
```
Find the executable path
```
(Get-Command PROGRAM-NAME).Source
```
---

## Cloning and Deleting a Repository from Bitbucket in PowerShell

### 1. Cloning a Repository:
Cloning a repository creates a copy of the repository on your local machine.

```powershell
# Clone the repository
git clone https://bitbucket.org/your_username/your_repository.git

# Navigate into the cloned directory
cd your_repository

# If you wish to remove the cloned repository from your local machine: Navigate to the parent directory outside the cloned repository
cd ..

# Delete the repository directory
Remove-Item -Recurse -Force your_repository

```

## Creating a branch of a cloned local repo on Bitbucket in PowerShell, then Committing, and Creating Pull Request

1. **Initialize Git in Local Project Parent Repo**:
    ```bash
    # Initialize Git
    git init
    ```

1. **Create a New Branch**:
    ```bash
    # Creates a new branch and switches to it
    git checkout -b your-branch-name
    ```

2. **Check Current Branch**:
    ```bash
    # Displays the list of branches and highlights the active branch
    git branch
    ```

3. **Stage Your Changes**:
    ```bash
    # Adds all changes in the current directory to the staging area
    git add .
    ```

4. **Commit Your Changes**:
    ```bash
    # Commits the staged changes with a message
    git commit -m "Your meaningful commit message here"
    ```

5. **Push the Branch to the Remote Repository**:
    ```bash
    # Pushes the branch to the remote repository and tracks it
    git push -u origin your-branch-name
    ```

6. **Edit message or add a new file in the same commit**
   
    ```bash
    git commit --amend -m "CA-490 fetch_signals updated date,version,author"
    
    # Realize you forgot to add the changes from main.py
    git add main.py 
    git commit --amend --no-edit
    ```

1. **Create a Pull Request**:
    After pushing the branch, a URL will be displayed in the terminal to create a pull request via Bitbucket's web interface.

    ```bash
    # Example URL displayed (this will vary based on your repo)
    remote: https://bitbucket.org/your-username/your-repo-name/pull-requests/new?source=your-branch-name
    ```

    Copy and paste this URL into a web browser to initiate the pull request creation.

2. **Clean Up (After Pull Request is Merged)**:
    ```bash
    # Deletes the local branch
    git branch -d your-branch-name
    
    # Removes the branch from the remote repository
    git push origin --delete your-branch-name
    ```

Remember to replace `your-branch-name` with the desired branch name and adjust the commit message as necessary.

## Git & GitHub in PowerShell

1. **Initialize Git in a Directory**:
    ```powershell
    git init
    ```

2. **Create and Commit a README File**:
    ```powershell
    echo "# SDA-code" > README.md
    git add README.md
    git commit -m 'first commit'
    ```

3. **Create a New GitHub Repository**:
    ```powershell
    # Requires the GitHub CLI tool (gh) to be installed
    gh repo create your-repo-name --public
    ```

4. **Link Local Repo to Remote and Push**:
    ```powershell
    git remote add origin https://github.com/SamuelDevdas/SDA-code.git
    git push -u origin SamuelDevdas
    ```

5. **Delete the .git Folder (Use with Caution!)**:
    ```powershell
    # Removes the entire git history and configuration
    Remove-Item -Recurse -Force .git
    ```

Replace `your-repo-name` with the desired repository name and adjust other placeholders like `SamuelDevdas` as necessary.

---
## PowerShell & Terminal Tips
**Run VSCode Terminal as Administrator**

Change execution policy
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
Activate Linux subsystem from PowerShell
```
wsl
```
For Code Runner in VSCode with virtual env
```
"python": "$pythonPath -u",
```
---
## Ocean.py Configuration
```
export MUMBAI_RPC_URL=https://rpc-mumbai.maticvigil.com
```
```
echo $MUMBAI_RPC_URL
```