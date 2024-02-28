# The Ultimate Workflow Tool for Remote Preview and Developer Environments

This is the public releases page of copl. Check [the web site](https://beta.commandplane.io) for more info abotu how yoiu can benefit from copl.

To reach out to us, email info@commandplane.io

## Quick intro

copl is a cli tool that creates short live ephemeral environments. These environments are created on AWS and runs on dedicated kubernetes clusters with production grade resources like 8vCpu and 32 GB RAM and runs the app with all the dependencies. This environment then is seamlessly attached to the local machine and all the components can be accessed via a browser. 

Where the primary user is the developer, anybody can use it to demo the app, see the latest changes, test the app or scan the app.
## Installation
You can either download from github releases page or use brew to install ther app.

For brew installation, it is simply
```
brew tap commandplaneio/copl
brew install copl
```
To get the latest version via brew, you need to do 
```
brew update
brew upgrade
```
### How to use it

```
copl dev aws --branch main --clean --wait-for-helm  --user nobody
```


It creates the environment on AWS, from the main branch, cleans the existing one and waits for the helm deployment to finish.


```
copl attach --no-log --no-sync
```


It attaches the local computer to the remote environment.You can add ```--no-log``` argument to stop logs streaming.

#### Optional
If you want to upload a specific synchronisation config file, you can do this via the command below.
```
copl config -s any.yaml
```

It uploads the synchronization configuration as a yaml file.

The common pattern is that the remote hot loading environment responds well to the code changes but for library changes the runtime must be restarted. Using this configuration you can tell the copl to kill the pod when there is a library change.
Also this will save you from downloading real time directories like logs, no_modules, etc. For further details check the syncconfig.yaml file under ~/.config/copl directory to see all the options.

## What's next
- VS Code extension
- Point to point VPN
- Persistence
