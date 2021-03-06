vault
=====

[![NPM](https://nodei.co/npm/vault-tool.png?mini=true)](https://nodei.co/npm/vault-tool/)

Module and command line interface (cli) for encrypting, storing retrieving, and decrypting text.
Encrypted text entries are retrieved by keys (names) in a JSON file stored in your home directory
(`~/.vault.json`).

    npm install -g vault-tool
    
    export VAULT_PASS=secret
    
    vault set <key> <text>
    vault get <key>
    vault remove <key>
    
    vault --help

or add to your own package

    npm install --save vault-tool

and add a run script to your `package.json` file to access the cli:

    "scripts": {
      "vault": "vault"
    }
 
This works because `npm` adds `node_modules/.bin` to the path when executing a package run script. Invoke
like this:

    npm run vault

Vault password
--------------

Vault requires that the `VAULT_PASS` environment variable be set before use.

    export VAULT_PASS=secret

You probably want to store the password in your shell profile.

Note: you can use different passwords to encrypt/decrypt different text entries. You can supply
the password directly on the command line, like this:

    VAULT_PASS=secret vault set <key> <text>
    VAULT_PASS=secret vault get <key>
    VAULT_PASS=secret vault remove <key>

API
---

    var vault = require('vault-tool');
    
    
    vault.put(key, plainText, function(err) {
    });
    
    vault.get(key, function(err, plainText) {
    });
    
    vault.remove(key, function(err) {
    });
    
    
    // utility methods
    
    var cipherText = vault.encrypt(key, plainText, function(err, cipherText);
    
    var plainText = vault.decrypt(key, cipherText, function(err, plainText);


