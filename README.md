The slowest function in createTaskPositionMap is _getItemPosition, generateAppointmentSettings takes the most time in it (on the average 43.(3) ms, this is a lot in comparison with the calculation of geometry taking an average of 3.9 ms, 11 times more). ~19% of the time generateAppointmentSettings is occupied by the calculation of cell positions (on the average 8.(3) ms), takes almost the rest of the time (~69%, on the average 29.8 ms) is taken by _prepareAppointmentInfos. Most of the time is spent on the method "cropAppointmentsByStartDayHour" - on the average 8.5(3) ms (!!! it is 28.6% !!!). IT NEEDS TO BE OPTIMIZED FIRST.
There are two more slow methods in this function: createAppointments - 3.2 ms, createGridAppointmentList - 3.2 ms.
|           function/case name          | amount of time, % | amount of time, ms |
|:-------------------------------------:|:-----------------:|:------------------:|
|         createTaskPositionMap         |        100        |        46.7        |
|            getItemPosition            |        94.8       |        44.27       |
|                geometry               |        8.35       |         3.9        |
|      generateAppointmentSettings      |        92.8       |       43.(3)       |

|   function/case name   |PF GAS T*, %| amount of time, % | amount of time, ms |
|:----------------------:|:----------:|:-----------------:|:------------------:|
| calculateCellPositions |   19.23    |       19.15       |        8.(3)       |
|prepareAppointmentInfos |     69     |       68.77       |        29.8        |
*PF GAS T - partt from generateAppointmentSettings time.

|      function/case name      |PF PAI T*, %|PF GAS T, %| amount of time, % | amount of time, ms |
|:----------------------------:|:----------:|:---------:|:-----------------:|:------------------:|
|cropAppointmentsByStartDayHour|    28.64   |   19.69   |       18.27       |       8.5(3)       | !!!!!!
|     createAppointments       |    10.74   |   7.38    |        6.85       |        3.2         |
|  createGridAppointmentList   |    10.74   |   7.38    |        6.85       |        3.2         |
*PF PAI T - partt from prepareAppointmentInfos time.
