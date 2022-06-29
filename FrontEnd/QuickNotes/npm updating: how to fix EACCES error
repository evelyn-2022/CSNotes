# npm update error

## Problem:

Copied and pasted `npm install -g npm@8.13.1`, got a bunch of errors:

```bash
npm ERR! code EACCES
npm ERR! syscall mkdir
npm ERR! path /usr/local/lib/node_modules/npm-upgrade
npm ERR! errno -13
npm ERR! Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules/npm-upgrade'
npm ERR!  [Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules/npm-upgrade'] {
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'mkdir',
npm ERR!   path: '/usr/local/lib/node_modules/npm-upgrade'
npm ERR! }
npm ERR!
npm ERR! The operation was rejected by your operating system.
npm ERR! It is likely you do not have the permissions to access this file as the current user
npm ERR!
npm ERR! If you believe this might be a permissions issue, please double-check the
npm ERR! permissions of the file and its containing directories, or try running
npm ERR! the command again as root/Administrator.

npm ERR! A complete log of this run can be found in:
```

## Cause:

Need to update node first

## How to fix it:

Update node:

1. First, clear the npm cache: `npm cache clean -f`
2. Install n, Node’s version manager: `npm install -g n`
3. Install the latest stable node release): `sudo n latest`
