# mac-dev-setup
Steps for setting up a new Mac computer for development  


## General Setup  

Using the Terminal, follow the steps below.  

### Download command line tools
`xcode-select --install`  

### Configure [Github SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

**Create new ssh key**  
`ssh-keygen -t ed25519 -C "<email>"`

**Copy the ssh public key to the clipboard**  
`pbcopy < ~/.ssh/id_ed25519.pub`

**Add public key to Github**  
From the Github console, navigate to the SSH key settings:  
Settings > SSH and GPG keys  
Click New SSH key button, give the key a name, select Authentication Key, and paste the public key from the clipboard.
Click the Add SSH key button to save the key.

**Add key to ssh-agent (to save passphrase)**  
```
eval "$(ssh-agent -s)"
touch ~/.ssh/config
vi ~/.ssh/config
```
Add the following:
```
  Host github.com
    AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```

`ssh-add --apple-use-keychain ~/.ssh/id_ed25519`

**Github config**

Configure User's name and email  
```
git config --global user.name "<name>"
git config --global user.email "<email>"
```

### Install [Homebrew](https://brew.sh)

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

**Add Homebrew to your PATH variable**  
```
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Setup the build environment for Mac OS:  
`brew install openssl readline sqlite3 xz zlib tcl-tk`


## Setup Python
### Setup [pyenv](https://github.com/pyenv/pyenv)
**Install pyenv**  
`brew install pyenv`

**Setup shell environment**  
```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

**Restart shell**  
`exec "$SHELL"`

**Install python version**  
`pyenv install <version>`

**Notes on using pyenv**  
Show all installed versions:  
`pyenv versions`
Select a python version:  
```
pyenv shell <version>
pyenv local <version>
pyenv global <version>
```

Set the python version in the root directory file .pyenv


Setup virtual environments (venv)
Create a virtual environment
python -m venv venv

Activate a virtual environment:
source venv/bin/activate

Deactivate:
deactivate

## Setup Javascript
**Install [NVM](https://github.com/nvm-sh/nvm#installation-and-update)**  
`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash`

**Install the latest LTS verions of Node.js**  
`nvm install --lts`

**Notes on useing NVM**  
**Show all installed versions**  
`nmv ls`

Install version of node:  
`nvm install <version>`

Use a version of node:  
`nvm use <version>`

## Setup zprofile and zshrc
	env variables
	GitHub shortcuts

## Setup Vs Code
