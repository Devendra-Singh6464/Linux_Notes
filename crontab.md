# Crontab 
# CRONTAB------

Show all current jobs---
```
crontab -l 
```

edit o add new	jobs----
```
crontab -e
```

## cron job create Syntax 
```
MIN HOUR DOM MON DOW CMD
*   *	 *   *    *  path/cmd

Field    Description    Allowed Value
MIN      Minute field    0 to 59
HOUR     Hour field      0 to 23
DOM      Day of Month    1-31
MON      Month field     1-12
DOW      Day Of Week     0-6
CMD      Command         Any command to be execute

34 11 17 05 * bash /home/users/devendra.singh/backup.sh

05 12 	*2,4 * :   at 12:05 Pm, only in february and april 


	
