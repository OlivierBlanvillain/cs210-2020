# Tools Setup

# Step 1: Create an account on gitlab.epfl.ch

Go to [gitlab.epfl.ch](https://gitlab.epfl.ch/) and log in with your EPFL account, do this as soon as
possible because it will take some time between the account creation and the
assignment submission system working for your account.

## Step 2: Installing the Java Development Kit (JDK)

### On Linux
#### On Ubuntu and Debian

```shell
sudo apt-get update && sudo apt-get install openjdk-8-jdk
sudo update-java-alternatives --set /usr/lib/jvm/java-1.8.0-openjdk-amd64
```

#### On Fedora
```shell
sudo dnf install java-1.8.0-openjdk-devel
```

### On macOS

First, install Homebrew:
```shell
/usr/bin/ruby -e "$(curl -kfsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Install OpenJDK 8:
```shell
brew tap AdoptOpenJDK/openjdk
brew cask install adoptopenjdk8
```

Set it as the default Java version:
```shell
echo 'export JAVA_HOME="$(/usr/libexec/java_home -v 1.8)"' >> ~/.bash_profile
echo 'export PATH="$JAVA_HOME/bin:$PATH"' >> ~/.bash_profile
```

At this point, make sure to close the terminal and open a new one.

### On Windows

[Download and run the OpenJDK 8 installer.](https://adoptopenjdk.net)

## Step 3: Verify your JDK installation

In a terminal, run:
```shell
java -version
```
The version number displayed on the first line should start with `1.8`. If this is not the case, then the wrong version of Java is on your `$PATH`.
See [https://www.java.com/en/download/help/path.xml](https://www.java.com/en/download/help/path.xml) for information on how to change this.


## Step 4: Installing sbt

`sbt` is the build tool we use to compile and run Scala programs.

### On Linux

See [https://www.scala-sbt.org/1.x/docs/Installing-sbt-on-Linux.html](https://www.scala-sbt.org/1.x/docs/Installing-sbt-on-Linux.html).

### On macOS

```terminal
brew install sbt@1
```

### On Windows

Download and run [https://piccolo.link/sbt-1.2.8.msi](https://piccolo.link/sbt-1.2.8.msi)

## Step 5: Installing git

git is a version control system.

See [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)


Once git is installed, please run:

```shell
git config --global core.autocrlf false
```

If this command worked it will not print anything.

## Step 6: Installing VSCode

VSCode is the IDE we strongly recommend using for this class (you are free to use any editor you want, but we won't don't have the resources to help you configure it for Scala).

### On Linux

See [https://code.visualstudio.com/docs/setup/linux](https://code.visualstudio.com/docs/setup/linux)

### On macOS

See [https://code.visualstudio.com/docs/setup/mac](https://code.visualstudio.com/docs/setup/mac).
Make sure to follow both the "Installation" and "Launching from the Command Line" parts of the setup!

### On Windows

See [https://code.visualstudio.com/docs/setup/windows](https://code.visualstudio.com/docs/setup/windows).
Make sure that the checkbox "Add to PATH (available after restart)" in the installer is checked.

## Step 7: Verify your VSCode installation

Run:
```shell
code
```
VSCode is correctly installed if this opens a window, you can then close this
window. If the `code` command is not recognized, try restarting your computer.

## Step 8: Generate a public/private SSH key pair

To submit assignments, you will need an SSH key. If you don't already have one, here's how to generate it:

### Installing OpenSSH

#### Ubuntu and Debian

```shell
sudo apt-get update && sudo apt-get install openssh-client
```

#### macOS

Nothing to do, OpenSSH is pre-installed

#### Windows

The simplest solution is to have an up-to-date Windows 10 and follow [https://www.howtogeek.com/336775/how-to-enable-and-use-windows-10s-built-in-ssh-commands/](https://www.howtogeek.com/336775/how-to-enable-and-use-windows-10s-built-in-ssh-commands/).

### Generating the key pair

```shell
ssh-keygen -t rsa -b 4096 -C "youremail@example.com"
```

 The command will then ask for a location, which you can leave as the default. It will then also ask for a passphrase to encrypt your private key, which you may leave empty. If you don't, make sure to remember your passphrase!

### Adding your public key on Gitlab

To be able to push your code, you'll need to add the public part of your key on Gitlab:
- Go to [gitlab.epfl.ch](https://gitlab.epfl.ch), log in with your EPFL account
- Go to [gitlab.epfl.ch/profile/keys](https://gitlab.epfl.ch/profile/keys) and copy-paste the content of the `id_rsa.pub` file created by the `ssh-keygen` command you just ran (when the command was ran it printed the location where this file was saved).
- Press `Add key`

## Step 9: Follow the example assignment

The description of the example assignment (in your personnal gitlab repository) contains critical information to properly use the tools you just installed, don't miss it!
