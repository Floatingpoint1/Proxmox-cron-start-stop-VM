# Auto Start or Shutdown for Container or Virtual Machine

## First create a script file for the VM or download it from Git Repro

### Manual Way for start

```
#!/bin/bash
export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin
qm start 100
```

## And a second one for shutdown

```
#!/bin/bash
export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin
qm shutdown 100
```

## Finally, just add a cron task and you're done.

### Sample:

```
0 13 * * 1-5 /usr/sbin/Scripte/Cron/qm-start-100.sh >/dev/null 2>&1 >/dev/null 2>&1
0 20 * * 1-5 /usr/sbin/Scripte/Cron/qm-shutdown-100.sh >/dev/null 2>&1 >/dev/null 2>&1
```

## Notes:

Unfortunately, in order to run the script, you must have an: 
**export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin**
must be set, because otherwise the job cannot be executed from Cron.

 **>/dev/null 2>&1 >/dev/null 2>&1** in cron must be added so that irrelevant error messages do not block the start of the machine.
