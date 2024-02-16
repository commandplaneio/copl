# copl-releases

The public release page of copl.
Check the web site for more [info](https://beta.commandplane.io).


To reach out to us, email info@commandplane.io

## Quick intro

copl is a cli tool that creates short live ephemeral environments. These environments are created on AWS and runs on dedicated kubernetes clusters with production grade resources like 8vCpu and 32 GB RAM and runs the app with all the dependencies. This environment then is seamlessly attached to the local machine and all the components can be accessed via a browser. 

Where the primary user is the developer, anybody can use it to demo the app, see the latest changes, test the app or scan the app.

### How to use it


```copl dev aws -b main -c -w```
creates the environment on AWS, from the main branch, cleans the existing one and waits for the helm deployment to finish.


```copl attach```
attaches the local computer to the remote environment.


```copl config -s any.yaml```
uplods the synchronization configuration as a yaml file.

## What's next
- Granular config options for different personas
- Point to point VPN.
