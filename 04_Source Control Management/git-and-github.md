#### Download and install git
``` shell
sudo apt install git-all -y
```

#### Check version
``` shell
git version
```

#### Configure a username
``` shell
git config --global user.name "username"
```

#### Configure an email
``` Shell
git config --global user.email "user@host.com"
```
Use the no-reply email address provided by github if your email is set to private. (Settings > Emails > Primary Email)

#### Configure credential store
``` shell
git config --global credential.helper store
```
This will save your username and password to the ~/.git-credentials file in plaint text. Insecure

#### Generate a PAT (Personal Access Token)
On the github website, go to:
- Settings > 
	- Developer Options > 
		- Personal Access Tokens > 
			- Generate New Token > Enter your password >
				- Enter a Note
				- Set Expiration
				- Grant permissions (all)
				- Generate Token

 Keep a copy of this locally as you can only see it once. 

#### Clone the repo
``` shell
git clone https://repo-url
```

#### Check the status
Make sure you're in the directory of the project
``` shell
git status
```

#### Add files to staging
``` shell
git add <file-name>
```

#### Commit changes to repo
``` Shell
git commit -m "A message about the reason for a commit"
```

#### Update the remote repo
``` Shell
git push
```
Note: Depending on how the repo is configured you may need to enter your username and PAT

#### Remove a file from the repo
```
git rm <file-name>
```

