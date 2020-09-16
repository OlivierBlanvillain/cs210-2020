# Tools Setup

## Note

We recommend using Linux or macOS for this course, we also support Windows but
typically people have more trouble getting everything working correctly on
Windows and it's harder for us to help them since we don't use Windows
ourselves.

**On Windows, if your username has spaces or special characters in it, the IDE might not
work properly. Please create a new user with a username containing only letters.**

# Step 1: Create an account on gitlab.epfl.ch, register in a group

If you haven't already [log into gitlab](https://gitlab.epfl.ch/users/sign_in)
and [register in a
group](https://gitlab.epfl.ch/lamp/cs210/-/blob/master/exercises/Group%20workspaces.md),
do this as soon as possible because it will take some time between the account
creation and the lab submission system working for your account.

## Step 2: Installing the Java Development Kit (JDK) and sbt via coursier

We will use coursier to install the correct version of
Java as well as the sbt build tool:

### On Linux

```shell
curl -fLo cs https://git.io/coursier-cli-linux
```
```shell
chmod +x cs
```
```shell
./cs setup -y --jvm 8 --apps cs,sbt
```

### On macOS

First, install the Homebrew package manager:
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
Use Homebrew to install coursier:
```scala
brew install coursier/formulas/coursier
```
```shell
[ -f ~/.bash_profile ] && sudo chmod 0666 ~/.bash_profile
```
```shell
cs setup -y --jvm 8 --apps sbt
```

### On Windows

Download and install the [Visual C++ 2010 Redistributable Package](https://www.microsoft.com/en-us/download/details.aspx?id=14632).

Open `cmd.exe` (and not powershell)

```shell
bitsadmin /transfer cs-cli https://git.io/coursier-cli-windows-exe "%cd%\cs.exe"
```
```shell
.\cs setup -y --jvm 8 --apps cs,sbt
```

(This command might cause your anti-virus to misidentify cs.exe as a virus,
please override that).

If this command fails with `Error running powershell script`, use the following
alternative instructions (if the command didn't fail, continue to the next
step):

1. Run `.\cs setup --jvm 8 --apps cs,sbt`, at every question answer "n" and
   press Enter.
2. The last question should look like "Should we add `C:\...\bin` to your PATH?",
   please copy the `C:\...\bin` part here.
3. Edit the Path environment variable and paste the path you just copied to it, see
   https://www.architectryan.com/2018/08/31/how-to-change-environment-variables-on-windows-10/
   and make sure the path you're adding is the first entry in the Path environment
   variable.
4. Start a **new** cmd.exe and continue with the rest of the instructions

## Step 5: Installing git

git is a version control system.

### On Linux

#### On Ubuntu and Debian

```shell
sudo apt update && sudo apt install git
```

### On Fedora

```shell
sudo dnf install git
```

### On macOS

```shell
brew install git
```

### On Windows

Download and install git from [https://git-scm.com/downloads](https://git-scm.com/downloads).
Once git is installed, open a **new** terminal and run:

```shell
git config --global core.autocrlf false
```

If this command worked it will not print anything.

## Step 6: Installing Code

Visual Studio Code is the IDE we strongly recommend using for this class (you are free to use any editor you want, but we won't don't have the resources to help you configure it for Scala).

### On Linux

See [https://code.visualstudio.com/docs/setup/linux](https://code.visualstudio.com/docs/setup/linux)

### On macOS

See [https://code.visualstudio.com/docs/setup/mac](https://code.visualstudio.com/docs/setup/mac).
Make sure to follow both the "Installation" and "Launching from the Command Line" parts of the setup!

### On Windows

See [https://code.visualstudio.com/docs/setup/windows](https://code.visualstudio.com/docs/setup/windows).
Make sure that the checkbox "Add to PATH (available after restart)" in the
installer is checked.

## Step 7: Installing the Scala support for Code

Open a **new** terminal and run:
```scala
code --install-extension lampepfl.dotty-syntax
```

If you're on Windows and the command is not found, try closing and restarting
the terminal, if that doesn't work

## Step 8: Generate a public/private SSH key pair

To submit labs, you will need an SSH key. If you don't already have one, here's how to generate it:

### Step 8.1: Installing OpenSSH

### On Linux

#### On Ubuntu and Debian

```shell
sudo apt install openssh-client
```

#### On Fedora

```shell
sudo dnf install openssh
```

#### macOS

Nothing to do, OpenSSH is pre-installed

#### Windows

Follow the instructions under "Enable OpenSSH Client in Windows 10" on
[https://winaero.com/blog/enable-openssh-client-windows-10/](https://winaero.com/blog/enable-openssh-client-windows-10/)

### Step 8.2: Generating the key pair

Open a **new** terminal and run:

```shell
ssh-keygen -t rsa -b 4096 -C "youremail@example.com"
```

The command will then ask for a location, which you can leave as the default. It will then also ask for a passphrase to encrypt your private key, which you may leave empty. If you don't, make sure to remember your passphrase!

### Adding your public key on Gitlab

To be able to push your code, you'll need to add the public part of your key on Gitlab:
- Go to [gitlab.epfl.ch](https://gitlab.epfl.ch), log in with your EPFL account
- Go to [gitlab.epfl.ch/profile/keys](https://gitlab.epfl.ch/profile/keys) and copy-paste the content of the `id_rsa.pub` file created by the `ssh-keygen` command you just ran (when the command was ran it printed the location where this file was saved).
- Press `Add key`

## Step 9: Follow the example lab

Time to do the [example lab](example-lab.md)!
