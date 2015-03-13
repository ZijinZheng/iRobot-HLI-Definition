#iRobot High-Level Instruction Definition

OP: iRobot Open Interface Document

## Navigation

### FORWARD

	FORWARD [distance], [duration]
	
Example

	// FORWARD 300mm in 20s
	FORWARD 300, 20
	
### BACKWARD

The same as FORWARD.

### LEFT

	LEFT [angle]
	
Example
	
	// Left rotate 90 degree
	LEFT 90
	
### RIGHT

The same as LEFT.
	

## DEMO
Play the built-in demo. Refer to OP, p. 8.

To play demo 0 to cover the floor:

	DEMO 0
	
## IF

IF contains `IF`, `ELSE` and `END_IF`. `ELSE` part cannot be ommited, even though there is no sub-program inside it.

	IF [condition]
		[subprogram]
	ELSE
		[subprogram]
	END_IF

[subprogram]
	A HLProgram. 
	
[condition]
	
	[sensor], [operator], [value]
	
[operator]

They are defined in `HLProgram`:

	EQUAL                 0
	NOT_EQUAL             1
	GREATER_THAN          2
	GREATER_THAN_OR_EQUAL 3
	LESS_THAN             4
	LESS_THAN_OR_EQUAL    5

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

	// Bump = 0, NOT_EQUAL = 1
	LOOP 0, 1, 1
		// SRAIGHT = 32768
		DRIVE 300, 32768
		DELAY 300
	END_LOOP
	DRIVE 0, 32768
