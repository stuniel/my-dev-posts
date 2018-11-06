## Processes

### Find and kill a process

Assuming you're looking to kill whatever is on port 3000 (which is what webrick normally uses), type this in your terminal to find out the PID of the process:
```
$ lsof -wni tcp:3000
```

Then, use the number in the PID column to kill the process:
```
$ kill -9 PID
```
