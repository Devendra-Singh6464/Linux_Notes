# CRONTAB------

### View thelist of existing cron jobs in your crontab---
```
crontab -l 
```

### If you remove to all cron jobs from your crontab,------
```
crontab -r
```

### prompt before deleting the current user's crontab file.
```
crontab -i
```
 
### Run cron in the foreground (useful for troubleshooting). 
```
cron -f
```
 
### Access and edit the cron table,----
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


###  / devide a value into steps: The slash is used to create specified intervals of time within a range.[Every 10 of every day]
```
*/10 * * * */home/users/devendra.singh/echo "hello"
```

### - a range of values : The Hyphen is used to specify the range of the time in which the task run.
```
0-59 0-23 * * * /home/users/devendra.singh/cp backup1.txt backup1.old
```

example ---
```
30 8 * * 1-5 /home/users/devendra.singh/backup.sh
```
Explanation: This cron job executes the command at 8:30 from Manday to Friday.


## Valuse----
*	any value
,	value list separator
-	range of values
/	step values
@yearly	(non-standard)
@annually	(non-standard)
@monthly	(non-standard)
@weekly	(non-standard)
@daily	(non-standard)
@hourly	(non-standard)
@reboot	(non-standard)
