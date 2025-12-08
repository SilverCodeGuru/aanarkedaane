# Processes

ps 

shows only processes running in this shell

ps -u username | grep progamname

pgrep programname

top

htop

two types of processes
foreground
background


ctrl+c
another version of kill

sleep 30

ctrl+z - stopped a process - put it to sleep
jobs - 

bg job-number - run the job in background
fg job-number - bring the job to foreground so you can now kill it with ctrl+c

process with status T means traced (stopped)

kill -l
to see a list of all the signals you can send

sleep 900 &
apersand at the end makes the process backgroud

interrupt signal is 2
kill -2 kills the background sleep process

pkill ping - all pings will be killed
