#iRobot High-Level Instruction Definition

OP: iRobot Open Interface Document

## DEMO
Play the built-in demo. Refer to OP, p. 8.

To play demo 0 to cover the floor:

	DEMO 0
	
## IF

There are several pre-defined operators in `HLProgram`:

    EQUAL
    NOT_EQUAL
    GREATER_THAN
    GREATER_THAN_OR_EQUAL
    LESS_THAN
    LESS_THAN_OR_EQUAL

Example

	IF CLIFF,EQUAL,1
		INS
		INS
	ELSE
		INS
		INS
	END IF


## LOOP

	LOOP BUMP, NOT_EQUAL, 1
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
