# npm-on-windows
This is the guideline for nodejs + npm installation on Windows (including windows 7)

# Description
npm and Node.js are quite common to the developers but they are unfriendly to Windows.

If you use .msi installation, it usually fails. (see https://github.com/npm/npmlog/issues/48)

Here is to introduce a proper method for its installation.

# Official Files
| File | Version | Release Date | Download |
| --- | --- | --- | --- |
| Node.js (Windows 7) | v12.22.6 (LTS) | 31-Aug-2021 | https://nodejs.org/download/release/v12.22.6/win-x64/node.exe
| Node.js (Windows 8.1+) | v14.17.6 (LTS) | 31-Aug-2021 | https://nodejs.org/download/release/v14.17.6/win-x64/node.exe
| npm (Windows 7+) | 1.4.9 (zip) | 01-May-2014 | https://nodejs.org/dist/npm/npm-1.4.9.zip
| npm (Windows 7+) | 1.4.9 (tgz) | 01-May-2014 | https://nodejs.org/dist/npm/npm-1.4.9.tgz

![qwcdsvf](https://user-images.githubusercontent.com/44498510/131765520-60a3c2e1-5e92-4e8b-a4b0-971440705c71.PNG)
![qdsvfdbt](https://user-images.githubusercontent.com/44498510/131765523-f522ed26-6a03-4973-8367-2d753a639d8b.PNG)

## Node.js v13?

* Last installable Node.js on Windows 7 is v13.14.0 ( see [Install Node.js on Windows 7](https://www.centennialsoftwaresolutions.com/post/install-node-js-on-windows-7) )
* There is no LTS version in v13 ( https://nodejs.org/en/blog/release/ )
* Up to 2021-09-01, Node.js's [Committee](https://nodejs.org/en/about/community/) has chosen to maintain v12 LTS instead of v13
* Therefore, it is highly not recommended to install any v13 version

## Official Releases

* List of releases: https://nodejs.org/en/blog/release/
* List of downloads: https://nodejs.org/en/download/releases/

# Installation Guide

The following installations is to Node.js v12.18.4 (LTS) and npm v6.14.6. 

(For your own installation, you shall refer the corresponding npm version in https://nodejs.org/en/download/releases/ )

## Part A - Basic Files for nodejs and npm

1. Download node.exe from https://nodejs.org/download/release/v12.18.4/win-x64/node.exe and save it to C:\nodejs
2. Download npm.zip from https://nodejs.org/dist/npm/npm-1.4.9.zip and extract "node_modules" and "npm.cmd" to C:\nodejs
3. Download npm.tgz from https://nodejs.org/dist/npm/npm-1.4.9.tgz and extract "npm" (from npm/bin) to C:\nodejs *(Optional?)*

![explorer-downloaded](https://user-images.githubusercontent.com/44498510/131765182-cd87006e-39ae-4aec-95f2-db1c0859ffc8.png)

4. Open **[cmd](https://www.lifewire.com/how-to-open-command-prompt-2618089)** and type to check the following:
```
C:
cd nodejs
node -v //display "v12.18.4"
npm -v //display "v1.4.9"
```
![cmd-result-version-check](https://user-images.githubusercontent.com/44498510/131615142-186d7407-4e4f-40a4-9bb7-9771abda9c1d.png)

## Part B - Set your folder locations

1. Create Empty Directories "C:\nodejs\node_global" and "C:\nodejs\node_cache"

![1423556-20190119145310357-1442462088](https://user-images.githubusercontent.com/44498510/131615134-310e51b9-c196-4490-b085-4ab450d4e7cf.png)

2. add PATH "C:\nodejs\\;C:\nodejs\node_global\\;"

![1423556-20190119151816709-1265471023](https://user-images.githubusercontent.com/44498510/131615255-b52e05b6-e756-4663-9503-670821e29f69.png)![1423556-20190119152556038-514540680](https://user-images.githubusercontent.com/44498510/131615271-85d427dc-443a-4cd9-9bd9-1d59e27492ae.png)

3. add system variable "NODE_PATH" as "C:\nodejs\node_global\node_modules"

![1423556-20190119151816709-1265471023](https://user-images.githubusercontent.com/44498510/131615255-b52e05b6-e756-4663-9503-670821e29f69.png)![1423556-20190119152300535-790205673](https://user-images.githubusercontent.com/44498510/131615313-8d89e699-ff32-4fea-b253-e94f19e806da.png)

4. Open **[cmd](https://www.lifewire.com/how-to-open-command-prompt-2618089)** and type to check the following:
```
npm config set prefix "C:\nodejs\node_global"
npm config set cache "C:\nodejs\node_cache"
```
*As you have added the path "C:\nodejs\" to your system environment, "C: cd nodejs" is no longer required.

## Part C - Install the new npm to node_global

1. Type the following to install the npm in your "C:\nodejs\node_global" (using old npm)
```
npm install -g npm@6.14.6
```

2. Remove the unnecessary old npm files in "C:\nodejs" - leaving only "node.exe", "node_global" and "node_cache"
![wcdsvf](https://user-images.githubusercontent.com/44498510/132113281-1d21af19-01d5-4f77-9e52-da080e03aef2.PNG)

3. Open **[cmd](https://www.lifewire.com/how-to-open-command-prompt-2618089)** and type to check the following:
```
cd nodejs
node -v //display "v12.18.4"
npm -v //display "v6.14.6"
```

7. Run cmd again to ensure the npm paths are set
```
npm config set prefix "C:\nodejs\node_global"
npm config set cache "C:\nodejs\node_cache"
```

# Appendix

## Install Yarn
```
npm install --global yarn
```

## Install Vue CLI
```
npm install --global @vue/cli
```

* It is highly recommended to use `vue create XXXXX --packageManager npm` instead of yarn
* Default Profile for PackageManager: `%HOMEPATH%\.vuerc`

## Install A Package Locally
```
npm install xxxx
```
## Run A Package Installed Locally
```
npx xxxx .....
```

## VS Code
```
cd xxxxx
code .
```
