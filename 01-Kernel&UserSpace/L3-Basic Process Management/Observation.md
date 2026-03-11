# Observations – Linux Process Management

## 1. Identifying the Shell Process

First, I checked the PID of my current shell using:

echo $$

This command returned the process ID of the shell that is running my commands.

Every process in Linux has a unique identifier called a PID (Process ID).  
The shell acts as the parent process for commands started from it.

---

## 2. Creating a Background Process

I started a background process using:

sleep 120 &

The `&` symbol allowed the process to run in the background while the shell remained usable.

Using:

jobs -l

I was able to identify the PID of the running `sleep` process.

This confirmed that the shell created a new child process to run the command.

---

## 3. Observing Parent–Child Relationships

To inspect the process hierarchy, I used:

ps -f --forest

This command displayed a tree view of running processes.

Example observation:

bash (parent process)
└─ sleep (child process)

This confirmed that the `sleep` command was started by the shell and inherited it as the parent process (PPID).

---

## 4. Inspecting Process Details

Using:

ps aux

I observed detailed information about running processes, including:

- `%CPU` – CPU usage
- `%MEM` – Memory usage
- `STAT` – Process state
- `PID` – Process identifier
- `USER` – Process owner

This information is useful for system monitoring and troubleshooting.

---

## 5. Controlling Processes Using Signals

I practiced sending signals to processes using:

pkill -STOP sleep

This paused the running process.

Then I resumed it using:

pkill -CONT sleep

Finally, I terminated the process using:

kill <PID>

The default signal sent by `kill` is **SIGTERM**, which politely requests the process to terminate.

If necessary, a forced termination can be performed using:

kill -9 <PID>

which sends **SIGKILL** and immediately stops the process.

---

## Conclusion

This lab demonstrated how Linux creates and manages processes.  
Processes started from the shell become child processes with their own PID while keeping the shell as their parent (PPID).

Using tools like `ps`, `jobs`, `kill`, and `pkill`, it is possible to inspect and control running processes.  
Understanding process hierarchy and signals is essential for Linux system administration and troubleshooting.