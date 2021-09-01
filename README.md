# npm-on-windows
This is the guideline for nodejs + npm installation on Windows (including windows 7)

# Description
npm and Node.js are quite common to the developers but they are unfriendly to Windows.
If you use .msi installation, it usually fails. (see "https://github.com/npm/npmlog/issues/48")
Here is to introduce a proper method for its installation.

# Official Files
| File | Version | Release Date | Download |
| --- | --- | --- | --- |
| Node.js (Windows 7) | v12.22.6 (LTS) | 31-Aug-2021 | https://nodejs.org/download/release/v12.22.6/win-x64/node.exe
| Node.js (Windows 8.1+) | v14.17.6 (LTS) | 31-Aug-2021 | https://nodejs.org/download/release/v14.17.6/win-x64/node.exe
| npm (Windows 7+) Part 1 | 1.4.9 (zip) | 01-May-2014 | https://nodejs.org/dist/npm/npm-1.4.9.zip
| npm (Windows 7+) Part 2 | 1.4.9 (tgz) | 01-May-2014 | https://nodejs.org/dist/npm/npm-1.4.9.tgz

Remarks: 
* Last installable Node.js on Windows 7 is v13.14.0 ( https://www.centennialsoftwaresolutions.com/post/install-node-js-on-windows-7 )
* There is no LTS version in v13 ( https://nodejs.org/en/blog/release/ )
* Up to 2021-09-01, nodejs choose to maintain LTS versions in v12 instead of v13 - it is highly not recommended to install any v13 version
* List of downloads: https://nodejs.org/en/download/releases/


# Installation Guide

The following installations is to Node.js v12.18.4 (LTS) and npm v6.14.6. 
(npm versions shall refer to https://nodejs.org/en/download/releases/ )

1. Download node.exe from https://nodejs.org/download/release/v12.18.4/win-x64/node.exe and save it to C:\nodejs
2. Download npm.zip from https://nodejs.org/dist/npm/npm-1.4.9.zip and extract "node_modules" and "npm.cmd" to C:\nodejs
3. Download npm.tgz from https://nodejs.org/dist/npm/npm-1.4.9.tgz and extract "npm" (from npm/bin) to C:\nodejs

4. Create Empty Directories "C:\nodejs\node_global" and "C:\nodejs\node_cache"

5. add PATH "C:\nodejs; C:\nodejs\node_global; "
6. open cmd 
7. check "node -v" (12.18.4) and "npm -v" (1.4.9)
8. npm install -g npm@6.14.15

9. npm config set prefix "C:\nodejs\node_global"
10. npm config set cache "C:\nodejs\node_cache"

11. add system variable "NODE_PATH" as "C:\nodejs\node_global\node_modules"
