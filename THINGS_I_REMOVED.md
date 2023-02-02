# Things I removed that could be useful

## From Windows -> WSL

This section was about mounting for the sake of hot-reloading. It is complex but perhaps necessary so we can keep it around, but I think the core thing is teaching the Windows students to predominantly do development from within the WSL environment itself and not to keep their files in Windows file system and then this sort of trickery is unnecessary I believe. Basically I don't want to share instructions that I myself don't understand and am simply treating as black magic to solve a problem I have not yet myself encountered.

---

The last thing we will need to do is mount WSL to share metadata: (This will enable your computer to run hot-reloads during development)

```bash
#Enter
cd ..
#until your path on your teminal looks like this
<UnixUsername>@<YourComputer>:/mnt

#Now run (You wont see any changes)
sudo umount /mnt/c

#finally end it by running (You wont see any changes)
sudo mount -t drvfs C: /mnt/c -o metadata

#now go back to the original path
cd c
cd Users
cd <UnixName>

#This should be the final outcome
<UnixUsername>@<YourComputer>: /mnt/c/Users/<username>$
```

---

## From General -> Postgresql

Once again this just feels like an overly complex solution to a specific problem that invovles commands that are not installed on most systems by default and that I don't actually understand myself, so I don't want to share them as a canonical solution. I also didn't run into this problem, its a very specific problem (the port is occupied), and the solution is questionable (outright kill the port, assuming what is running on it is unimportant)

---

If you'd like to check what port PostgreSQL is running in, you could type in the following on the terminal:

```bash
pg_lsclusters
```

A table will pop up on the terminal, under the Owner header look for postgres, then go left you'll see the Status and after that you'll see the port. Typically the port will be 5432.

In case port 5432 is occupied by a different process run the following:

```bash
#this will find out what is currently on port 5432 and tell you which PID belongs to you
netstat -aon | findstr 5432

#it will provide the following
TCP    [::]:5432[::]:0                 LISTENING       18996

#this will kill the current process using port 5432
taskkill /pid 18996 /f <desired pid>
```

---
