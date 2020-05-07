README last updated on 07/08/2005.

AFIT Data Files
---------------
This data distribution consists of the following 14 files provided by
the Air Force Institute of Technology (AFIT):

    reqlf12.dat requp12.dat
    reqlf13.dat requp13.dat
    reqlf14.dat requp14.dat
    reqlf15.dat requp15.dat
    reqlf16.dat requp16.dat
    reqlf17.dat requp17.dat
    reqlf18.dat requp18.dat

The AFIT data consists of seven problems, with two files for each
problem: one file for high-altitude requests and one for low-altitude
requests.  The files are organized as follows:

  Column 1: request ID
  Column 2: antenna ID
  Column 3: visibility window start time
  Column 4: visibility window end time
  Column 5: task duration
  Column 6: turn-around time (setup time)
  Column 7: orbit information (not used)

Example:

   1 INDI-A   13   28   15 20 655305565.9
   1 INDI-B   13   28   15 20 655305565.9
   2 POGO-A   26   42   16 20 253209733.2
   2 POGO-B   26   42   16 20 253209733.2
   2 POGO-C   26   42   16 20 253209733.2
   3 BOSS-A   39   55   16 20 975702430.1
   3 BOSS-B   39   55   16 20 975702430.1

Request 1 may run on INDI-A or INDI-B (subject to the note on obsolete
antennas below).  Its visibility window is from minute 13 to minute 28
and it will take 15 minutes.

Request 2 may run on POGO-A, POGO-B or POGO-C.  Its visibility window
is from minute 26 to minute 42 and it will take 16 minutes.

Request 3 may run on BOSS-A or BOSS-B.  Its visibility window is from
minute 39 to minute 55 and it will take 16 minutes.

(Note that none of these requests have any slack since they are low-
altitude requests.)


Antennas
--------
Even though some antennas are specified as possible alternatives
in the files, they cannot considered when solving problems.  (For
example, the antenna may not exist anymore.)  Thus the following 3
antennas cannot be used to schedule requests:

     INDI-B, PIKE-B, REEF-B


Time Windows
-----------
Time windows are half-open intervals.  In our implementation they are
defined as (start-time, end-time], so that if there is a task starting at
time 0 and ending at time 5, the minutes included are 1, 2, 3, 4, 5.


Turnaround Time
---------------
The turnaround time is a duration that is scheduled right before a task
starts and during which no other task can be scheduled on the same antenna. 


Impossible Tasks?
-----------------
In some cases it will appear that a task is impossible.  For example,
in file reqlf12.dat the following task appears:

   1 INDI-A   13   28   15 20 655305565.9

This request runs on INDI-A, has a time window of (13,28], a duration
of 15 minutes and a turnaround time of 20 minutes.

Note that this implies that with the turnaround time, the task can't
start until minute 20 and can't finish until minute 35 -- well outside
its prescribed time window.

To address this issue, we assume that the turnaround time may begin
before minute 0.  Thus the first available slot for the task is at
minute 14 and it could run from minute 14 through minute 28.

