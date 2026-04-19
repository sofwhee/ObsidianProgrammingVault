
StartExecution - Start a whole state machine (not task activity)
StopExecution - Stop a whole state machine

GetActivityTask - Retrieve a scheduled task

A developer builds an inventory application that runs on employee tablets. The tablet application serves as an activity worker for an AWS Step Functions state machine. The application must retrieve a scheduled task, periodically report on task progress, and report task completion or task failure.


## Example

Which Step Functions API actions does the tablet application need to make?

- The activity worker must first call the **CreateActivity** API action to obtain the activity Amazon Resource Name (ARN). 
- The **GetActivityTask** API action then retrieves a scheduled task. 
- The **SendTaskHeartbeat** API action periodically reports on task progress. 
- The **SendTaskFailure or SendTaskSuccess** API actions report success or failure.