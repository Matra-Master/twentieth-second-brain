---
created: 20231109-1044
tags:
  - linux
  - commands
  - devops
---
Logrotate configs go in:
* `/etc/logrotate.conf` - Default conf file
* `/etc/logrotate.d/` - Folder with specifics for each program or logfile

I made one for caf production because it's logfile was growing rapidly
```
/var/www/caf-api/storage/logs/laravel.log {
  weekly
  rotate 4
  missingok
  notifempty
  compress
  delaycompress
  su www-data www-data
}
```

This config does rotations *weekly*, supports 4 logfiles total and deletes the last one when it rotates to the next. *Ignores when empty* and also *uses www-data user* because the folder is from that user. 

There's a way to make a _dry run_ of logrotate to test configs

```bash
logrotate -d /etc/logrotate.d/prod-laralog
```


---
## Related Ideas:
* [[fleeting]]
* [[]]