## Kill the unwated user using PID Id

View the loginned user with timing we use,
```
who -H
```
Find the specified user pid id,
```
ps -U (user)

example:
--------
ps -U ubuntu
```
Kill the pid id for your unwanted user,
```
sudo pkill -9 -s (pid_id)

example:
--------
sudo pkill -9 -s 17123
```
