# kubectl-backup-diff

A kubectl plugin to take backup of a kubernetes resource and diff the state change with current


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

