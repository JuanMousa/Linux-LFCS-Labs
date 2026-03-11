# Linux Process Management Lab – Basic Process Control

## Objective
Understand how Linux manages processes and how operators can inspect and control them.

## Tools Used
- echo
- sleep
- jobs
- ps
- kill
- pkill

## Experiment

1. Checked the PID of the current shell:
   echo $$

2. Started a background process:
   sleep 120 &

3. Found the PID of the running process:
   jobs -l

4. Observed the parent-child process relationship:
   ps -f --forest

5. Inspected detailed process information:
   ps aux

6. Practiced stopping and continuing processes using signals:
   pkill -STOP sleep  
   pkill -CONT sleep

7. Terminated the process:
   kill <PID>

## Key Findings

- Each running process has a unique identifier called a PID.
- Processes started from the shell become child processes and inherit the shell as their parent (PPID).
- Background processes allow the shell to continue executing other commands.
- The `ps` command can be used to inspect running processes and understand their hierarchy.
- Signals such as SIGTERM, SIGKILL, SIGSTOP, and SIGCONT can be used to control process behavior.

## Learning Outcome

This lab demonstrates:
- Basic Linux process management
- Understanding of PID and PPID relationships
- Using `ps` for process inspection and troubleshooting
- Controlling processes using signals
- Practical use of process management tools for system administration