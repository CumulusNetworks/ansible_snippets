# Collect Supports

This ansible snippet will login to devices and issue the cl-support command.
Once the CL support command has been executed and a new file is available, the 
script uploads the file back to the ansible server into the destination_directory.

### Using the Snippet

Update the included hosts file with the hosts used in your network.


```
$ ansible-playbook ./collect_support.yml
```

Similarly, there is another matching script that will login to a switch and remove any existing CL support files.

```
$ ansible-playbook ./remove_support_files.yml
```


Warning:
This code may not be complete or even functional.

Use at your own risk!


