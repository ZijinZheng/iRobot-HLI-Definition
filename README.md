#iRobot High-Level Instruction Defination

## IF

    IF CLIFF,EQUAL,1
        INS
        INS
    ELSE
       INS
       INS
    END IF


## LOOP

    LOOP BUMP, NOT_EQUAL,1
        INS
        INS
    END LOOP


## DELAY

    DELAY 1000

Example: Keep driving forward until a wall is met 

    LOOP BUMP, NOT_EQUAL, 1
    	DRIVE 300, STRAIGHT
    	DELAY 300
    END LOOP
    DRIVE 0, STRAIGHT
