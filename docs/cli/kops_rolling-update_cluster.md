## kops rolling-update cluster

Rolling update a cluster.

### Synopsis


This command updates a kubernetes cluster to match the cloud, and kops specifications. 

To perform rolling update, you need to update the cloud resources first with "kops update cluster" 

Note: terraform users will need run the following commands all from the same directory "kops update cluster --target=terraform" then "terraform plan" then "terraform apply" prior to running "kops rolling-update cluster" 

Use export KOPS FEATURE FLAGS="+DrainAndValidateRollingUpdate" to use beta code that drains the nodes and validates the cluster.  New flags for Drain and Validation operations will be shown when the environment variable is set.

```
kops rolling-update cluster
```

### Examples

```
  # Roll the currently selected kops cluster
  kops rolling-update cluster --yes
  
  # Roll the k8s-cluster.example.com kops cluster
  # use the new drain an validate functionality
  export KOPS_FEATURE_FLAGS="+DrainAndValidateRollingUpdate"
  kops rolling-update cluster k8s-cluster.example.com --yes \
  --fail-on-validate-error="false" \
  --master-interval=8m \
  --node-interval=8m
  
  
  # Roll the k8s-cluster.example.com kops cluster
  # only roll the node instancegroup
  # use the new drain an validate functionality
  export KOPS_FEATURE_FLAGS="+DrainAndValidateRollingUpdate"
  kops rolling-update cluster k8s-cluster.example.com --yes \
  --fail-on-validate-error="false" \
  --node-interval 8m \
  --instance-group nodes
```

### Options

```
      --bastion-interval duration    Time to wait between restarting bastions (default 5m0s)
      --cloudonly                    Perform rolling update without confirming progress with k8s
      --force                        Force rolling update, even if no changes
      --instance-group stringSlice   List of instance groups to update (defaults to all if not specified)
      --master-interval duration     Time to wait between restarting masters (default 5m0s)
      --node-interval duration       Time to wait between restarting nodes (default 2m0s)
      --yes                          perform rolling update without confirmation
```

### Options inherited from parent commands

```
      --alsologtostderr                  log to standard error as well as files
      --config string                    config file (default is $HOME/.kops.yaml)
      --log_backtrace_at traceLocation   when logging hits line file:N, emit a stack trace (default :0)
      --log_dir string                   If non-empty, write log files in this directory
      --logtostderr                      log to standard error instead of files (default false)
      --name string                      Name of cluster
      --state string                     Location of state storage
      --stderrthreshold severity         logs at or above this threshold go to stderr (default 2)
  -v, --v Level                          log level for V logs
      --vmodule moduleSpec               comma-separated list of pattern=N settings for file-filtered logging
```

### SEE ALSO
* [kops rolling-update](kops_rolling-update.md)	 - Rolling update a cluster.

