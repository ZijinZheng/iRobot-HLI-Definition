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

	// Cliff = 2, EQUAL = 0
	IF 2,0,1
		INS
		INS
	ELSE
		INS
		INS
	END_IF


## LOOP

	// Bump = 0, NPT_EQUAL = 1
	LOOP 0, 1, 1
		INS
		INS
	END_LOOP


## DELAY

	DELAY 1000

Example: Keep driving forward until a wall is met 

	// Bump = 0, NPT_EQUAL = 1
	LOOP 0, 1, 1
		// SRAIGHT = 32768
		DRIVE 300, 32768
		DELAY 300
	END_LOOP
	DRIVE 0, 32768
