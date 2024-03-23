## DBWn (D**atabase writer)**:

Database writer process (DBWn) is **an Oracle background process created when you start a database instance**.  
Database writer process (DBWn) is a background process that writes  
buffers in the database buffer cache to data files. Database writer is  
one of the mandatory process.  

![[Untitled 30.png|Untitled 30.png]]

## **LGWR (Log Writer):**

The Log Writer process is **responsible for writing the contents of the redo log buffer to the log file on disk, and for management of the log buffer**.  
Redo log data is always written first to a buffer in memory, then written to disk by the LGWR process when: LGWR is not active for three seconds.  

![[Untitled 1 9.png|Untitled 1 9.png]]

## **SMON (System Monitor):**

SMON (System MONitor) is **an Oracle background process created when you start a database instance**.  
The SMON process performs instance recovery, cleans up after dirty shutdowns and coalesces adjacent free extents into larger free extents. SMON wakes up every 5 minutes to perform housekeeping activities.  

![[Untitled 2 7.png|Untitled 2 7.png]]

## PMON (**Process Monitor**):

The process monitor (PMON) performs process recovery when a user process fails. PMON is responsible for cleaning up the database buffer cache and freeing resources that the user process was using.

![[Untitled 3 7.png|Untitled 3 7.png]]

## CKPT (**Checkpoint**):

**When a checkpoint occurs, Oracle must update the headers of all datafiles to record the details of the checkpoint**.  
This is done by the CKPT process. The CKPT process does not write blocks to disk; DBWn always performs that work.  

![[Untitled 4 7.png|Untitled 4 7.png]]