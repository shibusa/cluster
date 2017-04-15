### Cisco IOS Cluster deploy

# Requirements:
- Python 2.7.10
- napalm_ios (https://napalm.readthedocs.io/en/latest/#)
- privileged, SSH access to respective Cisco IOS devices

# Installation
1. Install "napalm_ios" library.
```
pip install napalm-ios
```

2. Make nscript executable
```
chmod +x nscript
```

# Usage
1. Create a file(s) with the respective clustername in the same directory as 'cluster'.  The file should contain standard Cisco IOS formatting with "version #" on the top and "end" at the bottom.

Example:
Filename: basiccluster
```
version {versionnum}

hostname {hostname}

end
```

2. Create a json file with a dictionary of clusternames in the same directory as 'cluster'.  Within each cluster name should be a list of hosts belonging to the cluster and dictionary of options matching cluster file.

```javascript
{
  "basiccluster":{
    "hosts": ["HOST1","HOST2","HOST3"],
    "options":{
      "versionnum":"12.4",
      "hostname":"router"
    }
  }
  "CLUSTERNAME2":{
    "hosts": ["HOST4","HOST5"],
    "options":{
      "versionnum":"12.4",
      "hostname":"switch"
    }
  }
}
```

3. Run scripts
```
./cluster FILE.json
```
