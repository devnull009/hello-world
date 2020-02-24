# Configure your development environment

## Step 1 - Generate SSH keys

`ssh-keygen -t rsa -f devkey`<br>
**Note:** The same SSH keys will be used to communicate with GitHub repository. Make sure key name is called after the repository for convenience.<br>

## Step 2 - Make the key available for GitHib

Login to GitHub and navigate to top right corner and then select Settings. On the next page select **SSH and GPG keys**.<br>
Click on **New SSH key**, give it a name and paste the contents of your **public** key which was generated.<br>
Use the following command to find out what is generated:<br>
`cat devkey.pub`<br>

**Note:** You will be asked to confirm the new key by entering your GitHub password!

## Step 3 - (Optional) For developers

**Note:** In Unix-like environment you have to start **ssh-agent** in background and import your **private** key - devkey.

``eval `ssh-agent` ``<br>
`ssh-add devkey`<br>
`git clone git@github.com:devnull009/hello-world.git`<br>

## Step 4 - (Optional) Build the code manually

Build: `javac src/main/java/App.java`<br>
Run: `cd src/main/java && java App`

## Step 5 - Configure Jenkins to work with GitHub

This step could be considered as security step because configuration is done manually and requires human interaction. To avoid publishing any credentials please follow this scenario.<br>

1. Login inside Jenkins
2. Go to **Credentials**
3. Click on **Jenkins**
4. Click on **Global credentials (unrestricted)**
5. On the left, click on **Add credentials**
6. Select the kind to be **SSH username with private key**
7. Leave the scope to **global**
8. (Optional) Provide meaninful **description**
9. Put your **username**
10. On **Private Key**, click **Enter directly** and paste you generated private **devkey**

Now, when you create a new **Pipeline** job and select **SCM** to be **Git** - from the **Credentials** drop-down you will be able to select your key by name.