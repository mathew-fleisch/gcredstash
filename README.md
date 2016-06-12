# gcredstash

## Description

This is a port of [CredStash](https://github.com/fugue/credstash) to Go.

gcredstash manages credentials using AWS Key Management Service (KMS) and DynamoDB.

[![Build Status](https://travis-ci.org/winebarrel/gcredstash.svg?branch=master)](https://travis-ci.org/winebarrel/gcredstash)

## Usage

```
usage: gcredstash [--version] [--help] <command> [<args>]

Available commands are:
    delete    Delete a credential from the store
    get       Get a credential from the store
    getall    Get all credentials from the store
    list      list credentials and their version
    put       Put a credential into the store
    setup     setup the credential store
```

```
$ gcredstash -h delete
usage: gcredstash delete [-v VERSION] credential

$ gcredstash -h get
usage: gcredstash get [-v VERSION] [-n] credential [context [context ...]]

$ gcredstash -h getall
usage: gcredstash getall [context [context ...]]

$ gcredstash -h list
usage: gcredstash list

$ gcredstash -h put
usage: gcredstash put [-k KEY] [-v VERSION] [-a] credential value [context [context ...]]

$ gcredstash -h setup
usage: credstash setup
```

## Put from stdin

```
$ echo 300 | gcredstash put xxx.zzz -
```

## Installation

see https://github.com/winebarrel/gcredstash/releases.

### OS X

```sh
brew install https://raw.githubusercontent.com/winebarrel/gcredstash/master/homebrew/gcredstash.rb
```

### Ubuntu

```sh
wget -q -O- https://github.com/winebarrel/gcredstash/releases/download/vN.N.N/gcredstash_N.N.N_amd64.deb | dpkg -i -
```

## Setup

* `IAM > Encryption Keys`
  * Create Encryption Key: `Alias`: `credstash`
* Run `gcredstash setup`

## Environment variables

```sh
export AWS_REGION=...
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...

# default: credential-store
#export GCREDSTASH_TABLE=...

# default: alias/credstash
#export GCREDSTASH_KMS_KEY"),
```