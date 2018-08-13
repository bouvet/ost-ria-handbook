# Installing Java

This chapter describes how to install java and how to configure virtual Java environments. This is not a guide for writing Java code.

## TLDR to get started

If you just want the quick commands for the installation.

```sh
brew install cask jenv
brew tap caskroom/versions
brew cask install java java8
```

You will also need to edit your .bash_profile. See below.

## Get started with detailed descriptions

We assume you already have [installed Homebrew](https://brew.sh/) to get packages for Mac OS.

You will need cask.
```sh
brew install cask
```

Tap cask versions to get access to older versions of java.
```sh
brew tap caskroom/versions
```

Install Java 8. This installation will require that you input your password near the end, before the installation can complete.
```sh
brew cask install java8
```

If you want or need the latest Java version.
```sh
brew cask install java
```

JDKs will be installed at the following directories. Your JDKs versions might be different.
```
/Library/Java/JavaVirtualMachines/jdk1.8.0_181.jdk/Contents/Home/
/Library/Java/JavaVirtualMachines/jdk10.0_2.jdk/Contents/Home/
```

This is a tool for creating Java virtual environments.
```sh
brew install jenv
```

## Editing .bash_profile (initialize jEnv)

Open this file for editing (using whatever editor).
```sh
atom ~/.bash_profile
```

Add this:
```
if which jenv > /dev/null; then eval "$(jenv init -)"; fi
```

Then source your bash_profile file
```
source ~/.bash_profile
```

## Creating a Java Virtual Environment

We will be using jEnv to create Java virtual environments.
[Official jEnv docs](http://www.jenv.be/)

jEnv doesn’t install JDKs, so we have to tell jEnv where to look for them. Type these commands to register JDKs in jEnv (replace the versions with yours):

```
jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0_181.jdk/Contents/Home/
jenv add /Library/Java/JavaVirtualMachines/jdk10.0_2.jdk/Contents/Home/
```

After that, run this command to list all registered JDKs:

```
jenv versions
```

You can set global Java version like this:
```
jenv global 10.0
```

And in your project folder you can use another version like this:
You can set global Java version like this:
```
cd my-project-folder
jenv local 1.8
```

The above command will create a .java-version file at project root.

[Detailed description](http://davidcai.github.io/blog/posts/install-multiple-jdk-on-mac/)