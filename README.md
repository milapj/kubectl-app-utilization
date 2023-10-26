# kubectl-backup-diff

A kubectl plugin to take backup of a kubernetes resource and diff the state change with current. Learn more about kubectl plugins [here](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/).

* backup-diff creates a backup of a resource and compares the change between the backed-up state at a specific point in time and the current state, showing the state drift.

* Functions similar to git diff. This can be pretty useful during disaster recovery or debugging to recover previous states of resources that were updated on the fly w/o having to re-release.

* The backup is stored at /tmp/backups/<resource-type> by default, but it can be stored at a user-specified path. The resources can also be re-created using the backup files.

## Installation

### Pre-requisite
* [krew](https://krew.sigs.k8s.io/) - check out [this](https://krew.sigs.k8s.io/docs/user-guide/setup/install/) guide on how to install krew


### Instal via Krew

1. Add kubezone index to krew
    ```console
    $ kubectl krew index add kubezone https://github.com/milapj/kubezone
    ```
1. Verify kubezone index is added
    ```console
    $ kubectl krew index list
    INDEX    URL
    default  https://github.com/kubernetes-sigs/krew-index.git
    foo      https://github.com/foo/custom-index.git
    ```
1. Install plugin indexed in kubezone
    ```console
    $ kubectl krew install kubezone/backup-diff
    Updated the local copy of plugin index.
    Updated the local copy of plugin index "kubezone".
    Installing plugin: backup-diff
    Installed plugin: backup-diff
    \
    | Use this plugin:
    |      kubectl backup-diff
    | Documentation:
    |      https://github.com/milapj/kubectl-backup-diff
    /
    ```


## Usage
```shell
Usage:
    -c create a backup of a resource
    -d print diff of current and a specific backup version
    -n namespace
    -t resource type
    -v specific backup version in time
    -p path to store backups at the user specified path, default is /tmp/backups/
    
    Example:
        kubectl backup-diff -c -n my-app -t configmap my-configmap
        kubectl backuo-diff -d -n my-app -t configmap -v 4 my-configmap
```

## Demo

https://github.com/kubernetes-sigs/krew-index/assets/9828402/380264cf-1f04-44f7-b4e3-6c928f4c8fa7

## Bug Reports

If you're having an issue with an installed plugin, file an issue.